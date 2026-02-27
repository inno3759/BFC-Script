---
title: Comandos | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/comandos
crawled_at: 2026-02-27 12:59:23
---

Pular para o conteúdo principal

Nessa página

A seguir, temos a lista de todos os comandos que podem ser utilizados no desenvolvimento dos scripts juntamente com alguns exemplos de utilização.

## imprimir​

Exibe uma mensagem no console.

    imprimir 'John Doe'  

## percorrer​

Permite iterar valores e obter o índice atual da iteração.

    percorrer(ate:5){  
        imprimir indice  
    }  

O comando disponibiliza uma variável implícita chamada índice que representa o índice corrente da interação.

    percorrer(de:3, ate:5){  
        imprimir indice  
    }  

A variável índice pode ser atribuída a uma outra variável com um nome personalizado, permitindo que a mesma seja acessada em diversos níveis do comando percorrer.

    percorrer(de:3, ate:5){ idPrincipal ->  
        imprimir idPrincipal  
        percorrer(de:6, ate:8){ idSecundario ->  
            imprimir 'ID princial: ' + idPrincipal  
            imprimir 'ID secundário: ' + idSecundario  
        }  
    }  

É possível também iterar pelos valores de uma lista informando ou não o índice inicial e final da iteração

    numeros = [1,2,3]  
    percorrer(de:1, ate:3, itens: numeros){   
        imprimir item  
    }  
    // Irá imprimir os números 1, 2 e 3  
    letras = ['A','B','C']  
    percorrer(de:2, ate:3, itens: letras){   
        imprimir item  
    }  
    // Irá imprimir as letras B e C, ou seja, do índice 2 até o índice 3  

  * Caso o índice inicial não seja informado, irá utilizar como padrão o valor 1 (primeiro item).
  * Caso o índice final não seja informado, irá utilizar como padrão o índice final da lista (último item).

### Controle do fluxo de execução​

O fluxo de execução de um comando percorrer pode ser alterado utilizando as funções **parar()** e **continuar()**. Este controle é especialmente útil quando se deseja interromper a execução de um comando percorrer devido a uma condição específica ou avançar para um próximo item do laço.

### parar()​

A função parar interrompe um comando percorrer em determinada condição, e continua a execução do script sem passar pelas repetições seguintes.

O seguinte código irá imprimir os números 1, 2 e a palavra Ok:

    numeros = [1,2,3,4]  
    percorrer(numeros){  
      se(item == 3){  
        parar()  
      }   
      imprimir item  
    }  
       
    //As instruções fora do comando percorrer serão executadas normalmente, somente o comando percorrer   
    //será interrompido e não todo o script  
    imprimir 'Ok'  

### continuar()​

A função continuar faz com que o comando passe para a próxima repetição/item. Esta função é especialmente útil em situações em que se deseje ignorar o processamento de um item com base em uma condição.

O seguinte código irá imprimir os números 1, 2 e 4 ignorando o número 3:

    numeros = [1,2,3,4]  
    percorrer(numeros){  
      se(item == 3){  
        continuar()  
      }   
      imprimir item  
    }  

### Nomeando os comandos percorrer​

Em situações onde são utilizados mais de um comando percorrer aninhados e se deseje ** _parar_** ou ** _continuar_** um percorrer específico, a atribuição de um nome ao comando se faz necessário. Para nomear o comando basta preencher a propriedade **nome** na declaração da instrução:

    numeros = [1,2,3,4]  
    percorrer(itens: numeros, nome: 'p1'){   
      imprimir 'p1: ' + item   
      percorrer(de: 1, ate: 5){  
        se (indice == 3){  
          parar 'p1'  
        }  
        imprimir 'p2: ' + indice  
      }  
    }  

A saída do script será:

    p1: 1 // primeiro item da lista de números do percorrer 'p1'  
    p2: 1 // primeiro índice do segundo percorrer  
    p2: 2 // ...  
    p2: 3 // ...  
    p2: 4 // No índice 4 o comando parar 'p1' foi executado interrompendo a execução de todos os comandos percorrer até o 'p1'  

