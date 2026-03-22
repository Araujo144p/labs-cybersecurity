## 1. Objetivo

O objetivo deste laboratório é simular um ambiente real de infraestrutura de servidores Linux. O foco está na configuração de acesso remoto seguro via protocolo SSH, gestão de usuários com diferentes níveis de privilégios e a validação prática das permissões de sistema de arquivos e comandos administrativos.

## 2. Ambiente

- VirtualBox 
- SOs usados: Ubuntu server, Windows
- Tipo de rede: placa em modo bridge

## 3. Configuração

IPs definidos
- Windows: 192.168.0.17
- Ubunt server: 192.168.0.21

Comandos Usados

Windows:
- `ssh boss@192.168.0.21` - comando para acessar remotamente o SSH do Ubuntu server com usuario boss
- `ssh estagiario@192.168.0.21` - comando para acessar remotamente o SSH do Ubuntu server com usuario estagiario
- `sudo ls -a /root` - comando para olhar todos os arquivos dentro da pasta root dentro da sessão SSH(comando também usado para testar as permissões dos usuarios)

Ubuntu Server:
- `ip a` - Comando para exibir o IP e as configurações da interface de rede.
- `ls /etc/netplan/` - Comando usado para exibir os arquivos dentro da pasta netplan(local centralizado para configurar interface de rede manualmente).
- `sudo nano /etc/netplan/nome_do_arquivo.yaml` - comando `nano` é um editor de texto, com ele podemos configurar a interface de rede.
- `sudo systemctl enable ssh` - comando para habilitar o serviço SSH na inicialização.
- `sudo systemctl start ssh` - comando para rodar o SSH.
- `sudo systemctl stop ssh` - comando para parar o SSH.
- `sudo systemctl restart ssh` - comando para reiniciar o SSH.
- `sudo systemctl status ssh` - comando para verificar se o SSH esta rodando.
- `sudo adduser boss` - comando para criar um usuario.
- `sudo usermod -aG sudo boss` - comando para adiciona o usuário boss ao grupo de superusuários.
- `sudo adduser estagiario` - comando para criar um usuario (criei um usuario comum sem permissões).


## 4. Problemas e solução

- Problema: Usuário boss não conseguia usar o comando sudo
- Solução: Utilizei o comando `sudo usermod -aG sudo boss` para dar adiciona o usuário boss ao grupo de superusuários.


## 5. Resultado final

Oque funcionou
- O protocolo SSH foi ativado corretamente.
- Criação de usuarios comuns e com permissões.
- Acesso remoto no windows.
- Validação de que o usuário estagiario não possui privilégios administrativos, enquanto o boss atua como administrador.

O que eu aprendi
- Aprendi a configurar a interface de rede no Ubuntu server.
- Aprendi a ativar o protocolo SSH.
- Aprendi a criar usuarios e dar permissões.
- Aprendi a acessar os usuarios remotamente.
