# Level 17
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [x] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Há dois arquivos no homedirectory: **passwords.old** e **passwords.new**. A senha para o próximo level estpa no arquivo **passwords.new** e é a única linha que diferente entre  **passwords.old** e **passwords.new**.

*NOTA: se você resolveu este nível e vê 'Tchau!' ao tentar entrar no bandit18, isso está relacionado ao próximo nível, bandit19*

## Comandos para esse level
`cat`, `grep`, `ls`, `diff`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 cat      |printa os arquivos na saída padrão
 grep     |printa as linhas que batem com os padrões
 ls       |lista os conteúdos do diretório
 diff     |compara arquivos linha por linha

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
O `diff` é um comando que compara arquivos linha por linha.

`diff [OPTION]... FILES`

Nesse desafio não passaremos nenhuma flag. 

Note que a linha de difereça irá apontar na ordem que os arquivos foram colocados no comando. Ou seja, a primeira linha será do primeiro arquivo e a segunda do segundo arquivo.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit17`
- Password: `VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Por precaução, vamos checar se os arquivos estão no homedirectory, usando `ls`.

***[# Passo3.]*** Usando o `diff` vamos ver a diferença entre os arquivos. 

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit17@bandit.labs.overthewire.org -p 2220</b>
bandit17@bandit.labs.overthewire.org's password: <b>senhaDoLevelemQueEsta</b>

[# Passo2.]
<b>bandit17@bandit:~$</b> ls
passwords.new  passwords.old

[# Passo3.]
<b>bandit17@bandit:~$</b> diff passwords.new passwords.old
42c42
< hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
---
> 810zq8IK64u5A9Lb2ibdTGBtlcSZsoe8

[# Passo4.] 
<b>bandit17@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 18:**
- Username: `bandit18`
- Password: `hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit18.html)



