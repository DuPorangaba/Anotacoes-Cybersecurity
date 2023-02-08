# Linux Fundamentals

## Linux
Linux é um sitema operacional baseado em um kernel. 

Um sistema operacional é um software responsável por gerenciar todos os recursos do hardware associados ao computador. Dessa maneira, o Linux gerencia toda a comunicação entre o software e o hardware. 

## Filosofia
Príncipios | Descrição
-----------|----------
Tudo é arquivo |Todos os arquivos de configuração para os vários serviços em execução no sistema operacional Linux são armazenados em um ou mais arquivos de texto.
Programas pequenos e de propósito único |O Linux oferece muitas ferramentas diferentes que podem ser combinadas para trabalhar em conjunto.
Capacidade de encadear programas para executar tarefas complexas |A integração e combinação de diferentes ferramentas nos permite realizar muitas tarefas grandes e complexas, como processar ou filtrar resultados de dados específicos.
Evite interfaces de usuário cativas |O Linux foi projetado para funcionar principalmente com o shell (ou terminal), o que dá ao usuário maior controle sobre o sistema operacional.
Dados de configuração armazenados em um arquivo de texto |Um exemplo desse tipo de arquivo é o arquivo /etc/passwd, que armazena todos os usuários cadastrados no sistema.

## Componentes
Componentes | Descrição
------------|----------
Bootloader  |Um pedaço de código que é executado para guiar o processo de inicialização para iniciar o sistema operacional
OS kernel   |O kernel é o principal componente de um sistema operacional. Ele gerencia os recursos dos dispositivos de E/S do sistema no nível do hardware.
Daemons     |Os serviços de segundo plano são chamados de "daemons" no Linux. Sua finalidade é garantir que as principais funções, como agendamento, impressão e multimídia, estejam funcionando corretamente. Esses pequenos programas são carregados depois que inicializamos ou efetuamos login no computador.
OS Shell   |O shell do sistema operacional ou o interpretador de linguagem de comando (também conhecido como linha de comando) é a interface entre o sistema operacional e o usuário. Essa interface permite que o usuário diga ao sistema operacional o que fazer.
Graphics server |Isso fornece um subsistema gráfico (servidor) chamado "X" ou "X-server" que permite que programas gráficos sejam executados local ou remotamente no sistema X-windowing.
Window Manager  |Também conhecida como interface gráfica do usuário (GUI).  Um ambiente de área de trabalho geralmente possui vários aplicativos, incluindo arquivos e navegadores da web. Eles permitem que o usuário acesse e gerencie os recursos e serviços essenciais e acessados com frequência de um sistema operacional.
Utilities       |Aplicativos ou utilitários são programas que executam funções específicas para o usuário ou outro programa.Aplicativos ou utilitários são programas que executam funções específicas para o usuário ou outro programa.

## Arquitetura do Linux
O sistema operacional Linux pode ser dividido em camadas:

Camada      | Descrição
------------|----------
Hardware    |Dispositivos periféricos como RAM do sistema, disco rígido, CPU e outros.
Kernel      |O núcleo do sistema operacional Linux cuja função é virtualizar e controlar recursos comuns de hardware do computador, como CPU, memória alocada, dados acessados e outros. O kernel fornece a cada processo seus próprios recursos virtuais e evita/atenua conflitos entre diferentes processos.
Shell       |Uma interface de linha de comando (CLI), também conhecida como shell na qual um usuário pode inserir comandos para executar as funções do kernel.
System Utility |Disponibiliza ao usuário todas as funcionalidades do sistema operacional.

## Hierarquia do sistema de arquivos
O sistema operacional Linux é estruturado em uma hierarquia semelhante a uma árvore e está documentado no [Filesystem Hierarchy Standard (FHS)](https://www.pathname.com/fhs/). 

Caminho     | Descrição
------------|----------
/           | O diretório de maior nível é o root filesystem. Ele contém todos os arquivos necessários para a inicialização do OS antes da montagem dos outros filesystem, assim como os arquivos necessários para inicializar os outros filesystem. Depois da inicialização, todos os outros filesystems são montados em pontos padrão de montagem como subdiretórios do root
/bin        |Contém os comandos binários essenciais. (Binário)
/boot       |Consiste no bootloader estático, executável do kernel, e todos os arquivos necessários para inicializar o Linux OS. (Bootloader)
/dev        |Contém os arquivos de dispositivos para facilitar o acesso os dispositivos de hardware ligados ao sistema. (Devices - Dispositivos)
/etc        |Arquivos de configuração dos sistema local. Arquivos de configuração para aplicativos também podem ser salvos aqui. (Et cetera)
/home       |Cada usuário do sistema tem um subdiretório aqui para armazenamento
/lib        |Arquivos de biblioteca compartilhada necessários para a inicialização do sistema. (Libraries - bibliotecas)
/media      |Dispositivos externos de média removivéis, como drives USB, são montados aqui. 
/mnt        |Ponto de montagem temporário para filesystems regulares. (Mount - Montagem)
/opt        |Arquivos opcionais como ferramentas de terceiros podem ser salvos aqui. (Optional - Opcional)
/root       |É o diretório home do usuário root
/sbin       |Esse diretório contém executáveis usados para administração do sistema (sistema de arquivos binários). (System binaries - Sistemas binários)
/tmp        |O OS e muitos programas usam esse diretório para armazenar arquivos temporários. Esse diretório é geralmente limpo na inicialização do sistema e pode ser excluído em outros momentos sem qualquer aviso. (Temporários)
/usr        |Contém executáveis, bibliotecas, arquivos de manuais e etc. (User System Resources)
/var        |Contém arquivos de dados variáveis, como arquivos de logs, caixas de entrada de email, arquivos relacionados a aplicativos web, arquivos cron, etc. 
