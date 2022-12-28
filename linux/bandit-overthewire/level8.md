# Level 8
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em um arquivo **data.txt** e é a única linha do texto que apenas ocorre uma vez.

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
**Mistake made**
Usei o `uniq` passando a flag `-u` que faz com que imprima apenas linhas únicas, sem perceber que `uniq` filtra linhas semelhantes/iguais que são adjacentes, ou seja, o `uniq` retornava o **data.txt**, já que as linhas iguais entre si não estão adjacentes uma da outra.

**Resolvendo o problema**
Para esse desafio usaremos dois comandos. 

O `uniq` que omite linhas repetidas, e para isso passaremos a flag `-u` ou `--unique`, que mostra apenas as linhas que são únicas.

Mas antes é preciso notar que o **data.txt** está todo fora de ordem, assim, as linhas adjacentes de uma linha não necessariamente são iguais a essa linha. Logo, o `uniq` não conseguirá achar a **a única linha do texto que apenas ocorre uma vez**

Para isso, usaremos antes do `uniq`, o `sort` que ordena as linhas de um texto.

E usaremos **piping** para que o output do `sort`, documento ordenado, seja o input do `uniq`.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit8`
- Password: `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Para ver onde está o arquivo **data.txt**, usamos `ls`

***[# Passo3.]*** Usando piping, ordernar primeiro o **data.txt** utilizando o `sort` e selecionar a única linha que não repete com o `uniq`

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit8@bandit.labs.overthewire.org -p 2220</b>
bandit8@bandit.labs.overthewire.org's password: <b>TESKZC0XvTetK0S9xNwm25STk5iWrBvP</b>

[# Passo2.] 
<b>bandit8@bandit:~$</b> ls
data.txt

[# Passo3.] 
<b>bandit8@bandit:~$</b> sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t

[# Passo4.] 
<b>bandit8@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 9**
- Username: `bandit9`
- Password: `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit9.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
