# Level 2
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em um arquivo chamado **spaces in this filename** que está no home.

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

**cat**

`cat [OPTION] [FILE]`

Concatena o arquivo para a saída padrão (terminal).

Para ler arquivos que possuem espaços em seu nome, basta envolver o nome do arquivo em aspas.

*Nota: esse arquivo tem um nome muito grande, para facilitar podemos colocar a inicial do arquivo e clicar em TAB, o nome será completado*

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit2`
- Password: `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Rodar `ls`, para localizar o **spaces in this filename**.

***[# Passo3.]***  Para ver o que tem dentro do **spaces in this filename**  e obter a senha, rodar `cat 'spaces in this filename'`.

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit1@bandit.labs.overthewire.org -p 2220</b>
bandit0@bandit.labs.overthewire.org's password: <b>rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi</b>

[# Passo2.] 
<b>bandit0@bandit:~$</b> ls 
spaces in this filename

[# Passo3.] 
<b>bandit0@bandit:~$</b> cat 'spaces in this filename'
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

[# Passo4.]
<b>bandit0@bandit:~$</b> exit
logout
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 3**
- Username: `bandit3`
- Password: `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit2.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
