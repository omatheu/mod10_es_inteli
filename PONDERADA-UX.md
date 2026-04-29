# DESIGN_OPS.md: Plano Operacional de DesignOps

## 1. Introdução e Objetivo

DesignOps é, na prática, o DevOps do design: a disciplina que organiza pessoas, processos e ferramentas para que decisões visuais cheguem ao código sem atrito. Segundo o Nielsen Norman Group, DesignOps tem três eixos (como trabalhamos juntos, como entregamos trabalho e como geramos impacto) e é exatamente essa estrutura que orienta este documento.

No contexto do nosso projeto (uma pipeline de qualidade de código de software para os drones da Jacto), o papel do DesignOps é específico: usar as ferramentas de design para minimizar o esforço do usuário em adaptar o ativo atual da Jacto ao Horizonte Digital que estamos propondo com essa pipeline. Em outras palavras, o design entra como redutor de fricção de adoção — é ele que faz com que a transição do fluxo legado para o novo ambiente seja perceptivelmente leve, e não um custo extra empurrado para quem já opera o sistema. Dois desdobramentos práticos sustentam isso: garantir que protótipos do Figma virem componentes reais no frontend sem retrabalho e que mudanças visuais não quebrem builds já validados no pipeline de CI/CD.

> Referência: Nielsen Norman Group — [Design Operations 101](https://www.nngroup.com/articles/design-operations-101/)

_Responsável: [Nome do Aluno]_

## 2. Como Trabalhamos Juntos (Pessoas)

### Papéis

| Papel | Responsabilidade |
|---|---|
| UX/UI Lead | Mantém o Design System no Figma e valida protótipos antes do handover |
| Dev Lead | Consome os tokens de design e garante implementação fiel |
| DevOps Engineer | Automatiza a publicação do Storybook e os testes de regressão visual |

### Rituais

Design Sync semanal (30 min): alinha o que está em design com o que está em desenvolvimento. Handover via Figma + Issue no GitLab: toda mudança de interface abre uma issue descrevendo o que muda e por quê. Review de MR com screenshot: antes de aprovar um merge request com mudanças visuais, o revisor compara o layout com o protótipo aprovado.

Essa estrutura segue o modelo de colaboração contínua proposto pelo Figma Design Systems Handbook, que recomenda reduzir reuniões longas em favor de artefatos assíncronos bem documentados.

> Referência: Figma — [Design Systems Handbook](https://www.designbetter.co/design-systems-handbook)

_Responsável: [Nome do Aluno]_

## 3. Como o Trabalho é Feito (Processos e Ferramentas)

### Ferramentas

As principais ferramentas do fluxo são: Figma (protótipos e componentes), Git com tokens em JSON exportados via plugin Style Dictionary, Storybook para documentação de componentes e GitLab CI para a esteira de automação.

### Fluxo Design para Código

```
Figma (protótipo aprovado)
  ↓
Export de Design Tokens (JSON via Style Dictionary)
  ↓
Commit na branch de feature
  ↓
GitLab CI: lint de CSS + build do Storybook
  ↓
MR com screenshot de comparação
  ↓
Merge na main → publicação automática do Storybook
```

Os Design Tokens (cores, tipografia, espaçamentos) vivem em `src/tokens/` como variáveis CSS e são a fonte única de verdade entre design e código. Isso garante que o Figma e o frontend falem a mesma língua.

> Referência: Salesforce — [Lightning Design System: Design Tokens](https://www.lightningdesignsystem.com/design-tokens/)

_Responsável: [Nome do Aluno]_

## 4. Como Geramos Impacto (Mensuração e Definition of Done)

Uma entrega de design só entra no pipeline se passar pelos critérios abaixo.

### Definition of Done (DoD) — Design

- [ ] Protótipo revisado tecnicamente pelo Dev Lead
- [ ] Tokens de design atualizados e commitados
- [ ] Assets exportados em SVG/WebP otimizados
- [ ] Acessibilidade básica verificada (contraste WCAG AA)
- [ ] Storybook atualizado com o novo componente

### Métricas acompanhadas

Consistência visual é medida por testes de regressão visual (BackstopJS). O cycle time do handover registra o tempo entre aprovação do protótipo e o merge na main. A cobertura do Design System acompanha a porcentagem de telas implementadas com componentes do Storybook, com meta acima de 80%.

Acompanhamos essas métricas no dashboard operacional do projeto, integrado ao GitLab.

> Referência: Medium Designer Hangout — [Measuring Design Ops](https://medium.com/designer-hangout/what-is-design-operations-and-why-should-you-care-b72f02b477761)

_Responsável: [Nome do Aluno]_

## 5. Integração com a Esteira de CI/CD

Este é o ponto central do DesignOps no projeto: onde o design vira automação verificável. A ideia é simples — qualquer mudança visual que não passe por validação automatizada não entra na `main`. O pipeline de CI/CD é o portão de qualidade do design, não só do código.

### Estrutura do pipeline

O `.gitlab-ci.yml` define quatro estágios sequenciais para o fluxo de design:

```yaml
stages:
  - lint
  - build
  - visual-test
  - deploy-storybook

lint-css:
  stage: lint
  script: npx stylelint "src/**/*.css"

build-storybook:
  stage: build
  script: npm run build-storybook

visual-regression:
  stage: visual-test
  script: npx backstop test
  allow_failure: false

deploy-storybook:
  stage: deploy-storybook
  script: npx storybook-deployer
  only:
    - main
```

### O que cada etapa faz e por que existe

**Lint de CSS (`lint-css`):** O stylelint verifica se o CSS commitado está dentro dos padrões definidos pelos tokens do projeto. Se um dev hardcodear uma cor (`#FF0000` em vez de `var(--color-danger)`), o pipeline falha aqui. Isso previne que decisões de design tomadas no Figma sejam ignoradas silenciosamente no código. A regra é simples: nenhum valor visual entra no projeto sem passar pelo token correspondente.

**Build do Storybook (`build-storybook`):** Compila todos os componentes documentados. Se um componente quebra durante o build, o problema é detectado antes de qualquer deploy. Essa etapa também valida que o componente está devidamente isolado e documentado, não só funcionando dentro de uma tela específica.

**Testes de regressão visual (`visual-regression`):** O BackstopJS tira screenshots dos componentes do Storybook e compara pixel a pixel com um baseline salvo no repositório. Se houver diferença acima do threshold configurado, o pipeline falha com `allow_failure: false`, bloqueando o merge. Isso é o equivalente visual de um teste unitário: garante que uma mudança de CSS não quebrou silenciosamente outro componente. O baseline é atualizado intencionalmente pelo time quando uma mudança visual é aprovada, nunca de forma automática.

**Deploy do Storybook (`deploy-storybook`):** Só roda em merges na `main`. Publica o guia de componentes atualizado em um ambiente acessível a todos (devs, designers e stakeholders). Isso elimina a pergunta "qual versão do componente está em produção?" porque a resposta está sempre disponível e atualizada.

### Fluxo de aprovação de mudança visual

Quando uma mudança de interface é proposta, o caminho é: o designer atualiza o protótipo no Figma e abre uma issue no GitLab descrevendo o que muda. O dev implementa na branch de feature, commita os tokens atualizados se necessário, e abre um MR com um screenshot do antes e depois. O pipeline roda automaticamente. Se passar, o UX/UI Lead revisa o MR visualmente e aprova. Só então o merge acontece e o Storybook é publicado.

Esse fluxo garante rastreabilidade completa: toda decisão visual tem uma issue de origem, um MR com evidência de implementação e um pipeline que confirma que nada quebrou.

> Referências:
> BackstopJS — [Visual Regression Testing](https://github.com/garris/BackstopJS)
> Storybook — [Automate with CI](https://storybook.js.org/docs/react/workflows/continuous-integration)
> Stylelint — [Getting Started](https://stylelint.io/user-guide/get-started)

_Responsável: [Nome do Aluno]_

## 6. Referências Gerais

1. Nielsen Norman Group — https://www.nngroup.com/articles/design-operations-101/
2. Medium Designer Hangout — https://medium.com/designer-hangout/what-is-design-operations-and-why-should-you-care-b72f02b477761
3. Figma Design Systems Handbook — https://www.designbetter.co/design-systems-handbook
4. Salesforce Lightning Design Tokens — https://www.lightningdesignsystem.com/design-tokens/
5. BackstopJS — https://github.com/garris/BackstopJS
6. Storybook CI — https://storybook.js.org/docs/react/workflows/continuous-integration
7. Stylelint — https://stylelint.io/user-guide/get-started
