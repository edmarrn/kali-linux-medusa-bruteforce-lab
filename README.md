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
* [x] Análise de aplicação web (DVWA)
* [ ] Ataque DVWA (força bruta)
* [ ] Ataque SMB

---

## 🧪 Ambiente

* Kali Linux (máquina atacante)
* Metasploitable 2 (máquina alvo vulnerável)
* VirtualBox

---

## 🌐 Configuração de Rede

Foi configurado um ambiente isolado utilizando **Host-Only Adapter**, permitindo comunicação entre as máquinas sem acesso à internet externa.

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

```bash
ping 192.168.56.102
```

---

## 🔍 Reconhecimento com Nmap

```bash
nmap -sV 192.168.56.102
```

### 📸 Evidência

<img width="457" height="474" src="https://github.com/user-attachments/assets/e1be39fd-d047-4476-93ea-000c02c21ef3" />

---

# 💣 Ataque de Força Bruta em FTP

## 📌 Objetivo

Explorar credenciais fracas no serviço FTP.

---

## 🚀 Execução

```bash
medusa -h 192.168.56.102 -u msfadmin -P wordlists/simple-wordlist.txt -M ftp
```

---

## 🔓 Resultado

* **Usuário:** msfadmin
* **Senha:** msfadmin

---

## 📸 Evidências

<img width="567" height="590" src="https://github.com/user-attachments/assets/44790a07-506d-44e9-8cbe-7649af270b54" />

<img width="567" height="391" src="https://github.com/user-attachments/assets/d7033392-caf8-4f0c-8bfd-0a631ef9b018" />

---

## 🔎 Validação

```bash
ftp 192.168.56.102
```

---

## 📄 Análise de Logs

Múltiplas tentativas de login falhas foram identificadas.

### 📸 Evidência

<img width="567" height="391" src="https://github.com/user-attachments/assets/47f6cb5c-cc9b-4f33-92e7-b621c7148da5" />

---

# 🌐 Análise de Aplicação Web (DVWA)

## 📌 Objetivo

Analisar vulnerabilidades em formulário web de autenticação.

---

## 🔍 Acesso

```bash
http://192.168.56.102/dvwa
```

---

## 🔐 Login

* **Usuário:** admin
* **Senha:** password

---

## ⚙️ Configuração

* Security Level: **Low**

---

## 🎯 Identificação da Vulnerabilidade

Ao testar o login, foi possível identificar parâmetros na URL:

```bash
http://192.168.56.102/dvwa/vulnerabilities/brute/?username=admin&password=123&Login=Login
```

---

## 📸 Evidência

<img width="949" height="1053" alt="image" src="https://github.com/user-attachments/assets/011b9ace-d39e-4af4-acc1-a6a4760c5cf7" />


---

## 🧠 Análise de Segurança

A aplicação apresenta vulnerabilidades como:

* Uso do método GET (exposição de credenciais)
* Ausência de bloqueio por tentativas
* Falta de proteção contra automação

---

## 🛡️ Mitigação

* Utilizar método POST
* Implementar CAPTCHA
* Limitar tentativas de login
* MFA

---

## 📸 Evidências

```
/images
```

---

## 📚 Conclusão

O projeto demonstrou na prática como ataques de força bruta podem comprometer sistemas vulneráveis.

A análise reforça a importância de:

* Senhas seguras
* Monitoramento de logs
* Boas práticas de desenvolvimento seguro
