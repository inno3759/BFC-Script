---
title: API de notificações | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-notificacoes
crawled_at: 2026-02-27 13:00:10
---

Pular para o conteúdo principal

Nessa página

O bfc-script disponibiliza uma API para envio de notificações aos usuários do sistema. Essas funções estarão disponíveis ao usuário final apenas através da **Ferramenta de Scripts** e serão absorvidas plenamente conforme a utilização.

Para criar uma nova notificação deve-se utilizar a função **Notificacao.nova()**

     msg1 = Notificacao.nova()  
    msg2 = Notificacao.nova('Seja bem vindo!') //Define a mensagem na inicialização  

Uma mensagem contém diversas características que serão apresentadas a seguir, uma vez configurada a mensagem, o envio é realizado através da função **enviar()** a mensagem.

    msg = Notificacao.nova()  
    //configurações da mensagem  
    msg.enviar()  

### Mensagem​

A seguir são descritas todas as funções disponíveis para mensagens de notificações.

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**para(usuarios)**|  Adiciona um (ou vários) usuário como destinatário da notificação.  

    Notificacao.nova('Seja bem vindo!')  
        .para('joao.silva', 'maria.silva')  
        .enviar()  

Também é possível adicionar o usuário logado como destinatário da notificação usando o identificador usuario.id:

    Notificacao.nova('Seja bem vindo!')  
        .para(usuario.id)  
        .enviar()  

Mais um exemplo, usando o usuário logado e outros usuários:

    Notificacao.nova('Seja bem vindo!')  
        .para(usuario.id, 'joao.silva', 'maria.silva')  
        .enviar()  

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**mensagem(mensagem)**|  Define a mensagem a ser enviada pela notificação.  
**link(href)**|  Define o link a ser enviado pela notificação.  
**link(href, titulo)**|  Define o link com título a ser enviado pela notificação.  
**link(href, titulo, label)**|  Define o _link_ , titulo e _label_ a ser enviado pela notificação.  
**link(href, titulo, label, target)**|  Define o _link_ , titulo, _label_ e o _target_ a ser enviado pela notificação.  
**enviar()**|  Realiza o envio da notificação aos destinatários.  
  
Para o `target` são suportado os valores: 

  * `blank` indica que o link será aberto sempre numa nova aba 
  * `self` indica que o link será aberto na mesma aba

    Notificacao.nova('Seja bem vindo!')  
        .para('usuario.betha', 'suite.betha')  
        .enviar()  
      
    Notificacao.nova()  
        .para('suite.betha')  
        .mensagem('Obrigado!')  
        .enviar()  
      
    Notificacao.nova()  
        .para('suite.betha')  
        .mensagem('Obrigado!')  
        .link('https://centraldeajuda.betha.com.br/', 'Betha', 'Informativo', 'self')  
        .enviar()  

  * Mensagem