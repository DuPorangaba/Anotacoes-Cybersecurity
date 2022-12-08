# Start
**Tópicos**

- [X] [Goal](#goal)
- [X] [Comandos para o desafio](#comandos-para-esse-level)
- [X] [Um pouco de Teoria](#teoria)
- [X] [Write Up](#write-up)
- [X] [Solução](#soluçao)
- [X] [Resources](#resources)

## Goal
Logar dentro do jogo usando SSH.

## Comandos para esse level
`ssh`

## Teoria
SSH é uma sigla para Secure Socket Shell.

SSH é usado para logar em máquinas de maneira remota e executar comandos. 
Também pode ser usado para transferir arquivos quando associado a protocolos 
como SSH file transfer ou secure copy (SCP).

SSH usa o modelo [client-server](https://en.wikipedia.org/wiki/Client%E2%80%93server_model)

SSH usa criptografia de chave pública para autenticar o computador remoto e permitir
autenticar o usuário, se necessário.

**Sintaxe**
Importante lembrar de ter o SSH instalado ou ativado na máquina.

```
ssh user@ip-alvo

ssh user@ip-alvo -p numeroPorta
```
Em que:
user - é nome do usuário que você vai acessar dentro daquela máquina

ip-alvo - pode ser uma url, um ip da máquina que você quer acessar

Você também pode especificar a porta adicionando `-p numeroPorta` no final. 
Por padrão a porta do SSH é 22.

## Write up
**Informações**
- Host Name: `bandit.labs.overthewire.org`
- Username: `bandit0`
- Password: `bandit0`
- Port Number: `2220`

**Passo a Passo**

***[# Passo1.]*** No terminal, rodar `bandit0@bandit.labs.overthewire.org -p 2220`

***[# Passo2.]*** Colocar a senha `bandit0`

***[# Passo3.]*** Por fim, deve aparecer essa tela.
![image](https://user-images.githubusercontent.com/62816035/206586254-900f822e-3981-4a4d-89c9-590a57b1f9c8.png)

## Solução
```
[# Passo1.] 
> ssh bandit5@bandit.labs.overthewire.org -p 2220

[# Passo2.] 
bandit0@bandit.labs.overthewire.org's password: bandit0

[# Passo3.] 
Pronto
```

## Resources
[OverTheWire](https://overthewire.org/wargames/bandit/bandit0.html)

