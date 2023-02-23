# Instalando Kali Linux no Windows (WSL)

**O que é WSL?**

**Diferenças entre WSL e WSL2**

## Antes de Instalar 
Verifique os requisitos para executar o WSL. 

É necessário que, você esteje rodando o windows 10 ou windows 11. 
- Em sistemas x64: versão 1903 ou posterior, com o build 18362 ou posterior.
- Em sistemas ARM64: versão 2004 ou posterior, com o build 19041 ou posterior.

**Para verificar a versão e o número de build**

Pressione _tecla do logotipo do Windows + R_, digite _winver_ e selecione OK. 

Se estiver dentro das versões listadas acima, prossiga. Senão, busque atualizar o seu Windows.

## 1. Instalando WSL 2

### Ajustando os detalhes para a instalação

- Rode o POWERSHELL como administrador.

  - Rode o comando para permitir o uso do Subsistema do Windows para Linux.
    ```
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    ```

- ***Reinicie o computador***

- De volta no POWERSHELL, rodando como administrador.

  - Rode o seguinte comando para habilitar o recurso de Máquina Virtual
    ```
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```

  - Rode o seguinte comando para habilitar o recurso de Subsistema do Windows para Linux.
    ```
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    ```

- ***Reinicie o computador***

> Você também pode ativar ou verificar se o recurso de Máquina Virtual e o recurso de Subsistema do Windows para Linux estão habilitados, acessando o **Ativar e Desativar Recursos Windows** basta pesquisar dentro do painel de controle.

### Definitivamente Instalando o WLS2

- Faça o download do Linux Kernel: <https://aka.ms/wsl2kernel>

- De volta no POWERSHELL, rodando como administrador.

  - Defina o WLS2 como o padrão
    ```
    wsl --set-default-version 2
    ```
  - Verifique a versão
    ```
    wsl --list --verbose
    ```

- Entre na [Microsoft Store](https://aka.ms/wslstore), e instale a sua versão do Linux de Prerência. Neste caso, vamos instalar o Kali. Para isso basta, digitar kali linux na barra de pesquisa ou [clique aqui](https://www.microsoft.com/store/apps/9PKR34TNCV07).
- Abra o aplicativo, e defina um nome para o usuário e uma senha. 

A partir de agora você consegue acessar o Kali Linux apenas pela linha de comado, basta abri o app que acabamos de instalar. No entanto, se você quer uma interface gráfica, siga as instruções a seguir.

## 2. Instalando o GUI
- Abra o aplicativo que acabamos de instalar no Microsoft Store.
  -   Rode os seguites códigos

    ```
    sudo apt update && sudo apt upgrade -y
    ```

    ```
    sudo apt install kali-desktop-xfce -y
    ```

  - Para instalar o XRDP, rode:

    ```
    sudo apt install xrdp -y
    ```

### Acessando Remotamente a Interface Gráfica do Kali
- Para iniciar, rode
  ```
  sudo service xrdp start
  ```
- Depois, use o comando `ip add`, para saber o endereço IP em que o Kali está rodando. É o denominado **eth0**. Copie o IP.
- Pesquise por **Conexão Remota da Área de Trabalho** nos aplicativos windows. Abra, cole o IP e clique em conectar. Por fim, coloque o usuário e a senha que você definiu na primeira vez que entrou no app do Kali. 
> Para parar a conexão remota, use `sudo service xrdp stop`

## Instalando mais ferramentas
A versão WSL2 instalada do Kali vem apenas com o básico, pois é a instalação mínima. Para instalar outras ferramentas que vem com o Kali, veja <https://www.kali.org/docs/general-use/metapackages/>.


## Referências
[Vídeo do NetworkChuck](https://www.youtube.com/watch?v=AfVH54edAHU&ab_channel=NetworkChuck)

[Guia da Microsoft](https://learn.microsoft.com/pt-br/windows/wsl/install-manual)
