# TODO (uso interno — Claude Code)

Este arquivo é mantido pelo Claude Code entre sessões, não é um artefato voltado ao usuário. Regras de manutenção:
- Sempre que uma tarefa for concluída nesta conversa/sessão, marque-a aqui (`- [x]`) antes de encerrar.
- Sempre que uma tarefa nova surgir (pedida pelo usuário ou identificada durante o trabalho), adicione-a na seção correspondente.
- Cobre o ciclo de vida completo do projeto, do levantamento de requisitos ao deploy — não apenas a implementação.
- Referências RF/RN apontam para `REQUIREMENTS.md`; convenções de banco estão em `docs/database-schema.md`.

## 0. Requisitos e documentação
- [x] Criar repositório GitHub (privado) e configurar remoto
- [x] Adicionar `.gitignore` (Node/JavaScript)
- [x] Adicionar `README.md`
- [x] Adicionar `LICENSE` (MIT)
- [x] Renomear `requisitos.md` para `REQUIREMENTS.md`
- [x] Remover trailer de co-autoria do histórico de commits
- [x] Adicionar expansão futura (Vestuário, TI) ao contexto
- [x] Adicionar condição de item (novo/em_manutencao/danificado) e fluxo de reparo
- [x] Corrigir notificações de atraso/estoque mínimo para supervisão (relatório semanal em vez de notificação imediata)
- [x] Adicionar edição de perfil e configuração do relatório semanal (RF06)
- [x] Preencher Modelo de Dados (rascunho) com diagrama ER conceitual (Seção 7)
- [x] Criar `docs/database-schema.md` (schema técnico detalhado, convenções snake_case)
- [x] Substituir "Referências e Anexos" por Cronograma (Seção 11)
- [x] Remover estimativas de tempo do cronograma, manter apenas ordem
- [x] Adicionar etapa de Design de UI/UX ao cronograma
- [x] Mesclar colunas Ordem/Fase na linha do Marco de Teste do MVP
- [x] Criar `CLAUDE.md`
- [x] Criar `TODO.md` e apontar `CLAUDE.md` para ele
- [ ] Definir e preencher uma nova seção "Referências e Anexos" (se necessário)

## 1. Preparação
- [ ] Configurar CI/CD
- [ ] Configurar ambiente de desenvolvimento (Ubuntu 24.04 LTS local)
- [ ] Criar schema inicial do banco de dados (ver `docs/database-schema.md`)
- [ ] Scaffolding do backend (Node.js)
- [ ] Scaffolding do frontend (React)
- [ ] Implementar autenticação com hash de senha
- [ ] Configurar HTTPS

## 2. Design de UI/UX
- [ ] Wireframes das telas principais: login, cadastro de itens, consulta, retirada/devolução
- [ ] Protótipo navegável
- [ ] Apresentar e validar protótipo com stakeholders (coordenação/supervisores do SENAI)

## 3. MVP
- [ ] RF06 — cadastro de usuários
- [ ] RF01 — cadastro de itens
- [ ] RF04 — consulta de itens
- [ ] RF02 simplificado — retirada e devolução sem validação das regras de negócio (apenas usuário atual e último a devolver)
- [ ] Interface responsiva (mobile/tablet/desktop)

## Marco: Teste do MVP
- [ ] Teste de aceitação com piloto reduzido (uma turma/oficina)
- [ ] Validar responsividade nos três dispositivos
- [ ] Coletar feedback e aplicar correções antes de avançar

## 4. Regras de negócio
- [ ] RN1/RN2 — prazos de devolução por turno/perfil
- [ ] RF02 completo — estados de movimentação (pendente/aprovada/negada/disponível/atrasada)
- [ ] RN6 — aprovação por docente/supervisor conforme eixo
- [ ] Fluxo de item danificado/reparo (RF02)
- [ ] RF03 — alertas de estoque mínimo
- [ ] RN3 — notificações de atraso
- [ ] RF07 — pedido de compra

## 5. Relatórios e configuração
- [ ] RF05 — relatórios (histórico, itens mais/menos usados, inventário, movimentação por usuário)
- [ ] RF05 — exportação para PDF/Excel
- [ ] RF05 — relatório semanal
- [ ] RF06 — edição de perfil (todo usuário)
- [ ] RF06 — configuração do relatório semanal pelo supervisor (dia/horário, toggles)

## 6. Não funcionais e hardening
- [ ] Log de auditoria
- [ ] Backup diário automatizado
- [ ] Teste de restauração de backup
- [ ] Proteção contra SQL injection, XSS e CSRF
- [ ] Teste de carga (30–50 usuários simultâneos)

## 7. Homologação e lançamento piloto
- [ ] Deploy em ambiente de homologação
- [ ] Teste de aceite final (UAT) com docentes e supervisores
- [ ] Treinamento de usuários
- [ ] Deploy em produção (VPS)
- [ ] Acompanhamento pós-lançamento (hipercare)
