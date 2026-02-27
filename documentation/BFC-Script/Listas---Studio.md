---
title: Listas | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/listas
crawled_at: 2026-02-27 12:59:27
---

Pular para o conteúdo principal

Também conhecida como Arrays, podemos trabalhar com listas de maneira bem simplificada.

    //Instancia uma lista com valores  
    valores = [0, 1, 2, 3, 4]  
       
    //Instancia uma lista vazia  
    nomes = []  
       
    //Adiciona um item na lista  
    nomes << 'Chuck Norris'  
       
    //Itera uma lista  
    percorrer(valores){  
        imprimir item  
    }  

O comando percorrer possui uma variável implícita para obter o valor da iteração chamada **item**.

A variável item e índice podem ser atribuídas à outras variáveis com nomes personalizados utilizando a seguinte sintaxe do comando percorrer:

    percorrer(valores){ valor ->  
        imprimir valor  
    }  
       
    percorrer(valores){ valor, posicao ->  
        imprimir valor // Equivale a item  
        imprimir posicao // Equivale a indice  
    }  
       
    percorrer(valores){ item, posicao ->  
        imprimir item  
        percorrer(outros){  
            imprimir item //Equivale ao item do percorrer principal pois utilizou o mesmo nome da variável implícita  
        }  
    }  

Obtendo e atribuindo valores em posições **específicas** da lista. A primeira posição da lista tem o índice **0 (zero)** , a segunda posição tem o índice **1** , e assim por diante. Os dados são acessados assim: **lista[indice]**

    //Instancia uma lista com valores  
    nomes = ['Harrison Reid', 'Thomas Sharpe', 'Louie Hill']  
       
    //nomes[0] contém o valor 'Harrison Reid'  
    //nomes[1] contém o valor 'Thomas Sharpe'  
    //nomes[2] contém o valor 'Louie Hill'  
       
    //Obtendo o nome da segunda posição da lista:  
    nomeDaSegundaPosicao = nomes[1]