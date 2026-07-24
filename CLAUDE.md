# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository currently contains **planning/requirements documentation only** — there is no application code, package manifest, or build tooling yet. Do not assume a backend/frontend scaffold exists; check before running build/lint/test commands, since none are defined at this stage.

## Task tracking — read and update TODO.md every session

`TODO.md` is an internal task log (not user-facing) that tracks the project's full lifecycle, from requirements through deployment. It is the working memory across sessions:
- At the start of a session, check it to see what's already done and what's pending.
- Whenever a task gets completed in this repo, check it off there before finishing.
- Whenever new work is requested or discovered, add it there in the matching phase (or a new one).

## Repository structure

- `REQUIREMENTS.md` — the requirements document (SRS), written in Portuguese, and the source of truth for scope and business rules. It is organized in numbered sections (Visão Geral, Objetivos, Contexto e Usuários, Requisitos Funcionais RF01–RF07, Requisitos Não Funcionais, Regras de Negócio RN1–RN6, Modelo de Dados, Integrações, Restrições Técnicas, Critérios de Aceite MVP, Cronograma).
- `docs/database-schema.md` — the technical, column-level database schema (types, keys, indexes). Keep this file, not `REQUIREMENTS.md`, in sync with any real migrations/ORM schema once code exists; `REQUIREMENTS.md` §7 only holds a conceptual ER diagram and links here.
- `README.md` — short project overview, links to `REQUIREMENTS.md`.

Project documentation is written in Portuguese (the audience is SENAI staff/students). Keep documentation edits in Portuguese for consistency.

## Domain model (from REQUIREMENTS.md)

Inventfy is a tool/parts inventory and loan-tracking system for SENAI workshops (initially eletroeletrônica and metalmecânica; vestuário and TI are future scope — do not build for them yet).

- **Three user roles**: `aluno` (requests withdrawals only), `instrutor`/`docente` (these two terms are used interchangeably throughout the docs), `supervisor` (full access, manages users, approves, generates reports).
- **Eixo-scoped stock** (RN5): each workshop/eixo has its own stock. Alunos only see their own eixo's stock; docentes and supervisores can access any eixo's stock.
- **Approval routing** (RN6): a docente can withdraw items from their own eixo without approval; withdrawing from another eixo requires approval from *that eixo's* supervisor.
- **Item condition**: items have a `condicao` (novo/em_manutencao/danificado) field, but only `ferramenta_equipamento` and `componente_reutilizavel` types carry it — `insumo` (consumables) never has a condition.
- **Notification routing is intentionally asymmetric** — this was refined over several rounds and should not be "simplified" without re-reading RN3/RF02/RF03: the supervisor only receives *instant* notifications for (1) pedido de compra e-mails (RF07) and (2) reminders about their own overdue loans (RN3). Late returns by aluno/docente, low-stock thresholds, and damaged items are surfaced to the supervisor only in the weekly report (RF05/RF06); docentes still get those as instant alerts.
- **Weekly report** (RF05/RF06): configurable by each supervisor (day/time, on/off toggles per content type) — it replaces what would otherwise be several real-time notifications.

## Database naming conventions (docs/database-schema.md)

Already decided — follow these once migrations/ORM models are created: tables in snake_case, plural (`usuarios`, `itens`); columns in snake_case, singular; primary key `id` (bigserial); every table has `created_at`, mutable tables also have `updated_at`; `logs_auditoria` is append-only and has no `updated_at`.

## Planned tech stack (Restrições Técnicas, §9)

- Backend: Node.js
- Frontend: React — single responsive interface (mobile/tablet/desktop), not separate mobile/desktop codebases
- Database: PostgreSQL

## Build order (Cronograma, §11)

The documented sequence is: Preparação (repo/CI/CD/schema/scaffolding) → Design de UI/UX (wireframes validated with SENAI stakeholders *before* frontend implementation) → MVP → **Marco: Teste do MVP** (pilot acceptance test — a checkpoint before deepening scope) → Regras de negócio completas → Relatórios e configuração → Não funcionais e hardening → Homologação e lançamento piloto.

Note the MVP is deliberately minimal (Critérios de Aceite, §10): user cadastro, item cadastro, consulta, and simplified retirada/devolução **without** business-rule validation (only current user + last returner tracked). Full business rules (deadlines, approval flows, alerts, notifications) are explicitly a later phase — don't front-load them into MVP work.
