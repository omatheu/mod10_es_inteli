# Possíveis formas de automatizar a criação de tarefas no GitLab

> Contexto: temos a organização do Sprint 1 documentada em [SPRINT-1-ORGANIZACAO.md](SPRINT-1-ORGANIZACAO.md) e queremos popular o board/kanban do GitLab com as 4 epics + sub-issues sem digitar tudo manualmente.

## Opção 1 — MCP do GitLab (mais direto)

Há um conector GitLab disponível no Claude. Autentica uma vez (`/connect` ou pela UI do Claude) e o assistente pode criar as issues, labels e milestone do Sprint 1 direto no projeto, sem abrir o GitLab. Funciona bem para criação one-shot.

**Prós:**
- Sem instalação local
- Sem script para manter
- Conversacional (peço ajustes e aplica na hora)

**Contras:**
- Depende de autorização do MCP
- Se mudar de projeto/grupo, precisa reautenticar
- Não fica versionado no repo (não é reproduzível pelo time)

---

## Opção 2 — `glab` CLI + script bash

Instalar o [`glab`](https://gitlab.com/gitlab-org/cli) (CLI oficial do GitLab), rodar `glab auth login` uma vez, e gerar um script `.sh` que cria as 4 epics + sub-issues com labels (`frente-1`, `frente-2`, `assignee:vinicius`, etc.) e adiciona ao board.

**Prós:**
- Script fica versionado no repo do projeto, qualquer membro do time pode rerodar
- Reproduzível (útil se precisar recriar em outro projeto/grupo)
- `glab` lida bem com epics, labels, assignees, milestones e colunas do board

**Contras:**
- Requer instalar `glab` e autenticar localmente
- Manutenção do script se o escopo mudar muito

**Comando exemplo:**
```bash
glab issue create \
  --title "Frente 1.1 — Funcionalidades (AS-IS)" \
  --description "$(cat docs/frente-1-1.md)" \
  --label "sprint-1,frente-1,as-is" \
  --assignee "vinicius.ibiapina,thiago.gomes" \
  --milestone "Sprint 1"
```

---

## Opção 3 — Import CSV nativo do GitLab

GitLab tem import de issues por CSV (Issues → ⋯ → Import CSV). Geramos o CSV a partir do `SPRINT-1-ORGANIZACAO.md` e subimos pela UI.

**Prós:**
- Zero dependência (sem CLI, sem MCP)
- Funciona com qualquer permissão de Reporter+
- Gera arquivo simples e auditável

**Contras:**
- Upload manual na UI
- CSV só cria issues simples — relação parent/child de epic precisa ser feita depois (ou via API)
- Não cria labels/milestone automaticamente; precisam existir antes

**Formato esperado:**
```csv
title,description,due_date,milestone,labels
"Frente 1.1 — Funcionalidades (AS-IS)","Mapear funcionalidades atuais...",2026-05-06,"Sprint 1","frente-1,as-is"
```

---

## Recomendação

Para 4 epics + ~14 sub-issues: **Opção 2 (glab + script)**.

Motivos:
- Script fica versionado no repo, qualquer um do time pode rerodar
- `glab` lida bem com epics, labels, assignees, milestones e board columns
- Não depende de auth MCP que pode expirar
- Serve de template para Sprints 2–5

---

## Inputs necessários para gerar o script da Opção 2

1. URL/path do projeto no GitLab (ex.: `inteli-t13/jacto-drones-os`)
2. Os usernames GitLab das 8 pessoas (não os nomes do WhatsApp):
   - Matheus Santos → `?`
   - Daniel Augusto → `?`
   - Thiago Volcati → `?`
   - João Souza → `?`
   - Lucas Nunes → `?`
   - Thiago Gomes → `?`
   - Vinicius Ibiapina → `?`
   - Pedro Henrique → `?`
3. Se já existe board de Sprint, ou se criamos labels de status (`Sprint 1::Backlog`, `::Doing`, `::Done`)
4. Se quer milestone "Sprint 1" com data de fim

Com esses 4 itens, dá para entregar `create-sprint1-issues.sh` pronto para rodar.

---

## Comparativo rápido

| Critério | MCP | glab + script | CSV |
|---|---|---|---|
| Setup | Auth no Claude | Instalar `glab` + login | Nenhum |
| Reproduzível pelo time | ❌ | ✅ | ⚠️ (precisa do CSV) |
| Versionável no repo | ❌ | ✅ | ✅ |
| Lida com epics/parent-child | ✅ | ✅ | ❌ (manual depois) |
| Custo de manutenção | Zero | Médio | Baixo |
| Reusável p/ próximas sprints | ⚠️ | ✅ | ✅ |
