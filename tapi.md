### Cópia por Reginaldo Arakaki em 21.04.

## PROJETO PARCEIRO

### ESMD10 - Esteira ágil de produção de software


##### PROJETO:

Jacto Drones Operating System v0.
Continuous Delivery Across Drone Software Platforms

##### EMPRESA:

Jacto Máquinas Agrícolas S/A
Jacto Drones, São José dos Campos/SP.

##### BREVE DESCRIÇÃO EMPRESA / MINI BIO:

A Jacto é uma empresa brasileira fundada em 1948 e referência internacional em tecnologias para agricultura, com
presença global em mecanização agrícola, agricultura digital e soluções para operações no campo. Ao longo de sua
trajetória, a empresa construiu forte reputação em engenharia aplicada, confiabilidade operacional e inovação
tecnológica.
A iniciativa Jacto Drones representa a evolução dessa base industrial para o desenvolvimento de sistemas
autônomos físicos e plataformas digitais associadas a operações críticas. A estratégia atual busca utilizar o
mercado agrícola como ambiente inicial de escala e aprendizado operacional, ao mesmo tempo em que desenvolve
progressivamente capacidades proprietárias em autonomia embarcada, software e integração regulatória.
Nesse contexto, o objetivo de longo prazo é construir uma plataforma tecnológica de sistemas autônomos físicos
com relevância internacional, iniciando com drones agrícolas e evoluindo para aplicações multissetoriais baseadas

##### em autonomia, dados e integração sistêmica.

##### PROFESSOR ORIENTADOR: Reginaldo Arakaki

#### OVERVIEW

##### PROBLEMA:

A Jacto Drones está estruturando simultaneamente três frentes de desenvolvimento de software que suportam a
evolução de sua estratégia tecnológica:

1. Software embarcado do drone, incluindo firmware de controle de voo, percepção, navegação e interface
    cognitiva de operação.
2. Plataforma de serviços para clientes, responsável por planejamento de missão, gestão de frota, operação
    em campo e pós-vendas.
3. Plataforma de gestão e inteligência de negócios, que integra telemetria, dados operacionais e sistemas
    corporativos para geração de valor baseado em dados.
Apesar da interdependência entre essas frentes, atualmente não existe um sistema operacional de continuous
delivery unificado que organize cadência de desenvolvimento, priorização, qualidade e fluxo de entrega entre elas.
Na prática:
● as equipes utilizam ferramentas diferentes e pouco integradas (Notion, Word, Jira, Confluence e GitHub);
● rituais de engenharia e critérios de qualidade não são padronizados;
● atividades repetitivas de gestão de tarefas e documentação são executadas manualmente;
● não existe pipeline consistente de integração e entrega contínua;
● métricas essenciais de desenvolvimento (cycle time, throughput, backlog health) não são monitoradas de
forma integrada.
Essa fragmentação reduz a previsibilidade do desenvolvimento e dificulta a coordenação entre firmware,
plataformas digitais e sistemas de dados — um fator crítico para uma organização que busca desenvolver
arquitetura proprietária de autonomia embarcada e sistemas autônomos físicos.

##### OBJETIVO:

Desenvolver um protótipo funcional de um Operating System de continuous delivery para software de drones (OS
v0.1).


Esse sistema operacional deverá:
● estruturar um workflow unificado de desenvolvimento para firmware, plataformas digitais e sistemas de
dados;
● automatizar atividades recorrentes de gestão de tarefas, rituais e documentação;
● estabelecer critérios padronizados de qualidade e Definition of Done;
● implementar um pipeline básico de integração e entrega contínua (CI/CD);
● disponibilizar um dashboard operacional com métricas de desenvolvimento.
Como caso pedagógico para experimentação técnica, o projeto poderá utilizar componentes do ecossistema
open-source de software para drones (como o stack Dronecode), permitindo demonstrar o funcionamento do OS
em um ambiente realista de desenvolvimento de sistemas autônomos.

##### BENEFÍCIOS ESPERADOS PARA O PARCEIRO:

