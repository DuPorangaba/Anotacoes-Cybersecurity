# Level 15
**Tópicos**

- [ ] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [ ] [Um pouco de Teoria](#teoria)
- [ ] [Write Up](#write-up)
- [ ] [Solução](#soluçao)
- [ ] [Resources](#resources)

## Goal
Enunciado resumido do Bandit

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
Um pouco sobre os comandos, sobre como funciona etc

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit15`
- Password: `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** passo2

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit15@bandit.labs.overthewire.org -p 2220</b>
bandit#@bandit.labs.overthewire.org's password: <b>jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt</b>

[# Passo2.]
...

[# Passo*.] 
<b>bandit15@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level:**
- Username: bandit#
- Password: ##############################

## Resources
[OverTheWire](http_do_overthewire)

[Template inspirado no The Girl Who Encrypts](https://medium.com/@theGirlWhoEncrypts/overthewire-bandit-level-5-level-6-155eda2a35a)

