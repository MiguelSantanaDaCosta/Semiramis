# Sistema IoT para Automação de Estufa Agrícola

## Descrição dos Componentes do Sistema

### Microcontrolador

O sistema de automação da estufa utiliza o **ESP32** como unidade central de processamento. Esse microcontrolador foi escolhido devido à sua elevada capacidade de processamento, baixo consumo energético e conectividade Wi-Fi integrada, características que o tornam adequado para aplicações de **Internet das Coisas (IoT)**.

No contexto do projeto, o ESP32 é responsável por coletar os dados provenientes dos sensores instalados na estufa, processar essas informações e acionar automaticamente os atuadores responsáveis pelo controle ambiental. Além disso, o microcontrolador permite a transmissão dos dados para sistemas externos de monitoramento, possibilitando a visualização em tempo real por meio de painéis de controle ou aplicações web.

---

### Sensor de Temperatura e Umidade

Para o monitoramento das condições climáticas internas da estufa foi utilizado o **DHT22**, um sensor digital capaz de medir simultaneamente a temperatura e a umidade relativa do ar.

A escolha desse sensor se justifica pela sua boa precisão, facilidade de integração com microcontroladores e ampla utilização em projetos de automação ambiental. O controle dessas variáveis é fundamental para o cultivo de hortaliças, pois variações excessivas de temperatura ou umidade podem comprometer o crescimento das plantas, favorecer o surgimento de doenças e reduzir a produtividade.

No sistema proposto, o sensor é conectado ao **pino GPIO15 do ESP32**, com alimentação em **3,3 V** e utilização de um **resistor de pull-up de 10 kΩ** entre os pinos de alimentação e dados para garantir estabilidade na comunicação digital.

---

### Sensor de Luminosidade

O monitoramento da intensidade luminosa da estufa é realizado por meio de um **Photoresistor Sensor**, também conhecido como **sensor LDR (Light Dependent Resistor)**.

Esse sensor apresenta variação de resistência elétrica conforme a intensidade de luz incidente, permitindo que o sistema determine se a iluminação do ambiente é suficiente para o desenvolvimento das plantas. A partir dessas medições, o sistema pode acionar automaticamente sistemas de iluminação artificial ou armadilhas luminosas utilizadas no controle de pragas.

No projeto, o sensor é conectado à **entrada analógica GPIO34 do ESP32**, permitindo a leitura contínua da intensidade luminosa dentro da estufa.

---

### Display de Monitoramento

Para exibição local das informações coletadas pelos sensores foi utilizado um **SSD1306 OLED Display**, um display OLED que utiliza comunicação **I2C**.

Esse componente permite visualizar diretamente no painel do sistema parâmetros importantes como temperatura, umidade, luminosidade e nível de água do reservatório. A utilização desse display facilita a operação do sistema pelo agricultor, permitindo a verificação rápida das condições ambientais da estufa sem a necessidade de acessar um sistema externo.

O display é conectado aos pinos **GPIO21 (SDA)** e **GPIO22 (SCL)** do ESP32, que correspondem ao barramento de comunicação I2C.

---

### Sistema de Iluminação da Estufa

O controle de iluminação artificial é representado no sistema por meio de um **LED**, que simula as lâmpadas de cultivo utilizadas em estufas modernas.

A iluminação suplementar pode ser ativada automaticamente quando o nível de luz natural é insuficiente para o desenvolvimento adequado das plantas. Esse recurso é especialmente importante em períodos de baixa luminosidade ou em dias nublados.

No sistema proposto, o LED é conectado ao **pino GPIO27 do ESP32**, com a utilização de um **resistor limitador de corrente de 220 Ω** para proteção do circuito.

---

### Sistema de Irrigação Automatizada

O acionamento do sistema de irrigação é realizado por meio de um **Relay Module**, que atua como um interruptor eletrônico controlado pelo microcontrolador.

O relé permite controlar dispositivos que operam com tensões e correntes superiores às suportadas diretamente pelo ESP32, como bombas de água ou válvulas solenóides utilizadas na irrigação da estufa. Dessa forma, o sistema pode ligar ou desligar automaticamente a irrigação com base nas condições ambientais monitoradas.

No projeto, o relé é conectado ao **pino GPIO26 do ESP32**.

---

### Monitoramento do Nível de Água

