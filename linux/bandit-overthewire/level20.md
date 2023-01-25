# Level 20
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há um setuid binary no homedirectory que faz o seguinte: ele faz uma conexão com o localhost com a porta especificada como argumento do commandline. Então, lê uma linha de texto da conexão e compara com a senha do level anterior. Se a senha estiver correta, ela era transmitir a senha para o próximo level (bandit21)

*NOTE: Tente conectar-se ao seu próprio daemon de rede para ver se funciona como você pensa*

## Comandos para esse level
`ssh`, `nc`, `cat`, `bash`, `screen`, `tmux`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ssh      |loga em uma máquina remota e executa comandos remotamente nesta máquina
 nc       |canivete suíço de TCP/IP
 cat      |Concatena arquivos e printa na saída padrão
 bash     |GNU Bourne-Again SHell. 
 screen   |gerenciador de tela com emulação de terminal VT100/ANSI
 tmux     |multiplexador terminal

 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

**Unix Job Control**

 O controle de trabalho refere-se à capacidade de interromper (suspender) seletivamente a execução de processos e continuar (retomar) sua execução posteriormente.
 
 A tabela a seguir lista comandos básicos do [Unix Job Control](https://www.gnu.org/software/bash/manual/html_node/Job-Control-Basics.html)

  Comandos |                             O que faz?
 --------- |--------
 &         |Executa o comando no segundo plano
 Ctrl-z    |Interrompe o processo em primeiro plano
 jobs      |Lista os processos em segundo plano
 bg        |Recomeça um processo em segundo plano interrompido 
 fg        |Traz um processo em segundo plano para o primeiro plano
 kill      |Mata um processo
 ~ Ctrl-z  |Suspende um `rlogin` ou uma sessão `ssh` 
 ~~ Ctrl-z |Suspende um `rlogin` ou uma sessão `ssh` de segundo nível
 %n        |Refere-se ao processo em segundo plano de número `n`
 %?str     |Refere-se ao processo em segundo plano que contém `str`



## Teoria

**echo**

É um comando utilizado para mostrar uma linha de texto. 

**nc**

No seu uso mais simples, `nc host port` cria uma conexão TCP na porta dada no host de destino dado. A sua entrada padrão é enviada para o host, e tudo que volta pela conexão é enviada para a saída padrão

Além disso, netcat pode funcionar com um server, ouvindo conexões de entrada em portas arbitrárias. 

**&**

É um controle de trabalho que executa o comando em segundo plano. Tem uma sintaxe simples: `<comando> &`


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit20`
- Password: `VxCazJaVykI6W36BkBU0mJTCM8rR95XT`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Usar `ls` para verificar se o **setuid binary** está no homedirectory.

***[# Passo3.]*** Usaremos o `nc` como server no modo listening. Dessa forma através do `piping`, utilizaremos o `echo` para passar a senha para o server criado. E executaremos isso em segundo plano.

***[# Passo4.]*** Por fim, utilizaremos o **setuid binary** para acessar o localhost na porta que está rodando o server criado pelo `nc`.

***[# Passo5.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit20@bandit.labs.overthewire.org -p 2220</b>
bandit20@bandit.labs.overthewire.org's password: <b>VxCazJaVykI6W36BkBU0mJTCM8rR95XT</b>

[# Passo2.]
<b>bandit20@bandit:~$</b> ls
suconnect

[# Passo3.] 
<b>bandit20@bandit:~$</b> echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -l 1234 &
[1] 468393

[# Passo4.]
<b>bandit20@bandit:~$</b> ./suconnect 1234
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

[# Passo5.]
<b>bandit20@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 21:**
- Username: `bandit21`
- Password: `NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit21.html)


