# Linux Fundamentals
- [X] [Estrutura do Linux](#estrutura-do-linux)
- [X] [Introdução ao Shell](#introdução-ao-shell)
- [X] [Descrição do Prompt](#descrição-do-prompt)
- [X] [Buscando Ajuda?](#precisa-de-uma-ajuda-aí)
- [X] [Onde é que eu tô? Quem sou eu?](#informações-sobre-o-sistema)
- [X] [Gerenciamento de Usuários](#gerenciamento-de-usuários)
- [X] [Gerenciamento de Pacotes](#gerenciamento-de-pacotes)
- [X] [Gerenciamento de Serviço e Processo](#gerenciamento-de-serviço-e-processo)


## Estrutura do Linux
### Linux
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

### Componentes
Componentes | Descrição
------------|----------
Bootloader  |Um pedaço de código que é executado para guiar o processo de inicialização para iniciar o sistema operacional
OS kernel   |O kernel é o principal componente de um sistema operacional. Ele gerencia os recursos dos dispositivos de E/S do sistema no nível do hardware.
Daemons     |Os serviços de segundo plano são chamados de "daemons" no Linux. Sua finalidade é garantir que as principais funções, como agendamento, impressão e multimídia, estejam funcionando corretamente. Esses pequenos programas são carregados depois que inicializamos ou efetuamos login no computador.
OS Shell   |O shell do sistema operacional ou o interpretador de linguagem de comando (também conhecido como linha de comando) é a interface entre o sistema operacional e o usuário. Essa interface permite que o usuário diga ao sistema operacional o que fazer.
Graphics server |Isso fornece um subsistema gráfico (servidor) chamado "X" ou "X-server" que permite que programas gráficos sejam executados local ou remotamente no sistema X-windowing.
Window Manager  |Também conhecida como interface gráfica do usuário (GUI).  Um ambiente de área de trabalho geralmente possui vários aplicativos, incluindo arquivos e navegadores da web. Eles permitem que o usuário acesse e gerencie os recursos e serviços essenciais e acessados com frequência de um sistema operacional.
Utilities       |Aplicativos ou utilitários são programas que executam funções específicas para o usuário ou outro programa.Aplicativos ou utilitários são programas que executam funções específicas para o usuário ou outro programa.

### Arquitetura do Linux
O sistema operacional Linux pode ser dividido em camadas:

Camada      | Descrição
------------|----------
Hardware    |Dispositivos periféricos como RAM do sistema, disco rígido, CPU e outros.
Kernel      |O núcleo do sistema operacional Linux cuja função é virtualizar e controlar recursos comuns de hardware do computador, como CPU, memória alocada, dados acessados e outros. O kernel fornece a cada processo seus próprios recursos virtuais e evita/atenua conflitos entre diferentes processos.
Shell       |Uma interface de linha de comando (CLI), também conhecida como shell na qual um usuário pode inserir comandos para executar as funções do kernel.
System Utility |Disponibiliza ao usuário todas as funcionalidades do sistema operacional.

### Hierarquia do sistema de arquivos
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

## Introdução ao Shell
Um terminal Linux, também conhecido por shell ou linha de comando, fornece uma interface input/output baseada em texto entre os usuários e o kernel do computador. O termo console também é usado, mas não se refere a janela e sim a uma tela no modo texto. Na janela do terminal, comandos podem ser executados para controlar o sistema.

### Emuladores de Terminal
Emuladores de terminal são softwares que emulam a função de um terminal. 

Ele permite o uso de programas baseados em texto dentro de uma interface gráfica do usuário (GUI).

Existem muitos emuladores de terminal diferentes, como Terminal GNOME, Terminal XFCE4, XTerm e muitos outros.

Existem também as chamadas interfaces de linha de comando que funcionam como terminais adicionais em um terminal e, portanto, são multiplexadores. Esses multiplexadores incluem Tmux, GNU Screen e outros. 

Resumindo, um terminal serve como uma interface para o interpretador de shell.

### Shell
O shell mais usado no Linux é o Bourne-Again Shell (BASH), ele faz parte do projeto GNU. 

Tudo que conseguimos fazer via GUI, conseguimos fazer no shell.

O shell nos dá muito mais possibilidades de interagir com programas e processos para obter informações mais rapidamente. 

Além disso, muitos processos podem ser facilmente automatizados com scripts menores ou maiores que facilitam muito o trabalho manual.

Além do Bash, também existem outros shells como Tcsh/Csh, Ksh, Zsh, Fish shell e outros.

## Descrição do Prompt
O prompt do bash é fácil de entender. O formato pode ser mais ou menos assim:
```
<username>@<hostname><current working directory>$
```
O home directory do usuário está marcado com um til <~>, e é a pasta padrão quando logamos.
```
<username>@<hostname>[~]$
```
O cifrão representa um usuário. Se logarmos com o root, o caracter muda para um hashtag <#> e se parece com isso:
```
root@<hostname>[current working directory]#
```
Por exemplo, quando carregamos e executamos um shell no sistema alvo, podemos não ver o nome de usuário, o nome do host e o diretório de trabalho atual. Isso pode ocorrer porque a variável PS1 no ambiente não foi definida corretamente. Nesse caso, veríamos os seguintes prompts:

**Unprivileged - User Shell Prompt**
```
$
```

**Privileged - Root Shell Prompt**
```
#
```

O prompt do bash pode ser customizado e alterado de acordo com suas necessidade. De uma olhada [bashrcgenerator](https://bashrcgenerator.com/) [powerline](https://github.com/powerline/powerline)

## Precisa de Uma Ajuda Aí
Quando você precisar saber o que um certo comando/ferramenta faz ou saber mais sobre os seus paramêtros, temos as páginas de manual e ferramentas de ajuda "embutidas" no terminal.

Nas páginas do manual, encontraremos os manuais detalhados com explicações detalhadas.
```
user@hostname[~]$ man <tool>
```

Se quisermos algo mais rápido só para nos relembramos de parâmetro em específico, sem precisar olhar para a documentação. Podemos usar sa ferramentas de ajuda.
```
user@hostname[~]$ <tool> --help

ou

user@hostname[~] <tool> -h
```

Outra ferramenta que pode ser útil no começo é o `apropos`. Cada página de manual tem uma breve descrição disponível dentro dela. Essa ferramenta pesquisa as descrições de instâncias de uma determinada palavra-chave.
```
user@hostname[~] apropos <keyword>
```

Outro recurso interessante se você tiver problemas para entender comandos longos é o site https://explainshell.com/

## Informações sobre o sistema
Comando | Descrição
--------|-----------
`whoami`|Exibe o nome de usuário atual.
`id`    |Retorna a identidade dos usuários
`hostname` |Define ou imprime o nome do sistema host atual. Ou seja, o computador em que estamos logados
`uname` |Imprime informações básicas sobre o sistema operacional e o hardware
`pwd`   |Retorna o nome do working directory
`ifconfig` |É usado para atribuir ou visualizar um endereço para uma interface de rede e/ou configurar parâmetros de uma interface de rede
`ip`    |Mostra ou manipula roteamento, dispositivos de rede, interfaces e túneis
`netstat` |Mostra o status da rede
`ss`    |Usado para investigar soquetes
`ps`    |Mostra o status do processo
`who`   |Exibe quem está logado
`env`   |Imprime o ambiente ou define e executa comandos
`lsblk` |Lista dispositivos bloqueados
`lsusb` |Lista dispositivos USB
`lsof`  |Lista arquivos abertos
`lspci` |Lista dispositivos PCI

### Logando via SSH
Secure Shell (SSH) se refere a um protocolo que permite que clients acessem e executem comandos ou ações em computadores remotos. 

## Gerenciamento de Usuários
O gerenciamento de usuários nos permite criar novos usuários, adicionar usuários em grupos específicos, executar comandos como um usuário diferente, etc. 

Isso é importante, pois é muito comum que apenas alguns usuários de um grupo específico tem as permissões de visualizar e editar arquivos ou diretórios. 

**Como executar um comando como um usuário diferente**
Executando como um usuário
```
> user1@hostname[~]$ cat /etc/shadow

cat: /etc/shadow: Permission denied
```

Executando como o root
```
> user1@hostname[~]$ sudo cat /etc/shadow

root: <SNIP>:18395:0:99999:7:::
daemon:*17737:0:99999:7:::
bin:*:17737:0:99999:7:::
<SNIP>
```

Comando | Descrição
--------|-----------
`sudo`  |Executa um comando como um usuário diferente. Atribuir poderes de administrador de maneira passageira. 
`su`    |A utilidade `su` irá requisitar credenciais de usuário apropriadas via PAM e mudar para aquele user ID (the default is the superuser). Então, um shell é executado. Tem a função de troca de usuário ou a chamada do superusuário. Também, pode atribuir poderes de admin para uma janela do terminal.
`useradd`|Cria um novo usuário ou atualiza a informação padrão do novo usuário
`userdel`|Delete a conta de usuário e arquivos relacionados a conta
`usermod`|Modifica a conta de um usuário
`addgroup`|Adiciona um grupo ao sistema
`delgroup`|Remove um grupo do sistema
`passwd`|Muda a senha do usuário

## Gerenciamento de Pacotes
Pacotes são arquivos que contém binários de softwares, arquivos de configuração, informações sobre dependências, e acompanha os updates e upgrades. 

Os sistemas de gerenciamento de pacotes fornecem os seguintes serviços: instalação de pacotes, resolução de dependências, um formato padrão dos pacotes binários, locais comuns de instalação e configuração, configuração e funcionalidade adicionais relacionadas ao sistema, e controle de qualidade.

Comando | Descrição
--------|-----------
`dpkg`  |É uma ferramenta para instalar, construir, remover, gerenciar pacotes Debian. O front-end principal e mais amigável para o dpkg é o aptitude.
`apt`   | Apt fornece uma interface de linha de comando de alto nível para o sistema de gerenciamento de pacotes.
`aptitude` |Aptitude é uma alternativa ao apt e é uma interface de alto nível para o gerenciador de pacote
`snap`  |Instala, configura, atualiza, e remove os pacotes snap. Os Snaps permitem a distribuição segura dos aplicativos e utilitários mais recentes para nuvem, servidores, desktops e internet das coisas.
`gem`   |Gem é um front-end para o RubyGems, o gerenciador de pacotes padrão do Ruby
`pip`   |Pip é um instalador de pacotes Python, recomendado para instalar pacotes Python que não estão disponíveis no arquivo Debian. Ele pode funcionar com repositórios de controle de versão, registra a saída extensivamente e evita instalações parciais baixando todos os requisitos antes de iniciar a instalação. 
`git`   |é um sistema de controle de revisão rápido, escalável e distribuído com um conjunto de comandos extraordinariamente rico que fornece operações de alto nível e acesso total aos internos.

### Advanced Package Manager (APT)
Distribuições Linux baseadas no Debian usam o APT.

Um pacote é um arquivo que contém múltiplos arquivos ".deb". 

O utilitário `dpkg` é usado para instalar programas do arquivo ".deb" associado.

O `APT` facilita a atualização e instalação dos programas, já que muitos deles possuem dependências. 

Quando instalamos um programa de um arquivo ".deb" autônomo, poderemos ter problemas com as dependências e precisaremos instalar arquivos adicionais. O `APT` torna isso mais fácil e eficiente empacotando todas as dependências necessárias para instalar um programa. 

**Como os gerenciadores de pacote buscam os programas**

Cada distribuição do Linux usa repositórios de software que são atualizados com frequência. Quando atualizamos um programa ou instalamos um novo, o sistema consulta esses repositórios em busca do pacote desejado. Os repositórios podem ser rotulados como estáveis, em teste ou instáveis. A maioria das distribuições Linux utiliza o repositório mais estável ou "principal".

O `APT` usa um banco de dados chamado APT cache. Isso é usado para fornecer informações sobre pacotes instalados em nosso sistema offline.

### DPKG

Também podemos instalar os programas e ferramentas dos repositórios separadamente. 

## Gerenciamento de Serviço e Processo

