lambda.py

import json

def lambda_handler(event, context):

    pedido = event.get("pedido_id", "0000")

    resposta = {
        "pedido_id": pedido,
        "status": "Em preparação",
        "tempo_estimado": "20 minutos"
    }

    return {
        "statusCode": 200,
        "body": json.dumps(resposta)
    }








stepfunctions.json


{
  "Comment": "Assistente de Delivery",
  "StartAt": "ConsultarPedido",
  "States": {
    "ConsultarPedido": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:ID_DA_CONTA:function:delivery-assistant",
      "End": true
    }
  }
}






prompt.txt


Você é um assistente virtual de delivery.

Responda sempre em português.

Informe:

- Número do pedido
- Status do pedido
- Tempo estimado
- Seja educado e objetivo.





README.md



# Delivery Assistant com AWS Step Functions e Amazon Bedrock

## Descrição

Este projeto demonstra um assistente de delivery utilizando AWS Step Functions, AWS Lambda e Amazon Bedrock.

O fluxo recebe um número de pedido, consulta seu status e gera uma resposta simples ao usuário.

## Tecnologias

- AWS Lambda
- AWS Step Functions
- Amazon Bedrock

## Fluxo

Cliente

↓

Step Functions

↓

AWS Lambda

↓

Amazon Bedrock

↓

Resposta ao Cliente

## Exemplo

Entrada:

```json
{
  "pedido_id": "1001"
}
```

Saída:

```json
{
  "pedido_id": "1001",
  "status": "Em preparação",
  "tempo_estimado": "20 minutos"
}
```

## Autor

Projeto desenvolvido para o laboratório da DIO.
