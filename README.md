# Pedido Infra Consumer

Este � um servi�o consumidor desenvolvido em .NET Core 8 para gerenciar o cadastro de Pedidos. 
Este projeto � parte da solu��o para o Hackathon da Fase 5 do curso de p�s gradua��o 6NETT na FIAP.

## �ndice
- [Pr�-requisitos](#pr�-requisitos)
- [Configura��o do Projeto](#configura��o-do-projeto)
- [Eventos](#eventos)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)

## Pr�-requisitos

- [Docker](https://www.docker.com/get-started/) e [Docker Compose](https://docs.docker.com/compose/install/) (necess�rio para executar o projeto)
- [.NET SDK 8.0](https://dotnet.microsoft.com/download/dotnet/8.0) (somente para executar local)

## Configura��o do Projeto

**1. Clone o reposit�rio:**

   ```bash
   git clone https://github.com/Grupo-1-6NETT/hackathon-pedido-infra
   cd Pedido.Infra
   ```

**2. Adicione configura��es necess�rias

Adicione as credenciais do Postgres no appsettings do ambiente que estiver rodando.  
Por exempo, em ambiente de desenvolvimento, adicione a propriedade em `appsettings.Development.json`.  

```json
 "ConnectionStrings": {
    "DefaultConnection": "Host=batcave-server;Database=batbase;Username=alfred;Password=******;SSL Mode=Require;Trust Server Certificate=true"
  }
``` 

Adicione as credenciais do RabbitMQ

``` json
  "RabbitMQ": {
    "Hostname": "rabbitmq",
    "Username": "guest",
    "Password": "guest"    
  },
```


**3. Crie a imagem Docker:**

```bash
docker-compose up --build
```

---
## Eventos
|Evento|Fila padr�o|Descri��o|
|---|---|---|
|AddPedido|addpedido|Adiciona um pedido|
|DeletePedido|deletepedido|Remove um pedido|
|UpdatePedido|updatepedido|Atualiza um pedido|
|AddPedidoItem|addpedidoitem|Adiciona um item no pedido|
|DeletePedidoItem|deletepedidoitem|Remove um item do pedido|
|UpdatePedidoItem|updatepedidoitem|Atualiza um item no pedido|

---
## Tecnologias Utilizadas
- **ASP.NET Core 8** - Framework principal para desenvolvimento do servi�o
- **Entity Framework Core** - ORM para manipula��o do banco de dados
- **Postgres** - Banco de dados
- **RabbitMQ** - Message Broker
- **MassTransit** - Transporte de mensagens
- **Docker** - Cria��o de conteiners