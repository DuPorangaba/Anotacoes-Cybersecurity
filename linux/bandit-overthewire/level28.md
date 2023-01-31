# Level 28
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [x] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há um repositório git em ssh://bandit28-git@localhost/home/bandit28-git/repo. A senha do usuário bandit28-git é a mesma do usuário bandit28.

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

*git show*
Mostra vários tipos de objetos

Para commits, ele mostra a mensagem de log e o diff textual.

*Observação*
Os commits são enumerados de acordo com a distância deles para o passado. Podemos referenciar um commit como "HEAD~1", que seria o estado do repositório um commit no passado. Ou "HEAD~3", que seria o estado do repositório em três commits no passado.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit28`
- Password: `AVanL161y9rsbcJIsFHuw35rjaOM19nR`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Temos que criar um  diretório temporário e ir para ele.

***[# Passo3.]*** Usar `git clone` para clonar o repositório. Basta `git clone URL ou SSH`.  No meu caso, tive que especificar a porta, usando o modelo `ssh://[user@]host.xz[:port]/path/to/repo.git/`.

***[# Passo4.]*** Usando o `ls` para checar se deu certo a clonagem. Se deu certo, entrar no diretório **repo**. Dentro do repo, temos o **README.md**, dentro do arquivo temos o usuário e a senha para o bandit29, no entanto a senha está censurada.  

***[# Passo5.]*** Com o `git log` iremos ver os logs dos commits.

***[# Passo6.]*** Temos que o último commit foi onde a senha foi censurada, assim apenas precisamos ver ele. Para isso usaremos `git show`. E pronto temos a senha.

***[# Passo7.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit28@bandit.labs.overthewire.org -p 2220</b>

bandit28@bandit.labs.overthewire.org's password: <b>AVanL161y9rsbcJIsFHuw35rjaOM19nR</b>

[# Passo2.]

<b>bandit28@bandit:~$</b> mktemp -d

/tmp/tmp.qhGgQP48T6

<b>bandit28@bandit:~$</b> cd /tmp/tmp.qhGgQP48T6

<b>bandit28@bandit:/tmp/tmp.qhGgQP48T6$</b>

[# Passo3.]

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX$</b> git clone ssh://bandit28-git@localhost:2220/home/bandit27-git/repo

...

bandit28-git@localhost's password:<b>AVanL161y9rsbcJIsFHuw35rjaOM19nR</b>
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.

[# Passo4.]

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX$</b> ls

repo

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX$</b> cd repo

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX/repo$</b> ls

README.md

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX/repo$</b> cat README.md

    # Bandit Notes
    Some notes for level29 of bandit.

    ## credentials

    - username: bandit29
    - password: xxxxxxxxxx

[# Passo5.]

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX/repo$</b> git log

    commit c6dc61e6ffdc717253130886555d087cac472f50 (HEAD -> master, origin/master, origin/HEAD)
    Author: Morla Porla <morla@overthewire.org>
    Date:   Wed Jan 11 19:18:53 2023 +0000

        fix info leak

    commit 2c1f82f75ab09c89166dd9e6e351bf479fb2d48f
    Author: Morla Porla <morla@overthewire.org>
    Date:   Wed Jan 11 19:18:53 2023 +0000

        add missing data

    commit 444da53e268c462d39cf7441a3bbf7af1832e21f
    Author: Ben Dover <noone@overthewire.org>
    Date:   Wed Jan 11 19:18:53 2023 +0000

        initial commit of README.md

[# Passo6.]

<b>bandit28@bandit:/tmp/tmp.I1LTThjopX/repo$</b> git show

    commit c6dc61e6ffdc717253130886555d087cac472f50 (HEAD -> master, origin/master, origin/HEAD)
    Author: Morla Porla <morla@overthewire.org>
    Date:   Wed Jan 11 19:18:53 2023 +0000

        fix info leak

    diff --git a/README.md b/README.md
    index b302105..5c6457b 100644
    --- a/README.md
    +++ b/README.md
    @@ -4,5 +4,5 @@ Some notes for level29 of bandit.
    ## credentials

    - username: bandit29
    -- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
    +- password: xxxxxxxxxx

[# Passo7.] 
<b>bandit#@bandit:~$</b> exit

logout

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 29:**
- Username: `bandit29`
- Password: `tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit29.html)


