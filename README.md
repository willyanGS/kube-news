# Desafios da "Jornada DevOps de Elite"

Forked do repositório indicado (kube-news), foram adicionados aqui o Dockerfile (para fazer o docker build da imagem) e os manifestos deployment (para aplicar o banco de dados e a aplicação em um cluster k8s local)

##
##


## Projeto base:

### Projeto kube-news

### Objetivo
O projeto Kube-news é uma aplicação escrita em NodeJS e tem como objetivo ser uma aplicação de exemplo pra trabalhar com o uso de containers.

### Configuração
Pra configurar a aplicação, é preciso ter um banco de dados Postgre e pra definir o acesso ao banco, configure as variáveis de ambiente abaixo:

DB_DATABASE => Nome do banco de dados que vai ser usado.

DB_USERNAME => Usuário do banco de dados.

DB_PASSWORD => Senha do usuário do banco de dados.

DB_HOST => Endereço do banco de dados.
