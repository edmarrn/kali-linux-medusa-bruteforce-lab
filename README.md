# 🔐 Laboratório de Segurança com Kali Linux e Medusa

## 📌 Descrição

Este projeto demonstra ataques de força bruta em serviços vulneráveis em um ambiente controlado, utilizando Kali Linux e a ferramenta Medusa. O objetivo é compreender como ataques funcionam na prática, identificar vulnerabilidades e propor medidas de mitigação.

> ⚠️ Este laboratório foi realizado em ambiente controlado para fins educacionais.

---

## ✅ Progresso do Projeto

* [x] Configuração do ambiente
* [x] Reconhecimento com Nmap
* [x] Ataque FTP com Medusa
* [x] Análise de logs
* [ ] Ataque DVWA
* [ ] Ataque SMB

---

## 🧪 Ambiente

* Kali Linux (máquina atacante)
* Metasploitable 2 (máquina alvo vulnerável)
* VirtualBox

---

## 🌐 Configuração de Rede

Para a realização dos testes, foi configurado um ambiente isolado utilizando máquinas virtuais no VirtualBox.

O modo de rede escolhido foi o **Host-Only Adapter**, permitindo a comunicação entre as máquinas virtuais sem acesso à internet externa, garantindo segurança durante os testes.

---

## 🖥️ Máquinas Utilizadas

* Kali Linux (atacante)
* Metasploitable 2 (alvo)

---

## 📡 Endereçamento IP

| Máquina        | IP             | Função   |
| -------------- | -------------- | -------- |
| Kali Linux     | 192.168.56.101 | Atacante |
| Metasploitable | 192.168.56.102 | Alvo     |

---

## 🔗 Teste de Conectividade

Foi realizado teste de comunicação entre as máquinas:

```bash
ping 192.168.56.102
```

---

## 🔍 Reconhecimento com Nmap

Foi realizada uma varredura para identificar serviços ativos na máquina alvo:

```bash
nmap -sV 192.168.56.102
```

### 📸 Evidência

<img width="457" height="474" alt="image" src="https://github.com/user-attachments/assets/e1be39fd-d047-4476-93ea-000c02c21ef3" />


---

## 💣 Ataque de Força Bruta em FTP

### 📌 Objetivo

Realizar um ataque de força bruta no serviço FTP da máquina Metasploitable 2, com o objetivo de identificar credenciais válidas e demonstrar vulnerabilidades relacionadas ao uso de senhas fracas.

---

### 🔍 Identificação do Serviço

Através do Nmap, foi identificado que o serviço FTP estava ativo na porta 21.

---

### 🧪 Validação do Serviço

```bash
ftp 192.168.56.102
```

---

### 🚀 Execução do Ataque

O ataque foi realizado com a ferramenta Medusa:

```bash
medusa -h 192.168.56.102 -u msfadmin -P wordlists/simple-wordlist.txt -M ftp
```

---

### 🔓 Resultado

O ataque foi bem-sucedido, permitindo a descoberta das credenciais:

* **Usuário:** msfadmin
* **Senha:** msfadmin

Isso evidencia o uso de credenciais padrão e ausência de políticas de segurança adequadas.

---

### 📸 Evidência do Ataque

![FTP Bruteforce](images/ftp/ftp-bruteforce.png)

---

### 🔎 Validação de Acesso

Após a descoberta das credenciais, foi realizado login manual no serviço FTP:

```bash
ftp 192.168.56.102
```

O acesso foi realizado com sucesso, confirmando o comprometimento do sistema.

---

## 📄 Análise de Logs

Foi realizada a análise dos logs do sistema, onde foram identificadas múltiplas tentativas de login falhas provenientes do IP atacante.

Esse comportamento caracteriza um ataque de força bruta.

---

### 📸 Evidência dos Logs

<img width="567" height="391" alt="log" src="https://github.com/user-attachments/assets/47f6cb5c-cc9b-4f33-92e7-b621c7148da5" />


---

## 🛡️ Medidas de Mitigação

Para evitar esse tipo de ataque, recomenda-se:

* Utilização de senhas fortes
* Implementação de bloqueio por tentativas de login
* Uso de ferramentas como Fail2Ban
* Monitoramento contínuo de logs
* Implementação de autenticação multifator (MFA)

---

## 📸 Evidências

As evidências completas estão disponíveis na pasta:

```
/images
```

---

## 📚 Conclusão

O teste demonstrou que serviços expostos com credenciais fracas representam um alto risco de segurança, podendo ser facilmente comprometidos por ataques automatizados de força bruta.

Além disso, foi possível observar como esse tipo de ataque pode ser detectado através da análise de logs, reforçando a importância de monitoramento e boas práticas de segurança.


