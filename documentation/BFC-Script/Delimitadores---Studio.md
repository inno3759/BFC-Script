---
title: Delimitadores | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/delimitadores
crawled_at: 2026-02-27 12:59:18
---

Pular para o conteúdo principal

Nessa página

Os delimitadores têm função importante no editor de _Scripts_. Através deles torna-se possível adicionar comentários de linha e bloco, ou seja, pode-se incluir notas aos _scripts_ para descrever o que se quiser. Assim, não modificam o programa executado e servem somente para ajudar o programador a melhor organizar os códigos.

## Comentários de linha​

Comentário de linha, como o próprio nome diz, são notas que podem ser incluídas nas linhas do código fonte, com objetivo de ajudar o programador a organizar seu código. Ou seja, pode-se descrever o que se quiser, pois os comentários não modificam os _scripts_.

Eles podem ser representados da seguinte forma: 

**_// comentario_**

## Comentários de bloco​

Os comentários de bloco tem a mesma função do comentário de linha, exceto por ponderações longas que ocupam várias linhas. Isso pode ser representado da seguinte forma: 

**_/ * comentário_**

** _em bloco */_**

## Operadores​

Os operadores indicam ao _script_ a necessidade de se fazer manipulações matemáticas ou lógicas.

### Atribuição ( = )​

Este operador indica a atribuição de um determinado valor a uma variável, como mostra os exemplos abaixo:

**Atribuição de um valor para uma variável**

valor = 10

imprimir 'O valor é: ' + valor

**Atribuição de uma _string_ para uma variável**

nome = 'Antônio da Silva'

imprimir nome

### Adição ( + )​

O operador de adição (+) poderá ser utilizado em diversas situações não somente em cálculos aritméticos, mas também em concatenações de _strings_. 

**Exemplo**

valor = 5 + 1

imprimir 'Resultado: ' + (valor + 4)

### **Subtração ( - )**​

O operador de subtração (-) subtrai um determinado valor de outro.

**Exemplo**

valor1 = 10

valor2 = 20

imprimir 'Resultado: ' + (valor2 - valor1)

### Operadores de multiplicação ( * )​

O operador de multiplicação (*) efetua a multiplicação de um valor por outro.

**Exemplo**

valor1 = 10

valor2 = 20

imprimir 'Resultado: ' + (valor2 * valor1)

### Operadores de divisão ( / )​

O operador de divisão (/) divide um determinado número por outro.

**Exemplo**

valor1 = 200

valor2 = 4

imprimir 'Resultado: ' + (valor1 / valor2)

### Operadores de igualdade ( == )​

O operador de igualdade verifica se uma determinada expressão ou valor é igual a outro. Geralmente este operador é utilizado em comandos se … senao … ou onde houver necessidade de se utilizar uma comparação.

**Exemplo**

valor = 'S'

se ( valor == 'S' ){

imprimir 'O valor é ...'

}senao{

imprimir O valor não é...'

}

### Operadores de diferenciação ( != )​

O operador de diferenciação ( != ) verifica se uma determinada expressão ou valor é diferente de outro. Geralmente é utilizado em comandos como se … senão ... ou onde houver necessidade de se utilizar comparação.

**Exemplo**

se (valor != 'S'){

imprimir 'Valor do imposto está sendo retido' 

}senao{

imprimir 'Valor do imposto não está sendo retiro'

}

### Operadores lógico OU ( || )​

O operador lógico OU ( || ) é utilizado para comparar duas expressões, sendo o resultado verdadeiro quando uma das duas expressões forem verdadeiras. Geralmente é utilizado em comandos se … senão … ou onde houver necessidade de se utilizar uma comparação.

**Exemplo**

se (valor1.vazio || valor2.vazio){

suspender 'Os valores estão vazios ...' 

}

### Operadores lógico E ( && )​

O operador lógico E ( && ) é utilizado para comparar duas expressões, sendo o resultado verdadeiro quando as duas expressões forem verdadeiras. Geralmente é utilizado em comandos se … senão … ou onde houver necessidade de se utilizar uma comparação.

**Exemplo**

se (valor1.vazio && valor2.vazio){

suspender 'Informe os valores ...' 

}

  * Comentários de linha
  * Comentários de bloco
  * Operadores
    * Atribuição ( = )
    * Adição ( + )
    * **Subtração ( - )**
    * Operadores de multiplicação ( * )
    * Operadores de divisão ( / )
    * Operadores de igualdade ( == )
    * Operadores de diferenciação ( != )
    * Operadores lógico OU ( || )
    * Operadores lógico E ( && )