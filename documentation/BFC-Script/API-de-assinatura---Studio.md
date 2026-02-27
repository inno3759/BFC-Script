---
title: API de assinatura | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-assinatura
crawled_at: 2026-02-27 13:00:39
---

Pular para o conteúdo principal

Nessa página

A assinatura de um documento por meio do script pode ser feita por arquivo ou por lote. Apenas documentos nos formatos **xml** , **pdf** , **txt** e **p7s** podem ser assinados. Todo processo de assinatura envolve a criação de dois scripts, um para chamada da api de assinatura e outro de _call-back,_ que é executado após a assinatura e pode receber o arquivo assinado e o arquivo original como parâmetro.

## Assinando documentos​

A seguir, veja como um exemplo de script de **assinatura de um documento no formato pdf.**

assinar(arquivo, opcoes)

    arquivo = parametros.arquivo.valor;  
       
    opcoes = [  
        nome: 'pdfassinado', // nome do arquivo enviado por parâmetro para o script de callback  
        tipo: 'pdf',  
        lote: false,  // indica se é lote ou não  
        retorno: [  
            script: 'callback_assinatura',  // identificador do script de callback que deve ser executado após assinar o documento/lote  
            parametro: 'assinado', // nome do parâmetro do tipo arquivo no script de callback que recebe o arquivo assinado    
            notificacao: true  
        ],  
        parametros: [  
            original: arquivo  
        ]  
    ];  
       
    Assinador.assinar(arquivo, opções) ;  

A seguir, veja como um exemplo de script de **com parâmetros não obrigatórios.**

     arquivo = parametros.arquivo.valor;  
      
    opcoes = [  
        nome: 'pdfassinado', // nome do arquivo enviado por parâmetro para o script de callback  
        tipo: 'pdf',  
        lote: false,  // indica se é lote ou não  
        retorno: [  
            script: 'callback_assinatura',  // identificador do script de callback que deve ser executado após assinar o documento/lote  
            parametro: 'assinado', // nome do parâmetro do tipo arquivo no script de callback que recebe o arquivo assinado    
            notificacao: true  
        ],  
        parametros: [  
            original: arquivo  
        ],  
        naturezaQualificadora: "CADASTRO_APOSENTADO", // identificador da natureza do documento  
        marcadores: [ //marcadores do relatório  
          marcador1: 'valor1',  
          marcador2: 'valor2'  
        ],  
        expiraEm: "2024-10-27 00:00:00", // Estabelece a data e hora limite para a conclusão do processo de assinatura  
        permiteAdicionarNovosAssinantes: false, // Enquanto o processo de assinatura estiver aberto, será possível adicionar novos assinantes  
        publico: false, // Define a visibilidade das informações do processo.  
        bloqueiaCertificadoCorporativo: false, // indica que o documento não deve ser assinado por um certificado corporativo  
        permiteCertificadoAvancadoParaUsuarioVerificado: false, // permite que o documento seja assinado por um certificado do tipo Avançado  
        assinarComCampoInvisivel: false, // Aplicável somente a documentos do tipo PDF. Quando true, o processo de plotagem não é realizado  
    ];  
      
    Assinador.assinar(arquivo, opcoes);  

A seguir, veja como um exemplo de script de **assinatura de um documento no formato xml.**

     arquivo = parametros.arquivo.valor;  
       
    opcoes = [  
        nome: 'xmlassinado', // nome do arquivo enviado por parâmetro para o script de callback  
        tipo: 'xml',  
        lote: false,  // indica se é lote ou não  
        tagAssinatura: 'TEXTO', // nome da tag do xml que deve ser assinada  
        retorno: [  
            script: 'callback_assinatura',  // identificador do script de callback que deve ser executado após assinar o documento/lote  
            parametro: 'assinado', // nome do parâmetro do tipo arquivo no script de callback que recebe o arquivo assinado    
            notificacao: true  
        ],  
        parametros: [  
            original: arquivo  
        ]  
    ];  
       
    Assinador.assinar(arquivo, opcoes);  

## Assinando lote de documentos​

Exemplo de script de **assinatura de um lote de documentos de formato xml.**

assinar(arquivo, opcoes)

    arquivo = parametros.arquivo.valor;  
    zip = Arquivo.novo('arquivos.zip', 'zip');  
    zip.adicionar(arquivo, 'a.xml');  
    zip.adicionar(arquivo, 'b.xml');  
       
    opcoes = [  
        nome: 'xmlassinado', // nome do arquivo enviado por parâmetro para o script de callback  
        tipo: 'xml',  
        lote: true,  // indica se é lote ou não  
        tagAssinatura: 'TEXTO', // nome da tag do xml que deve ser assinada  
        retorno: [  
            script: 'callback_assinatura',  // identificador do script de callback que deve ser executado após assinar o documento/lote  
            parametro: 'assinado', // nome do parâmetro do tipo arquivo no script de callback que recebe o arquivo assinado    
            notificacao: true  
        ],  
        parametros: [  
            original: zip  
        ]  
    ];  
       
    Assinador.assinar(zip, opcoes);  

## Múltiplos assinantes​

Exemplo de script de assinatura de um documento PDF com múltiplos assinantes:

  * Observação: Apenas documentos do tipo PDF podem utilizar o recurso de múltiplos assinantes.

assinar(arquivo, opcoes)

    arquivo = parametros.arquivo.valor;  
       
    opcoes = [  
        nome: 'pdfassinado',  
        tipo: 'pdf',  
        lote: false,    
        assinantes: [  
            incluirUsuarioCorrente: true, //indica se o usuário que solicitou a execução do script deve assinar o documento  
            usuarios: [ // lista de assinantes  
                'joao',  
                'maria.silva'  
            ]  
        ],  
        retorno: [  
            script: 'callback_assinatura',  
            parametro: 'assinado',    
            notificacao: true  
        ],  
        parametros: [  
            original: arquivo  
        ]  
    ];  
       
    Assinador.assinar(arquivo, opcoes);  

## Script de callback​

O script de _callback_ é o script executado automaticamente após a execução do script que chama a api de assinatura com Assinador.assinar(arquivo, opcoes).

Com base no script de assinatura do exemplo anterior, o script de _callback_ deve ter dois parâmetros do tipo arquivo, que são:

  * **assinado:** o que foi definido no script de assinatura no item retorno.parametro do objeto de opções.
  * **original:** o que também foi definido no script de assinatura no item parametros do objeto de opções.

E por último o identificador que também foi definido no script de assinatura no item script do objeto de opções.

  * Assinando documentos
  * Assinando lote de documentos
  * Múltiplos assinantes
  * Script de callback