A implementação do OS v0.1 permitirá à Jacto Drones:
● estabelecer uma cadência estruturada de desenvolvimento de software;
● reduzir o tempo de ciclo entre concepção e entrega de funcionalidades;
● aumentar a previsibilidade e transparência do desenvolvimento;
● padronizar processos de engenharia entre firmware, plataformas digitais e dados;
● criar a base inicial para continuous delivery de software para drones;
● estruturar métricas operacionais de desenvolvimento;
● acelerar a evolução da arquitetura de software necessária para a construção de uma plataforma de
sistemas autônomos físicos.
Além disso, o projeto permitirá experimentar modelos de automação e integração contínua em um ambiente
controlado, facilitando a futura adoção dessas práticas na operação real da Jacto Drones.

#### MATERIAIS DE ESTUDOS ANEXADOS (detalhar):

O projeto poderá utilizar como base de estudo e referência técnica:
● documentação do ecossistema open-source Dronecode (incluindo PX4 Autopilot, MAVLink e
QGroundControl);
● literatura e guias técnicos sobre Continuous Integration e Continuous Delivery (CI/CD);
● documentação de pipelines de desenvolvimento no GitHub;
● referências de práticas de engenharia de software ágil aplicadas a sistemas embarcados e plataformas
digitais.
Esses materiais permitirão aos alunos compreender tanto o contexto tecnológico de sistemas autônomos quanto
as práticas modernas de engenharia de software aplicadas ao desenvolvimento de plataformas complexas..

##### DESCRIÇÃO CURTA DO PROJETO

Operating system for continuous delivery across drone software platforms.

##### ESCOPO MACRO

(Ex.: Descrever com o maior detalhe possível o que se espera do projeto, o que deverá conter, como,
quando, qual o público-alvo, quem estará envolvido, quem validará, como validará, quem utilizará, como
utilizará. Enfim, quanto mais informações, melhor...)
O projeto tem como objetivo desenvolver um protótipo funcional de um Operating System de
continuous delivery para software de drones, capaz de estruturar e automatizar o fluxo de
desenvolvimento entre diferentes camadas de software associadas à operação de drones.
Esse sistema operacional deverá organizar e integrar o ciclo completo de desenvolvimento, incluindo
gestão de tarefas, priorização, versionamento de código, integração contínua, validação técnica e
acompanhamento de métricas de desenvolvimento.
O protótipo deverá incluir os seguintes componentes principais:


1. Workflow de desenvolvimento unificado
Criação de um fluxo estruturado de desenvolvimento baseado em práticas ágeis, incluindo:
    ● backlog estruturado de funcionalidades
    ● regras de priorização de tarefas
    ● definição de estados de workflow (ex.: backlog, em desenvolvimento, validação, pronto)
    ● critérios de qualidade e Definition of Done
Esse workflow deverá suportar diferentes tipos de desenvolvimento associados ao ecossistema de
software de drones, como firmware, aplicações de plataforma e sistemas de dados.
2. Automação de tarefas operacionais
Implementação de mecanismos de automação para atividades recorrentes do processo de
desenvolvimento, incluindo:
    ● criação automática de tarefas a partir de templates
    ● templates de reuniões e rituais de engenharia
    ● checklists de validação de entregas
    ● notificações e controles básicos de SLAs internos
Essas automações deverão reduzir atividades manuais e aumentar a consistência dos processos de
engenharia.
3. Pipeline de integração e entrega contínua
Desenvolvimento de um pipeline básico de Continuous Integration / Continuous Delivery (CI/CD) para
software relacionado a drones, incluindo:
    ● versionamento de código
    ● build automatizado
    ● validações básicas de integração
    ● estrutura para deploy e testes em ambiente controlado
Esse pipeline permitirá demonstrar como alterações de software podem ser integradas e testadas de
forma rápida e consistente.
4. Dashboard de desenvolvimento
Criação de um painel de acompanhamento que permita visualizar métricas essenciais do
desenvolvimento, incluindo:
    ● cycle time
    ● throughput de entregas
    ● estado do backlog
    ● identificação de gargalos no fluxo de desenvolvimento
O objetivo é fornecer visibilidade operacional sobre o desempenho do processo de engenharia.
5. Caso de validação pedagógica
Para demonstrar o funcionamento do sistema operacional em um contexto realista de engenharia de
drones, o projeto poderá utilizar como referência componentes open-source do ecossistema
Dronecode, como firmware de autopiloto, protocolos de comunicação e interfaces de controle.
Esse caso de uso permitirá validar o fluxo de desenvolvimento e integração contínua em um ambiente
representativo de software para sistemas autônomos.


