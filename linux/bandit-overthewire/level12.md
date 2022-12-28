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


## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
-  Username: `bandit12`
- Password: `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<pre>
[# Passo1.] 
<b>> ssh bandit12@bandit.labs.overthewire.org -p 2220</b>
bandit12@bandit.labs.overthewire.org's password: <b>JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv</b>

[# Passo*.] 
<b>bandit12@bandit:~$</b> 



[# Passo*.] 
<b>bandit12@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</pre>

**Credenciais do Level 13**
- Username: `bandit13`
- Password: ``

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit13.html)

[Manual Linux](https://man7.org/linux/man-pages/index.html)
