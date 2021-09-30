# Kafka por Linha de Comando

#### PREPARAÇÃO DO AMBIENTE 

$ docker-compose up -d

$ docker-compose start

$ docker exec -it broker bash

$ docker ps

root@broker:/# kafka-topics --bootstrap-server localhost:9092 --list

ou

root@broker:/# kafka-topics --bootstrap-server broker:9092 --list

#### 1. Criar o tópico msg-cli com 2 partições e 1 réplica
root@broker:/# kafka-topics --bootstrap-server broker:9092 --create --topic msg-cli --partitions 2 --replication-factor 1

#### 2. Descrever o tópico msg-cli
root@broker:/# kafka-topics --bootstrap-server broker:9092 --topic msg-cli --describe

#### 3. Criar o consumidor do grupo app-cli
OBS: Não precisa estar na pasta kafa
lserra@engdados:~$ docker exec -it broker bash
root@broker:/# kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app-cli 

AGUARDANDO MENSAGENS

#### 4. Enviar as seguintes mensagens do produtor
CRIANDO UM PRODUTOR

lserra@engdados:~$ docker exec -it broker bash
root@broker:/# kafka-console-producer --broker-list localhost:9092 --topic msg-cli
>Msg 1
>Msg 2

#### 5. Criar outro consumidor do grupo app-cli
root@broker:/# kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app-cli 

#### 6. Enviar as seguintes mensagens do produtor

Msg 4
Msg 5
Msg 6
Msg 7

#### 7. Criar outro consumidor do grupo app2-cli
lserra@engdados:~$ docker exec -it broker bash
root@broker:/# kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app2-cli 

#### 8. Enviar as seguintes mensagens do produtor

>Msg 8
>Msg 9
>Msg 10
>Msg 11

#### 9. Parar o app-cli
Ctrl + c

#### 10. Definir o deslocamento para -2 offsets do app-cli
root@broker:/# kafka-consumer-groups --bootstrap-server localhost:9092 --reset-offsets --shift-by -2 --execute --topic msg-cli --group app-cli

#### 11. Descrever grupo
kafka-consumer-groups --bootstrap-server localhost:9092 --group app-cli describe

#### 12. Iniciar o app-cli
root@broker:/# kafka-console-consumer --bootstrap-server localhost:9092 --topic msg-cli --group app-cli

#### 13. Redefinir o deslocamento o app-cli
ctrl + c

#### 14. Iniciar o app-cli
kafka-console-consumer --bootstrap-server localhost:9092 --reset-offsets --to-earliest --execute --topic msg-cli --group app-cli

#### 15. Listar grupo
root@broker:/# kafka-consumer-groups --bootstrap-server localhost:9092 --list