Para garantir o funcionamento adequado do sistema hidropônico, é necessário monitorar constantemente o nível de água no reservatório. Para essa finalidade foi utilizado o **HC-SR04**, um sensor ultrassônico capaz de medir distâncias por meio da emissão e recepção de ondas sonoras.

Ao ser instalado na parte superior do reservatório, o sensor mede a distância até a superfície da água, permitindo calcular o nível do líquido disponível no sistema. Caso o nível fique abaixo do limite ideal, o sistema pode emitir alertas ou acionar automaticamente mecanismos de reposição.

No circuito, os pinos **TRIG** e **ECHO** são conectados aos **pinos GPIO5 e GPIO18 do ESP32**, respectivamente.

---

### Monitoramento da Qualidade do Ar

A qualidade do ar no interior da estufa é monitorada por meio de um **MQ Gas Sensor**. Esse sensor é capaz de detectar a presença de gases e compostos voláteis que podem indicar problemas ambientais ou presença de matéria orgânica em decomposição.

No contexto agrícola, esse sensor também pode auxiliar na identificação indireta de pragas ou condições inadequadas de ventilação dentro da estufa.

O sensor é conectado à **entrada analógica GPIO35 do ESP32**.

---

### Sistema de Ventilação Automatizada

Para o controle da circulação de ar e regulação da temperatura interna da estufa foi incorporado um **Stepper Motor**, que pode ser utilizado para abrir ou fechar automaticamente janelas de ventilação ou cortinas laterais da estrutura.

O controle da ventilação é essencial para evitar superaquecimento, reduzir umidade excessiva e garantir condições adequadas para o desenvolvimento das plantas.

No projeto, o motor de passo é controlado por meio de um **driver ULN2003** conectado aos **pinos GPIO14, GPIO12, GPIO13 e GPIO4 do ESP32**.

---

### Fonte de Alimentação

Para garantir o funcionamento estável de todos os componentes eletrônicos do sistema, será utilizada uma **fonte de alimentação de 5 V e 10 A**, responsável por fornecer energia ao microcontrolador, sensores e atuadores instalados na estufa.

A escolha dessa fonte se deve à necessidade de alimentar simultaneamente diversos dispositivos eletrônicos, garantindo distribuição de energia estável e evitando quedas de tensão que poderiam comprometer o funcionamento do sistema.

Cada conjunto de sensores e controladores instalado na estufa poderá utilizar uma fonte dedicada para garantir maior confiabilidade operacional.

---

### Monitoramento Visual (Opcional)

Como recurso adicional de monitoramento, o sistema pode incorporar a utilização de uma **ESP32-CAM**, que permite realizar o acompanhamento visual das plantas e das condições da estufa.

Esse módulo integra uma câmera ao microcontrolador ESP32, possibilitando a captura e transmissão de imagens em tempo real. Dessa forma, o agricultor pode acompanhar remotamente o desenvolvimento das culturas, verificar possíveis pragas e monitorar o funcionamento do sistema de irrigação e iluminação.

---

# Dimensões da Estufa no Projeto Conceitual

Como o projeto menciona que o Sr. João já possui duas estufas, uma destinada ao cultivo de **alface** e outra ao cultivo de **repolho**, o tamanho da estrutura não será definido de forma arbitrária, mas sim baseado em dimensões típicas utilizadas em estufas agrícolas comerciais.

Para fins de projeto conceitual, será considerada uma **estufa do tipo túnel alto**, amplamente utilizada para o cultivo de hortaliças.

### Dimensões adotadas

- **Largura:** 7 metros  
- **Comprimento:** 20 metros  
- **Altura do pé-direito:** entre 2,5 e 3 metros  
- **Altura máxima no centro:** aproximadamente 4 metros  

Essa configuração resulta em uma área aproximada de **140 m² por estufa**.

---

## Justificativa da Escolha das Dimensões

A adoção dessas dimensões no projeto conceitual se justifica por três fatores principais.

Primeiramente, trata-se de um tamanho comercial padrão amplamente utilizado em estufas agrícolas destinadas ao cultivo de hortaliças. Modelos com vão livre de aproximadamente **7 metros** são comuns no mercado por oferecerem boa ventilação natural e facilidade de manejo.

Em segundo lugar, essa dimensão é adequada para a implementação de sistemas de automação agrícola, pois permite a instalação de sensores distribuídos ao longo da estufa sem tornar o sistema excessivamente complexo ou oneroso.

