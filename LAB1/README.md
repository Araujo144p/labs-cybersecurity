## 1. Objetivo

Simular comunicação entre máquinas em rede interna e aplicar regras de firewall.

## 2. Ambiente

- VirtualBox 
- SOs usados: Linux Mint, Windows
- Tipo de rede: placa em modo bridge

## 3. Configuração

IPs definidos
- Windows: 192.168.0.17
- Linux Mint: 192.168.0.20

Comandos usados

Windows:
- `ipconfig` - Comando para exibir as configurações da rede TCP/IP, com endereço IP, Mascará de sub-rede e gateway.
- Pelo painel `Propriedades de protocolo IP Versão 4 (TCP/IPv4)` foi definido manualmente o IP 192.168.0.17.
- `ping 192.168.0.20` - Comando para testar comunicão via protocolo ICMP com a maquina do Linux.

Linux Mint:
- `ifconfig` - comando para exibir os parâmetros de interface de rede, como endereço IP, mascará de sub-rede e gateway.
- `nmcli device show` - comando para exibir os devices da rede.
- `nmcli connection show` - comando para exibir as conexões de rede do computador.
- `sudo nmcli connection modify "Conexão cabeada 1" ipv4.address 192.168.0.20/24` - comando para definir o IP da máquina.
- `sudo nmcli connection modify "Conexão cabeada 1" ipv4.gateway 192.168.0.1` - comando para definir o IP do gateway.
- `sudo nmcli connection modify "Conexão cabeada 1" ipv4.dns "8.8.8.8,8.8.4.4"` - comando para definir o DNS do IP.
- `sudo nmcli connection modify "Conexão cabeada 1" ipv4.method manual` - alterar o método para manual.
- `sudo nmcli connection up "Conexão cabeada 1"` - ativar a conexão.
- `python3 -m http.server 8080` - comando para abrir uma porta.
- `sudo ufw deny 8080` - comando que bloqueia o tráfego de entrada na porta 8080.

Problemas e solução

- O windows conseguia localizar o linux utilizando o comando ping, porém o linux não conseguia localizar o windows.
- A solução foi entrar no firewall do windows, regras de entrada e ativar as 4 regras "Partilha de Ficheiros e Impressoras (Pedido de Eco - Entrada de ICMPv4)" e Partilha de Ficheiros e Impressoras (Pedido de Eco - Entrada de ICMPv6).

Resultado final

Oque funcionou
- A comunicação entre dois computadores (TCP e IMCP).
- Bloqueio de porta pelo firewall.
- Após aplicar a regra do firewaall no Linux, tentei acessar o IP pelo navegador do Windows (192.168.0.20:8080) e a conexão foi recusada/timeout, confirmando o bloqueio.

O que eu aprendi
- Visualizar configurações de rede (Linux e Windows).
- Configurar IP manualmente (Linux e Windows).
- Fazer a comunicação TCP e IMCP utilizando python para criar um server http com a porta 8080 e pelo comando ping.
- Aprendi a definir regras no firewall.
