# Level 10
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está em um arquivo **data.txt** que contém dados codificados em base64.

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
Para codificar e decodificar dados em base64, usa-se o comando `base64`. 

No caso de decodificar, devemos passar a flag `-d`.

`base64 [OPTION]... [FILE]`

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit10`
- Password: `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Confirmar a existência do arquivo **data.txt**, usamos `ls`

***[# Passo3.]*** Usar `base64` para decodificar os dados dentro do arquivo **data.txt** e assim conseguir a senha

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit10@bandit.labs.overthewire.org -p 2220</b>
bandit10@bandit.labs.overthewire.org's password: <b>G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s</b>

[# Passo2.] 
<b>bandit10@bandit:~$</b> ls 
data.txt

[# Passo3.] 
<b>bandit10@bandit:~$</b> base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

[# Passo4.] 
<b>bandit10@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 11**
- Username: `bandit11`
- Password: `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit11.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
