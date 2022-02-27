## Comandos Docker
- Listar containers
```bash
    sudo docker ps
```

- Renomear container
```bash
    sudo docker rename nome_antigo nome_novo
```

- Acessar container
```bash
    sudo docker attach CONTAINER_ID
```

- Executar comando no container e sair após fim do comando
```bash
    sudo docker exec CONTAINER_ID COMANDO -ef
```

- Parar container
```bash
    sudo docker stop CONTAINER_ID
```

- Listar imagens dos container
```bash
    sudo docker images
```

## Portas
- Executando e informando porta do container (porta_host:porta_container)
```bash
    sudo docker run -P -d -p 8000:80 CONTAINER_ID
```

## Compartilhando Volumes
- Executando e informando volume compartilhado do container (porta_host:porta_container / path_volume_host:path_volume_container)
```bash
    sudo docker run -P -d -p 8000:80 -v /docker/volume:/var/volume CONTAINER_ID
```