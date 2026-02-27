---
title: API de execução | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-execucao
crawled_at: 2026-02-27 13:00:58
---

Pular para o conteúdo principal

Nessa página

O bfc-script disponibiliza uma API para a consulta das informações relacionadas à execução.

## Consultar o protocolo da execução​

    Execucao.atual.protocolo  

## Consultar se a execução foi cancelada pelo usuário​

    Execucao.atual.foiCancelada  

## Exemplos​

Monitorar o cancelamento e interromper a execução: 

    percorrer(...) {  
       
      // processamento da aplicação  
       
      // verifica e interompe caso a execução atual foi cancelada  
      se(Execucao.atual.foiCancelada){  
        interomper 'Execucao cancelada'  
      }  
       
    }  

  * Consultar o protocolo da execução
  * Consultar se a execução foi cancelada pelo usuário
  * Exemplos