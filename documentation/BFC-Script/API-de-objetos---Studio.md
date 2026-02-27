---
title: API de objetos | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-objetos
crawled_at: 2026-02-27 13:00:53
---

Pular para o conteúdo principal

Nessa página

O módulo **bfc-script** fornece uma API para manipulação de objetos, permitindo a introspecção e análise de dados ao mapear campos e seus respectivos tipos. Esta funcionalidade está disponível exclusivamente na **Ferramenta de Eventos** para uso nas críticas, facilitando a extração de informações de campos tanto de objetos quanto de mapas

## Funções Disponíveis​

**campos(objeto):**

Mapeia os campos do objeto fornecido e retorna os respectivos tipos de dados de cada campo.

### Exemplos​

Sintaxe Básica

    Objeto.campos(objeto);  

Exemplo de Uso em Conjunto com a API de Mensagens:

A seguir, um exemplo de como utilizar a função **campos** da API de Objetos em conjunto com a API de Mensagens. 

Este exemplo usa o evento de criação que disponibiliza os dados cadastrados no **registro.novo** suponhamos que o objeto tenha os campos (id, emUso e descricao)

    campos = Objeto.campos(registro.novo);  
      
    // Usa a API de Mensagens para informar sobre a estrutura do objeto  
    Mensagens.info(campos);  
      
    // O resultado será uma mensagem de informação com a estrutura dos campos:  
    //{emUso=java.lang.Boolean,id=java.lang.Double, descricao=java.lang.String}  

IMPORTANTE!

Para que o recurso funcione, é necessário ser homologado nos sistemas, ou seja, precisa ser implementado pelas equipes. Caso contrário, será necessário abrir um chamado para o produto onde a crítica está sendo implementada, solicitando a melhoria para suportar o recurso.

  * Funções Disponíveis
    * Exemplos