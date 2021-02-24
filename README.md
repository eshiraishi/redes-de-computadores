# Redes de Computadores

Disciplina cursada na UFABC em 2021.1, ministrada pelo [Prof. Dr. Carlo Kleber da Silva Rodrigues](https://sites.google.com/site/carlokleber/disciplinas-ministradas/redes-computadores).

- [Redes de Computadores](#redes-de-computadores)
  - [Semana 1: Conceitos e Fundamentos](#semana-1-conceitos-e-fundamentos)
    - [Requisitos de uma rede](#requisitos-de-uma-rede)
    - [Aspectos de uma rede](#aspectos-de-uma-rede)
    - [Comutação de Circuitos e Pacotes](#comutação-de-circuitos-e-pacotes)
    - [Redes convergentes](#redes-convergentes)
      - [Vantagens](#vantagens)
    - [Redes com fio e sem fio](#redes-com-fio-e-sem-fio)
  - [Aula 2: Internet](#aula-2-internet)
    - [Modelo OSI](#modelo-osi)
    - [Modelo TCP-IP](#modelo-tcp-ip)

## [Semana 1](https://drive.google.com/file/d/1hXh3Z0Z29k6RTCtAl6PjDhQB6VMvEdJb/view): Conceitos e Fundamentos

Um Rede de Computadores é um conjunto de dispositivos conectados por enlaces de comunicação. Um dispositivo pode ser um computador, uma impressora ou qualquer outro elemento capaz de enviar e/ou receber dados gerados a partir de outros dispositivos.
As redes de computadores representam a estrutura de interligação dos sistemas distribuídos e impactam diretamente na funcionalidade e desempenho dos sistemas distribuídos.

### Requisitos de uma rede

- **Desempenho:**
  - **Latência:** tempo decorrido entre a operação de envio e o início da chegada dos dados ao destino.
  - **Taxa de transferência:** velocidade com que os dados são injetados na rede.
    - **Tempo de transferência: (latência) + (tam. da msg / tx. de transf.)**
- **Confiabilidade:** imunidade a falhas de comunicação ou capacidade de se recuperar das falhas
- **Segurança:** Proteger os dados do usuário e os recursos de acessos externos à rede
  - **Confidencialidade:** Disponibilizar informações apenas com autorização
- **Mobilidade:** Possibilidade de conexão de dispositivos móveis em diferentes pontos da rede de forma persistente.
- **Qualidade de serviço:** garantia da performance fornecida e de atender os prazos finais estabelecidos pelo cliente.

### Aspectos de uma rede

1. **Hardware:**  Auto explicativo.

2. **Software:** Auto explicativo.

3. **Heterogeniedade:** Diferença entre as partes de uma rede. Por exemplo, protocolos para redes sem fio domésticas são diferentes das de uma rede de fibra óptica. Por isso é preciso definir uma rede lógica intermediária que traga compatibilidade entre as partes.

   - **Redes físicas:** atendem uma demanda específica
     - Embora não seja uma exclusividade, é onde estruturas compartilhadas geralmente são usadas, que podem ser feitas de forma arbitrada ou sem organização. O segundo caso precisa de tratamento de colisões
   - **Redes lógicas** (ou tecnologias de enlace): interligam as redes físicas incompatíveis entre si
     - A rede lógica mais utilizada no mundo é a internet
     - Podem ser ponto a ponto (em geral redes locais) ou multiponto (em geral redes de longa distância)
     - Pela importância desse tipo de rede, pode ser necessário fazer o controle de acesso ao meio por segurança.
     - Os protocolos das tecnologias de enlace definem a estrutura do pacote de dados que será transmitido pelo meio físico.
     - Exemplos: Ethernet (redes locais), Wi-Fi (redes locais sem fio), Bluetooth (Comunicação sem fio em pequenas distâncias), Frame Relay (ligações de longa distância implementadas por um circuito virtual de operação baseada na comutação de pacotes), Wi-Max (Comunicação sem fio em redes metropolitanas).

4. **Topologia física:** Descreve como a rede está distribuída fisicamente

    | Tipo    | Descrição                                                                                                                                  |
    | ------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
    | Estrela | Todos os computadores estão ligados a um equipamento concentrador, que pode criar domínios de colisão (switch) ou não (hub).               |
    | Anel    | cada computador está ligado a dois vizinhos, e para percorrer a rede completa, é preciso passar por todos os computadores ligados no anel. |
    | Barra   | Os computadores estão ligados em um meio de comunicação compartilhado (por exemplo, um fio único).                                         |
    | Grafo   | Os nós estão conectados irregularmente de forma n - n.                                                                                     |
    | Híbrida | Topologias compostas.                                                                                                                      |

5. **Abrangência geográfica:** Define a escala alcançada pela rede

    | Raio    | Abrangência                     | Exemplos                                                                                                     |
    | ------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------ |
    | 10m     | PAN (Personal Area Network)     | PDA, teclados, mouses e impressoras, Bluetooth.                                                              |
    | 100m    | LAN (Local Area Network)        | interligação de computadores em ambientes como salas, restaurantes e saguões de aeroportos. Ethernet, Wi-Fi. |
    | 50km    | MAN (Metropolitan Area Network) | interligação de redes LAN. Wi-Max.                                                                           |
    | Mundial | WAN (Wide Area Network)         | Interligação de redes MAN ou LAN. Frame Relay                                                                |

### Comutação de Circuitos e Pacotes

- **Comutação de circuitos:** Os recursos necessários a para que haja comunicação entre os terminais ao longo de um caminho na rede (como buffer, largura de banda, etc.) são reservados durante a sessão de comunicação. Pode integrar FDM ou TDM. Exemplos: telefonia tradicional.
  - **FDM (*Frequency Division Multiplexing* ou Multiplexação por Divisão de Frequência):** cada conexão recebe uma continuamente uma fração da largura de banda.
  - **TDM: (*Time-Division Multiplexing* ou Multiplexação por
Divisão de Tempo):** cada conexão usa toda a largura de banda por um período de tempo.
- **Comutação de pacotes:** Os recursos são distribuídos e acessados sob demanda. Os pacotes de informação são organizados em filas e podem ter de esperar para acessar os recursos. Pode se basear em circuitos virtuais ou em datagramas. Exemplos: Internet, ATM.
  - **Circuitos Virtuais:** proporcionam apenas  um serviço com conexão virtual na camada de rede. Os roteadores reenviam pacotes dependendo do número de circuitos virtuais e mantém o estado da conexão.
  - **Datagramas:** proporcionam um serviço sem conexão na camada de rede, ou seja, os pacotes não tem que seguir pelo mesmo caminho. Os roteadores reenviam pacotes dependendo do endereço de destino de cada pacote, e não mantêm o estado da conexão.
  - **Transmissões do tipo armazenar-enviar:** implicam que o roteador deve receber o pacote completo antes de transmiti-lo pelo *link* de dados.

### Redes convergentes

Tendência de utilização de uma única infraestrutura de tecnologia para prover serviços que usariam requisitos tecnológicos independentes. Reúnem serviços de voz, dados e imagens em uma só rede digital integrada.

Todos os dados convergem para uma plataforma de transporte comum que permite que os serviços sejam entregues aos usuários de forma simples: através de uma rede de acesso único.

#### Vantagens

- O ambiente se torna mais gerenciável
- há maior segurança no registro de informações
- maior controle dos canais de comunicação
- maior possibilidade de criação de políticas de usabilidade (e por consequência o uso coreto dos recursos disponíveis)
- Menor custo
- Garantia de qualidade

### Redes com fio e sem fio

- **Redes com fio:** fibra óptica, cabo coaxial, par trançado, etc.
- **Redes sem fio:** Pode ser infraestruturada ou sem infraestrutura (ou MANET, *Mobile Ad Hoc Network*).
  - **Infraestruturada:** possui uma estrutura envolvendo a rede, que é acessada de pontos principais como antenas de provedoras de rede, roteadores que geram uma área de cobertura, e hospedeiros.
  - **MANET:** todos os nós da rede compartilham as funções de hospedeiro e roteador.
- **O desafio da mobilidade:** Redes sem fio nem sempre precisam ser móveis e se encontram em um espectro de mobilidade. O aumento na mobilidade é necessário com o crescente aumento de celulares e outros dispositivos conectados à internet. É preciso:
  - Aumentar a comunicação feita sem fios.
  - Aumentar a quantidade de pontos possíveis de conexão à rede sem fio (área de cobertura).
  - Aumentar a força de sinal de rádio.
  - Reduzir a interferência externa por outras fontes (como telefone sem fio e ruídos externos).
  - Reduzir a reflexão do sinal pelo caminho (fator que reduz a velocidade do sinal).
- **Problemas comuns**
  - **Terminal oculto:** TODO
  - **Terminal exposto:** TODO

## [Aula 2](https://drive.google.com/file/d/1Y3X4H8Rv3BqTxzzN5OtugFxADL1MA5Wu/view): Internet

A internet é a rede lógica mais usada no mundo. Na internet, a visão que os usuários têm da comunicação é apenas a das camadas lógicas de alto nível, sendo assim detalhes da rede física são ocultados. É consolidada pela *Internet Society* (ISOC) desde 1992 e no Brasil desde 1996 principalmente pela Rede Nacional de Ensino e Pesquisa (RNP), fundada em 1989.

### Modelos em camadas

Redes são construídas em camadas para reduzir a complexidade de um projeto. Nesse modelo, cada camada é responsável por uma função de nível maior de abstração e atende um nível superior, até chegar no usuário final.

De forma geral, cada camada de uma máquina se comunica com sua correspondente de outra máquina. As regras de comunicação entre camadas são chamadas de **protocolos** de uma camada e estabelece a forma como a comunicação será feita.

Os serviços oferecidos por uma camada à sua superior podem ser de dois tipos:

- **Serviços orientados a conexão:** baseado no sistema postal. Durante o serviço, é estabelecida uma conexão, a conexão é usada e então liberada. Durante a conexão, parâmetros envolvidos como o tamanho da mensagem ou a qualidade do serviço podem ser negociados entre as máquinas.

  A conexão é feita enviando os dados (geralmente em ordem) pelo transmissor para o receptor de forma que os bits sejam recebidos na mesma sequência que são enviados. A mensagem é roteada pelo sistema independente das outras mensagens até chegar no destino. Porém, é possível alterar a ordem 

- **Serviços sem orientação à conexão:** TODO

Entre os modelos em camadas podemos citar os modelos OSI e TCP/IP.

### Modelo OSI

É proposto pela ISO Mais conceitual e apesar de possuir menos camadas, é mais completo. Possui 7 camadas:

  1. Aplicação
  2. Apresentação
  3. Sessão
  4. Transporte
  5. Rede
  6. Enlace de Dados
  7. Física

### Modelo TCP-IP

Mais prático e é o que baseia a internet e a primeira rede geograficamente distribuida, a ARPANET.
