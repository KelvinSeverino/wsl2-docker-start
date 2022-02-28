## Criando arquivo Docker-compose.yml
#### O arquivo Docker-compose.yml permite criar e priorizar ordem de execucao dos containers e outras parametrizações

- Criando arquivo docker-compose.yml
```bash
    cd /docker/projeto
    nano docker-compose.yml
```

- Informações no docker-compose.yml
```bash
    #Versao do arquivo docker-compose
    version: "3.8"

    #Servicos
    services:
    #Nome de indentificacao do servico, pode colocar outro se necessario
    db:
        #imagem de origem
        image: mariadb:10.8
        #parametros para configuracao
        environment:
        - MARIADB_USER=root
        #- MARIADB_PASSWORD=1234
        - MARIADB_ALLOW_EMPTY_ROOT_PASSWORD=yes
        - MARIADB_DATABASE=laravel
        #Porta de Comunicacao Local > Container
        ports:
        - 8011:3306
        #Caminho da pasta local para armazenar os dados (./ seria o caminho atual do arquivo docker-compose)
        volumes:
        - ./db_data:/etc/mysql/conf.d

    app:
        #Imagem de origem
        image: kelvinsev/webserver:1.0
        #Caminho da pasta local para armazenar os dados (./ seria o caminho atual do arquivo docker-compose)
        volumes:
        - ./:/var/www/html
        #Porta de Comunicacao Local > Container
        ports:
        - 8010:80
        #Gera link de comunicacao com o database acima
        links:
        - db
        #Para instalar o app, depende da finalizacao do db
        depends_on:
        - db
        tty: true
```

#### Documentação de Instalação Docker Compose
- [Instalação do Docker Compose](https://documentation.wazuh.com/current/docker/docker-installation.html)

- Antes de Rodar o Compose, precisa realizar build do dockerfile, pois ele gera a imagem kelvinsev/serverweb:1.0
```bash
    sudo docker build . -t kelvinsev/webserver:1.0
``` 

- Realizar criacao e configuracao do container pelo compose
```bash
    sudo docker-compose up -d
```

