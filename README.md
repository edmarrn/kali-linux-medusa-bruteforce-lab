# 🔐 Laboratório de Segurança com Kali Linux e Medusa

## 📌 Descrição
Este projeto demonstra ataques de força bruta em serviços vulneráveis...

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

```bash
ping 192.168.56.102

## 🔍 Reconhecimento com Nmap

Foi realizada uma varredura para identificar serviços ativos na máquina alvo.

```bash
nmap -sV 192.168.56.102

## 💣 Ataque de Força Bruta em FTP

### 📌 Objetivo

Realizar um ataque de força bruta no serviço FTP da máquina Metasploitable 2, com o objetivo de identificar credenciais válidas e demonstrar vulnerabilidades relacionadas ao uso de senhas fracas.

---

### 🔍 Identificação do Serviço

Através do uso do Nmap, foi identificado que o serviço FTP estava ativo na porta 21 do alvo.

```bash
nmap -sV 192.168.56.102

## 🛡️ Mitigações
(a preencher)

## 📸 Evidências
(ver pasta /images)
