# Level 12
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [ ] [Um pouco de Teoria](#teoria)
- [ ] [Write Up](#write-up)
- [ ] [Solução](#solução)
- [ ] [Resources](#resources)

## Goal
A senha para o próximo level está no arquivo **data.txt**, que é hexdump de um arquivo que foi repetidamente comprimido. 

Para esse level, pode ser útil criar um diretório depois /tmp usando mkdir. Por exemplo, mkdir /tmp/myname123. Depois copiar o arquivo de dados usando `cp`, e renomear o arquivo usando mv (leia as páginas do manual).

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
 mkdir    |cria diretórios
 cp       |copia arquivos e diretórios
 mv       |move (renomeia) arquivos
 file     |determina o tipo do arquivo
 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
**Resolvendo o problema**

***mv***

`mv [OPTION]... SOURCE DEST`  irá renomear SOURCE para DEST.

***cp***

`cp [OPTION]... SOURCE DEST` irá copiar o SOURCE para o DEST.

***xxd***

`xxd -r[evert] [options] [infile [outfile]]` esse é comando para reverter o hex dump. 

Se nenhum `infile` é dado, o stdin é lido. E se nenhum `outfile` é dado, os resultados são enviados para stdout.

***gzip e bzip2***

Quando comprimimos(gzip) ou compactamos(bzip2) arquivos, o arquivo vai ser  substituído por um outro com uma extensão diferente, se usamos gzip, a extensão será `.gz` e se for bzip2, será `.bz` ou `.bz2`.

Assim, para informar que queremos reverter o processo, usamos a flag `-d`. Para descomprimir ou descompactar pegamos um arquivo `.gz` (se gzip) ou `.bz` (se bzip2) e ele perderá a sua extensão.

***tar***

Segue a mesma lógica do `gzip e bzip2` em relação a extensão, só com a extensão `.tar`. 

Mas passaremos outras flags, e não `-d`. Passaremos `xvf`, em que:

- x: extrai o arquivo
- v: Exibe informações detalhadas
- f: cria um arquivo com o <fileName> que foi passado 



## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit12`
- Password: `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Checar que o arquivo ***data.txt*** está no home directory

***[# Passo3.]*** Como indicado no enunciado, vamos criar uma pasta depois do /tmp, `mkdir /tmp/teste1` e copiar o arquivo ***data.txt*** para esse diretório. Por fim, vamos para o `/tmp/teste1`.

***[# Passo4.]*** No `/tmp/teste1` checar que o arquivo foi copiado. 

***[# Passo5.]*** Reverter o hexdump usando `xxd`, direcionando  a saída para um arquivo denominado ***data1***. E checar se foi criado a saída.

***[# Passo6-13.]*** Checar o tipo do arquivo ***data#I***. Renomear ele, dependendo do tipo da compressão, usando `mv`, mudando o tipo dele e o nome para ***data#I+1***. E descomprimir ele.

***[# Passo14.]*** Quando der o `file` no arquivo e ele for ASCII text. Dê um `cat` e veja se recebe a mensagem contendo a senha.

***[# Passo15.]*** Delete o diretório que foi criado temporariamente `/tmp/teste1` usando `rm -rf /tmp/teste1`

***[# Passo16.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit12@bandit.labs.overthewire.org -p 2220</b>
bandit12@bandit.labs.overthewire.org's password: <b>JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv</b>

[# Passo*.] 
<b>bandit12@bandit:~$</b> 

[# Passo2.] 
<b>bandit12@bandit:~$</b> ls 
data.txt

[# Passo3.] 
<b>bandit12@bandit:~$</b> mkdir /tmp/teste1
<b>bandit12@bandit:~$</b> cp data.txt /tmp/teste1
<b>bandit12@bandit:~$</b> cd /tmp/teste1
<b>bandit12@bandit:/tmp/teste1$</b> 

[# Passo4.]
<b>bandit12@bandit:/tmp/teste1$</b> ls
data.txt

[# Passo5.] 
<b>bandit12@bandit:/tmp/teste1$</b> xxd -r data.txt data1 
<b>bandit12@bandit:/tmp/teste1$</b> ls
data1 data.txt

[# Passo6.]
<b>bandit12@bandit:/tmp/teste1$</b> file data1
data1: gzip compressed data, was "data2.bin", last modified: Wed Jan 11 19:18:38 2023, max compression, from Unix, original size modulo 2^32 572 
<b>bandit12@bandit:/tmp/teste1$</b> mv data1 data2.gz
<b>bandit12@bandit:/tmp/teste1$</b> gzip -d data2.gz
<b>bandit12@bandit:/tmp/teste1$</b> ls
data2  data.txt

[# Passo7.]
<b>bandit12@bandit:/tmp/teste1$</b> file data2
data2: bzip2 compressed data, block size = 900k
<b>bandit12@bandit:/tmp/teste1$</b> mv data2 data3.bz2
<b>bandit12@bandit:/tmp/teste1$</b> bzip2 -d data3.bz2
<b>bandit12@bandit:/tmp/teste1$</b> ls
data3  data.txt

[# Passo8.]
<b>bandit12@bandit:/tmp/teste1$</b> file data3
data3: gzip compressed data, was "data4.bin", last modified: Wed Jan 11 19:18:38 2023, max compression, from Unix, original size modulo 2^32 20480
<b>bandit12@bandit:/tmp/teste1$</b> mv data3 data4.gz
<b>bandit12@bandit:/tmp/teste1$</b> gzip -d data4.gz
<b>bandit12@bandit:/tmp/teste1$</b> ls
data4  data.txt

[# Passo9.]
<b>bandit12@bandit:/tmp/teste1$</b> file data4
data4: POSIX tar archive (GNU) 
<b>bandit12@bandit:/tmp/teste1$</b> mv data4 data5.tar
<b>bandit12@bandit:/tmp/teste1$</b> tar xvf data5.tar
data5.bin
<b>bandit12@bandit:/tmp/teste1$</b> ls
data5.bin  data5.tar  data.txt

[# Passo10.]
<b>bandit12@bandit:/tmp/teste1$</b> file data5.bin
data5.bin: POSIX tar archive (GNU) 
<b>bandit12@bandit:/tmp/teste1$</b> mv data5.bin data6.tar
<b>bandit12@bandit:/tmp/teste1$</b> tar xvf data6.tar
data6.bin
<b>bandit12@bandit:/tmp/teste1$</b> ls
data5.tar  data6.bin  data6.tar  data.txt

[# Passo11.]
<b>bandit12@bandit:/tmp/teste1$</b> file data6.bin
data6.bin: bzip2 compressed data, block size = 900k 
<b>bandit12@bandit:/tmp/teste1$</b> mv data6.bin data7.bz2
<b>bandit12@bandit:/tmp/teste1$</b> bzip2 -d data7.bz2
<b>bandit12@bandit:/tmp/teste1$</b> ls
data5.tar  data6.tar   data7  data.txt

[# Passo12.]
<b>bandit12@bandit:/tmp/teste1$</b> file data7
data7: POSIX tar archive (GNU) 
<b>bandit12@bandit:/tmp/teste1$</b> mv data7 data8.tar
<b>bandit12@bandit:/tmp/teste1$</b> tar xvf data8.tar
data8.bin
<b>bandit12@bandit:/tmp/teste1$</b> ls
data5.tar  data6.tar  data8.bin  data8.tar  data.txt

[# Passo13.]
<b>bandit12@bandit:/tmp/teste1$</b> file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Wed Jan 11 19:18:38 2023, max compression, from Unix, original size modulo 2^32 49
<b>bandit12@bandit:/tmp/teste1$</b> mv data8.bin data9.gz
<b>bandit12@bandit:/tmp/teste1$</b> gzip -d data9.gz
<b>bandit12@bandit:/tmp/teste1$</b> ls
data5.tar  data6.tar  data8.tar  data9  data.txt

[# Passo14.]
<b>bandit12@bandit:/tmp/teste1$</b> file data9
data9: ASCII text
<b>bandit12@bandit:/tmp/teste1$</b> cat data9
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

[# Passo15.]
<b>bandit12@bandit:/tmp/teste1$</b> rm -rf /tmp/teste1

[# Passo16.] 
<b>bandit12@bandit:/tmp/teste1$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 13**
- Username: `bandit13`
- Password: `wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit13.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
