# Level 16
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
As credenciais para o próximo nível podem ser recuperadas enviando a senha do nível atual para uma porta no host local no intervalo de 31000 a 32000. Primeiro descubra qual dessas portas tem um servidor escutando nelas. Em seguida, descubra quais deles falam SSL e quais não. Existe apenas 1 servidor que fornecerá as próximas credenciais, os outros simplesmente enviarão de volta para você o que você enviar para ele.

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
**nmap**

É uma ferramenta de exploração de rede e de scanner de segurança e portas. Neste desafio, usaremos sua função de scannear portas.

`nmap [Scan Type...] [Options] {target specification}`

Passaremos como flags:

**-sV**: sonda portas abertas para determinar informações de serviço/versão

**-p**: Escaneia as portas especificadas. Por exemplo: -p1-65535.

E o alvo será o **localhost**.

**openssl s_client**

O comando `openssl s_client` implementa um client genérico que se conecta com um host remoto usando SSL/TLS.

`openssl s_client [flags] hostname:port`

Nesse caso, não passaremos nenhuma flag. E a porta será a encontrada pelo **nmap** que bate com as especificações do enunciado.

**chmod**

Alterar bits de modo de arquivo. [Para saber mais](https://www.gnu.org/software/coreutils/chmod)


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit16`
- Password: `JQttfApK4SeyHwDlI9SXGR50qclOAil1`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Vamos descobrir quais são as portas abertas, e qual delas "falam" SSL. Para isso, vamos usar `nmap` para analisar da porta 31000 até 32000 do localhost. A porta que queremos será aquela que "fala" SSL e não é echo (ou seja, envia de volta para você o que você enviar para ele).

***[# Passo3.]*** Depois de descobrir qual porta que é. Usaremos `openssl s_client` para se conectar com o localhost na porta encontrada. A conexão SSL retornará a chave privada para acessar o próximo level.

***[# Passo4.]*** No home directory(~) não temos a permissão de criar arquivos. Dessa maneira, iremos criar uma pasta no `/tmp` usando `mkdir`. E ir para a pasta criada através do `cd`. Por fim, criar um arquivo para colar a chave privada nele. 

***[# Passo5.]*** Se tentarmos acessar o bandit17 através do `ssh` usando a private key, ainda não conseguiremos, receberemos a mensagem:

`WARNING: UNPROTECTED PRIVATE KEY FILE!`

`Permissions 0664 for 'sshkey.private' are too open.`

`It is required that your private key files are NOT accessible by others.`

`This private key will be ignored.`

Dessa maneira, devemos mudar as permissões do arquivo que tem a private key com o `chmod`, para que apenas o proprietário leia e escreva no arquivo.

***[# Passo6.]*** Agora, é só logar no bandit17 usando o arquivo com a private key e `ssh`.

***[# Passo7.]*** Por fim, já logado no bandit17, pegue a senha do level 17 usando `cat /etc/bandit_pass/bandit17`

***[# Passo8.]*** Devemos sair do bandit17 e do bandit16, para isso rode `exit` duas vezes.

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit16@bandit.labs.overthewire.org -p 2220</b>
bandit16@bandit.labs.overthewire.org's password: <b>JQttfApK4SeyHwDlI9SXGR50qclOAil1</b>

[# Passo2.]
<b>bandit16@bandit:~$</b> nmap -sV -p31000-32000 localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2023-01-19 20:18 UTC                    
Nmap scan report for localhost (127.0.0.1)                                         
Host is up (0.00012s latency).                                                     
Not shown: 996 closed ports                                                        
PORT      STATE SERVICE     VERSION                                                
31046/tcp open  echo                                                               
31518/tcp open  ssl/echo                                                           
31691/tcp open  echo                                                               
<span style="color:green;">31790/tcp open  ssl/unknown</span>                                                       
31960/tcp open  echo


[# Passo3.]
<b>bandit16@bandit:~$</b> openssl s_client localhost:31790                                
CONNECTED(00000003)                                                                
...    
JQttfApK4SeyHwDlI9SXGR50qclOAil1                                                   Correct!                                                                           
 -----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----                                                                                                                                  
closed  

[# Passo4.]
<b>bandit16@bandit:~$</b> mkdir /tmp/teste
<b>bandit16@bandit:~$</b> cd /tmp/teste
<b>bandit16@bandit:/tmp/teste$</b> nano sshkey.private

<b>Dentro da sshkey.private pelo nano, cole a private key que foi retornada</b>

[# Passo5.]
<b>bandit16@bandit:/tmp/teste$</b> chmod 400 sshkey.private
<b>bandit16@bandit:/tmp/teste$</b> ls -l
total 4                                                                            
-rw-rw-r-- 1 bandit16 bandit16 1675 Jan 19 21:26 sshkey.private

[# Passo6.]
<b>bandit16@bandit:/tmp/teste$</b> ssh -i sshkey.private bandit17@localhost -p 2220
<b>bandit17@bandit:~$</b>

[# Passo7.]
<b>bandit17@bandit:~$</b> cat /etc/bandit_pass/bandit17
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e


[# Passo8.] 
<b>bandit17@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.

<b>bandit16@bandit:/tmp/teste$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 17:**
- Username: `bandit17`
- Password: `VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit17.html)


