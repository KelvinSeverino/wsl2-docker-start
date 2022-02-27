
## Instalação WSL2

#### Documentação de Instalação oficial WSL
- [Instalação do WSL](https://docs.microsoft.com/pt-br/windows/wsl/install)

- Após instalado o WSL, executar os comandos abaixo listar todas as distruibições e a versão do WSL correspondente
```bash
  wsl -l -v
```

- Se necessário mudar a versão do WSL1 para WSL2:
```bash
  wsl --set-version <distro name> 2
```

## Docker
- Desinstalar versões antigas:
```bash
  sudo apt-get remove docker docker-engine docker.io containerd runc
```

- Setar o repositório dos pacotes
```bash
  sudo apt-get update
  sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

- Adicionar a chave GPG official do Docker
```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

- Configurar repositorio estavel
```bash
    echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### Docker Engine
- Atualizar os pacotes e instalar pacotes Docker
```bash
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
```

#### Testar Docker
- Verificar status do Serviço Docker
```bash
    sudo service docker status
    sudo service docker start
```

- Listar containers
```bash
    sudo docker ps
```

- Instalar e Rodar container de HelloWorld
```bash
    sudo docker run -P -d nginxdemos/hello
```

- Listar containers
```bash
    sudo docker ps
```

Após executado ultimo passo, pegar a Porta do container e acessar no navegador.
