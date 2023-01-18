# Level  13
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [ ] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está armazenado em `/etc/bandit_pass/bandit14` e **apenas pode ser lida pelo usuário bandit14**. Para esse level, você não irá pegar a próxima senha, mas você vai ter acesso ao uma chave privada SSH que pode ser usada para logar no próximo level. 
*Nota: `localhost` é o hostname que se refere a máquina que você está trabalhando*

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

`ssh [-i identify file] user@hostname [-p port]`

Em que:

- **-i** é a flag utilizada para selecionar um arquivo do qual a identidade (chave privada) para autenticação de chave pública é lida.

- **user** é o username que você vai logar na máquina

- **hostname** é o endereço da máquina que você que logar

- **-p** é o número da porta em que você vai logar.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit13`
- Password: `wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Para localizar a private key e saber se ela está no home directory, usaremos `ls`.

***[# Passo3.]*** Vamos ver o que tem no arquivo encontrado através do `cat`

***[# Passo4.]*** Usaremos o `ssh` e a flag `-i` para logar no próximo level.

***[# Passo5.]*** Estamos logados no level 14. E para pegar a senha desse level usaremos `cat /etc/bandit_pass/bandit14`

***[# Passo6.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit13@bandit.labs.overthewire.org -p 2220</b>
bandit13@bandit.labs.overthewire.org's password: <b>wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw</b>

[# Passo2.]
<b>bandit13@bandit:~$</b> ls
sshkey.private

[# Passo3.]
<b>bandit13@bandit:~$</b> cat sshkey.private
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----

[# Passo4.]
<b>bandit13@bandit:~$</b> ssh -i  sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

[# Passo5.] 
<b>bandit14@bandit:~$</b> cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

[# Passo6.] 
<b>bandit14@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.

</prep>

**Credenciais para o Level 14:**
- Username: `bandit14`
- Password: `fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit14.html)



