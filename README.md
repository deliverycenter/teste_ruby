## Ruby Backend Test:

A Delivery Center está em constante expansão, e um dos pontos chave desse crescimento é a captação de pedidos em diversos canais. Recentemente, um destes canais efetuou a migração de seus serviços para uma nova API. Para manter a integridade da operação neste canal, precisamos refatorar um código legado que recebe e envia este pedido. Nesta nova integração iremos utilizar uma nova autenticação, onde iremos receber um token válido por uma hora para o envio do pedido.

Os detalhes da execução e avaliação do teste podem ser vistos [neste link](TEST.md).

**Após a finalização do teste sinta-se livre para utilizar este readme como documentação.**
#
## Stack
* `ruby 2.7.1`
* `rails 6.0.3`
* `postgres 12`
## About
This API receives an incoming order, parses it and send the parsed result to other API.
## Sending an order
To create a new order you must send a post request containing the raw order data. e.g:
* `verb` - `POST`
* `endpoint` - `/api/v1/order`
* `body` - [spec/fixtures/raw_order.json](spec/fixtures/raw_order.json)
```bash
curl -H 'Content-Type: application/json' \
     -d @spec/fixtures/raw_order.json \
     'http://localhost/api/v1/orders'
```

* Possible responses:
  - 202 - Successfully created
  - 404 - Cant create order, please check your params
  - 503 - Cant send order to remote server
