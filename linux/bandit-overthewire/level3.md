# Level 2
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em um arquivo escondido no diretório **inhere**.

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

**ls**

`ls [OPTION] [FILE]`

Lista informações sobre os ARQUIVOs, by default o diretório atual.

Para listar todos os arquivos, mesmos aqueles "escondidos" que começam com ".", use a flag -a  ou --all.

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

***[# Passo4.]*** Para ver todos os arquivos dentro de um diretório, rode `ls -a`.

***[# Passo5.]*** Depois de ter descoberto o arquivo `.hidden`, use o `cat .hidden`, para obter a senha

***[# Passo6.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit3@bandit.labs.overthewire.org -p 2220</b>
bandit0@bandit.labs.overthewire.org's password: <b>aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG</b>

[# Passo2.] 
<b>bandit0@bandit:~$</b> ls 
inhere

[# Passo3.] 
<b>bandit0@bandit:~$</b> cd inhere
<b>bandit0@bandit:~/inhere$</b> 

[# Passo4.] 
<b>bandit0@bandit:~/inhere$</b> ls -a
. .. .hidden

[# Passo5.] 
<b>bandit0@bandit:~/inhere$</b> cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

[# Passo4.]
<b>bandit0@bandit:~$</b> exit
logout
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 4**
- Username: `bandit4`
- Password: `2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit2.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
