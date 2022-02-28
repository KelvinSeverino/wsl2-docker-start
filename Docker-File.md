## Criando arquivo Dockerfile
#### O arquivo docker file reune varios comandos para omitizar o processo de criação de um container

- Criando arquivo Dockerfile sem extensao
```bash
    nano Dockerfile
```

- Preenchendo arquivo Dockerfile
```bash
    #Informa o Container base para baixar do Docker Hub
    FROM ubuntu:22.04

    #Setando variavel
    ENV timezone=America/Sao_Paulo

    #Comandos para rodar no ubuntu
    RUN apt-get update && \
        ln -snf /usr/share/zoneinfo/${timezone} /etc/localtime && echo ${timezone} > /etc/timezone && \
        apt-get install -y apache2 && \
        apt-get install -y php8.1 && \
        apt-get install -y php-xdebug && \
        apt-get install -y mariadb-server && \ 
        apt-get install -y mariadb-client && \ 
        apt-get install -y php8.1-mysql && \
        php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php composer-setup.php && rm composer-setup.php && mv composer.phar /usr/local/bin/composer && chmod a+x /usr/local/bin/composer

    #Porta de Comunicacao
    EXPOSE 80

    #Diretorio de Trabalho
    WORKDIR /var/www/html

    #Comando para serem rodados ao final do build
    ENTRYPOINT /etc/init.d/apache2 start && /bin/bash
```

- Realizando Build de um container a partir do Dockerfile
```bash
    cd /docker/projeto
    sudo docker build . -t kelvinsev/webserver:1.0
```

- Realizando Build de um container a partir do Dockerfile
```bash
    cd /docker/projeto
    sudo docker build . -t kelvinsev/webserver:1.0
``` 

- Executando container criado acima na porta 8000
```bash
    sudo docker run -it -p 8000:80 kelvinsev/webserver:1.0
``` 