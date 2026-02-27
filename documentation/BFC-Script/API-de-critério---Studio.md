---
title: API de critério | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-criterio
crawled_at: 2026-02-27 13:00:48
---

Pular para o conteúdo principal

Nessa página

## Criação​

A criação de um novo critério acontece das seguintes maneiras:

Iniciando uma expressão

    Criterio.onde(campo);  

Esse é o caso mais comum, onde a configuração padrão do critério já atende. Através dessa forma, o critério é criado já se iniciando uma expressão.

    Criterio.onde('nome').igual('João');​  

Configurando o critério / Configuração de parâmetro obrigatório:

    Criterio.​novo( [ parametros: Criterio.obrigatorio() ] );  

Configuração padrão

    Criterio.​novo( [ parametros: Criterio.​opcional() ] );  

Aceita um template que vai ser utilizado na geração da mensagem de erro quando um parâmetro de uma condição não tiver seu valor informado.

    Criterio.​novo( [ parametros: Criterio.obrigatorio(​template_mensagem_validacao​) ] );  

​Por padrão, os valores utilizados como parâmetros, são opcionais, e caso seu valor seja nulo, a expressão é desconsiderada na geração do filtro:

    valorIdade = nulo;   
    ​valorNome = 'João';​   
    Criterio.onde('idade').igual(valorIdade).e('nome').igual(valorNome);  

​O critério acima geraria o seguinte filtro:

    'nome = "João"'  

## Operações​

Após a criação do critério, é possível fazer uso de um conjunto de operações de comparação.

  * **igual(valor)**
  * **diferenteDe(valor)**
  * **maiorQue(valor)**
  * **maiorOuIgualQue(valor)**
  * **menorQue(valor)**
  * **menorOuIgualQue(valor)**
  * **ehNulo() nome is null**
  * **naoEhNulo()**
  * **ehVerdadeiro()**
  * **ehFalso()**
  * **naoEhVerdadeiro()**
  * **naoEhFalso()**
  * **comecaCom(valor)**
  * **naoComecaCom(valor)**
  * **terminaCom(valor)**
  * **naoTerminaCom(valor)**
  * **contem(valor)**
  * **naoContem(valor)**
  * **contidoEm(valores)**
  * **naoContidoEm(valores)**

    Criterio.onde('idade').igual(40);   
    Criterio.onde('casado).ehFalso();   
    Criterio.padrao().onde('agencia').ehNulo();   
    ​Criterio.novo([ parametros: Criterio.obrigatorio('É necessário informar um valor para o campo ${campo}') ]).onde('idade').igual(27);  

### Obrigatoriedade dos valores​

Caso seja necessário configurar a obrigatoriedade dos valores de forma pontual, é possível configurar em qualquer operação que aceite um valor como parâmetro:

    Criterio.onde('idade').igual(valor, [ parametro: Criterio.obrigatorio() ]);   
    Criterio.novo([ parametros: Criterio.obrigatorio('É necessário informar um valor para o campo ${campo}') ]).onde('idade').igual(27).e('nome').igual(valorNome, [ parametro: Criterio.opcional() ]);  

Quando se configura a obrigatoriedade para todos os parâmetros do critério, a propriedade se chama **parametros**. Porém quando é configurado a nível de operação, se chama **parametro**.

## Delimitador nas operações contidoEm/naoContidoEm​

Para as operações **contidoEm** e **naoContidoEm** pode ser informado um delimitador para os valores que não são String.

### Com delimitador​

    numero = [1,2,5]   
    criterio = Criterio.onde('idade').contidoEm(numero, [delimitador: '"']);  

O critério acima, gera o seguinte filtro:

    idade in ("1", "2", "5")  

### Sem delimitador​

    numero = [1,2,5]   
    criterio = Criterio.onde('idade').contidoEm(numero);  

O critério acima, gera o seguinte filtro:

    idade in (1, 2, 5)  

### Com formatação e delimitador​

    data1 = Datas.data(2017, 1, 11)   
    data2 = Datas.data(2016, 1, 10)   
    datas = [ data1, data2 ]   
    criterio = Criterio.onde('aniversario').contidoEm(datas, [formatacao: "data", delimitador: "'"])  

O critério acima, gera o seguinte filtro:

    aniversario in ('2017-01-11', '2016-01-10')  

## Filtros compostos​

Os filtros podem ser utilizados de forma composta, fazendo uso do **e** ou do **ou** :

    Criterio.onde('idade').igual(40).e('nome').igual('João').ou('bairro').igual('centro');  

O critério acima, gera o seguinte filtro:

    'idade = 40 and nome = "João" ou bairro = "Centro"'  

## Agrupamento​

O critério tem suporte a **grupos** , através da seguinte chamada:

    Criterio.grupo(CriterioInterno);  
    Criterio.onde('a').igual(12).e(Criterio.grupo(Criterio.onde('b').igual(24).ou('c').igual(30)));  

O critério acima, gera o seguinte filtro:

    a = 12 e (b = 24 or c = 30)  

## Datas​

Atualmente a engine de scripts tem suporte a **datas** através de seu formato completo (data e hora), e no critério ela é representada através do formato **ISO 8601**.

    Criterio.onde('dataNascimento').igual(Datas.hoje());  

O critério acima, gera um filtro parecido com:

    dataNascimento = 2018-02-05T09:37:09.009  

Caso queira submeter a data no filtro utilizando outros formatos, cujas opções serão exemplificadas a seguir.

### Informar uma das formatações pré-definidas (data e hora)​

    Criterio.onde('dataNascimento').igual(Datas.hoje()​, [formatacao: 'data']​);   
    Criterio.onde('​horaAlmoco').igual(Datas.hoje()​, [formatacao: 'hora']​);  

Os critérios acima, geram os seguintes filtros:

    dataNascimento = ​2018-02-05   
    horaAlmoco = 09:43:45.045  

​

### Informar uma ​formatação customizada​

    Criterio.onde('dataNascimento').igual(Datas.hoje(), [ formatacao: 'dd/MM/yyyy']);  

  * Criação
  * Operações
    * Obrigatoriedade dos valores
  * Delimitador nas operações contidoEm/naoContidoEm
    * Com delimitador
    * Sem delimitador
    * Com formatação e delimitador
  * Filtros compostos
  * Agrupamento
  * Datas
    * Informar uma das formatações pré-definidas (data e hora)
    * Informar uma ​formatação customizada