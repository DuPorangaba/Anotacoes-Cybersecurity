# Level 15
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level pode ser "retornada" enviando a senha do level atual para **o localhost na porta 30001** usando SSL encryption. *Nota útil: Obtendo “HEARTBEATING” e “Read R BLOCK”? Use -ign_eof e leia a seção “CONNECTED COMMANDS” na página de manual. Ao lado de ‘R’ e ‘Q’, o comando ‘B’ também funciona nesta versão desse comando…*

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
O comando `openssl s_client` implementa um client genérico que se conecta com um host remoto usando SSL/TLS.

A sintaxe é:  `openssl s_client [flags] hostname:port`. Em que para esse level, usamos: 

- a flag `-ign_eof` que não permite que a conexão seja "cortada" quando o fim do arquivo de input é atingido.

- como hostname usamos o **localhost** que se refere ao dispositivo em que você está trabalhando

- port foi a porta especificada no enunciado.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit15`
- Password: `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Estabelecemos conexão com o localhost na porta 30001 e enviamos a senha do level atual.

***[# Passo3.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit15@bandit.labs.overthewire.org -p 2220</b>
bandit#@bandit.labs.overthewire.org's password: <b>jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt</b>

[# Passo2.]
<b>bandit15@bandit:~$</b> openssl s_client -ign_eof localhost:30001

CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Jan 18 02:44:54 2023 GMT
verify return:1
depth=0 CN = localhost
notAfter=Jan 18 02:44:54 2023 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Jan 18 02:43:54 2023 GMT; NotAfter: Jan 18 02:44:54 2023 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEKEH7KDANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjMwMTE4MDI0MzU0WhcNMjMwMTE4MDI0NDU0WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCN
w/rBDpchUlcHWYGT2GjTuK9wI8PdZGMvtA88Ckh+BvVUa+zJ4zgjlIyYzbwUuEFi
anOELcTEb87fD9ivwUlEBtFES+GlZw7m+JCflFCLIeGLwCzRuUmkadiYyGDFLs2f
ACJsSz8GOrmgY8dv+SS0gF3/XtEQrL7Y5lhpsVt2DNRGB2WZf+nmIWim+W1xA+DE
y2edR+JlGdmCw5IcBmDFIGrYvHobQXEFfF7QugQ8YZppBckIFcDSG2yaq9HXdJmV
lesXLsTIWpa/59SP8V8es9KhrdMXTlUL/GIHIrSEytk2s4ZVs/9TdRde/XuEiwBB
PxvtmBr4KL7J6kL1Ge49AgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQA5
IBmtQd9F+8xRiD3xR3BJh5vCPP7kuQQq5ZqSuzAi/dJ9N65vuwylTzQYzrHelyyV
KY0ZyxcTKV384RVrIjx46mqrxMOn9WvSY/LrQnStLB2AvLO+YkzkdJmBpfkzE21J
2YdGx6KEfguUpZRjxpG76DvLng2JAk5BGdIHSzHLo810OSjs2UvO2G+hcyRF/i5x
dvQII18L6GIMC8ra2yj9tU1gwMDmgd8Ny/eOsR+0xj+Yk8M0PVpLiwLdVSw9F517
yo1yNjb8WalIFi/ZsTKYwT+ietijD6BzYZ38pFFZGFw2hRtCnleBGHJPdVy/SoG0
eHkglL+imJSZ70i9K1NH
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 4BADA0946B8D8FECD503B253204010F0BB8DB8B5FB2F31998974B3D270026884
    Session-ID-ctx:
    Resumption PSK: B255FC1113902A3568F18CE08EF878ECC7DD9FC597C76FF9803B2CA9A1AB3D4EE0DDCAF98AE6772C8C5BA3BAA3369AFE
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - e0 35 7b de 01 d5 00 96-28 88 bb 3f 0b 2f 46 8d   .5{.....(..?./F.
    0010 - e7 8f 92 57 8f 09 e5 b1-93 94 16 99 64 d3 71 52   ...W........d.qR
    0020 - 30 23 f6 3a fe 1c 18 fc-57 f6 70 12 0e 1c 15 76   0#.:....W.p....v
    0030 - 85 8b e4 e5 e6 ed 64 29-e4 e7 32 08 40 47 61 d9   ......d)..2.@Ga.
    0040 - 69 25 de 4a 7b 4f b1 26-23 1b 31 f2 ed e5 79 40   i%.J{O.&#.1...y@
    0050 - 26 7d 4a 4b b0 ad 7e ab-b0 23 d7 58 ef 08 69 5c   &}JK..~..#.X..i\
    0060 - 95 99 28 ec 8f db cf 53-a0 ef 39 1a f0 fe 86 7d   ..(....S..9....}
    0070 - b6 77 57 4d 58 7b 71 1d-17 07 97 66 4d fa a0 a0   .wWMX{q....fM...
    0080 - eb 9c d3 16 a3 6a be 92-d4 67 56 32 87 75 ac 10   .....j...gV2.u..
    0090 - 27 1b b6 5d da 0b 27 f2-fc 79 fc ae 54 38 c7 e4   '..]..'..y..T8..
    00a0 - 6a 4b 4b 06 9a 56 8c c3-81 98 78 b3 61 90 10 3d   jKK..V....x.a..=
    00b0 - 04 0a a4 05 39 4d a8 dd-57 1d fd 90 dc 3e 98 a8   ....9M..W....>..
    00c0 - 11 cd 49 18 c3 9d 1d 8b-9b 17 df d2 6b fd 70 7b   ..I.........k.p{

    Start Time: 1674086433
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: C3CFA4F1B1400ACC7475C1ED757EB4ACE0DDE8E77B711C14710794BD78B216B8
    Session-ID-ctx:
    Resumption PSK: 10E0F448E9BFCA91D956019021D679DEB4D4B3E015178AA654B4B90EDE374E6199E516D966711F7CE33EF621577A2405
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - e0 35 7b de 01 d5 00 96-28 88 bb 3f 0b 2f 46 8d   .5{.....(..?./F.
    0010 - 25 3a 34 f9 17 96 38 85-bb 2e ae 3f ea 71 cf c9   %:4...8....?.q..
    0020 - 13 47 98 42 69 8c 05 76-5a b1 ed 40 c7 e3 87 0d   .G.Bi..vZ..@....
    0030 - 9e 73 1f 47 9a 51 05 fd-b7 45 85 a3 e4 99 3a a0   .s.G.Q...E....:.
    0040 - 49 b9 85 74 3a 7b c2 a1-67 ac c6 93 42 73 76 48   I..t:{..g...BsvH
    0050 - c5 13 3c 69 42 57 74 b4-bd 39 03 15 42 cb 48 35   ..<iBWt..9..B.H5
    0060 - 70 87 f0 4e 64 a4 a6 c1-89 69 71 35 16 80 93 6d   p..Nd....iq5...m
    0070 - 11 c7 e3 18 19 e8 7a e9-dc a7 8e ee 8f fb 52 b9   ......z.......R.
    0080 - 4d 26 ec 56 c4 85 fd 45-b7 ba 29 4a 03 5a 53 8c   M&.V...E..)J.ZS.
    0090 - 97 9b 4e f3 6e 4c 0d 8a-ca aa ec 03 cf 30 79 3d   ..N.nL.......0y=
    00a0 - 09 75 b3 a7 76 3f 08 a5-6f 83 63 ea 76 35 6e a4   .u..v?..o.c.v5n.
    00b0 - ce ef ac 29 24 7a a9 8a-ae b9 d4 36 eb b9 0e c0   ...)$z.....6....
    00c0 - 93 12 e3 53 04 12 cf 87-09 22 cb a4 af f9 29 43   ...S....."....)C

    Start Time: 1674086433
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK

>jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

[# Passo*.] 
<b>bandit15@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 16:**
- Username: bandit16
- Password: JQttfApK4SeyHwDlI9SXGR50qclOAil1

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit16.html)
