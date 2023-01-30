# Level 25
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Logar no bandit26 do bandit25 deve ser bem fácil... O shell do usuário bandit26 não é /bin/bash, mas outra coisa. Descubra o que é, como funciona e como sair dela.

## Comandos para esse level
`ssh`, `cat`, `more`, `vi`, `ls`, `id`, `pwd`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ssh      |Client de login remoto OpenSSH
 cat      |concatenar arquivos e imprimir na saída padrão
 more     |filtro de leitura  de arquivo para visualização crt
 vi       |Vi IMproved, um editor de texto para programadores
 ls       |lista o conteúdo do diretório
 id       |imprima IDs reais e efetivas de usuários e grupos
 pwd      |imprimi o nome do diretório atual/de trabalho

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
**/etc/passwd**

É um arquivo que armazena as informações essenciais que são necessárias durante o login. É um arquivo texto simples. E contém uma lista com todas as contas do sistema, elencando o user ID, group ID, homedirectory, shell, etc, de cada uma das contas. [Para saber mais](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

**vim**
[Para saber mais](https://vimhelp.org/quickref.txt.html)

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit25`
- Password: `p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]***  Dando um `ls`, vemos que no nosso homedirectory, temos uma **private key** para acessarmos o próximo level, bandit26. Se tentarmos logar usando o arquivo, conseguimos logar no entanto a nossa conexão é fechada logo depois. 

***[# Passo3.]*** Para saber qual é o shell do usuário bandit26, temos que acessar o arquivo **/etc/passwd**. Para isso podemos usar o `grep` que facilita a localização do usuário bandit26. Temos que o shell do usuário bandit26, está definido em **/usr/bin/showtext**.

***[# Passo4.]*** Vamos ver o que tem dentro do **/usr/bin/showtext**, usando `cat`. 

O código dentro do **/usr/bin/showtext**, simplesmente, indica que quando entramos no bandit26, usado o `more` para abrir um arquivo **text.txt** no homedirectory e depois disso a execução é parada. Por isso, quando tentamos entrar da primeira vez não conseguimos, porque ele printa na tela o arquivo **text.txt** e logo depois já saímos. *Nota: é printado na tela bandit26*

***[# Passo5.]*** Para evitar a nossa saída do usuário bandit26, temos que deixar o nosso terminal pequeno e assim, tentar conectar usando o ssh novamente.

***[# Passo6.]*** Com isso, podemos rodar o `vim` dentro do arquivo,apenas apertando a tecla v. Primeiro, conseguir um shell e depois a senha. Para o shell, a partir do vim, podemos usar o comando `:shell`. No entanto, voltamos para o `more`. 

Isso ocorre, pois quando usamos `:shell` ele cria o shell que está definido no arquivo **/etc/passwd**, que no nosso caso é o */usr/bin/showtext*. Assim, iremos especificar qual shell queremos usando o `set` e depois dar um `:shell` novamente.

***[# Passo7.]*** Agora, podemos pegar a senha do bandit26, tranquilamente.

***[# Passo8.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit25@bandit.labs.overthewire.org -p 2220</b>

bandit25@bandit.labs.overthewire.org's password: <b>p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d</b>

[# Passo2.]

<b>bandit25@bandit:~$</b> ls 

bandit26.sshkey

<b>bandit25@bandit:~$</b> ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire -p 2220

...

Welcome to OverTheWire!

...

Connection to bandit.labs.overthewire.org closed.

[# Passo3.] 

<b>bandit25@bandit:~$</b> grep "bandit26" /etc/passwd

bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

[# Passo4.] 

<b>bandit25@bandit:~$</b> cat /usr/bin/showtext

<em>
#!/bin/sh

export TERM=linux

exec more ~/text.txt

exit 0
</em>

[# Passo5.]

Terminal com tamanho reduzido.

<b>bandit25@bandit:~$</b> ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire -p 2220

...

--More--(83%)

[# Passo6.]

**Dentro do more**

v

**Dentro do vim**

:set shell=/bin/bash

:shell

bandit26@bandit:~$

[# Passo7.]

bandit26@bandit:~$ cat /etc/bandit_pass/bandit26

c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1


[# Passo8.] 
<b>bandit25@bandit:~$</b> exit

logout      

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 26:**
- Username: `bandit26`
- Password: `c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit26.html)