Por fim, essa configuração é compatível com o cultivo de **alface** e **repolho**, culturas que se adaptam bem a esse tipo de estrutura e podem ser cultivadas tanto em canteiros no solo quanto em sistemas hidropônicos.

---

## Influência das Dimensões no Projeto IoT

A definição das dimensões da estufa influencia diretamente o planejamento do sistema de automação.

Com base em uma estufa de **7 × 20 metros**, é possível estimar a necessidade de múltiplos sensores distribuídos ao longo da estrutura para evitar medições pontuais. Dessa forma, podem ser utilizados **dois ou três sensores de temperatura e umidade do ar** distribuídos ao longo do comprimento da estufa, além de sensores adicionais instalados próximos aos reservatórios de irrigação.

Da mesma forma, o dimensionamento dos atuadores, como sistemas de **irrigação, ventilação e iluminação**, pode ser planejado considerando o alcance necessário para cobrir toda a área cultivada.

Além disso, o comprimento da estufa permite planejar adequadamente a infraestrutura de comunicação, garantindo que todos os sensores e dispositivos conectados possam transmitir dados de forma eficiente por meio de protocolos de comunicação IoT.

---

# Arquitetura IoT do Sistema

A arquitetura do sistema proposto baseia-se no paradigma de **Internet das Coisas (IoT)**, no qual dispositivos físicos equipados com sensores e atuadores são capazes de coletar dados do ambiente, comunicá-los através da internet e permitir o controle remoto de processos agrícolas.

No projeto de automação das estufas do Sr. João, a arquitetura IoT foi estruturada em camadas, permitindo a coleta, transmissão, processamento e visualização das informações ambientais da estufa de forma eficiente.

A arquitetura é composta por quatro elementos principais:

- sensores  
- gateway de comunicação  
- protocolo de transmissão de dados  
- plataforma de visualização (dashboard)

---

## Camada de Sensoriamento

A primeira camada da arquitetura é composta pelos sensores responsáveis pela coleta de dados ambientais dentro da estufa.

Entre os sensores utilizados no projeto destacam-se:

- **DHT22** – medição da temperatura e da umidade relativa do ar  
- **Photoresistor Sensor (LDR)** – monitoramento da intensidade luminosa  
- **HC-SR04** – monitoramento do nível de água  
- **MQ Gas Sensor** – detecção de gases e qualidade do ar  

Esses sensores são distribuídos em pontos estratégicos da estufa para garantir medições representativas das condições ambientais. Os dados coletados são enviados continuamente para o microcontrolador responsável pelo processamento inicial das informações.

---

## Camada de Controle e Gateway

A segunda camada da arquitetura é composta pelo **gateway IoT**, responsável por receber os dados dos sensores, processá-los e transmiti-los para a rede.

No sistema proposto, essa função é desempenhada pelo **ESP32**, que atua simultaneamente como controlador local e gateway de comunicação.

O ESP32 recebe os dados provenientes dos sensores conectados às suas portas digitais e analógicas, realiza o processamento dessas informações e toma decisões automáticas com base em parâmetros previamente definidos.

Por exemplo:

- ativação da iluminação artificial quando a luminosidade estiver baixa  
- acionamento do sistema de irrigação quando necessário  
- controle da ventilação com base na temperatura

Além disso, o microcontrolador é responsável por enviar os dados coletados para a rede por meio da conexão **Wi-Fi integrada**.

---

## Camada de Comunicação

A comunicação entre o sistema de sensoriamento e a plataforma de monitoramento é realizada por meio do protocolo **MQTT**, amplamente utilizado em aplicações de Internet das Coisas devido à sua leveza e eficiência na transmissão de dados.

O protocolo MQTT funciona com base no modelo **publicador/assinante**, no qual os dispositivos enviam mensagens para um servidor intermediário conhecido como **broker**.

Nesse modelo:

- o **ESP32 atua como publicador**  
- o **broker MQTT recebe e distribui os dados**  
- aplicações externas podem se inscrever para receber essas informações

Essa abordagem permite comunicação eficiente mesmo em redes com largura de banda limitada.

---

## Camada de Aplicação e Dashboard

A última camada da arquitetura corresponde à plataforma de **visualização e análise dos dados coletados**.

