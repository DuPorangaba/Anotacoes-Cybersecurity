# Level 27
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há um repositório git em ssh://bandit27-git@localhost/home/bandit27-git/repo. A senha do usuário bandit27-git é a mesma do usuário bandit27.

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


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit27`
- Password: `YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Temos que criar um  diretório temporário e ir para ele.

***[# Passo3.]*** Usar `git clone` para clonar o repositório. Basta `git clone URL ou SSH`. 

Eu tive problemas em me conectar com o SSH, pois dava que eu estava tentando logar na porta 22 e sabemos que devemos estar na porta 2220, então tive que especificar a porta assim: `ssh://[user@]host.xz[:port]/path/to/repo.git/`

***[# Passo4.]*** Vamos dar um `ls` para ter certeza que o repositório foi clonado. Depois, vamos entrar no repositório. Vemos que dentro dele, existe um README, com o `cat` vamos ler o README. E pronto temos a senha.

***[# Passo*.]*** Vamos voltar para o home directory, remover o diretório temporário, e por fim, sair rodando `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit27@bandit.labs.overthewire.org -p 2220</b>

bandit27@bandit.labs.overthewire.org's password: <b>YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS</b>

[# Passo2.]

<b>bandit27@bandit:~$</b> mktemp -d

/tmp/tmp.I1LTThjopX

<b>bandit27@bandit:~$</b> cd /tmp/tmp.I1LTThjopX

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX$</b>

[# Passo3.]

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX$</b> git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo

...

bandit27-git@localhost's password:<b>YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS</b>
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
Receiving objects: 100% (3/3), 286 bytes | 286.00 KiB/s, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0

[# Passo4.] 

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX$</b> ls

repo

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX$</b>cd repo

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX/repo$</b> ls

README

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX/repo$</b> cat README

The password to the next level is: AVanL161y9rsbcJIsFHuw35rjaOM19nR

[# Passo5.] 

<b>bandit27@bandit:/tmp/tmp.I1LTThjopX/repo$</b> cd ~

<b>bandit27@bandit:~$</b> rm -r /tmp/tmp.I1LTThjopX

<b>bandit27@bandit:~$</b> exit

logout               

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 28:**
- Username: `bandit28`
- Password: `AVanL161y9rsbcJIsFHuw35rjaOM19nR`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit28.html)

