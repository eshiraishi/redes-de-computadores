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
    - [Modelos em camadas](#modelos-em-camadas)
    - [Modelo OSI](#modelo-osi)
    - [Modelo TCP-IP](#modelo-tcp-ip)
    - [Arquiteturas de Aplicação](#arquiteturas-de-aplicação)
    - [Comunicação em Redes](#comunicação-em-redes)
    - [Protocolo TCP](#protocolo-tcp)
    - [Protocolo UDP](#protocolo-udp)

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

  A conexão é feita enviando os dados (geralmente em ordem) pelo transmissor para o receptor de forma que os bits sejam recebidos na mesma sequência que são enviados. A mensagem é roteada pelo sistema independente das outras mensagens até chegar no destino. Porém, é possível alterar a ordem.

- **Serviços sem orientação à conexão:** TODO

Entre os modelos em camadas podemos citar os modelos OSI e TCP/IP.

### Modelo OSI

É uma proposta de arquitetura em camadas que visa minimizar o fluxo de dados entre camadas e funções exercidas por cada camada. É composta por:

1. Aplicação
2. Apresentação
3. Sessão
4. Transporte
5. Rede
6. Enlace de Dados
7. Física

### Modelo TCP-IP

Mais prático e é o que baseia a internet e a primeira rede geograficamente distribuida, a ARPANET. Embora implemente o modelo OSI, é mais simples e é baseado principalmente nos protocolos TCP e IP e é dividido em 5 camadas:

1. **Aplicação:** Realiza o seviço de comunicação com o usuário (navegação web, e-mails, chats, etc.).
2. **Transporte:** Multiplexa e controla o fluxo e a comunicação entre pontas na rede e controla parte dos erros.
3. **Rede:** Identifica logicamente os pontos da rede e encaminha pacotes via roteadores.
4. **Enlace:** Gera compatibilidade entre a camada de rede (*software*) e as tecnologias de enlace (*hardware*).
5. **Física:** Representa o *hardware* e circuitos que compõe a parte material da rede.

### Arquiteturas de Aplicação

Aplicações podem ser de três tipos de arquitetura:

- **Cliente-servidor:** Sempre há um *host* funcionando (o servidor) para atender as requisições dos outros *hosts* (clientes). Seu endereço de IP é fixo. A web, transferência de arquivos, logins remotos e e-mails são feitos assim. Geralmente existem *server farms* para garantir que sempre haverá um servidor funcionando.
- **P2P (*Peer to Peer*):** Nem sempre haverá um servidor funcionando no centro da aplicação, havendo pares relativos de *hosts* (*peers*) se comunicando. Nenhum dos lados precisa estar funcionando sempre e é possível mudar o IP. Entre suas vantagens está a escalabilidade, porém por serem distribuídas e descentralizadas não são fáceis de serem gerenciadas. Exemplos são protocolos como BitTorrent, Limewire, Gnutella, etc.
- **Híbrida:** Possui características de ambas as partes. Por exemplo, o Napster usava arquitetura P2P para trocar MP3s entre os pares sem passar por servidores mas consultava um servidor central para identificar os clientes que possuíam os pares desejados.

### Comunicação em Redes

A comunicação não é feita entre programas e sim entre processos, que são programas que compõe o sistema final. Processos se comunicando entre si usando comunicação interprocessos são geridas pelo sistema operacional, porém processos entre sistemas finais diferentes, com sistemas operacionais diferentes, precisam implementar na internet o TCP/IP para se comunicarem.

No caso da comunicação via troca de mensagens, esse processo é feito da seguinte forma:

- Um processo de origem cria e envia mensagens para a rede.
- Um processo de destino recebe as mensagens e possivelmente as responde com outras mensagens pela rede.

Essas etapas passam pela camada de aplicação do TCP/IP e consiste nos processos de servidor e cliente, que enviam as mensagens entre si pela rede. O processo que contata é o cliente e o que espera a mensagem é o servidor nesse caso. Nesse processo, as seguintes comunicações são feitas:

- **Sockets:** O processo de envio e recepção de mensagens é feito através de **sockets**, que funcionam como uma porta entre o processo emissor e a infraestrutura de transporte pela camada de aplicação (todo o processo de envio é abstraído).
  Por definição sockets são a interface entre a camada de aplicação e transporte na máquina e é a API (Application Programming Interface) entre a aplicação e a rede. Após o socket há pouco controle que pode ser feito pela rede: apenas a escolha do protocolo de transporte.
- **Endereçamento:** UM processo envia uma mensagem a outro processo ao identificar o processo de destino especificando:
  - Seu nome ou endereço de host, como IPv4 (32 bits) ou IPv6 (128 bits).
  - Um identificador do processo de destino no host, como o número da porta. Existem $2^{16}$ portas disponíveis, e em geral aplicações populares possuem números de porta específicos, como 80 para Web (HTTP) e 25 para correio (SMTP). Mais portas comuns podem ser vistas na [Internet Assigned Number Authority](www.iana.org).
  Protocolos da camada de aplicação são apenas parte da aplicação de rede, e os protocolos da camada de aplicação definem característias como:
  - Tipos de mensagem
  - Sintaxe da mensagem
  - Semântica entre campos
  - Regras sobre quando e como um processo envia ou responde as mensagens
  Alguns protocolos são especificados nas RFCs (domínio público).
  Os protocolos da camada de transporte disponibiliza dois protocolos de tranporte para a aplicação: TCP e UDP.

### Protocolo TCP

- **Orientado à conexão:** Cliente e servidor trocam informações de controle da camada de transporte em um processo chamado de *handshake* antes da troca de mensagens pela camada de aplicação, agindo como uma apresentação entre as partes. Só então ocorre a conexão TCP.
- **Confiável:** O TCP garante que os dados serão enviados sem erro na ordem correta sempre.
- **Controle de congestionamento:** limita a velocidade de transmissão quando há congestionamento de rede.
  - **Observação:** não existe taxa de transmissão mínima garantida em caso de atrasos.

### Protocolo UDP

- **Não orientado à conexão:** Não existe uma conexão de fato, ou seja, as mensagens fluem sem que haja *handshake* entre cliente e servidor.
- **Não é confiável:** Não há garantia de entrega nem da ordem dos dados.
- Não oferece controle de congestionamento, taxa mínima de transmissão e garantia de atrasos.
