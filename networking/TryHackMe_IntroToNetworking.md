# Introductory Networking
Room: https://tryhackme.com/room/introtonetworking

O objetivo da sala é fornecer uma introdução aos princípios básicos de redes.

- [X] [Modelo OSI](#modelo-osi)
- [X] [Encapsulamento](#encapsulamento)
- [X] [Modelo TCP/IP](#modelo-tcp/ip)
- [X] [Ping](#ping)
- [] [Traceroute](#traceroute)
- [] [WHOIS](#whois)
- [] [Dig](#dig)

## Modelo OSI

O modelo OSI (Open Systems Interconnection, ou melhor, Sistemas Abertos de Interconexão) é um modelo padronizado utilizado para demonstrar a teoria por trás das redes de computadores.

*Nota: na prática, as redes na vida real são mais baseadas no modelo TCP/IP*

O modelo OSI consiste em 7 camadas: 
- [Layer 7: Aplicação (Application)](#layer-7---aplicação)
- [Layer 6: Apresentação (Presentation)](#layer-6---apresentação)
- [Layer 5: Sessão (Session)](#layer-5---sessão)
- [Layer 4: Transporte (Transport)](#layer-4---transporte)
- [Layer 3: Rede (Networking)](#layer-3---rede)
- [Layer 2: Enlace (Data Link)](#layer-2---enlace)
- [Layer 1: Física (Physical)](#layer-1---física)

### Layer 7 - Aplicação
Essa camada tem a função de fornecer opções de redes para os programas estão sendo executados no computador.

Promovendo uma interface para as aplicações transmitirem seus dados. 

Quando os dados são fornecidos à camada de aplicação, eles são passados para a camada de apresentação.

### Layer 6 - Apresentação
A camada de apresentação recebe os dados da camada de aplicação

Os dados recebidos serão convertidos para um formato padrão que o protocolo usado entenda. 

Essa camada tem a função de lidar com qualquer criptografia, compactação ou outros tipos de transformação de dados.

Com isso concluído, os dados são passados para a camada de sessão.

### Layer 5 - Sessão
Quando a camada de sessão recebe os dados corretamente formatados da camada de apresentação, ela irá ver se consegue consegue configurar/criar uma sessão com um outro computado na rede.

Senão conseguir ela envia uma mensagem de erro de volta e o processo não tem continuidade.

Se a conexão consegue ser estabelecida, então é a função desta camada manter a conexão, e cooperar com a camada de sessão do computador remoto para sincronizar a comunicação.

Essa camada é importante, pois a sessão que ela cria é exclusiva para a comunicação em questão. Ou seja, permite que você faça múltiplos requisitos para diferentes endpoints simultaneamente sem que os dados se misturem.

Depois da camada de sessão ter estebelecido uma conexão entre o host e o computador remoto, os dados são passados para a camada de transporte.

### Layer 4 - Transporte
A camada de tranporte tem inúmeras funções importantes.

A primeira delas é escolher o protocolo em que os dados serão transmitidos. 

Os protocolos mais comuns são: TCP (Transmission Control Protocol, ou seja, Protocolo de Controle de Transmissão) e UDP (User Datagram Protocol, ou melhor, Protocolo de Datagranas do Usuário). 

No TCP, a transmissão é *connection-based*, que significa que a conexão entre os computadores é estabelecida e mantida durante a solicitação. Essa caractéristica permite uma transmissão confiável, pois a conexão é utilizada para garantir que **todos** os pacotes cheguem no lugar certo. Assim, uma conexão TCP permite que os dois computadores permaneçam em comunicação constante para garantir que os dados sejam enviados em uma velocidade aceitável e que quaisquer dados perdidos sejam reenviados.

No UDP, os pacotes de dados são lançados para o computador receptor, e se ele não conseguir acompanhar, "o problema é dele". 

Dessa maneira, o TCP é utilizado em situações em que é mais necessário a precisão do que a velocidade, como transfêrencia de arquivos, ou carregando uma página. E o UDP é usado em situações em que a velocidade é mais importante, como no vídeo streaming.

A segunda função é dividir a transmissão em pedaços pequenos (no TCP, eles são chamados de segmentos, no UDP, de datagramas), o que torna mais fácil transmitir a mensagem com sucesso. 

### Layer 3 - Rede
A camada de rede é responsável por localizar o destinatário da sua requisição.

Digamos assim, quando você quer ir um site, a camada de rede é responsável por pegar o endereço IP do site e descobrir a melhor rota para chegar lá. 

Nessa camada, estamos trabalhando com endereços lógicos (endereços IP), que ainda são controlados por software. Endereços lógicos são usados para dar ordem às redes, categorizando-as e permitindo classificá-las adequadamente.

Atualmente, forma mais comum de endereço lógico é o formato IPV4.

### Layer 2 - Enlace
Também conhecida como camada de ligação de dados. 

Essa camada é se concentra no endereço físico da transmissão. Ela recebe um pacote da camada de rede (que inclui o endereço IP para o computador remoto) e adiciona o endereço físico (MAC) do do terminal receptor. 

Dentro de cada computador habilitado para rede há uma placa de interface de rede (NIC) que vem com um endereço MAC (Media Access Control) exclusivo para identificá-lo.

Endereços MAC são definidos pelos fabricantes e gravados na placa. eles não podem ser alterados - embora possam ser falsificados.

Quando as informações são enviadas por uma rede, na verdade é o endereço físico usado para identificar exatamente para onde enviar as informações.

Também é função da camada de ligação de dados apresentar os dados em um formato adequado para transmissão. 

Além disso, a camada de enlace tem uma função muito importante quando recebe dados, que é checar se a informação recebida não foi corrompida durante a transmissão. 

### Layer 1 - Física
A camada física está diretamente relacionado ao hardware do computador.

 O seu trabalho é converter dados binários da transmissão em sinais e transmití-los através da rede, assim também como, receber sinais e convertê-los devolta para binário.

## Encapsulamento
À medida que os dados são passados para cada camada do modelo, mais informações contendo detalhes específicos da camada em questão são adicionadas no início da transmissão. 

Por exemplo, na camada de rede é adicionado no cabeçalho informações sobre os endereços IP de origem e destino. 

Outro exemplo é a camada de enlace de dados que adiciona uma peça no começo e no final da transmissão, em que a do final é usada para verificar se os dados não foram corrompidos na transmissão. O que dá um bônus adicional de maior segurança, pois os dados não podem ser interceptados e adulterados sem quebrar o trailer (peça adicionada no final).

Todo esse processo é chamado de encapsulamento, ele vai da camada de aplicação a física. O processo pelo qual os dados podem ser enviados de um computador para outro.

![processo de encapsulamento](https://user-images.githubusercontent.com/62816035/216852139-760fc4be-3ef8-4fe0-9884-9ed5d1a94bfa.png)

Os dados encapsulados recebem nomes diferentes em diferentes etapas do processo. Nas camadas 7, 6, 5, os dados são simplesmente referidos como dados. Na camada de transporte o dado encapsulado é chamado de segmento ou datagrama (dependendo de qual protocolo foi selecionado, TCP ou UDP). Na camada de rede, os dados são referenciados como pacotes. E quando os dados chegam na camada de enlace recebem o nome de frame. E no momento em que é transmitido pela rede, o frame já foi dividido em bits.

Quando a mensagem é recebida pelo computador, ele faz o processo inverso - começando pela física e indo até a de aplicação, removendo as informações adicionadas à medida que avança. Esse processo é conhecido como desencapsulamento. 

![encapsulamento e desencapsulamento](https://user-images.githubusercontent.com/62816035/216852693-54cb1590-7ab8-4cbd-b91f-b6056bf76ecc.png)

O processo de encapsulamento e desencapsulamento são muito importantes - na apenas pelo seu uso prático, mas também por padronizar um método de envio de dados. Ou seja, permitir que ocorra transmissões de dados consistentes através de dispositivos independende de serem do mesmo produtro, ou mesmo SO, ou até outros fatores.

## Modelo TCP/IP
O modelo TCP/IP é muito similar ao modelo OSI. É alguns anos mais antigo e serve como base para redes do mundo real.

Ele consistem em quatro camadas: aplicação, transport, internet, network interface. Que cobrem as mesma funcionalidades das sete camadas do modelo OSI.

*Nota: Algumas fontes dividem o modelo TCP/IP em cinco camadas - dividindo a camada de networking interface em Enlace e Física, como o modelo OSI. Isto não está oficialmente definido (RFC1122), mas é conhecido e aceitado.*

Comparando os modelos OSI e TCP/IP temos:

![image](https://user-images.githubusercontent.com/62816035/216854142-c66e5e73-0d50-4da1-abe0-1321277116b8.png)

Os processos de encapsulamento e desencapsulamento funcionam da mesma maneira no modelo TCP/IP. A cada camada do modelo um cabeçalho é adicionado durante o encapsulamente e retirado durante o desencapsulamento.

---

**O Lado Prático**

O modelo de camadas é ótimo como uma forma de visualização. Mas como as coisas realmente funcionam?

Quando falamos sobre TCP/IP, estamos falando de um conjunto de protocolos - conjuntos de regras que definem como uma ação deve ser realizada. TCP/IP leva o nome dos dois protocolos mais importantes: **T**ransmission **C**ontrol **P**rotocol, que controla o fluxo de dados entre dois endpoints. E **I**nternet **P**rotocol, que controla como os pacotes são endereçados e enviados. 

Falando mais sobre o TCP, ele é um protocolo *connection-based*, como já falado anteriormente. Que significa, que antes de você enviar qualquer dado, deve-se estabelecer uma conexão estável entre os dois computadores. E esse processo de estabelecimento de conexão é chamado de *three-way handshake*. 

***Three-way Handshake***

Quando estamos tentando estabelecer uma comunicação, o nosso computador primeiro envia uma requisição especial para o servidor remoto indicando que quer inicializar uma conexão. Essa requisição contém um bit SYN (abreviação de *synchronise*), que essencialmente faz o primeiro contato para iniciar o processo de conexão. 

O servidor vai respondere com um pacote contendo o SYN bit e com o ACK bit ("*acknowledgement*" bit).

E por fim, o nosso computador vai enviar um pacote contendo o ACK bit por si só, confirmando que a conexão foi estabelecida com sucesso. 

![image](https://user-images.githubusercontent.com/62816035/216856378-a8ee50a4-9533-45bd-bc99-19ea642eab71.png)

Com o *three-way handshake* sendo completado com sucesso, os dados podem ser enviados de forma confiável entre os computadores. E qualquer dado que for perdido ou corrompido na transmissão será reenviado. Levando assim a uma conexão que parece não ter perdas.

*Nota: Há ainda muitos detalhes por trás do three-way handshake que não serão cobertos aqui*

---

**História**

É importante entender exatamente o porquê que os modelos TCP/IP e OSI foram originalmente criados.

No começo, não havia padronização - diferentes fabricantes seguiam suas próprias metodologias e, consequentemente, os sistemas feitos por diferentes fabricantes eram completamente incompatíveis quando se tratava de redes. 

O modelo TCP/IP foi introduzido pelo DoD americano em 1982 para fornecer um padrão -- algo a ser seguido por todos os diferentes fabricantes. Isso resolveu os problemas de inconsistência. 

Mais tarde, o modelo OSI também foi introduzido pela Organização Internacional de Padronização (ISO); no entanto, é usado principalmente como um guia mais abrangente para o aprendizado, pois o modelo TCP/IP ainda é o padrão no qual a rede moderna se baseia.

## Ping
O comando `ping` é usado quando queremos testar se uma conexão com um recurso remoto é possível. O recurso remoto pode ser um site na internet, ou um computador na sua internet (se você quiser checa se ele foi configurado corretamente).

Ping usa o Protocolo ICMP, que é um dos protocolos TCP/IP um pouco menos conhecidos. O Protocolo ICMP funciona na camada de rede do modelo OSI, e na camada de Internet no modelo TCP/IP.

A sintaxe básica do ping é `ping <target>`.

Quando executamos o comando `ping` ele retorna o endereço IP do server que ele se conectou e não a URL requisitada. Assim, uma função secundária do Ping é determinar o endereço IP do server que está hospedando o site. 

Uma das grandes vantagens do ping é que ele é praticamente onipresente em qualquer dispositivo habilitado para rede. Todos os sistemas operacionais oferecem suporte imediato e até mesmo a maioria dos dispositivos integrados pode usar ping!

## Traceroute

## WHOIS

## Dig
