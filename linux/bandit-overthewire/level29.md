# Level 29
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há um repositório git em ssh://bandit29-git@localhost/home/bandit29-git/repo. A senha do usuário bandit29-git é a mesma do usuário bandit29.

Clone o repositório e encontre a senha para o próximo nível.

## Comandos para esse level
`git`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 git      |o estúpido rastreador de conteúdo

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
**GIT**

Git é um sistema de controle de versão para acompanhar as alterações em arquivos e projetos ao longo do tempo. [Para saber mais](https://git-scm.com/docs)

*git log*
Mostra os commit logs.

Listando os commits que podem ser acessados seguindo os links pai do(s) commit(s) fornecido(s)

A saída é fornecida em ordem cronológica reversa por padrão.

*git show* ou *git log -p*
Mostra a mensagem de log e o diff textual dos commits.

*git branch*

Lista, cria, ou deleta branches

- *-l* Listar branches. Com <padrão> opcional..., por ex. git branch --list 'maint-*', lista apenas as ramificações que correspondem ao(s) padrão(s)
- *-r* lista ou deleta (se usado com -d) os branches de rastreamento remoto

*git checkout*

Muda entre as branches ou restaura arquivos da árvore de trabalho

`git checkout <branch>` 

Para se preparar para trabalhar no <branch>, mude para ele atualizando o índice e os arquivos na árvore de trabalho e apontando HEAD para o branch. As modificações locais nos arquivos na árvore de trabalho são mantidas, para que possam ser confirmadas no <branch>.

*Observação*
Os commits são enumerados de acordo com a distância deles para o passado. Podemos referenciar um commit como "HEAD~1", que seria o estado do repositório um commit no passado. Ou "HEAD~3", que seria o estado do repositório em três commits no passado.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit29`
- Password: `tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Temos que criar um  diretório temporário e ir para ele.

***[# Passo3.]*** Usar `git clone` para clonar o repositório. Basta `git clone URL ou SSH`.  No meu caso, tive que especificar a porta, usando o modelo `ssh://[user@]host.xz[:port]/path/to/repo.git/`.

***[# Passo4.]*** Entrar dentro do **repo**. Depois dar um `git log` e `git show` ou `git log -p` para ver o histórico de commits e as mudanças entre eles. 

Percebemos que não tem nada que pode nos ajudar. 

***[# Passo5.]*** Vamos ver as branches desse repositório. Primeiro, vamos ver as branch locais e depois as remotas. 

Vemos que há várias branches remotas. Vamos ver o que tem em cada, usando o `git checkout` para mudar de branch e o `git log -p` para ver o histórico de commits e as mudanças.

***[# Passo6.]*** Para sair, rode `exit`

## Solução
<prep>
[[# Passo1.] 
<b>> ssh bandit29@bandit.labs.overthewire.org -p 2220</b>

bandit29@bandit.labs.overthewire.org's password: <b>AVanL161y9rsbcJIsFHuw35rjaOM19nR</b>

[# Passo2.]

<b>bandit29@bandit:~$</b> mktemp -d

/tmp/tmp.Iz9wAAswVB

<b>bandit29@bandit:~$</b> cd /tmp/tmp.Iz9wAAswVB

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVB$</b>

[# Passo3.]

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX$</b> git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo

...

bandit29-git@localhost's password:<b>tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S</b>

bandit29-git@localhost's password:
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (16/16), done.
Resolving deltas: 100% (2/2), done.

[# Passo4.]

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX$</b> ls 

repo

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX$</b> cd repo

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> ls

README.md

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> cat README.md

    # Bandit Notes
    Some notes for bandit30 of bandit.

    ## credentials

    - username: bandit30
    - password: <no passwords in production!>


[# Passo5.] 

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> git branch -l

* master

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> git branch -r

    origin/HEAD -> origin/master
    origin/dev
    origin/master
    origin/sploits-dev

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> git checkout dev

Branch 'dev' set up to track remote branch 'dev' from 'origin'.

Switched to a new branch 'dev'

<b>bandit29@bandit:/tmp/tmp.Iz9wAAswVBX/repo$</b> git log -p

    commit be91af8ed9847de549d0e3361cfc675674b25867 (HEAD -> dev, origin/dev)
    Author: Morla Porla <morla@overthewire.org>
    Date:   Wed Jan 11 19:18:55 2023 +0000

        add data needed for development

    diff --git a/README.md b/README.md
    index 1af21d3..a4b1cf1 100644
    --- a/README.md
    +++ b/README.md
    @@ -4,5 +4,5 @@ Some notes for bandit30 of bandit.
    ## credentials

    - username: bandit30
    -- password: <no passwords in production!>
    +- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS


    commit 081cefe55da9661fb5e31f8f3a3132398c27be31
    Author: Ben Dover <noone@overthewire.org>
    Date:   Wed Jan 11 19:18:54 2023 +0000

        add gif2ascii

    diff --git a/code/gif2ascii.py b/code/gif2ascii.py
    new file mode 100644
    index 0000000..8b13789
    --- /dev/null
    +++ b/code/gif2ascii.py
    @@ -0,0 +1 @@
    +

    commit 8159c819f4d37d9491254035c9e74ffcb316652e (origin/master, origin/HEAD)
    Author: Ben Dover <noone@overthewire.org>
    Date:   Wed Jan 11 19:18:54 2023 +0000

        fix username

    diff --git a/README.md b/README.md
    index 2da2f39..1af21d3 100644
    --- a/README.md
    +++ b/README.md
    @@ -3,6 +3,6 @@ Some notes for bandit30 of bandit.

    ## credentials

    -- username: bandit29
    +- username: bandit30
    - password: <no passwords in production!>


    commit 23706c87f70872af9f04744569f7b6273647fb14 (master)
    Author: Ben Dover <noone@overthewire.org>
    Date:   Wed Jan 11 19:18:54 2023 +0000

        initial commit of README.md

    diff --git a/README.md b/README.md
    new file mode 100644
    index 0000000..2da2f39
    --- /dev/null
    +++ b/README.md
    @@ -0,0 +1,8 @@
    +# Bandit Notes
    +Some notes for bandit30 of bandit.
    +
    +## credentials
    +
    +- username: bandit29
    +- password: <no passwords in production!>


[# Passo6.] 
<b>bandit#@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 30:**
- Username: `bandit30`
- Password: `xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit30.html)
