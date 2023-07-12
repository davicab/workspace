# work
Espaço de trabalho ultilizando docker 

# iniciar container - docker start container_name
# parar container - docker stop container_name
# reiniciar container - docker restart container_name
# remover container - docker rm container_name

# Instalar containers - 

# 1 - clone esse repositorio em alguma pasta (ex: Documents)
# 2 - via terminarl : 
    - cd Documents/workspace
    - cd database/mariadb
    - docker-compose up -d
    - desça ate a pasta workspace novamente (para descer UMA pasta use : cd ../)
    - cd nginx
    - docker-compose up -d
    - cd ../
    - cd php/8_1
    - docker-compose up -d
    - desça ate a pasta workspace novamente
    - cd projects
    - docker-compose up -d
    
# Apos a instalacao, confira se os containers foram criados. 5 containers devem estar presentes : wks_php_8_1, wks_node18, php8_1, webserver, db
    - docker ps -a 

# Configurar hosts:
# 1 - via terminal:
    - sudo nano /etc/hosts (vai abrir o terminal de edicao, navege por ele usando as setas do teclado)
    - abaixo da primeira linha do editor, escreva : 127.0.0.1      wegresso.local
    - CTRL + o (salvar o arquivo)
    - ENTER
    - CTRl + X