6. Documentação e uso do protótipo
O protótipo deverá ser acompanhado de documentação mínima que permita compreender:
    ● arquitetura da solução
    ● fluxo de desenvolvimento proposto
    ● utilização do pipeline e dashboard
    ● boas práticas de engenharia associadas ao sistema
Essa documentação deverá permitir que o conceito desenvolvido possa ser posteriormente expandido
pela equipe da Jacto Drones.

##### MVP

Definir o que é minimamente esperado do principal entregável;
OBS: Lembre-se a definição de MPV é: MVP é a sigla que representa o Mínimo Produto Viável. De um jeito simples, podemos definir o
MVP como uma versão enxuta de uma solução, que contém apenas suas funcionalidades básicas. Pode ser um software, serviço,
produto físico ou digital.
O MVP do projeto consiste em um protótipo funcional de um Operating System de continuous delivery
para software de drones, demonstrando a integração básica entre workflow de desenvolvimento,
automação de tarefas e pipeline de integração contínua.
O MVP deverá incluir, no mínimo, os seguintes elementos:

1. Workflow estruturado de desenvolvimento
Implementação de um fluxo de trabalho padronizado para gestão de desenvolvimento de software,
incluindo:
    ● backlog estruturado de funcionalidades
    ● estados definidos de workflow (ex.: backlog, desenvolvimento, validação, concluído)
    ● critérios básicos de priorização
    ● Definition of Done para entregas de software
Esse workflow deverá ser demonstrado em um ambiente de gestão de tarefas integrado ao processo
de desenvolvimento.
2. Pipeline básico de integração contínua
Implementação de um pipeline simples de Continuous Integration, demonstrando:
    ● versionamento de código em repositório Git
    ● execução automática de build ou validação
    ● integração básica entre commits e tarefas do workflow
Esse pipeline permitirá demonstrar o conceito de integração contínua aplicado ao desenvolvimento de
software para drones.
3. Automação mínima de processos operacionais
Criação de automações simples para reduzir atividades manuais no fluxo de desenvolvimento,
incluindo:
    ● templates de criação de tarefas
    ● checklists de validação de entregas
    ● automação básica de notificações ou atualização de estados de tarefas
4. Dashboard operacional básico


Criação de um painel simples de acompanhamento que permita visualizar:
● quantidade de tarefas em andamento
● tempo médio de ciclo de desenvolvimento
● estado geral do backlog
O objetivo é demonstrar como métricas de desenvolvimento podem ser utilizadas para melhorar o
processo de engenharia.

5. Demonstração em um caso de uso técnico
O funcionamento do OS deverá ser demonstrado utilizando um caso pedagógico relacionado ao
desenvolvimento de software para drones, utilizando componentes open-source do ecossistema
Dronecode como referência.
Esse caso de uso servirá apenas como ambiente de validação do fluxo de desenvolvimento e não como
objetivo principal do projeto.

##### ENTREGÁVEIS DESEJÁVEIS

Além do MVP mínimo, os seguintes elementos são considerados desejáveis caso o projeto evolua além
do escopo mínimo:
**Automação mais avançada do workflow**
● automação de criação e configuração de pipelines de integração contínua;
● integração mais profunda entre gestão de tarefas e repositórios de código;
● automação de geração de documentação técnica a partir de artefatos de desenvolvimento.
**Evolução do dashboard operacional**
● visualização mais avançada de métricas de engenharia (cycle time, throughput, lead time);
● identificação automática de gargalos no fluxo de desenvolvimento;
● métricas comparativas entre tipos de tarefas ou módulos de software.
**Integração com ambientes de IA generativa para engenharia de software**
Exploração de integração com ferramentas de IA generativa aplicadas à engenharia de software,
permitindo:
● análise automática de código e arquitetura de software;
● geração ou sugestão de documentação técnica a partir do repositório;
● interação em linguagem natural para responder perguntas sobre arquitetura, dependências,
requisitos ou histórico de desenvolvimento;
● suporte a modelagem rápida e iterativa de soluções de software.
Essa integração permitiria utilizar modelos de IA como assistentes de engenharia, aumentando a
capacidade de compreensão e evolução do sistema.
**Integração com repositórios de engenharia de sistemas**
Integração com repositórios auxiliares de engenharia de sistemas (simulação, modelagem dinâmica,
matlab, simulink), capazes de armazenar e estruturar:
● requisitos de alto nível de software e sistemas;
● definições de interfaces entre módulos;
● requisitos operacionais e funcionais.


