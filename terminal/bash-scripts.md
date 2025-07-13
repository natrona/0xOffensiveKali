# Bash Scripting Guide

![Bash Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Bash_Logo_Colored.svg/1200px-Bash_Logo_Colored.svg.png)

<div align="center">
  <img src="https://img.shields.io/badge/Shell-Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="Bash">
  <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Open%20Source-✓-success?style=for-the-badge" alt="Open Source">
</div>

## Índice
- [Introdução](#introdução)
- [Sintaxe Básica](#sintaxe-básica)
- [Variáveis](#variáveis)
- [Estruturas de Controle](#estruturas-de-controle)
- [Funções](#funções)
- [Boas Práticas](#boas-práticas)
- [Exemplos Úteis](#exemplos-úteis)

## Introdução
Bash (Bourne Again Shell) é um interpretador de comandos e linguagem de script amplamente utilizada em sistemas Unix/Linux.

**Por que usar Bash?**
✔ Automatização de tarefas  
✔ Administração de sistemas  
✔ Processamento de texto  
✔ Portabilidade entre sistemas Unix-like

## Sintaxe Básica
Estrutura básica de um script Bash:

\`\`\`bash
#!/bin/bash
# Comentário explicativo
echo "Olá, Mundo!"
\`\`\`

**Como executar:**
\`\`\`bash
# Dar permissão de execução
chmod +x script.sh

# Executar o script
./script.sh
\`\`\`

## Variáveis
Declaração e uso de variáveis:

\`\`\`bash
nome="Usuário"
echo "Olá, $nome"

# Variáveis especiais
echo "Nome do script: $0"
echo "Primeiro argumento: $1"
echo "Número de argumentos: $#"
\`\`\`

## Estruturas de Controle
### Condicionais
\`\`\`bash
if [ $1 -gt 10 ]; then
  echo "Maior que 10"
elif [ $1 -eq 10 ]; then
  echo "Igual a 10"
else
  echo "Menor que 10"
fi
\`\`\`

### Loops
**For loop:**
\`\`\`bash
for i in {1..5}; do
  echo "Iteração $i"
done
\`\`\`

**While loop:**
\`\`\`bash
contador=1
while [ $contador -le 5 ]; do
  echo "Contagem: $contador"
  ((contador++))
done
\`\`\`

## Funções
Definição e chamada de funções:

\`\`\`bash
saudacao() {
  local nome=$1
  echo "Bem-vindo, $nome!"
}

saudacao "Carlos"
\`\`\`

## Boas Práticas
1. Sempre inclua `#!/bin/bash` no shebang
2. Use `set -e` para sair em caso de erro
3. Comente seu código adequadamente
4. Valide entradas de usuário
5. Use aspas para variáveis: `"$var"`
6. Prefira `[[ ]]` para testes em vez de `[ ]`

## Exemplos Úteis
### Backup simples
\`\`\`bash
#!/bin/bash
# Backup de diretório
backup_dir="/backup"
origem="$HOME/documentos"

tar -czf "$backup_dir/backup_$(date +%Y%m%d).tar.gz" "$origem"
\`\`\`

### Processamento de logs
\`\`\`bash
#!/bin/bash
# Conta erros no log
log_file="/var/log/syslog"
error_count=$(grep -i "error" "$log_file" | wc -l)

echo "Erros encontrados: $error_count"
\`\`\`

---

<div align="center">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License">
  <p>📅 Última atualização: $(date +'%d/%m/%Y')</p>
</div>
