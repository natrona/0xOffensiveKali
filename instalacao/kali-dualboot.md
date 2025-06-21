# Guia de Instalação em Dual Boot do Kali Linux

![Logo do Kali Linux](https://www.kali.org/images/kali-logo.svg)

Este guia fornece instruções passo a passo para instalar o Kali Linux junto com seu sistema operacional existente em configuração de dual boot.

## 📋 Pré-requisitos

- **Espaço em disco**: Mínimo 20GB livre (recomendado 50GB+)
- **Pen drive**: Capacidade de 8GB ou mais
- **Backup**: Faça backup de todos os dados importantes
- **Conexão com a internet**: Para baixar a ISO e atualizações
- **Tipo de firmware**: Conheça seu sistema (UEFI ou BIOS Legado)

## 📥 Passo 1: Baixar o Kali Linux

1. Acesse a [página oficial de downloads](https://www.kali.org/get-kali/)
2. Baixe a imagem ISO apropriada:
   - Para maioria dos usuários: **Kali Linux Live 64-bit (Installer)**
   - Opções alternativas disponíveis para ARM ou cloud

## 💾 Passo 2: Criar USB Bootável

### Para Windows
```powershell
# Usando Rufus (recomendado)
1. Baixe o Rufus em https://rufus.ie/
2. Selecione seu dispositivo USB
3. Escolha a ISO do Kali em "Seleção de boot"
4. Defina esquema de partição como GPT (para UEFI) ou MBR (para BIOS Legado)
5. Clique em "Iniciar" e aguarde
```

### Para Linux/macOS
```bash
# Identifique o dispositivo USB (CUIDADO para selecionar o correto)
lsblk  # Linux
diskutil list  # macOS

# Desmonte o USB (substitua /dev/sdX pelo seu dispositivo)
sudo umount /dev/sdX*  # Linux
diskutil unmountDisk /dev/diskX  # macOS

# Grave a ISO (substitua pelos seus caminhos)
sudo dd if=~/Downloads/kali-linux.iso of=/dev/sdX bs=4M status=progress  # Linux
sudo dd if=~/Downloads/kali-linux.iso of=/dev/diskX bs=1m  # macOS
```

## 🖥️ Passo 3: Preparar Espaço em Disco

### No Windows:
1. Pressione Win+X e selecione "Gerenciamento de Discos"
2. Clique direito na partição principal → "Diminuir Volume"
3. Libere pelo menos 50GB de espaço não alocado

### No Linux:
```bash
sudo apt install gparted
sudo gparted
```
1. Redimensione uma partição existente
2. Crie espaço não alocado para a instalação

## 🔄 Passo 4: Inicializar pelo USB

1. Reinicie o computador
2. Acesse a BIOS/UEFI (geralmente F2, F12, DEL ou ESC)
3. Desative o Secure Boot (se estiver ativado)
4. Configure a prioridade de boot para o USB
5. Salve e saia

## 🛠️ Passo 5: Instalar o Kali Linux

1. No menu de boot, selecione "Instalação Gráfica"
2. Configure idioma, localização e layout de teclado
3. Na parte de particionamento:
   - Selecione "Manual"
   - Crie estas partições no espaço não alocado:
     * `/` (sistema) - ext4 - 30GB+
     * `swap` - igual à sua RAM (opcional)
     * `/home` - ext4 - restante do espaço (opcional)
4. Instale o gerenciador de boot no disco principal (geralmente `/dev/sda`)
5. Configure usuário e senha
6. Complete a instalação e reinicie

## 🔧 Passo 6: Pós-instalação

### Atualizações básicas
```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt autoremove -y
```

### Instalar pacotes adicionais (opcional)
```bash
sudo apt install -y kali-linux-large
```

### Corrigir possíveis problemas

**Se o Windows não aparecer no GRUB:**
```bash
sudo apt install os-prober
sudo os-prober
sudo update-grub
```

**Problemas com horário (Windows/Linux):**
```bash
timedatectl set-local-rtc 1 --adjust-system-clock
```

**Drivers de vídeo (NVIDIA/AMD):**
```bash
sudo apt install -y nvidia-driver firmware-amd-graphics
```

## ⚠️ Avisos Importantes

1. Sempre faça backup dos seus dados antes de particionar o disco
2. A instalação do Kali Linux é recomendada apenas para usuários avançados
3. Evite usar a conta root para tarefas cotidianas

## 💡 Dicas Extras

- Para melhor desempenho, instale os drivers proprietários da sua placa de vídeo
- Configure o Timeshift para criar snapshots do sistema
- Considere criptografar sua instalação para maior segurança

```
📌 **Nota:** Este guia assume que você está instalando em um sistema UEFI moderno. Para sistemas BIOS legado, alguns passos podem variar.
```

Este arquivo está pronto para ser commitado no GitHub com formatação Markdown completa. Ele inclui:
- Títulos organizados
- Blocos de código para comandos
- Ênfase em avisos importantes
- Links para recursos externos
- Ícones visuais para melhor legibilidade
