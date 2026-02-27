---
title: API de assinatura sincrôna | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-assinatura-sincrona
crawled_at: 2026-02-27 13:00:43
---

Pular para o conteúdo principal

Nessa página

A assinatura sincrôna de um documento por meio do script por ser feita somente por arquivo. Apenas documentos nos formatos **xml** e **txt** podem ser assinados.

## Assinando documentos​

A seguir, veja como um exemplo de script de **assinatura de um documento no formato xml usando um certificado armazenado na ferramenta de documentos.**

     xml = parametros.arquivo.valor  
      
    // Aqui estamos utilizando o primeiro, porém, fica a criterio de quem for implementar, escolher o certificado correto.  
    certificado = Dados.plataforma.documentos.v1.certificados.entidade(campos: "id, descricao", primeiro:true)  
      
    xmlAssinado = Assinador.assinar(xml, opcoes = [  
        sincrono: true,  
        tipo:'xml',  
        tagAssinatura:'Message',  
        algoritmo: 'SHA1',  
        certificado: certificado  
    ])  

A seguir, veja como um exemplo de script de **assinatura de um documento no formato xml usando um arquivo contento o certificado (.pfx ou .p12).**

     xml = parametros.arquivo.valor  
    certificado = [arquivo: parametros.certificado.valor, senha: parametros.senha.valor]  
      
    xmlAssinado = Assinador.assinar(xml, opcoes = [  
        sincrono: true,  
        tipo:'xml',  
        tagAssinatura:'Message',  
        algoritmo: 'SHA1',  
        certificado: certificado  
    ])  

A seguir, veja como um exemplo de script de **assinatura de um documento no formato txt usando um certificado armazenado na ferramenta de documentos.**

     txt = parametros.arquivo.valor  
      
    // Aqui estamos utilizando o primeiro, porém, fica a criterio de quem for implementar, escolher o certificado correto.  
    certificado = Dados.plataforma.documentos.v1.certificados.entidade(campos: "id, descricao", primeiro:true)  
      
    xmlAssinado = Assinador.assinar(xml, opcoes = [  
        sincrono: true,  
        tipo:'txt',  
        algoritmo: 'SHA1',  
        certificado: certificado  
    ])  

A seguir, veja como um exemplo de script de **assinatura de um documento no formato txt usando um arquivo contento o certificado (.pfx ou .p12).**

     txt = parametros.arquivo.valor  
    certificado = [arquivo: parametros.certificado.valor, senha: parametros.senha.valor]  
      
    xmlAssinado = Assinador.assinar(xml, opcoes = [  
        sincrono: true,  
        tipo:'txt',  
        algoritmo: 'SHA1',  
        certificado: certificado  
    ])  

A seguir, veja como um exemplo de script de **assinatura de um documento no formato txt usando o certificado selecionado via parametro.**

     txt = parametros.arquivo.valor  
      
    // Pega o id do certificado selecionado pelo usuário a partir da fonte de documentos  
    certificado = [id: parametros.certificado.selecionado.valor]  
      
    xmlAssinado = Assinador.assinar(xml, opcoes = [  
        sincrono: true,  
        tipo:'txt',  
        algoritmo: 'SHA1',  
        certificado: certificado  
    ])  

  * Assinando documentos