# Level 4
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está dentro de um arquivo human-readable no diretório inhere

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

Para esse desafio, usaremos o comando *file*. Ele determinam os tipos de arquivo.

Arquivos [human-readable](https://en.wikipedia.org/wiki/Human-readable_medium) são comumente codificados como ASCII ou Unicode text. Assim, estamos procurando por arquivos deste tipo.

**file**  

file [OPTION] [FILE]

Para vermos o tipo de todos arquivos dentro da pasta, podemos utilizar o [caracter curinga *](https://pt.wikibooks.org/wiki/Linux_Essencial/Li%C3%A7%C3%A3o_Manipula%C3%A7%C3%A3o_de_arquivos#Asterisco_(*)) , que tem a função de completar os nomes, um exemplo de uso seria `ls *resto_nome` ou `ls inicio_nome*` 

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit3`
- Password: `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Rodar `ls`, para localizar o **inhere**.

***[# Passo3.]*** Para entrar dentro do diretório **inhere**, rode `cd inhere`. 

***[# Passo4.]*** Para ver o que temos dentro da pasta **inhere**, usamos `ls`.

***[# Passo5.]*** Use `file ./*` para ver o tipo de todos os arquivos.

***[# Passo6.]*** Depois de descobrir qual dos arquivos é human-readable (ASCII ou Unicode), usamos o `cat`, e conseguimos a senha.

***[# Passo7.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandi4@bandit.labs.overthewire.org -p 2220</b>
bandit4@bandit.labs.overthewire.org's password: <b>2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe</b>

[# Passo2.] 
<b>bandit4@bandit:~$</b> ls 
inhere

[# Passo3.] 
<b>bandit4@bandit:~$</b> cd inhere
<b>bandit4@bandit:~/inhere$</b> 

[# Passo4.] 
<b>bandit4@bandit:~/inhere$</b> ls 
-file00  -file02  -file04  -file06  -file08     
-file01  -file03  -file05  -file07  -file09 

[# Passo5.] 
<b>bandit4@bandit:~/inhere$</b> file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data

[# Passo6.]
<b>bandit4@bandit:~/inhere$</b> cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR 

[# Passo7.] 
<b>bandit4@bandit:~/inhere$</b> exit
logout                                                                      
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 5**
- Username: `bandit5`
- Password: `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit5.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
