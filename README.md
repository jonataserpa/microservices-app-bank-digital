## Microserviço de banco digital 
- Resumo do desenvolvimento: 
    * Desenvolvimento de um sistema banco digital que disponibiliza cartões de crédito 
        para seus clientes
    * O Cliente realizará o checkout de um produto
    * Banco processará a transação
    * Caso a transação seja aprovada, a transação constará no extrato bancário do cliente
    * Teremos um dashboard para acompanhar as métricas das transações

## Objetivo do sistema
- Comunicação de forma síncrona e assíncrona, para que possamos explorar 
    conceitos e tecnologia utilizadas em grandes empresas que necessitam de
    performace e resiliencia.

## Desafios e soluções
- Necessita de velocidade alta para performace na comunicação entre sistemas
    do checkout e o banco, logo precisamos uma solução mais veloz que o REST.
  * Solução: Usado o GRPC, um framework criado pela google, que permite realizarmos
    as transações de forma rápida transitando o payload em binário usando o 
    protocolo HTTP2.
- Necessita garantir resiliência entre a sincronização do processamento das transações
    com o serviço de extrato bancário.
  * Solução: Processamento de forma assíncrona e para isso foi usado o Apache Kafka.
- Necessita de dashboard, para gerarmos as métricas das transações do sistema e foi 
    usado o Elasticsearch e Kibana, porem não é responsabilida do microserviço do banco
    persistir os dados no Elasticksearch. Logo como armazenar as informações no Elasticsearch ?
  * Solução: Usado o Kafka Connect que também consumirá os dados de cada transação e 
    fará a inserção no Elasticsearch.

!.[Dinamica].(https://cdn.discordapp.com/attachments/1074644534748794891/1086270565372923974/codebank.png)    

## Ordem recomendada de execução
- Usado docker-compose:
    * Apache Kafka
    * Codebank (Golang e GRPC)
    * Back-end e front-end da loja (Nest.js e Next.js e REST)
    * Back-end e front-end das faturas (Nest.js e Next.js e REST)


# Imersão Fullcycle
Essa imersão foi realizada com o time fullcycle.
