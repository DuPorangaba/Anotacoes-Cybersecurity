# Level 21
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Um programa está rodando automaticamente em intervalos regulares do cron, o agendador de tarefas baseado em tempo. Procure em /etc/cron.d/ a configuração e veja qual comando está sendo executado.

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
**crontab(5)**

Nesse desafio, usaremos `man 5 crontab` para entender como uma tabela cron está organizada. E percebemos que em um arquivo crontab são organizados por um linhas que seguem um padrão:

`<cronograma_execucao> <usuário_que_executa> <comando> &> /dev/null`

*&>*

Indica o redirecionamento da saída padrão e da saída padrão de erro  para algum arquivo.

*Cronograma de execução*

No campo de cronograma de execução da linha do arquivo crontab, podemos ter 5 campos, ou alguma palavra chave. 

Nesse desafio aparece os dois tipos:

- a palavra chave: @reboot, que significa que o comando é rodado uma vez  na inicialização
- 5 campos: * * * * *, que representam, respectivamente, os minutos, as horas, um dia no mês, o mês, e o dia na semana. Além disso, a * significa sempre. Assim, o 5 asteriscos significam cada minuto de cada hora de cada dia de cada mês e cada dia da semana, ou seja, todo momento.

**.sh**

São arquivos conhecidos como scritps que o Bash programa e usa. Esses arquivos podem ser executados se os comandos estiverem digitados de acordo como a interface da linha de comando do shell. 

A primeira linha desses arquivos são o caminho para o intepretador. E depois temos os comandos.

**chmod 644**

O código 644 significa que o proprietário pode ler e escrever no arquivo, enquanto os membros do grupo e outros usuários podem apenas ler. 



## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit21`
- Password: `NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Como sugestão do enunciado iremos entrar no diretório `/etc/cron.d` e ver o que tem lá usando `ls`.

***[# Passo3.]*** Há diversos arquivos no `/etc/cron.d`. Iremos ver o que tem no `cronjob_bandit22` usando `cat`, já que queremos a senha para o bandit22.

***[# Passo4.]*** O código dentro do `cronjob_bandit22` significa que em um período de tempo um comando é executado. O comando nesse caso é rodar um arquivo `.sh`, e a stdout e stderr são descartadas. Dessa maneira, vamos dar uma olhada nesse arquivo `.sh`, usando `cat` novamente.

***[# Passo5.]*** Dentro do arquivo `.sh`, temos uma mudança de permissão (644 todos podem ler, mas apenas o proprietário pode alterar) para algum arquivo no /tmp e que pega-se a senha do bandit 22 e passam para esse arquivo. Assim, podemos acessar o arquivo no /tmp para conseguir a senha. 

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit21@bandit.labs.overthewire.org -p 2220</b>
bandit21@bandit.labs.overthewire.org's password: <b>NvEJF7oVjkddltPSrdKEFOllh9V1IBcq</b>

[# Passo2.]

<b>bandit21@bandit:~$</b> cd /etc/cron.d 

<b>bandit21@bandit:/etc/cron.d$</b> ls

cronjob_bandit15_root  cronjob_bandit23       e2scrub_all

cronjob_bandit17_root  cronjob_bandit24       otw-tmp-dir

cronjob_bandit22       cronjob_bandit25_root  sysstat

[# Passo3.]

<b>bandit21@bandit:/etc/cron.d$</b> cat cronjob_bandit22

@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

<code>* * * * *</code> bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

[# Passo4.]

<b>bandit21@bandit:/etc/cron.d$</b> cat /usr/bin/cronjob_bandit22.sh

#!/bin/bash

chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

[# Passo5.]

<b>bandit21@bandit:/etc/cron.d$</b> cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff

[# Passo6.] 

<b>bandit21@bandit:~$</b> exit

logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 22:**
- Username: `bandit22`
- Password: `WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit22.html)

