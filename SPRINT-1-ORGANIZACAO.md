# Sprint 1 — Organização de Tarefas

> **Foco do Sprint 1:** entender o **fluxo atual (AS-IS)** de desenvolvimento de software da Jacto Drones. Não é desenho de solução — é diagnóstico, levantamento e documentação do estado atual, com evidências do parceiro.

## Time (8 pessoas)

1. Matheus Santos
2. Daniel Augusto
3. Thiago Volcati
4. João Souza
5. Lucas Nunes
6. Thiago Gomes
7. Vinicius Ibiapina
8. Pedro Henrique (~ph)

## Visão geral das frentes

| Frente | Pontos | Dupla sugerida | Natureza |
|---|---|---|---|
| 1. Arquitetura Produto (ISO 10746) | 3 | Vinicius Ibiapina + Thiago Gomes | Mapear arquitetura **atual** do produto Jacto |
| 2. Configuração da Esteira de Sistemas | 3 | Daniel Augusto + Lucas Nunes | Levantar como a esteira **funciona hoje** |
| 3. Requisitos SCM (Registros, Evidências, Expectativas) | 3 | Thiago Volcati + João Souza | Coletar evidências e expectativas do parceiro |
| 4. Automação de contexto de IA + fluxo de trabalho | 1 | Matheus Santos + Pedro Henrique | Tooling transversal que acelera as outras 3 frentes |

**Total:** 10 pontos / 8 pessoas (4 duplas).

---

## Frente 1 — Arquitetura Produto (ISO 10746) [3 pts]

**Dupla:** Vinicius Ibiapina + Thiago Gomes
**Pergunta-guia:** "Como o produto/software da Jacto Drones está arquitetado **hoje**?"

### 1.1 Funcionalidades (AS-IS)
- Mapear quais funcionalidades existem hoje no software da Jacto (firmware embarcado, plataforma de serviços, plataforma de gestão/dados).
- Identificar fronteiras entre os 3 domínios e o que cada um entrega.
- Fonte primária: [tapi.md](tapi.md), [notes/notes-about-problem-mod.md](notes/notes-about-problem-mod.md), reuniões com o parceiro.

### 1.2 Aspectos não funcionais (AS-IS)
- Levantar requisitos não funcionais que **já existem na operação atual**: rastreabilidade ANAC, segurança de dados (Product Dev e Customer Data), performance, confiabilidade.
- Documentar tolerâncias atuais (ex.: "erros são pouquíssimo toleráveis", "tempo de simulação pré-vôo é métrica-chave").

### 1.3 Controle em Malha Fechada dos Requisitos (AS-IS)
- Descrever como hoje a Jacto **fecha o ciclo** entre requisito → desenvolvimento → teste → log de vôo → backlog novamente.
- Identificar onde o ciclo é manual, onde tem gap, onde tem retrabalho.

**Entregável:** seção do documento descrevendo a arquitetura atual sob os viewpoints da ISO 10746/RM-ODP.

---

## Frente 2 — Configuração da Esteira de Sistemas [3 pts]

**Dupla:** Daniel Augusto + Lucas Nunes
**Pergunta-guia:** "Como o pipeline/esteira de desenvolvimento da Jacto opera **hoje**?"

