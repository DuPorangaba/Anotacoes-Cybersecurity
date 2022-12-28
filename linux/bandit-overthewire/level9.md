# Level 9
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha do próximo level está no arquivo **data.txt** sendo uma das poucas linhas human-readable, e é procedida por vários caracteres "="

## Comandos para esse level
`man`, `grep`, `sort`, `uniq`, `strings`, `base64`, `tr`, `tar`, `gzip`, `bzip2`, `xxd`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 man      |uma interface para os manuais de referência do sistema
 grep     |imprime linhas que correspondem aos padrões procurados
 sort     |classifica as linhas de um arquivo de texto
 uniq     |relata ou omite linhas repetidas
 strings  |imprime a sequência de caracteres imprimíveis de um arquivo
 base64   |codifica ou decodifica dados em base64 e imprime na saída padrão
 tr       |traduz ou deleta caracteres
 tar      |salva vários arquivos juntos em uma única fita ou disco, e pode restaurar arquivos individuais dos arquivos 
 gzip     |comprime ou expande arquivos
 bzip2    |compacta arquivos usando o algoritmo de compactação de texto de classificação de bloco Burrows-Wheeler e codificação Huffman
 xxd      |faz um hexdump(visão hexadecimal dos dados do computador) ou o contrário
 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
**Resolvendo o problema**
 Em um arquivo que contém caracteres human-readable e caracteres not human-readable, usa-se o `strings` para imprimir apenas os carecteres human-readable, ignorando os outros caracteres.

Dentre dos caracteres human-readable, temos que a senha é procedida por "=", dessa forma, usa-se o `grep` para localizar a senha. 

Outra vez, utilizamos o **piping** para usar o output do `strings` como o input do `grep`.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit9`
- Password: `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Para ter certeza que o arquivo **data.txt** existe e está no home directory, usamos `ls`.

***[# Passo3.]*** Usaremos o output do comando `strings` como input do `grep`. Assim, os strings apenas irá mostrar os caracteres **human-readable** e o grep irá buscar os "="

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit9@bandit.labs.overthewire.org -p 2220</b>
bandit9@bandit.labs.overthewire.org's password: <b>EN632PlfYiZbn3PhVK3XOGSlNInNE00t</b>

[# Passo2.]
<b>bandit9@bandit:~$</b> ls
data.txt

[# Passo3.]
<b>bandit9@bandit:~$</b> strings data.txt | grep "="
TM9=\
========== the
=Dbb
P,f=l
2v&z+=
p.g=
bktk=
========== password
j[=Cq
========== is=
b@!g=J
        =LG
=0 E
=0}I
F========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
h=57

[# Passo4.] 
<b>bandit9@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 10**
- Username: `bandit10`
- Password: `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit10.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