Os dados transmitidos pelo sistema podem ser exibidos em um **dashboard**, permitindo ao agricultor acompanhar em tempo real as condições ambientais da estufa.

O painel pode apresentar informações como:

- temperatura  
- umidade  
- luminosidade  
- nível de água  

Além disso, o sistema pode emitir **alertas automáticos** caso algum parâmetro esteja fora da faixa ideal.

---

## Fluxo de Funcionamento do Sistema

Sensores → ESP32 (Gateway IoT) → WiFi → Broker MQTT → Dashboard
↓
Atuadores
(irrigação, iluminação,
ventilação e armadilhas)


Nesse fluxo:

1. os sensores coletam dados ambientais  
2. o ESP32 processa as informações  
3. os dados são enviados via Wi-Fi  
4. o broker MQTT distribui as mensagens  
5. o dashboard exibe os dados ao usuário

---

## Benefícios da Arquitetura Proposta

A arquitetura IoT adotada apresenta diversas vantagens para o sistema de automação da estufa:

- monitoramento contínuo das condições ambientais  
- automação de processos agrícolas  
- acesso remoto às informações da estufa  
- possibilidade de expansão do sistema com novos sensores  
- maior eficiência na gestão da produção agrícola  

Dessa forma, a utilização de tecnologias de Internet das Coisas contribui para tornar o cultivo **mais eficiente, sustentável e adaptado às demandas da agricultura moderna**.

---

# Layout de Posicionamento dos Sensores na Estufa (7 m × 20 m)

Para garantir medições ambientais representativas e um monitoramento eficiente das condições de cultivo, os sensores do sistema IoT devem ser distribuídos estrategicamente ao longo da estufa.

Considerando o modelo conceitual adotado para o projeto — **uma estufa de 7 metros de largura por 20 metros de comprimento (140 m²)** — foi definido um layout capaz de monitorar adequadamente as variações ambientais no interior da estrutura.

---

## Sensores de Temperatura e Umidade

O monitoramento é realizado por sensores **DHT22** posicionados ao longo da estufa:

- **Sensor 1:** entrada da estufa  
- **Sensor 2:** região central  
- **Sensor 3:** extremidade oposta  

Os sensores devem ser instalados entre **1,2 m e 1,5 m de altura**, próximos à zona de crescimento das plantas.

---

## Sensor de Luminosidade

O sensor **LDR** deve ser instalado na **região central da estufa**, em uma altura entre **2 m e 2,5 m**, evitando sombras causadas pelas plantas.

---

## Sensor de Nível de Água

O sensor **HC-SR04** deve ser instalado **no topo do reservatório de irrigação**, medindo a distância até a superfície da água.

---

## Sensor de Qualidade do Ar

O **MQ Gas Sensor** deve ser posicionado **na região central da estufa**, aproximadamente **1,5 m acima do solo**, permitindo detectar alterações na composição do ar.

---

# Atuadores do Sistema

### Sistema de Irrigação

A bomba de água é acionada por um **módulo de relé controlado pelo ESP32**, permitindo irrigação automática.

### Sistema de Iluminação

LEDs de alta intensidade instalados no teto da estufa podem ser ativados quando a luminosidade natural estiver baixa.

### Sistema de Ventilação

Um **motor de passo** pode abrir automaticamente janelas ou venezianas laterais para controlar a ventilação.

---

# Distribuição Espacial dos Sensores


Entrada da Estufa
┌─────────────────────────────────────┐
│ │
│ DHT22 Sensor Luz │
│ │
│ │
│ DHT22 (Centro) │
│ │
│ │
│ Sensor Gás │
│ │
│ │
│ DHT22 │
│ │
└─────────────────────────────────────┘
Extremidade da Estufa


O sensor ultrassônico de nível de água permanece instalado **no reservatório de irrigação**, normalmente localizado fora da área principal de cultivo.

---

# Benefícios do Posicionamento Estratégico

A distribuição adequada dos sensores permite:

- monitorar variações microclimáticas dentro da estufa  
- aumentar a precisão das medições ambientais  
- melhorar a eficiência do sistema de automação  
- reduzir riscos de falhas no controle climático  

Com essa abordagem, o sistema IoT proposto torna-se capaz de fornecer **informações mais confiáveis para a tomada de decisões**, contribuindo para o aumento da produtividade agrícola e para o uso mais eficiente de recursos naturais.
