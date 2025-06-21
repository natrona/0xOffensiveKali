# Guia de Instalação do Kali Linux no WSL (Windows Subsystem for Linux)

Este guia explica como instalar o Kali Linux no Windows usando o WSL 2, a versão mais recente do Subsistema do Windows para Linux.

## Pré-requisitos

- Windows 10 versão 2004 ou superior, ou Windows 11
- Acesso administrativo no computador
- Conexão com a internet estável
- Mínimo de 4GB de RAM recomendado

## Passo 1: Habilitar o WSL 2

1. Abra o PowerShell como Administrador
2. Execute os seguintes comandos:

```powershell
# Habilitar o recurso WSL
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Habilitar o recurso Virtual Machine Platform
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Reinicie o computador quando solicitado
```

## Passo 2: Definir WSL 2 como versão padrão

No PowerShell como Administrador:

```powershell
wsl --set-default-version 2
```

## Passo 3: Instalar o Kernel do Linux

Baixe e instale o pacote de atualização do kernel Linux da Microsoft:
[https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)

## Passo 4: Instalar o Kali Linux

1. Abra a Microsoft Store
2. Pesquise por "Kali Linux"
3. Selecione "Kali Linux" da Kali Linux Team
4. Clique em "Obter" para instalar

## Passo 5: Configurar o Kali Linux

1. Inicie o Kali Linux pelo menu Iniciar
2. Aguarde a conclusão da instalação
3. Defina um nome de usuário e senha quando solicitado

## Passo 6: Atualizar o sistema

No terminal do Kali Linux, execute:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt autoremove -y
```

## Configurações avançadas

### Acessar arquivos do Windows

Os discos do Windows são montados automaticamente em:

```bash
/mnt/c/  # Para a unidade C:
/mnt/d/  # Para a unidade D:
```

### Instalar ferramentas adicionais

Para instalar o conjunto completo de ferramentas:

```bash
sudo apt install -y kali-linux-large
```

### Configurar o VS Code com WSL

1. Instale a extensão "Remote - WSL" no VS Code
2. No terminal do Kali, navegue até sua pasta de projeto e execute:

```bash
code .
```

## Solução de problemas

### Verificar versão do WSL

```powershell
wsl --list --verbose
```

### Alterar versão do WSL para uma distribuição

```powershell
wsl --set-version kali-linux 2
```

### Resetar a instalação do Kali

```powershell
wsl --unregister kali-linux
```

## Considerações de segurança

1. O Kali Linux no WSL não substitui uma instalação completa para testes de penetração avançados
2. Algumas ferramentas podem ter limitações de funcionamento no WSL
3. Recomenda-se usar o modo de rede espelhada para atividades de rede

## Referências

- [Documentação oficial do WSL](https://docs.microsoft.com/pt-br/windows/wsl/)
- [Site oficial do Kali Linux](https://www.kali.org/)
- [Guia de ferramentas do Kali](https://www.kali.org/tools/)
