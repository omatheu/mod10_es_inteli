Vinícius (óculos) - Eng Aero
Camila - Adm/PM
Roosevelt - Eng Comp

===

Jacto Drones
Drones com fins agrícolas. Autônomo (Missões com 1 botão). 5m². 50-70L (até 100L). upTo200Kg. Opera em velocidades mais baixas. $$$ (100-200k)
Pulverizador (acidentes?).

Aviação (setor Regulado)
- Telemetria
- Dados em tempo real (localização no espaço aéreo)

Missão:
-> Plano de vôo (Manobras fixas + teste simulador + teste real). [Girar a frente do drone; Andar para frente; pairar]
-> Controle e Execução: Sinais para os motores

Plano de Missão:
1. Estação de solo: Consegue definir taxa de pulverização, áreas pulverizadas; Atualizar missão durante vôo.
2. Drone/Embarcado (Controle de vôo): Código que realiza a orquestração dos motores.

Pontos importantes:
- Tudo será um dia auditado (ANAC) -> precisa ser rastreável
- Diagrama [Controle (Quero alterar o vôo do drone), Simulação, Embarcado (Comunicação, servidores remotos, Drivers)]

Durante uma missão, são geradas diversas versões de simulação.

-- Envelope de Vôo: Conjunto de configurações de massa/velocidade que define uma área/volume no espaço cartesiano, o qual define os limites seguros de operação do drone

===
Fluxo de desenvolvimento estruturado:
- Time to Market menor, melhor concorrência;
- Quanto mais rápido a iteração entre ciclos ocorrer, melhor;
- Iteração rápido é bom para dev/melhoria/inovação;
- Mais rápido para conformidade com a ANAC;
- Processo controlado -> Garantia de qualidade;

- Testar em vôo (in live) é caro, portanto, quanto melhor os testes prévios, mais eficiente o processo.
- Hoje, eles pulam algumas etapas de teste para conseguir entregar as demandas necessárias 

- Métricas atuais: Somente olham padrões e se está estourando os limites.
- Falhas no software local não são metrificadas -> Esteira têm rastreabilidade de cada iteração em dev

* Empresa importante: DJI (China) {Baratos e dev rápido: anos -> dias}

===

DJI Agras T50, T100, T200

Desenvolvimento P&D:
1. Esteira Controle (>Firmware)
2. Esteira Firmware
==> Release
3. Ensaios de vôo
4. Logs do ensaio de vôo
5. Volta para Backlog

* Toda alteração do controle é só virtual, ela será transformada em código firmware.
* Nem toda alteração em firmware necessita de uma alteração de controle.

===

Esteira de Desenvolvimento + Plataforma/Integração de Dados é o mais importante;

Qual é a plataforma de dados?

Plataforma para o cliente é menos prioritário agora;

- Feature menor que vai para o simulador: Se o drone consegue fazer manobra "return to land", de emergência, não considera condições fora CNTP (testa só software).
- Simuladores MATLAB tem variáveis de ambiente e são mais complexas (recebe os sinais de software -> entrega os comandos de motor)

Testar controle (precisa confrontar log de vôo com MATLAB)
Testar firmware não precisa disso.


Maiores dores:
- Time from ideation to Flight test (Simulation tests)
- Time to analyze data (From flight test logs data to new backlog)
- Segurança dos dados é FUNDAMENTAL (tanto de Product Dev quanto de Tracking Customer Data)
- Rastreabilidade TAMBÉM é fundamental.
- ERROS são pouquíssimo toleráveis (Ensaio de vôo é extremamente caros e os drones/componentes são extremamente caros também e de difícil acesso)

Métrica-chave: Tempo de vôo/Tempo de simulação pré-vôo/Testes realizados e abertos a sugestões

Ferramentas:
- Jira (PM/métricas/produtividade) e Trello
- MATLAB e Math e Symolink (Controle)
- Git / GitHub (VCS)
- OneDrive é a Cloud

===
1. Dois fluxos mais críticos são (1) Análise de Dados para Backlog novamente e (2) Testes pré-vôo;
2. Logs de Vôo são produzidos/armazenados e baixados por onde? -> No próprio controlador e são exportados via USB (PixHawk, ESP32 via 4G ou Rádio)
3. No teste de simulação de vôo usaremos PX4 mas é predominantemente para controle? Ou para firmware também?  

=== Business
1. Revenda de Drones chineses
2. P&D para nacionalizar tecnologia (brasileira), seja hardware, software, etc