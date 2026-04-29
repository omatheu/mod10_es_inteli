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
| 4. Referências + Coordenação | 1 | Matheus Santos + Pedro Henrique | Consolidar fontes, normas e costurar o doc final |

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

## Frente 4 — Referências + Coordenação [1 pt + costura]

**Dupla:** Matheus Santos + Pedro Henrique
**Pergunta-guia:** "Que evidências e normas sustentam o que estamos descrevendo?"

### 4.1 Evidências do parceiro
- Consolidar todas as fontes do parceiro: [tapi.md](tapi.md), transcrições de reuniões em [notes/](notes/), screenshots, e-mails, calls.
- Catalogar cada citação/dado usado nas frentes 1, 2 e 3 com referência rastreável.

### 4.2 Normas de Engenharia
- ISO 10746 (RM-ODP) — base da Frente 1.
- IEEE 828 / ISO/IEC 12207 — gestão de configuração de software.
- Regulamentação ANAC aplicável a software de drones.
- Boas práticas de CI/CD (referenciadas nas aulas, ver [slides-prog/](slides-prog/)).

### 4.3 Coordenação e consolidação (atividade contínua)
- Garantir consistência terminológica entre as 3 frentes.
- Resolver conflitos quando duas frentes descrevem o mesmo processo de formas diferentes.
- Montar o documento final com formatação coesa.
- Conduzir as syncs do time (ritual diário/duas vezes na semana).

**Entregável:** seção de Referências + documento Sprint 1 consolidado.

---

## Cronograma sugerido (1 semana)

| Dia | Frente 1 | Frente 2 | Frente 3 | Frente 4 |
|---|---|---|---|---|
| 1 | Coletar dados de funcionalidades atuais | Listar testes existentes | Levantar ferramentas atuais | Indexar fontes + normas |
| 2 | NFRs atuais + ciclo de controle | Mapear fluxo de testes hoje | Mapear deployment atual | Validar consistência inicial |
| 3 | Documentar viewpoints ISO 10746 | Rastreabilidade atual | Indicadores hoje + expectativas | Costura parcial |
| 4 | Revisão cruzada com Frentes 2 e 3 | Revisão cruzada | Revisão cruzada | Revisão geral |
| 5 | Ajustes finais | Ajustes finais | Ajustes finais | Consolidação e entrega |

---

## Princípios para todas as frentes

1. **Descreva o que existe, não o que deveria existir.** Cada afirmação sobre o AS-IS deve ter uma evidência (citação de reunião, doc do parceiro, observação direta).
2. **Identifique gaps sem propor solução.** Anote "hoje não há X" ou "Y é manual" — a solução vem nas próximas sprints.
3. **Distinga registro × evidência × expectativa.**
   - **Registro:** algo que está documentado no parceiro (Jira, Confluence, etc.).
   - **Evidência:** algo observado/relatado em reunião.
   - **Expectativa:** algo que o parceiro disse que quer/espera (vai virar requisito futuro).
4. **Citar fonte sempre.** Toda afirmação no documento deve linkar para a evidência em [notes/](notes/) ou [tapi.md](tapi.md).

---

## Próximos passos

1. Validar duplas no grupo do WhatsApp.
2. Abrir 4 issues/épicos no board com as sub-tasks listadas.
3. Agendar 1 sync de kickoff com o parceiro Jacto para preencher gaps de informação que as Frentes 1–3 vão identificar logo no início.
