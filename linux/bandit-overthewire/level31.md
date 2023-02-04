# Level 31
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há um repositório git em ssh://bandit31-git@localhost/home/bandit31-git/repo. A senha do usuário bandit31-git é a mesma do usuário bandit31.

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

*.gitignore*

É um arquivo em que são especificados intencionalmente os arquivos untracked que devem ser ignorados.

*git push*

Atualize as referências remotas junto com os objetos associados

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit31`
- Password: `OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Temos que criar um  diretório temporário e ir para ele.

***[# Passo3.]*** Usar `git clone` para clonar o repositório. Basta `git clone URL ou SSH`.  No meu caso, tive que especificar a porta, usando o modelo `ssh://[user@]host.xz[:port]/path/to/repo.git/`.

***[# Passo4.]*** Entrar dentro do **repo**. E ver o que tem dentro.

Vemos que tem um arquivo README.md, que fala que devemos dar um "push" em um arquivo para o repositório remoto. E dá os detalhes do arquivo. 

Além disso, temos um arquivo .gitignore, que temos que olhar também.

***[# Passo5.]*** Vamos ver o git ignore. E depois criar um arquivo de acordo com os detalhes dado. 

***[# Passo6.]*** Pelo .gitignore, o git deve ignorar todos os arquivos que tenha a extensão **.txt**. Dessa maneira, devemos deletar o .gitignore (ou editá-lo) e depois da um push. 

***[# Passo7.]*** Antes de sair, volte para o homedirectory e remova a pasta temporária. Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit31@bandit.labs.overthewire.org -p 2220</b>

    bandit31@bandit.labs.overthewire.org's password: OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt

[# Passo2.]

<b>bandit31@bandit:~$</b> mktemp -d

    /tmp/tmp.9lC0Cm2oto

<b>bandit31@bandit:~$</b> cd /tmp/tmp.9lC0Cm2oto

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto$</b>

[# Passo3.]

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto$</b> git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo

    ...

    bandit31-git@localhost's password:<b>OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt</b>

    remote: Enumerating objects: 4, done.
    remote: Counting objects: 100% (4/4), done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
    Receiving objects: 100% (4/4), done.

[# Passo4.]

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto$</b> ls -la

    total 20
    drwxrwxr-x 3 bandit31 bandit31 4096 Feb  3 22:56 .
    drwx------ 3 bandit31 bandit31 4096 Feb  3 22:56 ..
    drwxrwxr-x 8 bandit31 bandit31 4096 Feb  3 22:56 .git
    -rw-rw-r-- 1 bandit31 bandit31    6 Feb  3 22:56 .gitignore
    -rw-rw-r-- 1 bandit31 bandit31  147 Feb  3 22:56 README.md

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto$</b> cd repo

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> ls

    README.md

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> cat README.md

    This time your task is to push a file to the remote repository.

    Details:
        File name: key.txt
        Content: 'May I come in?'
        Branch: master

[# Passo5.]

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> cat .gitignore

    *.txt

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> nano key.txt

    *Dentro do key.txt no nano* 
    May I come in?

[# Passo6.]

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> rm .gitignore

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> git add key.txt

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> git commit -m "Create key.txt"

<b>bandit31@bandit:/tmp/tmp.9lC0Cm2oto/repo$</b> git push origin master

    ...

    bandit31-git@localhost's password: OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
    Enumerating objects: 4, done.
    Counting objects: 100% (4/4), done.
    Delta compression using up to 2 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
    Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    remote: ### Attempting to validate files... ####
    remote:
    remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
    remote:
    remote: Well done! Here is the password for the next level:
    remote: rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
    remote:
    remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
    remote:
    To ssh://localhost:2220/home/bandit31-git/repo


[# Passo7.] 
<b>bandit30@bandit:tmp/tmp.jbs4uaL2wM/repo$</b> cd ~

<b>bandit30@bandit:~$</b> rm -r /tmp/tmp.jbs4uaL2wM

<b>bandit30@bandit:~$</b> exit

logout                    

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 32:**
- Username: `bandit32`
- Password: `rmCBvG56y58BXzv98yZGdO7ATVL5dW8y`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit32.html)

