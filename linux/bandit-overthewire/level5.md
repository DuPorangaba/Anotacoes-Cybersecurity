# Level 5
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha do próximo level está em um arquivo em algum lugar a partir do diretorio **inhere**, e possui 3 propriedades: 
- human-readable;
- 1033 bytes in size;
- not executable.

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

Para esse desafio usaremos o comando `find`.

**find**

Usaremos as flags:
`-size n` que busca arquivos que usam n unidades de espaço, para especificar a unidade, temos sufixos (b, c, w, j, M, G), para esse problema usaremos o `c` para bytes.

-executable que busca por arquivos executáveis

Para negar a flag `-executable`, usaremos a exclamação(!), semelhante a programação, a exclamação significa "não". Então, not executable é `! -executable`.

No enunciado, temos que o arquivo pode estar em algum lugar a partir do diretório inhere, isso significa que devemos especificar a hierarquia dos diretórios. 
Para isso, apenas usaremos o ".", que significa neste diretório atual.


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit5`
- Password: `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Rodar `ls`, para localizar o **inhere**.

***[# Passo3.]*** Para entrar dentro do diretório **inhere**, rode `cd inhere`. 

***[# Passo4.]*** Para ver o que temos dentro da pasta **inhere**, usamos `ls`.

***[# Passo5.]*** Use `find . -size 1033c ! -executable` para achar o arquivo que estamos procurando.

***[# Passo6.]*** Depois de descobrir qual dos arquivos é 1033 bytes in size e not executable, usamos o `cat`, e conseguimos a senha.

***[# Passo7.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandi5@bandit.labs.overthewire.org -p 2220</b>
bandit5@bandit.labs.overthewire.org's password: <b>lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR</b>

[# Passo2.] 
<b>bandit5@bandit:~$</b> ls 
inhere

[# Passo3.] 
<b>bandit5@bandit:~$</b> cd inhere
<b>bandit5@bandit:~/inhere$</b> 

[# Passo4.] 
<b>bandit5@bandit:~/inhere$</b> ls 
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16             
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17             
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18             
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19 

[# Passo5.] 
<b>bandit5@bandit:~/inhere$</b> find . -size 1033c ! -executable
./maybehere07/.file2 

[# Passo6.]
<b>bandit5@bandit:~/inhere$</b> cat ./maybehere07/.file2 
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU 

[# Passo7.] 
<b>bandit5@bandit:~/inhere$</b> exit
logout                                                                      
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 6**
- Username: `bandit6`
- Password: `P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit6.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
