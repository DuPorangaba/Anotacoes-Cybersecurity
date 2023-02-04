# Level 32
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Depois de tudo isso, é hora de outra fuga. Boa sorte!

## Comandos para esse level
`ssh`, `man`

*Nota: Nem todos os comandos listados são necessários*

 Comandos |                             O que faz?
 ---------|--------
 ssh      |OpenSSH remote login client
 man      |Uma interface para os manuais de referência do sistema

 
 **Obs:** Para saber mais informações sobre como usar os comandos, possíveis flags, etc. Use `comando --help` para obter um "resumo" do manual, ou `man comando` para acessar o manual do comando.

## Teoria
O Linux tem variáveis chamadas variáveis locais (válidas no shell atual), variáveis do shell (configuradas pelo shell) e variáveis de ambiente (válidas em todo o sistema). Essas variáveis têm seus nomes apenas em letras maiúsculas. Eles são definidos escrevendo VAR_NAME=var_value na linha de comando. Para ver o conteúdo de uma variável, você pode escrever echo $VAR_NAME.

Para imprimir todas as variáveis de ambiente, você pode usar printenv.

Alguns comuns que são bons de saber são:

- TERM - emulação de terminal atual
- HOME - o caminho para o diretório inicial do usuário conectado no momento
- LANG - configurações de localidades atuais
- PATH - lista de diretórios a serem pesquisados ao executar comandos
- PWD - nome do caminho do diretório de trabalho atual
- SHELL/0 - o caminho do shell do usuário atual
- USER - usuário atualmente logado

[Créditos](https://mayadevbe.me/posts/overthewire/bandit/level33/)

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit32`
- Password: `rmCBvG56y58BXzv98yZGdO7ATVL5dW8y`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** Conectar e logar no SSH usando as informações acima.

***[# Passo2.]*** Quando logamos, somos recebidos com a frase " WELCOME TO THE UPPERCASE SHELL". Logo tentamos digitar os comandos que já conhecemos, mas não funciona.

Pois, tudo que escrevemos é transformado em letra maiúscula, no entanto, os comandos que conhecemos só funcionam em letra minúscula.

Porém, no linux quando pensamos em letras maiúsculas podemos pensar nas variáveis.

***[# Passo3.]*** Vamos usar a variável `$0` que é uma referência ao shell, dessa maneira, irá executar um shell para a gente.

***[# Passo4.]*** Deu certo, agora vamos ver se os comandos funcionam mesmo. E depois vamos descobrir quem somos.

 Somos os usuário **bandit33**, logo podemos pegar a senha do próximo level.

***[# Passo5.]*** Para sair, rode `exit`

## Solução
<prep>
[# Passo1.] 
<b>> ssh bandit#@bandit.labs.overthewire.org -p 2220</b>
bandit#@bandit.labs.overthewire.org's password: <b>senhaDoLevelemQueEsta</b>

[# Passo2.]

.>> ls  

sh: 1: LS: not found

[# Passo3.]

.>> $0

$

[# Passo4.]

$ ls 

    uppershell

$ whoami

    bandit33

$ cat /etc/bandit_pass/bandit33

    odHo63fHiFqcWWJG9rLiLDtPm45KzUKy



[# Passo5.] 
<b>bandit#@bandit:~$</b> exit

logout                       

Connection to bandit.labs.overthewire.org closed.
</prep>

**Credenciais para o Level 33:**
- Username: `bandit33`
- Password: `odHo63fHiFqcWWJG9rLiLDtPm45KzUKy`

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit33.html)


