# Level 14
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level pode ser obtida usando a senha do level atual para a porta 30000 no localhost. *Nota: `localhost` é o hostname que se refere a máquina que você está trabalhando*

## Comandos para esse level
`ssh`, `telnet`, `nc`, `openssl`, `s_client`, `nmap`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ssh      |usado para logar em máquinas remotas e para executar comandos nelas
 telnet   |usado para se comunica com outro host usando o protocolo TELNET
 nc       |Canivete suiço TCP/IP. Lê e escreve dados através de conexões de rede, usando o protocolo TCP ou UDP
 openssl  |Programa de linha de comando de OpenSSL. Em que OpenSSL é um kit de ferramentas de criptografia.
 s_client |SSL/TLS client program
 nmap     |Ferramenta de exploração de rede e scanner de segurança/porta

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
**Localhost** é um hostname que se refere ao dispositivo atual usado para acessá-lo. O seu endereço de IP é 127.0.0.1.

**`nc` ou `netcat`**

é um comando que permite ler e escrever dados através de uma conexão de rede. Pode ser usado para conexões TCP e UDP. 

Para se conectar a um serviço (como client) em uma rede, a sintaxe do comando é a seguinte: `nc <host> <port>`. Para criar um servidor que escuta os pacotes recebidos, o comando se parece com este: `nc -l <port>`.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit14`
- Password: `fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Usando `nc` nos conectar com o localhost port 30000 e iremos enviar a senha.

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit14@bandit.labs.overthewire.org -p 2220</b>
bandit14@bandit.labs.overthewire.org's password: <b>fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq</b>

[# Passo2.]
<b>bandit14@bandit:~$</b> nc localhost 300000
>fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
 Correct!                                                              jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

[# Passo*.] 
<b>bandit14@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level:**
- Username: `bandit15`
- Password: `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`

## Resources
[OverTheWire](http_do_overthewire)

[Level14 -> 15](https://mayadevbe.me/posts/overthewir)

