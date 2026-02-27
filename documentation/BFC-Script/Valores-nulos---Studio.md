---
title: Valores nulos | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/valores
crawled_at: 2026-02-27 12:59:50
---

Pular para o conteúdo principal

Em programação de computadores, **null** é um valor especial para um ponteiro (ou qualquer outro tipo de referência) que indica que este ponteiro, intencionalmente, não se refere a um objeto (ponteiro nulo).

Este recurso se mostra útil para identificar quando um valor não está disponível, assumindo um valor próprio para este comportamento, o nulo ou vazio.

A palavra reservada nulo representa o valor para este comportamento, de modo que no exemplo abaixo estamos dizendo que a variável **valorCusto** é igual a nulo ou em outras palavras, que seu valor é vazio.

        valorCusto = nulo  

Um script pode receber variáveis com valores nulo, onde em certas ocasiões é necessário checar se o valor da variável é nulo ou não. Podemos realizar as checagens de duas formas:

    valorCusto = nulo  
       
        // Forma 1  
        se (valorCusto != nulo){  
            imprimir ("A variável valorCusto não está nula.")  
        }  
       
        // Forma 2  
        se (valorCusto){  
            imprimir ("A variável valorCusto não está nula.")  
        }  
       
        se (!valorCusto){  
            imprimir ("A variável valorCusto está nula.")  
        }  
       
        se (valorCusto && funcionario.agenciaBancaria){  
            imprimir ("A variável valorCusto a a agência bancária do funcionário não estão nulas.")  
        }  

O acesso às referências nulas gera erros durante a execução de um script. No exemplo abaixo, suponhamos que a agência bancária do funcionário esteja nula:

        nomeFuncionario = funcionario.agenciaBancaria.nome  

Ao tentar obter o nome de uma agência bancária nula, recebemos um erro de execução: A propriedade nome não é acessível em um elemento nulo. Para evitar este comportamento, podemos utilizar o operador de navegação segura (?):

        nomeFuncionario = funcionario.agenciaBancaria?.nome  

O operador deve ser utilizado em diversos níveis de uma referência, caso seja apropriado:

    nomeFuncionario = funcionario.agenciaBancaria?.municipio?.nome  
       
        // valor impresso 'null'  
        imprimir(nomeFuncionario)  

No exemplo acima, caso não utilizassemos o operador (?) no município (municipio?.nome), receberiamos um erro durante a execução, devido ao fato de que a agenciaBancária esta nula. Como resultado final o valor da variável nomeFuncionario é nula.

Em algumas ocasiões, gostariamos de considerar um valor padrão onde o resultado seria nulo. Para este propósito utilizamos a expressão ternária (?:), como podemos observar abaixo:

    nomeFuncionario = funcionario.agenciaBancaria?.municipio?.nome  
       
        imprimir(nomeFuncionario?:'Sem nome')  

No exemplo acima, quando o valor da variável nomeFuncionario for nulo, o valor retornado será Sem nome.

Poderíamos usar esta expressão diretamente, conforme o exemplo abaixo:

    nomeFuncionario = funcionario.agenciaBancaria?.municipio?.nome?:'Sem nome'  
       
        imprimir(nomeFuncionario)