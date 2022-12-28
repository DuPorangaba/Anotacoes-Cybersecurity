# Level 11
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#solução)
- [X] [Resources](#resources)

## Goal
A senha para o próximo level está no arquivo **data.txt**, em que todas as letras minúsculas (a-z) e maiúsculas (A-Z) foram rodadas por 13 posições 

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

Rotacionar 13 posições do alfabeto é conhecido como [ROT13](https://pt.wikipedia.org/wiki/ROT13), que é o procedimento simples de substituir uma letra pela 13º letra depois dela no alfabeto. Assim, o a equivalerá o n, e o Z equivalerá o M.

O comando que consegue traduzir caracteres é o `tr`, a sintaxe do `tr [OPTION]... STRING1 [STRING2]`, em que `STRING1` e  `STRING2` são lista de caracteres especificos que controlam a ação.

Para o ROT13, o `STRING1` será a-z e A-Z e o `STRING2` n-za-m e N-ZA-M.


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit11`
- Password: `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Para ver se o arquivo **data.txt** existe e que está no home directory, usamos `ls`. 

***[# Passo3.]*** Utilizamos **piping** para pegar o que está dentro do arquivo com o `cat` e "traduzir" usando o `tr` com as especificações do ROT13.

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit11@bandit.labs.overthewire.org -p 2220</b>
bandit11@bandit.labs.overthewire.org's password: <b>6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM</b>

[# Passo2.] 
<b>bandit11@bandit:~$</b> ls
data.txt

[# Passo3.] 
<b>bandit11@bandit:~$</b> cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

[# Passo4.] 
<b>bandit11@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 12**
- Username: `bandit12`
- Password: `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit12.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
