# Level 26
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Bom trabalho conseguindo um shell! Agora corra e pegue a senha do bandit27!

## Comandos para esse level
`ls`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ls       |lista os conteúdos do diretório

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit26`
- Password: `c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Se você já estiver conectado no bandit26 passe para o próximo passo. Senão, você deverá seguir este mini tutorial:

- Primeiro, deixe o terminal bem pequeno e conecte com o SSH usando as informações acima.
- Agora, estamos dentro do `more`, para acessar o vim, basta pressionar a tecla v.
- Dentro do `vim`, vamos setar o shell usando  `:set shell=/bin/bash` e depois rodar `:shell`. Assim, podemos prosseguir.

***[# Passo2.]*** Vamos dar um `ls` para ver o que temos no nosso homedirectory. Temos um setuid binary e um arquivo .tx.

Sabemos que o **text.tx** não tem nenhuma informação que precisamos. Então vamos focar no **bandit27-do**. Rodando ele apenas para teste. Vemos que ele executa comandos como o usuário bandit27. 

Dessa forma, executaremos o **bandit27-do** passando o comando `cat /etc/bandit_pass/bandit27`

***[# Passo3.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
Se você não estiver logado com o bandit26, consulte o passo 5 e 6 da solução no level25.md

[# Passo2.]
<b>bandit26@bandit:~$</b> ls 

bandit27-do  text.txt

<b>bandit26@bandit:~$</b> ./bandit27-do cat /etc/bandit_pass/bandit27

YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS

[# Passo3.] 
<b>bandit26@bandit:~$</b> exit

logout               

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 27:**
- Username: `bandit27`
- Password: `YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit27.html)