A mesma regra se aplica ao comando ** _continuar()_** , porém ao invés de interromper a execução do comando percorrer irá avançar para o próximo índice/item.

    numeros = [1,2,3]  
    percorrer(itens: numeros, nome: 'p1'){   
      imprimir 'p1: ' + item  
      percorrer(de: 1, ate: 5, nome: 'p2'){  
        se (indice == 2){  
          continuar 'p1'  
        }  
        imprimir 'p2: ' + indice  
      }  
    }  

A saída do script será:

    p1: 1 // primeiro item da lista de números do percorrer 'p1'  
    p2: 1 // primeiro índice do segundo percorrer   
          // Ao passar pelo segundo índice o comando continuar 'p1' foi executado parando a execução do percorrer atual e avançando o item do   
          // percorrer 'p1' para a próxima iteração, neste caso o número 2  
    p1: 2   
    p2: 1  
    p1: 3  
    p2: 1  

## retornar​

Permite submeter dados como retorno de um script.

Conforme podemos observar, a variável valor é submetida como retorno do script utilizando o comando retornar.

    valor = 10 * 2 * 3  
    retornar valor  

No exemplo abaixo, os valores são retornados pelo comando retornar através de um mapa. As chaves valor e nome recebem seus respectivos valores e são submetidas ao comando retornar e serão resgatadas programaticamente através de um java.util.Map.

    retornar valor:10 * 2 * 3, nome:'David Crosby'  

## se​

Permite criar expressões condicionais.

    se(10 == 10){  
       imprimir 'verdadeiro'  
    }  
       
    se(9 <= 20){  
        imprimir 'verdadeiro'  
    }senao{  
        imprimir 'falso'  
    }  

## tentar/tratar/finalizar​

Às vezes, a execução de uma ação pode acarretar em uma exceção. Quando isto ocorre, é possível que seja realizado um tratamento para que o script continue sua execução realizando alguma outra ação, como por exemplo, notificar outros usuários, tratar alguns retornos conhecidos, tentar realizar a ação novamente, etc.

No bloco  _tentar_ devem ser colocadas as ações onde pode ocorrer um erro. Por exemplo, chamar um serviço HTTP, SOAP, escrever em um arquivo, etc.

Dentro do bloco  _tratar_ deve ser especificado o código que será executado em caso de erro dentro do bloco tentar. Nele, existe uma variável chamada exceção que é uma representação do erro ocorrido. Ela possui os seguintes atributos:

código - É um identificador alfanumérico erro para facilitar sua localização nos manuais e documentações

mensagem - Uma mensagem passada pela API ou linguagem que representa a descrição do erro ocorrido

linha - Linha onde ocorreu o erro

    tentar {  
      resultado = Http.servico('https://endereco-nao-existe').GET()  
      imprimir resultado.codigo()  
    } tratar {  
       // Ao mandar imprimir o objeto excecao, será impresso o código, mensagem e linha (se existir)  
       imprimir 'Estou tratando uma exceção: ' + excecao  
    }  

Ainda é possível que independentemente de ocorrer uma falha ou não, ao final da execução do método seja executada alguma ação. Para isso, existe também o bloco  _finalizar_. Onde tudo o que for definido neste bloco, será executado independentemente de ocorrer um erro ou não.

    tentar {  
      resultado = Http.servico('https://endereco-nao-existe').GET()  
      imprimir resultado.codigo()  
    } tratar {  
       // Ao mandar imprimir o objeto excecao, será impresso o código, mensagem e linha (se existir)  
       imprimir 'Estou tratando uma exceção: ' + excecao  
    } finalizar {  
        imprimir 'O conteúdo deste bloco sempre será executado'  
    }  

Algumas observações referentes à este recurso:

  * O bloco finalizar sempre é executado
  * Dentro do bloco finalizar, a variável excecao já não está disponível
  * O comando suspender não é tratado

### suspender​

Permite suspender a execução de um script com uma exceção.

    se(codigo != 10){  
       suspender "O código $codigo é inválido"  
    }  

### esperar​

O comando esperar permite que a execução de um script entre em modo de pausa por um determinado intervalo de tempo.

