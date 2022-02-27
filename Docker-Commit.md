## Criando e Commitando Imagem do Container
- Executando imagem do ubuntu e acessando bash com -it
```bash
    sudo docker run -it --detach-keys="ctrl-p" ubuntu:22.04 /bin/bash
    sudo apt-get update
    sudo apt-get install apache2 -y && apt-get install php -y && apt-get install php-xdebug -y
```

- Listando historico dos containers
```bash
    sudo docker ps -a
```

- Commitando imagem (docker commit -m "What you did to the image" -a "Author Name" container_id repository/new_image_name:tag_version)
```bash
    docker commit container_id repository/new_image_name:1.0
```

- Realizando Login no Docker Hub
```bash
    docker login -u docker-registry-username
```

- Enviando imagem para repositorio
```bash
    docker push repository/new_image_name:1.0
```

- Baixando imagem do repositorio DockerHub
```bash
    docker -it --detach-keys="ctrl-p" -p 8000:80 -v /docker/volume:/var/www/html repository/new_image_name:1.0
```

## Atualizando Imagem e Commitando
- Executando imagem do ubuntu e acessando bash com -it
```bash
    sudo docker run -it --detach-keys="ctrl-p" ubuntu:22.04 /bin/bash
    sudo apt-get update
    sudo apt-get install php-xdebug -y
```

- Listando historico dos containers
```bash
    sudo docker ps -a
```

- Commitando imagem (docker commit -m "What you did to the image" -a "Author Name" container_id repository/new_image_name:tag_version)
```bash
    docker commit container_id repository/new_image_name:1.0
```

- Realizando Login no Docker Hub
```bash
    docker login -u docker-registry-username
```

- Enviando imagem para repositorio
```bash
    docker push repository/new_image_name:1.0
```