Esses repositórios poderiam alimentar automaticamente o backlog de desenvolvimento, conectando
decisões de engenharia de sistemas com tarefas concretas de implementação de software.
**Estrutura de documentação do Operating System**
● documentação estruturada da arquitetura do OS de desenvolvimento;
● guia de uso para equipes de engenharia;
● descrição de boas práticas de desenvolvimento associadas ao sistema.

##### PRÉ-REQUISITOS DO PROJETO

Para a realização do projeto, será necessário que os alunos tenham conhecimentos básicos ou
intermediários nas seguintes áreas:
programação em linguagens amplamente utilizadas em desenvolvimento de software (como Python ou
JavaScript);
● uso de sistemas de controle de versão (especialmente Git);
● conceitos básicos de desenvolvimento ágil de software;
● noções fundamentais de integração contínua e automação de pipelines.
Além disso, os alunos deverão utilizar ferramentas de desenvolvimento comumente adotadas na
indústria de software, incluindo:
● GitHub para versionamento e colaboração em código;
● ambientes de desenvolvimento como VSCode;
● ferramentas de automação de pipelines e integração contínua;
● ferramentas de gestão de tarefas e backlog.
Para fins pedagógicos e de experimentação técnica, o projeto poderá utilizar como referência
componentes open-source do ecossistema de software para drones, como os projetos mantidos pela
Dronecode Foundation.

##### RESTRIÇÕES DO PROJETO / O PROJETO NÃO CONTEMPLA

O projeto tem caráter exploratório e educacional e não contempla:
● desenvolvimento de novos algoritmos de controle de voo ou navegação de drones;
● desenvolvimento de hardware ou integração física com plataformas de voo;
● implementação de sistemas de produção ou deploy em ambientes operacionais da empresa;
● acesso a dados sensíveis, proprietários ou confidenciais da Jacto Drones.
O foco do projeto está no desenvolvimento de um protótipo de sistema de suporte ao processo de
engenharia de software, e não no desenvolvimento de funcionalidades específicas de operação de
drones.
Os protótipos entregues não são produtos prontos para serem utulizados ou comercializados.

##### CONTEÚDO RESTRITO

O projeto deverá utilizar predominantemente tecnologias, ferramentas e repositórios open-source,
permitindo que o desenvolvimento realizado pelos alunos possa ser compartilhado no ambiente
acadêmico do Inteli.


Não serão utilizados:
● códigos proprietários da Jacto Drones;
● dados operacionais reais;
● informações confidenciais relacionadas a produtos ou estratégias da empresa.
Caso seja necessário demonstrar cenários técnicos específicos, serão utilizados exemplos
simplificados ou ambientes simulados, garantindo que não haja exposição de propriedade intelectual
sensível da organização.

##### STAKEHOLDERS/MATRIZ RACI

Ponto Focal: Thamires Silva
Ponto Focal Backup: Camille Amaral
Líder Técnico: Vinícius Lopes
Líder Técnico: Roosevelt da Silva Junior
Líder Executivo: Nei Salis Brasil Neto

##### CHECKLIST DE IMPACTO OPERACIONAL E ALINHAMENTO DO PROJETO COM OS

##### OBJETIVOS DE DESENVOLVIMENTO SUSTENTÁVEL (ODS) DA AGENDA 2030 DA

##### ONU

###### Esta seção avalia a proposta de valor do projeto em duas frentes complementares. A primeira

###### parte foca nos impactos operacionais, buscando entender os benefícios práticos para a

###### organização.

###### A segunda analisa o alinhamento do Projeto com os Objetivos de Desenvolvimento

###### Sustentável (ODS), a agenda global da ONU para um futuro melhor, estruturada nas suas 5

###### dimensões: Pessoas, Planeta, Prosperidade, Paz e Parcerias (para saber mais, acesse aqui).

###### Avalie abaixo como seu projeto se conecta a essas duas frentes, marcando as opções

###### aplicáveis e descrevendo a iniciativa no campo de observações.

##### Impactos Operacionais do Projeto

###### ● Prática ou Contribuições Gerenciais (Foco em problemas práticos)

###### ● O projeto contribui para a resolução ou minimização de um problema prático (dentro

###### da empresa)?

###### ● O projeto promove competências para práticas de projetos de software?

###### ● Não se aplica

###### Observações (Gerais):

###### O projeto contribui principalmente para os objetivos relacionados à inovação

