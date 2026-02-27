---
title: Intervalos | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/intervalos
crawled_at: 2026-02-27 12:59:36
---

Pular para o conteúdo principal

Intervalos permitem que você crie uma lista de valores sequenciais podendo ser utilizados como listas. A notação define um intervalo, do primeiro item até o último. Intervalos definidos com a notação.< incluem o primeiro valor, mas não o último valor.

    //Cria um intervalo  
    dias = 1..3  
       
    //Percorre um intervalo      
    percorrer(dias){  
        imprimir item  
    }  
       
    //Percorre um intervalo          
    percorrer(4..7){  
        imprimir item      
    }  
       
    //Percorre um intervalo de forma decrescente  
    percorrer(8..7){  
        imprimir item      
    }  
       
    //Percorre um intervalo decrescente desconsiderando o último valor  
    percorrer(6..<4){  
        imprimir item      
    }  

O comando percorrer possui uma variável implícita para obter o valor da iteração chamada item.