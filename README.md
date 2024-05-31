# Food Microservice

Este projeto consiste em uma aplicação de microserviços chamada Food Microservice. A aplicação é construída em Java utilizando Spring Boot, MySQL e RabbitMQ, e é composta por cinco serviços: Pedido, Pagamento, Eureka, Gateway e Avaliação.

## Serviços

### Pedido
O serviço de Pedido é responsável por gerenciar os pedidos dos clientes. Ele permite as seguintes operações:

- Adicionar um novo pedido
- Ler detalhes de um pedido
- Atualizar um pedido existente
- Deletar um pedido

Quando um pedido é concluído, uma mensagem é enviada pelo RabbitMQ para o serviço de Pagamento.

### Pagamento
O serviço de Pagamento é responsável por processar os pagamentos dos pedidos. Ele recebe mensagens do serviço de Pedido via RabbitMQ e, em caso de pagamento bem-sucedido, reenvia uma confirmação ao serviço de Pedido e ao serviço de Avaliação.

### Avaliação
O serviço de Avaliação permite que os clientes avaliem os pedidos após o pagamento. Quando o pagamento é confirmado, uma mensagem é enviada ao serviço de Avaliação via RabbitMQ, que então cria uma nova avaliação.

### Eureka
Eureka é o serviço de descoberta utilizado para registrar e localizar os serviços da aplicação, permitindo que os serviços se comuniquem entre si de maneira eficiente.

### Gateway
O Gateway é responsável por rotear as requisições para os serviços apropriados, agindo como um ponto de entrada único para a aplicação.

## Tecnologias Utilizadas

- Java
- Spring Boot
- MySQL
- RabbitMQ
- Eureka (Spring Cloud Netflix)
- Spring Cloud Gateway

## Futuras Atualizações

- Adicionar o serviço de Usuário
