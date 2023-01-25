# Level 22
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Um programa está rodando automaticamente em intervalos regulares do cron, o agendador de tarefas baseado em tempo. Procure em /etc/cron.d/ a configuração e veja qual comando está sendo executado.

*NOTE: Observar scripts de shell escritos por outras pessoas é uma habilidade muito útil. O script para este nível é intencionalmente fácil de ler. Se você estiver tendo problemas para entender o que ele faz, tente executá-lo para ver as informações de depuração que ele imprime.*

## Comandos para esse level
`cron`, `crontab`, `crontab(5)`

*Nota: Nem todos os comandos listados são necessários*

 Comandos  |                          O que faz?
 ----------|--------
 cron      |daemon (é um programa de computador que executa como um processo em plano de fundo) para executar comandos programados
 crontab   |manter arquivos crontab para usuários individuais
 crontab(5)|tabelas para conduzir o cron
 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
É a mesma teoria da level 22. 

Nesse desafio, apenas devemos executar o script do arquivo `.sh` para achar a senha. 

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit22`
- Password: `WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Seguindo o enunciado iremos entrar no diretório `/etc/cron.d` e ver o que tem lá usando `ls`.

***[# Passo3.]*** Há diversos arquivos no `/etc/cron.d`. Iremos ver o que tem no `cronjob_bandit23` usando `cat`, já que queremos a senha para o bandit23.

***[# Passo4.]*** O código dentro do `cronjob_bandit23` significa que em um período de tempo um comando é executado. O comando nesse caso é rodar um arquivo `.sh`, e a stdout e stderr são descartados. Dessa maneira, vamos dar uma olhada nesse arquivo `.sh`, usando `cat` novamente.

***[# Passo5.]*** Dentro do arquivo `.sh`, temos um código que pega o nome de usuário e executa um comando que produz um hash através da mensagem "I am user $myname". Para descobrir o hash, rodaremos o código dentro do arquivo substituindo "$myname" para "bandit23", `echo I am user bandit23 | md5sum | cut -d ' ' -f 1`

***[# Passo6.]*** Além disso, no arquivo `.sh`, temos que a senha do bandit23 é passado para o arquivo /tmp/hash que achamos no passo anterior. Dessa maneira, iremos acessar esse arquivo para achar a senha.

***[# Passo7.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit22@bandit.labs.overthewire.org -p 2220</b>

bandit22@bandit.labs.overthewire.org's password: <b>WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff</b>

[# Passo2.]

<b>bandit22@bandit:~$</b> cd /etc/cron.d

<b>bandit22@bandit:/etc/cron.d$</b> ls

cronjob_bandit15_root  cronjob_bandit23       e2scrub_all

cronjob_bandit17_root  cronjob_bandit24       otw-tmp-dir

cronjob_bandit22       cronjob_bandit25_root  sysstat

[# Passo3.]

<b>bandit22@bandit:/etc/cron.d$</b> cat cronjob_bandit23

@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

[# Passo4.]

<b>bandit22@bandit:/etc/cron.d$</b> cat /usr/bin/cronjob_bandit23.sh

#!/bin/bash

myname=$(whoami)

mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

[# Passo5.]

<b>bandit22@bandit:/etc/cron.d$</b> echo I am user bandit23 | md5sum | cut -d ' ' -f 1

8ca319486bfbbc3663ea0fbe81326349


[# Passo6.]

<b>bandit22@bandit:/etc/cron.d$</b> cat /tmp/8ca319486bfbbc3663ea0fbe81326349

QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G

[# Passo7.] 

<b>bandit22@bandit:~$</b> exit

logout                     

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 23:**
- Username: `bandit23`
- Password: `QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit23.html)


