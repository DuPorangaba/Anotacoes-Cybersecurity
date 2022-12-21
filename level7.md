# Level 7
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [ ] [Um pouco de Teoria](#teoria)
- [ ] [Write Up](#write-up)
- [ ] [Solução](#solução)
- [ ] [Resources](#resources)

## Goal
A senha para o próximo level está no arquivo **data.txt** perto da palavra **millionth** 

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

Este level pode ser resolvido de duas maneiras. 

**1º Modo**

Usaremos o comando `grep`. 

A sintaxe é `grep [OPTION...] PATTERNS [FILE...]`, 

em que, 

OPTION são as flags

PATTERNS é o que estamos buscando

FILE são os arquivos

---

**2º Modo**

Usaremos o `grep` e o `cat`, atráves do piping.

O **piping** é uma forma de redirecionamento, o output de um comando serve de input do próximo comando. Dessa forma, o Pipe serve para usar dois ou mais comandos.

`cat [FILE] | grep [OPTION] PATTERNS`


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit7`
- Password: `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Rodar `ls` para localizar o arquivo **data.txt**, ele está no *home director* mesmo.

***[# Passo3.]*** Para achar a senha usaremos `grep "millionth" data.txt`

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit7@bandit.labs.overthewire.org -p 2220</b>
bandit7@bandit.labs.overthewire.org's password: <b>z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S</b>

[# Passo2.]
<b>bandit7@bandit:~$</b> ls
data.txt

[# Passo3.]
<b>bandit7@bandit:~$</b> grep "millionth" data.txt
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP

[# Passo4.] 
<b>bandit7@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 8**
- Username: `bandit8`
- Password: `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit7.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
