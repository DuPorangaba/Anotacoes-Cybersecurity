# Linux Fundamentals
**Introdução**
- [X] [Estrutura do Linux](#estrutura-do-linux)
- [X] [Introdução ao Shell](#introdução-ao-shell)

**Shell**
- [X] [Descrição do Prompt](#descrição-do-prompt)
- [X] [Buscando Ajuda?](#precisa-de-uma-ajuda-aí)
- [X] [Onde é que eu tô? Quem sou eu?](#informações-sobre-o-sistema)

**Workflow**
- [X] [Navegação](#navegação)
- [X] [Trabalhando com Arquivos e Diretórios](#arquivos-e-diretórios)
- [X] [Editando Arquivos](#editando-arquivos)
- [X] [Achando Arquivos e Diretórios](#achando-arquivos-e-diretórios)
- [X] [Descritores de arquivo e redirecionamentos](#descritores-de-arquivo-e-redirecionamentos)
- [X] [Visualizando e Filtrando Contéudos](#visualizando-e-filtrando-contéudos)
- [ ] [Expressões Regulares](#regex)
- [ ] [Gerenciando Permissões](#)

**Gerenciando o Sistema**
- [X] [Gerenciamento de Usuários](#gerenciamento-de-usuários)
- [X] [Gerenciamento de Pacotes](#gerenciamento-de-pacotes)
- [X] [Gerenciamento de Serviço e Processo](#gerenciamento-de-serviço-e-processo)
- [ ] [Trabalhando com Servidores Web](#servidores-web)


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

## Navegação
***pwd***

Antes de andar pelo sistema, precismos saber onde estamos. Para isso, usamos o comando `pwd` (print working directory)
```
cry0l1t3@htb[~]$ pwd

/home/cry0l1t3
```

***ls***

Para listar os contéudos que estão dentro de um diretório, usamos `ls`. 
```
cry0l1t3@htb[~]$ ls

Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

Quando apenas usamos o `ls`, apenas nos mostrará os arquivos e diretórios.

Se quisermos mais informações sobre esses arquivos e diretórios podemos usar `-l`.
```
cry0l1t3@htb[~]$ ls -l

total 32
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:37 Desktop
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Documents
drwxr-xr-x 3 cry0l1t3 htbacademy 4096 Nov 15 03:26 Downloads
...
```
Vamos traduzir as informações. 
- Na **primeira linha**, nós vemos a quantidade total de blocos (512-byte) que estão sendo utilizados pelos arquivos e diretórios. Para saber *quandos bytes do disco estamos utilizando, basta multiplicar o total por 512*.
- **drwxr-xr-x** - é o tipo do arquivo e as permissões (se for *d* é diretório, e se for *-* é arquivo)
- **2** - Hard links
- **cry0l1t3** - é o proprietário do arquivo/diretório
- **htbacademy** - é o grupo proprietário do arquivo/diretório
- **4096** - é o tamanho ou número de blocos utilizados para armazenar o arquivo/diretório
- **Nov 13 17:37** -  é a data e o horário 
- **Desktop** -  É o nome do arquivo/diretório

No entanto, às vezes não podemos ver tudo o que está na pasta. Para ver os arquivos escondidos de um diretório usamos `ls -la`.

Para listar os contéudos de um diretório qualquer sem estar nele, basta uar `ls /caminho/para/o/diretório`.

***cd***

Para se mover entre os diretórios, usamos o comando `cd /caminho/para/onde/queremos/ir` (change directory). 

Se quisermos voltar para onde estavámos, e não sabemos o caminho ou apenas queremos encurtar as coisas, usamos `cd -`.

Para facilitar a nossa vida, o shell tem a função de auto-complete. Começamos a digitar o caminho para o diretório e apertamos **[TAB]**. 

> **Pontos dentro do Shell**
> Um ponto (.) significa o diretório que estamos atualmente. 
> Dois pontos (..) representa o diretório pai. Assim, podemos ir para o diretório pai usando `cd ..`

Quando navegamos muito pelo shell, ele pode acabar cheio de informação. Para isso podemos limpar ele usando o comando `clean` ou o seu atalho `[Ctrl] + [L]`. 

Para ver o histórico do comando que usamos podemos usar as setinhas (↑ or ↓). E se quisermos pesquisar dentro do histórico de comandos podemos usar `[Ctrl] + [R]` e digitar o que estamos procurando.

## Arquivos e Diretórios
O terminal no Linux é muito eficiente, pois podemos acessar arquivos em poucos comandos, e editar e modificar os arquivos seletivamente com expressões regulares (regex). Assim, você pode rodar diversos comandos e redirecionar o output do arquivo.

Editamos os arquivos no linux usando o vim ou o nano.

### Criar

Para criar um arquivo vazio podemos usar o `touch <name>` e para criar um diretório vazio podemos usar `mkdir <name>`.

Se quisermos criar diretórios específicos no diretório, podemos usar o comando `mkdir` com a flag `-p` para adicionar diretórios pais.

> Para termos uma visualização gráfica da estrutura de diretórios pais, podemos usar `tree`

Também podemos criar arquivos diretamente nos diretórios especificando o caminho onde o arquivo deve ser armazenado. O truque é usar o ponto único (.) para informar ao sistema que queremos iniciar a partir do diretório atual.

### Mover

Para renomear e mover arquivos e diretórios usamos o comando `mv`.

**Renomear**
```
mv <file/directory> <renamed file/directory>
```

**Mover**
```
mv <file> <directory>
```

### Copiar

Se queremos copiar um arquivo para outro lugar podemos usar o comando `cp <caminho_do_arquivo> <caminho_de_destino>`

## Editando Arquivos
Os editores de textos mais comuns são o `Vi` e o `Vim`. E raramente, podemos usar o `Nano`.

*Obs: Se usar qualquer dos editores `nano/vim <arquivo>` para editar um arquivo, se este não existir o editor cria para você e se existir apenas irá abri-*

### Nano
Quando você abre o nano, você verá algo mais ou menos assim:
```
  GNU nano 2.9.3                                    notes.txt                                              

Here we can type everything we want and make our notes.▓


^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo
^X Exit        ^R Read File   ^\ Replace     ^U Uncut Text  ^T To Spell    ^_ Go To Line  M-E Redo
```

O acento circunflexo, ou chapeuzinho, (^) significa `[Ctrl]`.

Alguns comandos básicos para usar o `Nano`:
- `[CTRL + W]` para pesquisar alguma informação no arquivo
- `[CTRL + O]` para salvar um arquivo
- `[CTRL + X]` para sair do editor

### Ver o conteúdo de um arquivo no Shell

Para visualizar um arquivo no shell sem precisar abrir um editor de texto, podemos usar o `cat`.

### Vim
Quando abrimos o vim, temos isso:
```
1 $
~
~                              VIM - Vi IMproved                                
~                                                                               
~                               version 8.0.1453                                
~                           by Bram Moolenaar et al.                            
~           Modified by pkg-vim-maintainers@lists.alioth.debian.org             
~                 Vim is open source and freely distributable                   
~                                                                               
~                           Sponsor Vim development!                            
~                type  :help sponsor<Enter>    for information                  
~                                                                               
~                type  :q<Enter>               to exit                          
~                type  :help<Enter>  or  <F1>  for on-line help                 
~                type  :help version8<Enter>   for version info                 
~                                                                               
                                                                         
                                                                    0,0-1         All
```

O Vim, diferente do Nano, é um editor modal que consegue distinguir texto de entrada de comandos.

O Vim oferece seis modos fundamentais, que o torna muitos poderoso:
Mode   | Descrição
-------|-------------
Normal |Neste modo todos os inputs são considerados comandos para o editor. Assim, tudo que digitamos não é inserido no buffer do editor (no arquivo). Sempre que entrammos no Vim, estamos nesse modo.
Insert |Todos os caracteres digitados são inseridos no buffer do editor (no arquivo). Tem execeções.
Visual |Este modo é utilizado para marcar uma parte do texto, que ficará destacada. Essa área então pode ser editada de várias maneiras, como exclusão, cópia ou substituição
Command |Ele nos permite inserir comandos de linha única na parte inferior do editor. Isso pode ser usado para classificar, substituir seções de texto ou excluí-las.
Replace |Nesse modo, o texto inserido recentemente substituirá os caracteres de texto existentes, a menos que não haja mais caracteres antigos na posição atual do cursor. Em seguida, o texto recém-inserido será adicionado.

Quando temos o editor Vim aberto, podemos entrar no modo de comando digitando ":" e digitando "q" para fechar o Vim.

>Vim oferece uma excelente oportunidade chamada vimtutor para praticar e se familiarizar com o editor. Basta digitar `vimtutor` no terminal

## Achando Arquivos e Diretórios

No linux temos ferramentas que facilitam a nossa busca por arquivos e diretórios, assim não precisamos ficar pesquisando manualmente por esses.

### Which
Esse comando retorna o caminho para o arquivo ou um link que pode ser executado. 

Isso permite determinar se programas específicos estão disponíveis no sitema operacional. Se o programa não existir, não aparecerá nada.

### Find

Além de sua função de achar arquivos e diretórios, o `find` tem a função de filtra os resultados. Dessa forma, pode-se usar parâmetros como filtro, por exemplo, o tamanho do arquivo ou uma data. E, até mesmo, especificar se estamos apenas procurando por arquivos ou diretórios.

### Locate

Demoraria muito tempo para pesquisar em todo o sistema por alguns arquivos ou diretórios.

Assim, o comando `locate` oferece uma maneira rápida de pesquisar em todo o sistema. Já que, diferente do `find`, o `locate` trabalha com um banco de dados que contém toda informação sobre arquivos e diretórios existentes no sistema.

Para atualizar o banco de dados, usamos `sudo updatedb`.

No entanto, o `locate` não tem muitas opções de filtro. Dessa maneira, devemos analisar em que casos usar ele e em que casos usar o `find`.

## Descritores de arquivo e Redirecionamento
Um descritor de arquivo em sistemas Unix/Linux é um indicador de conexão mantida pelo kernel para executar operações de Entrada/Saída (E/S).

>No windows, é chamado de filehandle.

É a conexão (geralmente a um arquivo) do sistema operacional para realizar operações E/S (Entra/Saída de Bytes).

Por padrão, o Linux tem três descritores de arquivos:
- Fluxo de Dados para Entrada - `STDIN - 0`
- Fluxo de Dados para Saída - `STDOUT - 1`
- Fluxo de Dados para Saída relacionada a um erro ocorrendo - `STDERR - 2`

### STDIN e STDOUT
Vamos usar o `cat` para visualizar a entrada e saída padrão.

![image](https://user-images.githubusercontent.com/62816035/223893448-644b290c-04ef-42e2-bdbf-efdd825ddc8d.png)

Ao executar `cat`, damos ao programa em execução nossa entrada padrão `(STDIN - FD 0)`, marcada em verde. Assim que tivermos confirmado nossa entrada com `[ENTER]`, ela é retornada ao terminal como saída padrão `(STDOUT - FD 1)`, marcada em vermelho.

### STDOUT e STDERR
Para entender a saída e saída de erro padrão vamos usar o `find`.

![image](https://user-images.githubusercontent.com/62816035/223893780-fb5a5cf3-4e70-4755-ad96-ac5ae8406292.png)

Vemos a saída padrão `(STDOUT - FD 1)` de verde e a saída de erro padrão (STDERR - FD 2) marcada de vermelho.

Podemos redirecionar os **erros** para "null device", em todos os dados são descartados. Assim, só ficaremos com a saída padrão `(STDOUT - FD 1)`.

![image](https://user-images.githubusercontent.com/62816035/223894107-fcc3a613-8c16-4155-bfff-93978eded595.png)

### Redirecionando STDOUT para um arquivo
Para redirecionar a saida padrão para um arquivo, usamos o sinal de maior (**>**). Assim, basta colocarmos `1 > <arquivo>`.

![image](https://user-images.githubusercontent.com/62816035/224144201-6e0a0e43-eb33-47b8-b3b5-cd1648ae6ba4.png)


Outra opção, é redirecionar todos os erros (STDERR - 2) para o "null device" e depois redirecionar a saída padrão para um arquivo.

![image](https://user-images.githubusercontent.com/62816035/224144572-14f32ed4-eee5-40b5-8c4a-5994cd90b38a.png)

### Redirecionado STDOUT e STDERR para arquivos diferentes
Para sermos mais precisos, não descartar todos os erros (como fizemos no último exemplo), vamos redirecionar a saída de erro padrão (FD 2 - STDERR) e a saída padrão (FD 1 - STDOUT) para arquivos diferentes.

![image](https://user-images.githubusercontent.com/62816035/224145629-3def87ca-f1da-431b-a381-73c69027e324.png)


### Redirecionando o STDIN
Nos exemplos passados apenas usamos o caracter de maior (>). 

Também podemos usar o caracter de menor (<), este serve para a entrada padrão (FD 0 - STDIN). 

> Esses caracteres podem ser vistos como "direção" na forma de uma seta que nos diz "de onde" e "para onde" os dados devem ser redirecionados.

Vamos usar o conteúdo do arquivo "results.txt" como STDIN para o comando `cat`.
![image](https://user-images.githubusercontent.com/62816035/224152177-35ffe113-ba8d-4fa5-a9bd-14526fee2546.png)


### Redirecinando STDOUT e o anexando a um arquivo
Quando usamos o sinal de maior (>) para redirecionar o STDOUT, um novo arquivo é criado automaticamente, caso ainda não exista. 

Se o arquivo existir, ele será subsitituído se a solitação de uma confirmação. Se quisermos acrescentar o STDOUT ao nosso arquivo existente, podemos usar o sinal de maior duplo (>>)

![image](https://user-images.githubusercontent.com/62816035/224152737-5776b489-6b17-4ebb-bd06-c95cd3c71737.png)

Vemos o STDOUT do exemplo passado (de redirecionar o STDOUT) e os novos STDOUT.

### Redirecionar fluxo STDIN para um arquivo
Também podemos usar os caracteres duplos menores que (<<) para adicionar nossa entrada padrão por meio de um fluxo.

Podemos usar a chamada função End-Of-File (EOF) de um arquivo de sistema Linux, que define o final da entrada. 

No próximo exemplo, usaremos o comando `cat` para ler nossa entrada de streaming por meio do stream e direcioná-lo para um arquivo chamado "stream.txt". 
![image](https://user-images.githubusercontent.com/62816035/224155344-284c6fab-a583-464a-9b90-f1d5ad7c7430.png)

### Pipes
Outra maneira de redirecionar STDOUT é usar pipes (|). Estes são úteis quando queremos usar o STDOUT de um programa para ser processado por outro.

## Visualizando e Filtrando Contéudos

### Pagers
Não precisamos necessariamente usar editores para visualizarmos arquivos.

Existem pagers que nos permitem percorrer o arquivo em uma visão interativa.

#### More
Depois de ler o conteúdo usando cat e redirecioná-lo para more, o pager já mencionado é aberto e iniciaremos automaticamente no início do arquivo.

```
more <arquivo>
```

Com a tecla [Q], podemos sair deste pager. Notaremos que a saída permanece no terminal.

#### Less
O `less` funciona quase igual o `more`, no entanto ele possui mais recursos que o `more`, vemos isso em sua man page.

Ao fechar o `less` com a tecla [Q], notamos que a saída que vimos, ao contrário do `more`, não fica no terminal.

#### Head
Às vezes, estaremos interessados apenas em questões específicas no início ou no final do arquivo. Se quisermos apenas obter as primeiras linhas do arquivo, podemos usar 
de ferramenta o `head`. 

Por padrão, `head` imprime as primeiras dez linhas do arquivo ou input fornecido, se não for especificado de outra forma

#### Tail
Se nós queremos ver as últimas partes de um arquivo, podemos usar o `tail`, que nós devolve as últimas dez linhas.

#### Sort
Frequentemente, precisamos ver os resultados organizados na ordem alfabética ou númerica. Para isso, podemos usar o `sort`.

#### Grep
O `grep` serve para pesquisarmos por resultados específicos que contém padrões que definimos. 

#### Cut
Resultados específicos com caracteres diferentes podem ser separados como delimitadores. Aqui é útil saber como remover delimitadores específicos e mostrar as palavras em uma linha em uma posição especificada. Uma das ferramentas que podem ser utilizadas para isso é o `cut`.

#### Tr
Podemos substituir caracteres de uma linha por outro caracter que queremos usando o `tr`

#### Column
Essa ferramenta é usada para exibir os resultados em forma de tabela.

#### Awk
O  `awk` é uma linguagem de digitalização e processamento de padrões. Com ela, podemos, por exemplo, exibir o primeiro ($1) e o último ($NF) resultado da linha.

#### Sed
É um editor de stream. Um dos usos mais comuns disso é a substituição de texto. Aqui, o sed procura padrões que definimos na forma de expressões regulares (regex) e os substitui por outro padrão que também definimos.

#### Wc
Muitas vezes será útil saber quantas correspondências bem-sucedidas temos. Para evitar a contagem de linhas ou caracteres manualmente, podemos usar a ferramenta wc. Com a opção "-l", especificamos que apenas as linhas são contadas.

## Regex
Expressões regulares descreve um conjunto de cadeias de caracteres, de forma concisa, sem precisar listar todos os elementos do conjunto.

Elas são utilizadas para procurar par padrões específicos em textos ou arquivos. Além disso, regex também é utilizado em aplicações web para fazer a validação da entrada do usuário.

Alguns operadores regex:
Operadores | Descrição
-----------|-----------
(a)        |Usado para agrupar partes de um regex. Dentro dos parentêses, você pode definir outros padrões que devem ser processados juntos.  
[a-z]      |Usado para definir classes de caracteres. Dentro dos colchetes, você pode especificar a lista dos caracteres que você está buscando por.
[^a-z]     |Usado para negar. Corresponde aos caracteres que não está entre colchetes.
{1,10}     |Os  são usados para definir quantificadores. Dentro das chaves, você pode especificar um número ou um intervalo que indica a frequência com que um padrão anterior deve ser repetido.
|          |É o operador de OU, mostra os resultados quando uma das duas expressões corresponde
.*         |É o operador de E, os resultados são exibidos apenas se ambas as expressões corresponderem
^          |Corresponde à posição inicial dentro da string. Em ferramentas baseadas em linha, corresponde à posição inicial de qualquer linha.
$          |Corresponde à posição final da string ou à posição logo antes de uma nova linha no final da string. Em ferramentas baseadas em linha, corresponde à posição final de qualquer linha.

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
Há dois tipos de serviços: 
- Internos, serviços relevantes que são necessários para a inicialização do sistema;
- Que são instalados pelo usuário, que incluí todos os serviços do servidor

Esses serviços são executados em segundo palno sem qualquer interação com usuário. Eles são chamados de **daemons** e são identificados por uma letra **d** no final do nome do programa, por exemplo, sshd ou systemd.

**Systemd** é um daemon de _Init process_ (primeiro processo iniciado durante a inicialização), como ele é o primeiro iniciado, ele recebe o ID do processo (PID) 1. Ele monitora e cuida da inicialização e finalização ordenada de outros serviços.

Todos os processos tem um PID atribuído que pode ser visto  em `/proc/`  com o seu número correspondente. Um processo pode ter um ID do processo pai (PPID), então, ele é conhecido como um processo filho.

### Systemctl
É um comando utilizado para gerenciar o Systemd, que é um gerenciador de sistema e serviço.

### Kill a Process
Um processo pode estar nos seguintes estados: 
- Rodando (Running)
- Esperando (Waiting - esperando por um evento ou um recurso do sistema)
- Parado (Stopped)
- Zombie (parado, mas ainda tem uma entrada na tabela de processos)

Os processos podem ser controlados usando `kill`, `pkill`, `pgrep` e `killall`. 

Para interagir com os processos, devemos enviar um sinal para eles. Podemos ver todos os sinais usando o comando:

```
user1@hostname[~]$ kill -l

1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX
```

Os sinais mais usados são:

Sinais  | Descrição
--------|-----------
1       |SIGHUP - É enviado para um processo quando o terminal que o controla foi fechado
2       |SIGINT - Enviado quando o usuário pressiona `[Ctrl] + C` no terminal para interromper um processo
3       |SIGQUIT - Enviado quando um usuário pressiona `[Ctrl] + D` para sair
9       |SIGKILL - Imediatamente mata um processo sem operações de limpeza
15      |SIGTERM - Termina o programa
19      |SIGSTOP - Para o programa. Não pode mais ser manuseado.
20      |SIGSTP - Enviado quando um usuário pressiona `[Ctrl] + Z` para requisitar que um serviço seja suspenso. O usuário pode manusear o serviço mais tarde.

### Background a Process
Às vezes, precisamos colocar um processo que iniciamos em segundo plano para continuarmos usando a atual sessão para interagir com o sistema ou iniciar outros pocessos. Para isso, podemos suspender o processo usando `[Ctrl] + Z`, ou colocar eles em segundo plano.

Suspendendo processos.
```
user1@hostname[~]$ ping -c 10 www.google.com

user1@hostname[~]$ vim tmpfile
[Ctrl + Z]

[2]+  Stopped                 vim tmpfile
```

Todos os processos em segundo plano podem ser vistos usando o seguinte comando:
```
user1@hostname[~]$ jobs

[1]+  Stopped                 ping -c 10 www.google.com
[2]+  Stopped                 vim tmpfile

```

O `[Ctrl] + Z` suspende todos os processos, e eles não serão mais executados. Para mantê-los rodando em segundo plano, temos que digitar o comando `bg` para colocar o processo em segundo plano.

```
user1@hostname[~]$ bg

user1@hostname[~]$ 
---  www.google.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 113482ms

[ENTER]
[1]+  Exit 1                  ping -c 10  www.google.com

```

Outra opção para colocar um processo em segundo plano é colocar um sinal de AND (&) no final do comando.

```
user1@hostname[~]$ ping -c 10 www.google.com &

[1] 10825
PING www.google.com (172.67.1.1) 56(84) bytes of data.
```

Os processos em segundo plano não requerem interação do usuário e podemos usar a mesma sessão de shell sem esperar até que o processo termine primeiro. Assim que a verificação ou processo terminar seu trabalho, seremos notificados pelo terminal de que o processo foi concluído.

### Foreground a Process
Se quisermos colocar o processo em segundo plano em primeiro plano e interagir com ele novamente, podemos usar o comando `fg <ID>`.

```
Daradue@htb[/htb]$ fg 1
ping -c 10 www.google.com

--- www.google.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9206ms
```

### Executando Múltiplos Comandos
Existem três possibilidades para executar vários comandos, um após o outro. Estes são separados por:
- Ponto e vírgula (;)
- Dois Es comerciais (&&)
- Pipes (|)

A diferença entre eles está no tratamento dos processos anteriores e depende se o processo anterior foi concluído com sucesso ou com erros.

O **ponto e vírgula** (;) é um separador de comando e executa os comandos ignorando os resultados e erros dos comandos anteriores.
```
user1@htb[/htb]$ echo '1'; ls MISSING_FILE; echo '3'

1
ls: cannot access 'MISSING_FILE': No such file or directory
3

```

Os **&&** roda os comandos um após o outro. Se houver um erro em um dos comandos, os seguintes não serão mais executados e todo o processo será interrompido.

```
user1@htb[/htb]$ echo '1'; ls MISSING_FILE; echo '3'

1
ls: cannot access 'MISSING_FILE': No such file or directory

```

E os **pipes (|)** dependem não apenas da operação correta e sem erros dos processos anteriores, mas também dos resultados dos processos anteriores.

## Servidores Web
Um componente essencial no linux é a sua comunicação com servidores web. E há diversas maneiras de configurar um servidor web nos sistemas Linux.

### Apache
Apache é um dos servidores web mais utilizado, ao lado do IIS e Nginx.

Com o apache podemos usar módulos que criptografa a comunicação entre o navegador e o servidor (mod_ssl), usar um servidor proxy (mod_proxy), manipular complexos dados dos cabeçalhos HTTP (mod_header) ou de URLs (mod_rewrite).

O Apache nos permite criar páginas web dinamicamente usando linguagens de server-side scripting, como PHP, Perl or Ruby, ou outras linguagens como Python, Javascript, Lua e .NET.

**Instalando o Apache**
```
apt install apache2 -y

```
