---
title: API de rastreamento | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-rastreamento
crawled_at: 2026-02-27 13:01:07
---

Pular para o conteúdo principal

Nessa página

O bfc-script disponibiliza uma API para criar endereços (urls) rastreáveis. Endereço os quais ao serem acessados pelo usuário geram notificações.

Para criar um novo endereço rastreavel deve-se utilizar a função **Rastreamento.criar([])**

     rastreamento = Rastreamento.criar([])  

Parâmetros que da função criar:

Nome| Tipo| Obrigatório| Descrição  
---|---|---|---  
**requisicao**|  Objeto| Sim| Dados da requisição para o endereço a ser rastreado  
requisicao.endereco| String| Sim| Endereço da requisição. Deve ser informado uma url válida.  
requisicao.metodo| String| Não| Tipo de requisição. Valores válidos (GET, POST, PUT). Padrão: GET  
requisicao.cabecalho| Map<String, String>| Não| Cabeçalho da requisição.  
requisicao.corpo| String| Não| Corpo da requisição.  
**webhook**|  Objeto| Não| Dados da requisição de notificação de acesso  
webhook.endereco| String| Sim| Endereço da requisição do webhook. Debe ser informado uma url válida.  
webhook.metodo| String| Não| Tipo de requisição do webhook. Valores válidos (GET, POST, PUT). Padrão: GET  
webhook.cabecalho| Map<String, String>| Não| Cabeçalho da requisição do webhook.  
webhook.contexto| Map<String, Objeto>| Não| Contexto da requisição do webhook. Esse objeto deve ser utilizado para passar informações adicionais para o webhook.  
webhook.enviarSomenteContexto| Boleano| Não| Indica se somente o objeto de contexto deve ser enviado para o webhook, não incluindo nenhuma informação adicional do acesso. Padrão: falso.  
  
Retorno da função criar:

Nome| Tipo| Descrição  
---|---|---  
endereco| String| Endereço publico rastreável  
chave| String| Chave de rastreamento, pode ser utilizada para a consulta sistema de informações do rastreamento  
  
## Notificação via webhook​

Quando o rastreamento é configurado com um endereço para receber notificações via webhook, os seguintes valores são enviados.

#### Configuração `webhook.enviarSomenteContexto` igual a `falso`​

Conteúdo da mensagem quando o método for `POST` ou `PUT`

Nome| Tipo| Descrição  
---|---|---  
key| String| Chave do rastreamento  
accessCount| Long| Quantidade total de acesso  
accessedIn| LocalDateTime| Data e hora do acesso  
context| Objeto| Objeto de contexto que foi passado na criação do rastreamento  
  
#### Configuração `webhook.enviarSomenteContexto` igual a `verdadeiro`​

Somente o objeto de contexto que foi passado na criação do rastreamento é enviado.

## Exemplos​

#### Rastreamento de abertura de email​

No exemplo abaixo, demostramos como é possível rastrear a abertura de um email.

    rastreamento = Rastreamento.criar([  
            requisicao: [  
                    // Endereço que deve ser rastreado  
                    endereco: 'https://cdn.betha.cloud/plataforma/email/assets/v1/logo-betha.png'  
            ],  
            // Dados da notificação via webhook  
            // Nesse exemplo estão chamando a api de chatbot do Google Chats  
            webhook   : [  
                    endereco             : 'https://chat.googleapis.com/v1/...',  
                    metodo               : 'POST',  
                    contexto             : [  
                            text: "A url do protocolo $contextoExecucao.idProtocolo foi acessada."  
                    ],  
                    // Como é uma api a qual não temos controle, devemos passar somente os dados que estão detro do objeto contexto  
                    enviarSomenteContexto: true  
            ]  
    ])  
      
    // Envia o email com o endereço de rastreamento gerado.  
    Email.novo()  
            .de('betha@betha.com.br', 'Betha Sistemas')  
            .para('destinatario@exemplo.com', 'Destinatário')  
            .assunto('Email Rastreamento')  
            .mensagemHtml("Este é um teste de e-mail. <br/><br/>Att, <br/><br/>Betha Sistemas <p/><p/><img src=\"$rastreamento.endereco\" width=\"319\" height=\"51\" />")  
            .enviar()  

  * Notificação via webhook
  * Exemplos