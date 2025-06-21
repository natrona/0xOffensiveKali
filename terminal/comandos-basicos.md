# Guia Completo de Comandos Básicos do Kali Linux

## Índice
- [Sistema e Informações](#sistema-e-informações)
- [Navegação e Arquivos](#navegação-e-arquivos)
- [Gerenciamento de Pacotes](#gerenciamento-de-pacotes)
- [Redes e Conectividade](#redes-e-conectividade)
- [Processos e Serviços](#processos-e-serviços)
- [Usuários e Permissões](#usuários-e-permissões)
- [Ferramentas de Segurança](#ferramentas-de-segurança)
- [Compactação e Arquivos](#compactação-e-arquivos)
- [Atalhos do Terminal](#atalhos-do-terminal)

---

## Sistema e Informações

```bash
# Mostrar informações do sistema
uname -a

# Versão do Kali Linux
cat /etc/os-release

# Uso de disco
df -h

# Uso de memória
free -h

# Tempo de atividade do sistema
uptime

# Histórico de comandos
history

# Limpar terminal
clear
```

---

## Navegação e Arquivos

```bash
# Listar arquivos (detalhado)
ls -la

# Mudar diretório
cd /caminho/do/diretorio

# Voltar ao diretório anterior
cd -

# Mostrar diretório atual
pwd

# Criar diretório
mkdir novo_dir

# Copiar arquivos
cp arquivo_origem arquivo_destino

# Mover/renomear arquivos
mv antigo novo

# Remover arquivos
rm arquivo

# Remover diretório recursivo
rm -rf diretorio

# Ver conteúdo do arquivo
cat arquivo.txt

# Editar arquivos (nano)
nano arquivo.txt
```

---

## Gerenciamento de Pacotes

```bash
# Atualizar lista de pacotes
sudo apt update

# Atualizar todos os pacotes
sudo apt upgrade

# Instalar pacote
sudo apt install nome_do_pacote

# Remover pacote
sudo apt remove nome_do_pacote

# Procurar pacote
apt search termo_de_busca

# Listar pacotes instalados
apt list --installed

# Limpar cache de pacotes
sudo apt autoremove && sudo apt clean
```

---

## Redes e Conectividade

```bash
# Configurações de rede
ip a

# Testar conectividade
ping google.com

# Rota de rede
ip route

# Portas abertas
ss -tulnp

# Download arquivos
wget https://exemplo.com/arquivo

# Transferência via SCP
scp arquivo usuario@ip:/caminho/destino

# Verificar DNS
dig exemplo.com

# Alterar DNS temporário
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```

---

## Processos e Serviços

```bash
# Listar processos
ps aux

# Gerenciar processos (q para sair)
top

# Matar processo
kill -9 PID

# Listar serviços
systemctl list-units --type=service

# Iniciar serviço
sudo systemctl start servico

# Habilitar serviço
sudo systemctl enable servico
```

---

## Usuários e Permissões

```bash
# Adicionar usuário
sudo adduser novo_usuario

# Mudar para root
sudo su -

# Alterar senha
passwd

# Alterar permissões
chmod 755 arquivo

# Alterar dono do arquivo
chown usuario:grupo arquivo

# Ver usuários logados
who
```

---

## Ferramentas de Segurança

```bash
# Verificar portas abertas (Nmap)
sudo nmap -sV endereço_ip

# Analisar tráfego (tcpdump)
sudo tcpdump -i eth0

# Testar senhas (Hydra)
hydra -l usuario -P wordlist.txt ssh://ip

# Verificar vulnerabilidades (Nikto)
nikto -h http://alvo.com

# Teste de estresse (Slowloris)
slowhttptest -c 1000 -H -g -o slowhttp -i 10 -r 200 -t GET -u http://alvo -x 24 -p 3
```

---

## Compactação e Arquivos

```bash
# Compactar tar.gz
tar -czvf arquivo.tar.gz pasta/

# Extrair tar.gz
tar -xzvf arquivo.tar.gz

# Compactar zip
zip -r arquivo.zip pasta/

# Extrair zip
unzip arquivo.zip
```

---

## Atalhos do Terminal

| Atalho | Descrição |
|--------|-----------|
| Ctrl+C | Interromper processo |
| Ctrl+Z | Suspender processo |
| Ctrl+D | Sair do terminal |
| Ctrl+L | Limpar terminal |
| Ctrl+R | Buscar no histórico |
| Tab | Auto-completar |
| ↑/↓ | Navegar no histórico |
| Ctrl+A | Início da linha |
| Ctrl+E | Fim da linha |
| Ctrl+U | Apagar até início |
| Ctrl+K | Apagar até fim |

---

## Dicas Avançadas

1. Para redirecionar saída:
```bash
comando > arquivo_saida.txt  # Sobrescrever
comando >> arquivo_saida.txt # Acrescentar
```

2. Filtrar saída com grep:
```bash
cat arquivo.log | grep "erro"
```

3. Executar comandos como root temporariamente:
```bash
sudo !!  # Repete último comando como root
```

4. Monitorar alterações em arquivos:
```bash
tail -f /var/log/syslog
```

5. Criar alias para comandos frequentes:
```bash
alias ll='ls -la'
echo "alias ll='ls -la'" >> ~/.bashrc
```

> **Nota:** Muitos comandos de segurança requerem privilégios root. Use com cuidado!
