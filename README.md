# 🔐 Laboratório de Segurança com Kali Linux e Medusa

## 📌 Descrição
Este projeto demonstra ataques de força bruta em serviços vulneráveis...

## ✅ Progresso do Projeto

- [x] Configuração do ambiente
- [x] Reconhecimento com Nmap
- [x] Ataque FTP com Medusa
- [x] Análise de logs
- [ ] Ataque DVWA
- [ ] Ataque SMB
      
## 🧪 Ambiente
- Kali Linux
- Metasploitable 2
- VirtualBox

## 🌐 Configuração de Rede

Para a realização dos testes, foi configurado um ambiente isolado utilizando máquinas virtuais no VirtualBox.

O modo de rede escolhido foi o **Host-Only Adapter**, permitindo a comunicação entre as máquinas virtuais sem acesso à internet externa, garantindo segurança durante os testes.

### 🖥️ Máquinas utilizadas

- Kali Linux (máquina atacante)
- Metasploitable 2 (máquina alvo vulnerável)

### 📡 Endereçamento IP

| Máquina         | IP              | Função            |
|----------------|----------------|------------------|
| Kali Linux     | 192.168.56.101 | Atacante         |
| Metasploitable | 192.168.56.102 | Alvo             |

### 🔗 Teste de conectividade

Foi realizado teste de comunicação entre as máquinas utilizando o comando:

ping 192.168.56.102

## 🔍 Reconhecimento com Nmap

Foi realizada uma varredura para identificar serviços ativos na máquina alvo.


```bash
nmap -sV 192.168.56.102

```
## 💣 Ataque de Força Bruta em FTP

### 📌 Objetivo

Realizar um ataque de força bruta no serviço FTP da máquina Metasploitable 2, com o objetivo de identificar credenciais válidas e demonstrar vulnerabilidades relacionadas ao uso de senhas fracas.

---

### 🔍 Identificação do Serviço

Através do uso do Nmap, foi identificado que o serviço FTP estava ativo na porta 21 do alvo.

nmap -sV 192.168.56.102
### 🧪 Validação do Serviço
```bash
ftp 192.168.56.102
```

### 🚀 Execução do Ataque

O ataque de força bruta foi realizado utilizando a ferramenta Medusa, com uma lista simples de senhas (wordlist).
```bash
medusa -h 192.168.56.102 -u msfadmin -P wordlists/simple-wordlist.txt -M ftp
```
### 🔓 Resultado

O ataque foi bem-sucedido, permitindo a descoberta das credenciais válidas:

- **Usuário:** msfadmin  
- **Senha:** msfadmin

Isso demonstra a presença de credenciais padrão e ausência de políticas de segurança adequadas.

### 📸 Evidência do Ataque

### 🔎 Validação de Acesso

Após a descoberta das credenciais, foi realizado login manual no serviço FTP:
```bash

ftp 192.168.56.102
```
📄 Análise de Logs

Foi realizada...

### 📸 Evidência dos Logs

### 🛡️ Medidas de Mitigação

Para evitar esse tipo de ataque, recomenda-se:

- Utilização de senhas fortes  
- Implementação de bloqueio por tentativas de login  
- Uso de ferramentas como Fail2Ban  
- Monitoramento contínuo de logs  
- Implementação de MFA  
## 📸 Evidências
(ver pasta /images)

##📚 Conclusão

O teste demonstrou que serviços expostos com credenciais fracas representam um alto risco de segurança, podendo ser facilmente comprometidos por ataques automatizados de força bruta.


