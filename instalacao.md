# Instalação - Licença e Versões

![image](https://user-images.githubusercontent.com/27785070/135142078-ab2cce86-7605-43bf-8a2a-0f5b54470458.png)
![image](https://user-images.githubusercontent.com/27785070/135142124-8bee2c2b-eacb-4fdb-96f7-5bc2b7f206a3.png)
![image](https://user-images.githubusercontent.com/27785070/135142156-5ce41627-89ef-4fbb-a2d2-cd406444462d.png)

# Instalação - Docker

![image](https://user-images.githubusercontent.com/27785070/135142252-c0dc2759-9194-43ba-83e1-757a0938ec1a.png)
![image](https://user-images.githubusercontent.com/27785070/135142294-5443b1c3-2d7c-40ce-98bb-eb7115917247.png)
![image](https://user-images.githubusercontent.com/27785070/135142344-2f094e37-dbec-4d9c-a867-a0f215633653.png)

# Acessos Ambiente Docker

![image](https://user-images.githubusercontent.com/27785070/135142458-89114c1d-4b4e-482c-beec-88892baa2593.png)

# Confluent Portas

![image](https://user-images.githubusercontent.com/27785070/135142541-0ce855ed-944f-4fe5-8e00-27b8a8f3c4b6.png)

# Exercícios Instalação

![image](https://user-images.githubusercontent.com/27785070/135142815-70efb429-b5da-4c59-9e83-0d8f980895c4.png)

# Instalação Cluster Kafka

##### 1. Criar a pasta kafka e inserir o arquivo docker-compose.yml da Guia Arquivos do treinamento

##### 2. Instalação do docker e docker-compose

Docker: https://docs.docker.com/get-docker/ (Links para um site externo.)
Docker-compose: https://docs.docker.com/compose/install/ (Links para um site externo.)

##### 3. Inicializar o cluster Kafka através do docker-compose

`$ docker-compose up -d`

##### 4. Listas as imagens em execução

`$ docker images`

`$ docker ps -a`

##### 5. Visualizar o log dos serviços broker e zookeeper

`$ docker logs zookeeper`

`$ docker logs broker`

##### 6. Visualizar a interface do Confluent Control Center

Acesso: http://localhost:9021/


##### _Eu tive uns problemas na instalação do container do KAFKA pois não conseguia parar o serviço do Mongo que se utiliza da mesma porta._

###### SOLUÇÃO:
_Serviços a serem removidos:_

mongo e mongo-express

_Forcei a parada de cada serviço_

`$ docker container stop mongo`

`$ docker container stop mongo-express`

_Lista cada serviço para conhecer seu ID_

`$ docker ps -a`

_Removendo cada serviço pelo seu ID_

`$ docker container rm 0203bc25ee13`

`$ docker container rm <ID>`

_Remove todos os volumes e imagens não utilizadas_
  
`$ docker system prune --all --force --volumes`

![image](https://user-images.githubusercontent.com/27785070/135161237-cd3b9df7-70a2-488d-8306-1edfc3f36706.png)
![image](https://user-images.githubusercontent.com/27785070/135161277-c9a21386-71a2-447b-af26-d6c1538b1ccb.png)
![image](https://user-images.githubusercontent.com/27785070/135161335-d7cdd31b-6ae9-472e-8f4e-db60637bb8c8.png)