### 2.1 Testes Funcionais (AS-IS)
- Quais testes funcionais a Jacto executa hoje? (unit, integração, simulação MATLAB/Simulink, simulação PX4, ensaio de vôo real)
- Em que pontos do fluxo cada tipo é executado? Quem executa? O que disparou cada um?
- Documentar: "hoje pulam algumas etapas de teste para conseguir entregar as demandas necessárias" (ver [notes-about-problem-mod.md:40](notes/notes-about-problem-mod.md#L40)).

### 2.2 Testes Não Funcionais (AS-IS)
- Quais testes não funcionais existem hoje? (performance, segurança, confiabilidade)
- Há SAST/DAST? Há análise estática? Como segurança de dados é validada hoje?

### 2.3 Rastreabilidade das modificações dos Itens de SC (AS-IS)
- Como hoje uma modificação de software é rastreada? (Git/GitHub, branching, vínculo commit↔task em Jira/Trello)
- Como auditoria ANAC é suportada hoje?
- Onde a rastreabilidade quebra?

**Entregável:** seção descrevendo a esteira atual de testes e versionamento, com fluxograma do pipeline real.

---

## Frente 3 — Requisitos SCM (Registros, Evidências, Expectativas) [3 pts]

**Dupla:** Thiago Volcati + João Souza
**Pergunta-guia:** "Que requisitos de SCM emergem dos registros, evidências e expectativas do parceiro?"

### 3.1 Requisitos de Integração (AS-IS)
- Quais ferramentas a Jacto usa hoje? (Jira, Trello, Notion, Word, Confluence, GitHub, OneDrive, MATLAB, Simulink — ver [notes-about-problem-mod.md:86-90](notes/notes-about-problem-mod.md#L86))
- Como elas se comunicam (ou não) hoje?
- Que pontos de integração existem, quais são manuais, quais o parceiro **espera** que existam?

### 3.2 Requisitos de Deployment (AS-IS)
- Como hoje firmware é entregue ao drone? (USB, 4G, rádio, via PixHawk/ESP32)
- Como software de plataforma é entregue ao cliente?
- Como release é gerenciado hoje (Esteira Controle → Esteira Firmware → Release → Ensaio de vôo, ver [notes-about-problem-mod.md:50-56](notes/notes-about-problem-mod.md#L50))?

### 3.3 Indicadores e Rastreabilidade (AS-IS)
- Que métricas a Jacto **mede hoje**? ("Somente olham padrões e se está estourando os limites" — [notes-about-problem-mod.md:42](notes/notes-about-problem-mod.md#L42))
- O que **não mede e gostaria de medir**? (cycle time, throughput, falhas no software local, etc.)
- Como rastreabilidade requisito ↔ código ↔ teste ↔ release funciona hoje?

**Entregável:** lista estruturada de requisitos SCM AS-IS + expectativas explícitas do parceiro, com evidência (citação/referência) para cada.

---

## Frente 4 — Automação de contexto de IA + fluxo de trabalho [1 pt]

**Dupla:** Matheus Santos + Pedro Henrique
**Pergunta-guia:** "Como reduzimos atrito do time e damos contexto consistente para IA acelerar o trabalho das outras frentes?"

> Esta frente é **transversal**: o output dela é tooling/infra que as Frentes 1, 2 e 3 consomem ao longo da semana. Não produz seção do artefato final por si só, mas ergue o piso de produtividade do time.

### 4.1 Automação do board GitLab (criação de issues)
- Implementar a **Opção 2** documentada em [POSSIVEIS-FORMAS-DE-AUTOMATIZAR-A-ORGANIZACAO-DE-TAREFAS.md](POSSIVEIS-FORMAS-DE-AUTOMATIZAR-A-ORGANIZACAO-DE-TAREFAS.md): script `glab` que cria as 4 epics + sub-issues do Sprint 1 com labels, milestone e assignees.
- Versionar o script no repo (`scripts/create-sprint1-issues.sh`) para reuso nas Sprints 2–5.
- Coletar os 4 inputs listados no doc (URL do projeto, usernames GitLab, board, milestone).

### 4.2 Contexto compartilhado de IA para o time
- Criar um `CLAUDE.md` (ou equivalente para outras IAs) na raiz do repo com o contexto destilado: sumário do projeto Jacto, glossário (drone, firmware, controle, MATLAB, PX4, ANAC), links para [tapi.md](tapi.md) e [notes/](notes/), e princípios do Sprint 1 (AS-IS, evidência sempre, etc.).
- Padronizar uma estrutura `evidencias/` ou anotações que qualquer membro pode citar com link rastreável (`notes/<frente>/<data>-<topico>.md`), garantindo que a regra "citar fonte sempre" funcione na prática.
- Documentar 2–3 prompts/templates úteis para as outras frentes (ex.: "extrair requisitos de uma transcrição", "transformar nota em registro estruturado").

### 4.3 Templates e helpers para padronização do artefato
- Criar template Markdown para cada seção do artefato Sprint 1 (Frentes 1–3) com headers, checklist do que preencher e onde citar fonte. Cada dupla preenche o seu, garantindo consistência sem ter um "consolidador" centralizado.
- Definir convenção de citação de evidências (`[E#](notes/...)`) e de expectativas do parceiro (`[Exp#]`) para o documento final ficar coeso.
- Validar a junção dos templates ao final da semana (revisão final, não autoria).

**Entregável:** scripts e templates versionados no repo + `CLAUDE.md` atualizado. **Não** entrega seção do artefato Sprint 1 — apenas habilita as outras 3 frentes a entregarem com menos atrito e a seção "Referências" do artefato a ser composta por todos.

---

## Cronograma sugerido (1 semana)

| Dia | Frente 1 | Frente 2 | Frente 3 | Frente 4 |
|---|---|---|---|---|
| 1 | Coletar dados de funcionalidades atuais | Listar testes existentes | Levantar ferramentas atuais | Script glab + CLAUDE.md inicial |
| 2 | NFRs atuais + ciclo de controle | Mapear fluxo de testes hoje | Mapear deployment atual | Templates de seção das Frentes 1–3 |
| 3 | Documentar viewpoints ISO 10746 | Rastreabilidade atual | Indicadores hoje + expectativas | Convenção de citação + estrutura `evidencias/` |
| 4 | Revisão cruzada com Frentes 2 e 3 | Revisão cruzada | Revisão cruzada | Suporte às frentes (ajustes de tooling) |
| 5 | Ajustes finais | Ajustes finais | Ajustes finais | Revisão da junção + checagem de citações |

---

## Princípios para todas as frentes

1. **Descreva o que existe, não o que deveria existir.** Cada afirmação sobre o AS-IS deve ter uma evidência (citação de reunião, doc do parceiro, observação direta).
2. **Identifique gaps sem propor solução.** Anote "hoje não há X" ou "Y é manual" — a solução vem nas próximas sprints.
3. **Distinga registro × evidência × expectativa.**
   - **Registro:** algo que está documentado no parceiro (Jira, Confluence, etc.).
   - **Evidência:** algo observado/relatado em reunião.
   - **Expectativa:** algo que o parceiro disse que quer/espera (vai virar requisito futuro).
4. **Citar fonte sempre.** Toda afirmação no documento deve linkar para a evidência em [notes/](notes/) ou [tapi.md](tapi.md).
5. **Cada dupla é dona das suas referências.** Não há frente dedicada a consolidar bibliografia — a seção "Referências" [1 pt] do artefato é composta por agregação das fontes citadas em cada frente. A Frente 4 fornece o template/convenção, mas não autora a seção.

---

## Próximos passos

1. Validar duplas no grupo do WhatsApp.
2. Abrir 4 issues/épicos no board com as sub-tasks listadas.
3. Agendar 1 sync de kickoff com o parceiro Jacto para preencher gaps de informação que as Frentes 1–3 vão identificar logo no início.
