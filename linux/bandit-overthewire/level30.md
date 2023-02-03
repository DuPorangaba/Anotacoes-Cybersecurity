# Level 29
**Tópicos**

- [X] [Goal](#goal)
- [ ] [Comandos para o desafio](#comandos-para-esse-level)
- [ ] [Um pouco de Teoria](#teoria)
- [ ] [Write Up](#write-up)
- [ ] [Solução](#soluçao)
- [ ] [Resources](#resources)

## Goal
Há um repositório git em ssh://bandit30-git@localhost/home/bandit30-git/repo. A senha do usuário bandit30-git é a mesma do usuário bandit30.

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

*git tag*

Cria, lista, deleta, ou verifica um objeto de tag assinado com GPG

*git show*

Mostra vários tipos de objetos. 

O GIT tem diversos tipos de objetos, como: blobs, trees, tags and commits. [Para saber mais](https://matthew-brett.github.io/curious-git/git_object_types.html)

*Observação*
Os commits são enumerados de acordo com a distância deles para o passado. Podemos referenciar um commit como "HEAD~1", que seria o estado do repositório um commit no passado. Ou "HEAD~3", que seria o estado do repositório em três commits no passado.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit30`
- Password: `xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Temos que criar um  diretório temporário e ir para ele.

***[# Passo3.]*** Usar `git clone` para clonar o repositório. Basta `git clone URL ou SSH`.  No meu caso, tive que especificar a porta, usando o modelo `ssh://[user@]host.xz[:port]/path/to/repo.git/`.

***[# Passo4.]*** Entrar dentro do **repo**. Depois dar um `git log` e `git show` ou `git log -p` para ver o histórico de commits e as mudanças entre eles. 

Percebemos que não tem nada que pode nos ajudar. 

***[# Passo5.]*** Vamos ver as branches desse repositório. 

Percebemos que não tem nada que pode nos ajudar.

***[# Passo6.]*** Vamos procurar por outros objetos git. Vamos ver as tags, usando `git tag`. 

Vemos que temos uma tag. Para ver ela vamos usar o `git show`.


***[# Passo7.]*** Antes de sair, volte para o homedirectory e remova a pasta temporária. Para sair, rode `exit`

## Solução
<prep>
[[# Passo1.] 
<b>> ssh bandit30@bandit.labs.overthewire.org -p 2220</b>

bandit30@bandit.labs.overthewire.org's password: <b>xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS</b>

[# Passo2.]

<b>bandit30@bandit:~$</b> mktemp -d

/tmp/tmp.jbs4uaL2wM

<b>bandit30@bandit:~$</b> cd /tmp/tmp.jbs4uaL2wM

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM$</b>

[# Passo3.]

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM$</b> git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo

...

bandit30-git@localhost's password:<b>xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS</b>

remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (4/4), 299 bytes | 299.00 KiB/s, done.

[# Passo4.]

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM$</b> ls 

repo

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM$</b> cd repo

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM/repo$</b> ls

README.md

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM/repo$</b> cat README.md

    just an epmty file... muahaha


[# Passo5.] 

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM/repo$</b> git branch -a

    * master
    remotes/origin/HEAD -> origin/master
    remotes/origin/master

[# Passo6.] 

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM/repo$</b> git tag

    secret

<b>bandit30@bandit:/tmp/tmp.jbs4uaL2wM/repo$</b> git show secret

    OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt

[# Passo7.] 
<b>bandit30@bandit:tmp/tmp.jbs4uaL2wM/repo$</b> cd ~

<b>bandit30@bandit:~$</b> rm -r /tmp/tmp.jbs4uaL2wM

<b>bandit30@bandit:~$</b> exit

logout                    

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 31:**
- Username: `bandit31`
- Password: `OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit31.html)
