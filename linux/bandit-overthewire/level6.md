# Level 6
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em algum lugar no server e que possui todas essas 3 propriedades:
- owned by user bandit7;
- owned by group bandit6;
- 33 bytes in size.

## Comandos para esse level
`ls`, `cd`, `cat`, `file`, `du`, `find`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ls       |lista o que tem dentro do diretório
 cd       |muda o working directory (diretório atual)
 cat      |"lê" o arquivo e imprimir (o que tem dentro) na saída padrão
 file     |determina o tipo de arquivo
 du       |estima o espaço usado por um arquivo
 find     |procura por arquivos de acordo com a hierarquia dos diretórios
 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
Para esse level, usaremos novamente o comando `find`

Observe que o estaremos procurando o arquivo "em algum lugar no server", para isso usaremos `/` que significa a raiz do drive, assim estaremos procurando em todo o server

Para procurar pelas propriedades usaremos flags:

**-user uname** procura por um arquivo que é propriedade do usuário *uname*

**-group iname** procura por um arquivo que pertence a um grupo *iname*

**-size n** procura por um arquivo que tem *n* unidades de espaço. Nesse desafio, estamos tratando de bytes, então usamos o sufixo *c*.

>***OBS:*** 
>
>Se rodarmos o `find` com todas as propriedades acima, teremos a resposta de *Permission denied* para vários diretórios. E teriamos que buscar por um único que não deu *Permission denied*.
>
>![image](https://user-images.githubusercontent.com/62816035/208774251-4de50e26-feb1-4d7f-bbff-be65012b2a03.png)
>
>A fim de minizar essa quantidade de resposta e achar apenas a que precisamos usaremos `2>/dev/null`, que significa que estamos direcionando(>) os erros (standard error é representado pelo número 2)  para um diretório (/dev/null). 
>
>Dessa forma, todos os diretórios que deram *Permission denied* não irão aparecer.
>
>Para saber mais, procure sobre [redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit6`
- Password: `P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Para achar o arquivo use o comando `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`, assim encontraremos o arquivo

***[# Passo3.]*** Com o objetivo de acessar a senha usaremos o `cat`

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandi6@bandit.labs.overthewire.org -p 2220</b>
bandit6@bandit.labs.overthewire.org's password: <b>P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU</b>

[# Passo2.] 
<b>bandit6@bandit:~$</b> find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

[# Passo3.]
<b>bandit6@bandit:~$</b> cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

[# Passo4.] 
<b>bandit6@bandit:~$</b> exit
logout                                                                 
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 7**
- Username: `bandit7`
- Password: `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit6.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
