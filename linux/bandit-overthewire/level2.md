# Level 2
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em um arquivo chamado "-", que está no home.

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

Se não passa nenhum arquivo, or quando o arquivo é "-", lê a entrada padrão (terminal), ou seja, copia a entrada padrão para a saída padrão.

Para ler o arquivo "-", usa-se todo o caminho dele `./-`, em que: `.` refere-se ao diretório atual e `/` é raiz do drive atual, e juntos significam *dentro do diretório atual*

O "-" se refere a STDIN/STDOUT que seria dev/stdin ou dev/stdout.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit1`
- Password: `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Rodar `ls`, para localizar o **-**.

***[# Passo3.]***  Para ver o que tem dentro do **-**  e obter a senha, rodar `cat ./-`.

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit1@bandit.labs.overthewire.org -p 2220</b>
bandit0@bandit.labs.overthewire.org's password: <b>NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL</b>

[# Passo2.] 
<b>bandit0@bandit:~$</b> ls 
-

[# Passo3.] 
<b>bandit0@bandit:~$</b> cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

[# Passo4.]
<b>bandit0@bandit:~$</b> exit
logout
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 2**
- Username: `bandit2`
- Password: `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit2.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)

Para mais, pesquise [dashed filename](https://www.google.com/search?q=dashed+filename)
