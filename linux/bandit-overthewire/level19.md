# Level 19
**Tópicos**

- [X] [Goal](#goal)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Para ter acesso para o próximo level, você deve usar o **setuid binary** que está no homedirectory. Execute esse arquivo sem nenhum argumento para descobrir como usar. A senha para esse level pode ser encontrada em seu lugar habitual (/etc/bandit_pass), depois que você usar o **setuid binary**.

## Teoria
**Setuid (set user ID)** and **Setgid (set group ID)** é uma maneira de usuários rodarem um executável com permissões de um usuário ou grupo que é proprietário do arquivo. 

Eles são frequentemente usados para permitirem que usuários rodem programas com privilégios elevados temporariamente para realizarem uma tarefa específica.

Se rodarmos o `./bandit20-do id` receberemos como resposta `uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)`, em que:

- uid significa ID do usuário que executou o programa. Usuário original
- gid é o ID do grupo primário do usuário que executou o programa
- euid (effective uid) significa ID do usuário que está executando o processo. É o usuário para o qual você mudou.
- groups é a lista dos grupos suplementares

Para saber mais sobre [Setuid](https://en.wikipedia.org/wiki/Setuid) e sobre [Permissões de arquivo](https://www.gnu.org/software/coreutils/manual/html_node/File-permissions.html#File-permissions)

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit19`
- Password: `awhqfNnAbc1naukrpqDYcF95h7HoMTrC`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Por precaução, vamos rodar `ls` para saber qual é o **setuid binary**. E depois executar ele.

***[# Passo3.]*** Descobrimos que o **setuid binary** roda os comandos como outro usuário. Assim iremos rodar `cat /etc/bandit_pass/bandit20` executando o **setuid binary**. Pois, sem o **setuid binary** não temos acesso ao arquivo bandit20.

***[# Passo4.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit#@bandit.labs.overthewire.org -p 2220</b>
bandit#@bandit.labs.overthewire.org's password: <b>awhqfNnAbc1naukrpqDYcF95h7HoMTrC</b>

[# Passo2.]
<b>bandit19@bandit:~$</b> ls
bandit20-do
<b>bandit19@bandit:~$</b> ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id

[# Passo3.]
<b>bandit19@bandit:~$</b> ./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT

[# Passo4.] 
<b>bandit19@bandit:~$</b> exit
logout                                                             
Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 20:**
- Username: `bandit20`
- Password: `VxCazJaVykI6W36BkBU0mJTCM8rR95XT`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit20.html)