Este comando se mostra útil quando o acesso a um serviço é limitado por um intervalo de tempo.

    imprimir Datas.hoje()  
    esperar 2000 //O script irá pausar a execução neste ponto durante 2000 millisegundos  
    imprimir Datas.hoje()  

É possível informar o intervalo de tempo utilizando a forma simplificada de [tempo/datas](http://test.betha.com.br/documentacao/bfc-script/2.7.X/index.html#datas) da engine:

    imprimir Datas.hoje()  
    esperar 1.segundo //O script irá pausar a execução neste ponto durante 1 segundo  
    imprimir Datas.hoje()  

**Limite de tempo no método`esperar()` em Scripts**

Foi implementado um limite máximo de **10 minutos** (600 000 milissegundos) para o tempo de espera acumulado que pode ser invocado pelo método `esperar()` dentro de um único script. A medida visa otimizar o uso de recursos do servidor, prevenir que scripts fiquem inativos por tempo excessivo e garantir a estabilidade da aplicação. Para não impactar negativamente os scripts existentes, a validação é aplicada de forma distinta para scripts novos e antigos, através de um sistema de **Especificações**.

**Limite de Tempo**

  * O tempo de espera total acumulado por um script não pode exceder **10 minutos** (600 000 ms).

**Sistema de Especificações**

Para evitar a quebra de scripts antigos que dependiam do comportamento anterior, criamos duas especificações:

  * **Especificação 1 (Scripts Legados)**

    * **A quem se aplica:** scripts criados antes da atualização. 
    * **Comportamento:** o limite de 10 minutos **NÃO** é restritivo; o script não falhará. 
    * **Sinalização:** execução marcada com status **Aviso** (amarelo) quando o limite recomendado é excedido.
  * **Especificação 2 (Scripts novos e modificados)**

    * **A quem se aplica:** scripts criados ou editados a partir da atualização. 
    * **Comportamento:** o limite de 10 minutos **É OBRIGATÓRIO**. 
    * **Sinalização:** execução interrompida e registrada com status **Erro** se o limite for excedido.

Impacto

  * **Scripts antigos (Especificação 1):**

    * Continuam funcionando sem falhas. 
    * Recomenda-se monitorar avisos (amarelo) e revisar scripts para otimizar chamadas a `esperar()`.
  * **Scripts novos (Especificação 2):**

    * Devem respeitar o novo limite durante o desenvolvimento. 
    * Lógicas que dependam de pausas longas precisam ser reavaliadas ou divididas em múltiplos scripts.

**Boas Práticas**

  * **Use com moderação:** `esperar()` é para pausas curtas, não controle de fluxo prolongado. 
  * **Cuidado com loops:** evite chamadas a `esperar()` dentro de laços de repetição. 
  * **Revise a lógica:** se precisar “esperar” muito tempo, avalie quebrar o processo ou usar gatilhos alternativos.

### exportar​

Comando utilizado para exportar símbolos declarados no escopo atual. Aceita como parâmetro um mapa com o nome externo e uma referência ao recurso exportado.

    // exportando uma constante  
    exportar PI_APROXIMADO: 3.1415  
       
    // exportando múltiplos símbolos  
    exportar(  
        nomeExterno: referencia,  
        outroNome: outraReferencia  
    )  

Este comando está disponível apenas na **Ferramenta de Scripts**.

### importar​

Comando utilizado para importar recursos de um componente. Aceita como parâmetro uma String com o nome do identificador do componente desejado, e retorna um objeto com os recursos importados.

    log = importar("log")  
    math = importar("calculadora")  
    counter = importar("contador")  
       
    log.info("Iniciando execução")  
    acum = 0  
       
    percorrer(ate: 20) {  
      counter.incrementar()  
      acum = math.somar(acum, indice)  
      log.info("Executando operação #$indice")  
    }  

Este comando está disponível apenas na **Ferramenta de Scripts**.

  * imprimir
  * percorrer
    * Controle do fluxo de execução
    * parar()
    * continuar()
    * Nomeando os comandos percorrer
  * retornar
  * se
  * tentar/tratar/finalizar
    * suspender
    * esperar
    * exportar
    * importar