###### tecnológica, desenvolvimento de capacidades em engenharia de software e

###### fortalecimento de parcerias entre universidade e indústria.


###### Ao explorar a criação de um Operating System para continuous delivery aplicado ao

###### desenvolvimento de software para drones, a iniciativa promove o avanço de práticas

###### modernas de engenharia, automação de processos de desenvolvimento e

###### integração entre sistemas complexos.

###### Esse tipo de infraestrutura de engenharia é fundamental para o desenvolvimento de

###### sistemas autônomos físicos, que tendem a desempenhar papel crescente em

###### setores como agricultura, logística e monitoramento ambiental.

###### O projeto também fortalece a colaboração entre academia e indústria, permitindo

###### que estudantes trabalhem em desafios reais de engenharia e inovação tecnológica.

###### Alinhamento do Projeto com ODS

###### ● Dimensão 1: Pessoas (Foco em dignidade, igualdade e bem-estar)

###### ● (ODS 1, 2, 3) O projeto contribui para a erradicação da pobreza, fome zero, ou para a

###### promoção da saúde e bem-estar?

###### ● (ODS 4, 5) O projeto promove educação de qualidade ou a igualdade de gênero e o

###### empoderamento de mulheres e meninas?

###### ● Não se aplica

###### Observações (Pessoas):

###### O projeto contribui para a formação de estudantes em práticas modernas de

###### engenharia de software, integração contínua e automação de desenvolvimento,

###### ampliando competências técnicas relevantes para o mercado de tecnologia e

###### inovação.

###### ● Dimensão 2: Planeta (Foco na proteção dos ecossistemas e combate às mudanças

###### climáticas)

###### ● (ODS 6, 12) O projeto promove a gestão sustentável da água e o consumo e produção

###### responsáveis (ex: economia circular)?

###### ● (ODS 13, 14, 15) O projeto contribui para a ação climática ou para a proteção e

###### recuperação da vida na água e na terra?

###### ● Não se aplica

###### Observações (Planeta):

###### Drones e sistemas autônomos têm potencial crescente para apoiar práticas

###### agrícolas mais eficientes e baseadas em dados, contribuindo para o uso mais

###### racional de insumos e recursos naturais. O desenvolvimento de software robusto e

###### confiável para esses sistemas é um elemento fundamental para viabilizar esse tipo

###### de inovação tecnológica.


###### ● Dimensão 3: Prosperidade (Foco no crescimento econômico inclusivo e em

###### harmonia com a natureza)

###### ● (ODS 8, 10) O projeto promove trabalho decente e o crescimento econômico,

###### contribuindo para a redução das desigualdades?

###### ● (ODS 7, 11) O projeto promove o acesso a energias limpas ou o desenvolvimento de

###### cidades e comunidades mais sustentáveis?

###### ● Não se aplica

###### Observações (Prosperidade):

###### O projeto Promove a formação de profissionais qualificados em engenharia de

##### software e desenvolvimento de tecnologias avançadas. Ao apoiar o desenvolvimento

###### de capacidades tecnológicas em software e sistemas autônomos, o projeto contribui

###### para o avanço da inovação industrial e para o fortalecimento de cadeias de valor

###### baseadas em tecnologia.

###### ● Dimensão 4: Paz (Foco na promoção de sociedades pacíficas, justas e inclusivas)

###### ● (ODS 16) O projeto fortalece instituições de forma ética e responsável, promovendo a

###### transparência, a justiça e a paz?

###### Observações (Paz):

###### O projeto promove práticas de desenvolvimento tecnológico responsáveis, baseadas

###### em transparência, uso de tecnologias open-source e colaboração

###### acadêmico-industrial, reforçando princípios de desenvolvimento ético e

###### compartilhamento de conhecimento.

###### ● Dimensão 5: Parcerias (Foco na colaboração para alcançar os objetivos)

###### ● (ODS 9, 17) O projeto representa uma inovação para a indústria e infraestrutura e se

###### baseia em parcerias estratégicas para potencializar seu impacto?

###### ● Não se aplica

###### Observações (Parcerias):

###### O projeto contribui para o desenvolvimento de capacidades tecnológicas e práticas

###### modernas de engenharia de software aplicadas a sistemas autônomos e plataformas

###### digitais. E fortalece a colaboração entre universidade e empresa na construção de

##### conhecimento aplicado e inovação tecnológica.


