<!-- kali-vm.md -->

# Como Rodar o Kali Linux em uma Máquina Virtual (VM)

[![Kali Linux](https://img.shields.io/badge/Kali%20Linux-via%20VM-blue?logo=linux&style=for-the-badge)](https://www.kali.org/get-kali/#kali-virtual-machines)
[![VirtualBox](https://img.shields.io/badge/Compatível%20com-VirtualBox-lightgray?logo=virtualbox&style=for-the-badge)](https://www.virtualbox.org/)
[![VMware](https://img.shields.io/badge/Compatível%20com-VMware-lightgray?logo=vmware&style=for-the-badge)](https://www.vmware.com/)
[![Documentação Kali](https://img.shields.io/badge/Documentação-Oficial-informational?style=for-the-badge)](https://docs.kali.org/)

---

## 1. Download da Imagem Oficial

Acesse o site oficial e baixe a imagem do Kali Linux própria para máquinas virtuais:

https://www.kali.org/get-kali/#kali-virtual-machines

Formatos disponíveis:
- `.ova`: pronto para uso no VirtualBox e VMware
- `.iso`: instalação manual

---

## 2. Ferramentas Compatíveis

- [VirtualBox](https://www.virtualbox.org/): gratuito e open source
- [VMware Workstation Player](https://www.vmware.com/products/workstation-player.html): gratuito para uso pessoal

---

## 3. Instalação no VirtualBox (modo simplificado)

1. Abra o VirtualBox  
2. Vá em **Arquivo > Importar Appliance**  
3. Selecione o arquivo `.ova` baixado  
4. Clique em **Avançar > Importar**  
5. Após a importação, inicie a máquina virtual  
6. Credenciais padrão:  
   - Usuário: `kali`  
   - Senha: `kali`

---

## 4. Recomendações para Melhor Desempenho

- Ative clipboard e pastas compartilhadas nas configurações da VM  
- Instale as ferramentas de integração (Guest Additions / VMware Tools)  
- Altere a alocação de RAM e CPUs conforme o desempenho da sua máquina  
- Utilize snapshots para criar pontos de restauração antes de alterações importantes

---

## 5. Vantagens de Usar Kali em Máquina Virtual

- Isolamento completo do sistema principal  
- Restauração rápida em caso de erro  
- Ideal para testes, treinamentos e laboratórios CTF  
- Fácil descarte e reinício do ambiente

---

## 6. Aviso Legal

O uso das ferramentas do Kali Linux deve ser feito **exclusivamente em ambientes autorizados ou de laboratório**. Qualquer atividade em redes ou sistemas sem permissão pode constituir crime previsto na legislação brasileira.

Para aprendizado seguro, recomenda-se o uso de plataformas como:
- [TryHackMe](https://tryhackme.com)
- [Hack The Box](https://www.hackthebox.com)

---

Criado por **Ruše** para o repositório [0xOffensiveKali](https://github.com/RuseGit/0xOffensiveKali).
