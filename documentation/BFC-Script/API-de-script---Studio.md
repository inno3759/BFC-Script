---
title: API de script | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-script
crawled_at: 2026-02-27 13:00:29
---

Pular para o conteúdo principal

Nessa página

A linguagem disponibiliza uma série de funções que provê suporte à chamada entre scripts. Esta funcionalidade permite que uma lógica comum seja utilizada por diversos scripts e está disponível ao usuário final somente pela **Ferramenta de Scripts**.

Para que seja possível executar ou agendar um script através da API é necessário configurar o identificador único do script a ser executado.

## Executando scripts​

A execução de um script é realizada utilizando a palavra reservada **Scripts** , seguida do identificador e método de execução:

**Scripts.identificador.executar(parametros)**

     Scripts.calculos.somar.executar(parametros)  
    Scripts.dubai.consultas.funcionarios.executar(parametros)  

### identificador​

Identificador único do script.

### executar(parametros)​

Função responsável pela execução do script.

    parametros = [ p1 : 100, p2 : 200]   
    Scripts.somar.executar(parametros)  

### variaveis(Map)​

Função responsável por enviar variáveis para outro script sem a necessidade de ter parâmetros no script que recebe essas variáveis.

O script de exemplo tem dois parâmetros do tipo arquivo, com os nomes arquivo e arquivo2, esses arquivos são enviados para o segundo script identificado por scriptb:

    arquivos = [arquivo1: parametros.arquivo.valor, arquivo2: parametros.arquivo2.valor, val3:'teste teste 123']  
       
    Scripts.scriptb.variaveis(arquivos).executar();  

No script que recebe as variáveis, os valores estão disponíveis da seguinte maneira:

    Resultado.arquivo(variaveis.arquivo1)  
    Resultado.arquivo(variaveis.arquivo2)   
    imprimir variaveis.val3  

O scriptb não precisa ter nenhum parâmetro para receber as variáveis e qualquer tipo pode ser passado por variaveis().

Outro exemplo seria um script principal que gera um arquivo csv com valores obtidos em execuções de outros três scripts:

Script principal

    //Escrita  
    csv = Arquivo.novo('teste.csv', 'csv', [delimitador:';'])  
       
    csv.escrever('ID')  
    csv.escrever('NOME')  
    csv.escrever('SALARIO')  
       
    Scripts.geraarquivo.funcionarios1.variaveis(arquivo:csv).executar()  

    geraArquivo = {col1, col2, col3 ->  
      csv.novaLinha()  
        
      csv.escrever(col1)  
      csv.escrever(col2)  
      csv.escrever(col3)  
    }  
       
    Scripts.geraarquivo.funcionarios2.variaveis(retorno:geraArquivo).executar()  
       
    retorno = Scripts.componente3.executar()  
       
    imprimir retorno.variaveis.geraArquivo2();  // imprime o valor teste2 no log de execução do script principal  
       
    retorno.variaveis.geraArquivo(csv)  
       
    Resultado.arquivo(csv)  

Script com o identificador geraarquivo.funcionarios1:

    csv = variaveis.arquivo  
    criterio = Criterio.onde('nome').igual('Paulo Henrique')  
       
    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    percorrer(dadosFuncionarios.busca(campos:"nome, id, salario", criterio: criterio)){   
        csv.novaLinha()  
        csv.escrever(item.id)  
        csv.escrever(item.nome)  
        csv.escrever(item.salario)  
    }  

Script com o identificador geraarquivo.funcionarios2:

    dadosFuncionarios = Dados.dubai.v1.funcionarios  
    criterio = Criterio.onde('nome').igual('Wellington')  
       
    id = '';  
    nome = '';  
    salario = '';  
       
    percorrer(dadosFuncionarios.busca(campos:"nome, id, salario", criterio: criterio)){   
        id = item.id  
        nome = item.nome  
        salario = item.salario  
    }  
       
    variaveis.retorno(id, nome, salario)  

Script com o identificador componente3:

    geraArquivo2 = {  
      retornar "teste2"  
    }  
       
    geraArquivo = {csv ->  
      csv.novaLinha()  
        
      csv.escrever('Valor 31')  
      csv.escrever('Valor 32')  
      csv.escrever('Valor 33')  
        
    }  

Ao executar o script principal o arquivo csv é gerado.

## Retorno dos scripts​

A execução de um script através da API sempre irá produzir um resultado, Este resultado é representado da seguinte forma:

    resultado = Scripts.somar.executar([ p1 : 100, p2 : 200])  

As opções disponíveis em um resultado são: **valor** , **vazio** , **variável(nome)** e **retornar.**

### valor​

Recupera o valor retornado pelo script executado.

    imprimir resultado.valor()  

### vazio​

Verifica se o script invocado retornou algum resultado.

    resultado = Scripts.somar.executar([ p1 : 100, p2 : 200])  
       
    se(resultado.vazio){  
       imprimir 'Nenhum resultado foi retornado pelo script somar'  
    }  

### variavel(nome)​

Recupera o valor de uma variável declarada no script invocado.

    resultado = Scripts.somar.executar([ p1 : 100, p2 : 200])   
    imprimir resultado.variavel('log') //Realizando soma  

Note que a variável log foi declarada no conteúdo do script somar:

    log = "Realizando soma"    
    retornar parametros.p1.valor + parametros.p2.valor  

### retornar​

O retorno de um script é realizado utilizando o comando retornar: 

    retornar 'Retornando uma mensagem'  
    ret = [valor: 1, mensagem: 'Retornando um mapa']  
    retornar ret  

Nas validações de certidões/alvarás do Cidadão Web, deve ser retornado:

    ret = [resultado: 1, mensagem: 'Retornando um mapa']  

Não sendo permitido o uso da seguinte forma:

    se (x == 'teste')  
    {retornar resultado: 0}  
    senao  
    { retornar resultado: 1, mensagem: 'Teste'] }  

Ou seja, não sendo permitido dentro da condição "se" o retorno de mais de uma função retornar. Nestes casos, sendo indicado o uso no seguinte formato:

    se (x == 'teste')  
    { ret = [resutado:0] }  
    senao{  
    ret = [resultado:1, mensagem 'O ITBI está com pagamento pendente']  
    retornar ret;  

## Executando scripts em lotes​

A execução de scripts em lote pode ser realizada através da criação de um script centralizador. Este script será responsável por orquestrar a execução dos demais scripts obedecendo a ordem cronológica de execução. **Exemplo:**

     resultado = Scripts.somar.executar([ p1 : 100, p2 : 200])  
       
    Scripts.enviarEmailSoma.executar([valor: resultado.valor])  
       
    Scripts.enviarSmsSoma.executar([valor: resultado.valor])  

## Agendando scripts​

O agendamento de um script é realizado utilizando a palavra reservada **Scripts** , seguida do identificador e método de agendamento:

**Scripts.identificador.agendar(para)** **Scripts.identificador.agendar(parametros, para)**

     Scripts.calculos.somar.agendar(parametros, '10m')  
    Scripts.dubai.consultas.funcionarios.agendar(parametros, 2.horas)  

### identificador​

Identificador único do script.

### agendar([parametros], para)​

Função responsável pelo agendamento do script.

    parametros = [ p1 : 100, p2 : 200]   
    Scripts.somar.agendar(parametros, '15m')  

### Valores suportados no `para`​

  * Literal com a duração desejada. Ex: ('1m', '2h', etc)
  * Data e hora especifica. Ex: Datas.data(2022, 6, 20)
  * Duração usando a sintaxe do bfc-script. Ex: (1.minuto, 3.horas, 1.dia)

### Regras para o agendamento​

  * Não pode ser para menos que um minuto e nem para mais que um mês
  * Não pode encadear mais de 20 execuções agendadas (um script agendando outro ou ele mesmo sucessivamente)
  * Só é permitido um agendamento por execução
  * O agendamento ocorre somente no final da execução do script principal

### Sugestões de uso​

  * Esperar o processamento de um lote enviado para algum serviço
    * No lugar de parar a execução atual, utilizando o metodo `esperar`, basta agendar o mesmo ou outro script passando os parametros necessários para a consulta
  * Executar um processo incremental sem a necessidade de fazer um agendamento customizado
  * De forma geral, em todos os lugares onde hoje se utiliza o `esperar`

## Componentes​

**Quando utilizar componentes?**

Quando para resolver uma dada situação seja mais indicado fragmentar o script, seja por uma questão de organização ou de praticidade em ter funções com finalidades específicas devidamente separadas.

Por exemplo: Consideremos que um dado Tribunal de Contas exige bimestralmente a informação de todos os fornecedores de uma entidade via Web Service. Neste caso, poderiam existir os seguintes recursos:

  * Script principal, onde recebe os parâmetros para gerar as informações e enviá-las ao Tribunal de Contas;

  * Componente para identificar todos os fornecedores passíveis de envio ao Tribunal de Contas;

  * Componente para gerar o arquivo a ser enviado ao Tribunal de Contas;

  * Componente para enviar o arquivo ao Tribunal de Contas via Web Service;

**Por que utilizar componentes?**

São algumas vantagens na utilização dos componentes:

**Melhor performance na execução do script:** Por conta do recurso Exportar e Importar e também porque os componentes são executados exclusivamente a partir de um script que o invoca;

**Organização de código:** Por meio da fragmentação de código orientada ao objetivo fim do componente;

**Privacidade de variáveis e closures (funções):** Num componente é possível declarar variáveis e closures localmente, e então escolher quais serão expostos para quando o componente for importado por outro script;

**Reutilização de código:** Pode ser utilizado o mesmo componente em mais de um script;

**Exemplos de utilização:**

**Exemplo 1:** Este exemplo demonstra um componente que abstrai uma **API REST**.

Segue o código de um **componente** cujo identificador foi denominado ** _restapi_** e que será chamado pelo **script pai** :

    // variável local e privada ao componente  
    api = Http.servico('https://jsonplaceholder.typicode.com')  
       
    // closure privada ao componente  
    extractContent = { response ->  
      conteudo = -1  
        
      se (response.sucesso() && response.contemResultado()) {  
        conteudo = response.conteudo()  
      }  
        
      retornar conteudo  
    }  
       
    getPost = { id ->  
      extractContent(api.caminho("posts/$id").GET())  
    }  
       
    getComments = { idPost ->  
      extractContent(api.caminho("posts/$idPost/comments").GET())  
    }  
       
    Scripts.exportar(  
      buscarPublicacao: getPost,  
      buscarComentarios: getComments  
    )  

O comando **exportar** é utilizado para definir quais recursos serão expostos pelo componente. Repare que as declarações que não foram exportadas permanecem privadas ao componente, permitindo assim uma modelagem mais robusta de funcionalidades comuns a vários scripts.

Segue o código do **script pai** que chama o componente acima:

    api = Scripts.restapi.importar()  
       
    publicacao = api.buscarPublicacao(1)  
       
    se (publicacao != -1) {  
      imprimir "Publicacao: " + publicacao  
    }  
       
    comentarios = api.buscarComentarios(1)  
       
    se (comentarios != -1) {  
      imprimir "Comentarios: " + comentarios  
    }  

A importação dos recursos de um componente é realizada utilizando a palavra reservada **Scripts** , seguido do identificador e o método de importação. O resultado é atribuído a uma variável, a partir da qual os recursos importados podem ser acessados.

Alternativamente, pode-se utilizar a palavra reservada **importar** passando como parâmetro o identificador do componente, no caso, fica assim:

    api = importar "restapi"  

**Exemplo 2:** Este exemplo trata de múltiplos componentes para um único Script Pai:

Existem 3 componentes:

Que simula uma calculadora;

Que executa um contador;

Que gera um log;

Componente 1: identificador ped.calculadora

    add = { p1, p2 ->  
      p1 + p2  
    }  
       
    sub = { p1, p2 ->  
      p1 - p2  
    }  
       
    mul = { p1, p2 ->  
      p1 * p2  
    }  
       
    div = { p1, p2 ->  
      p1 / p2  
    }  
       
    exportar(  
      somar: add,  
      subtrair: sub,  
      multiplicar: mul,  
      dividir: div  
    )  

Componente 2: identificador ped.contador

    current = 0  
       
    inc = { amount = 1 -> current += amount }  
    dec = { amount = 1 -> current -= amount }  
    reset = { current = 0 }  
    get = { current }  
       
    Scripts.exportar(  
            incrementar: { inc(1) },  
            incrementarEm: inc,  
            decrementar: { dec(1) },  
            decrementarEm: dec,  
            zerar: reset,  
            atual: get  
    )  

Componente 3: identificador ped.log

    logFile = Arquivo.novo('log.txt')  
       
    logInfo = { text ->  
      logFile.escrever("INFO: $text")  
      logFile.novaLinha()  
    }  
       
    logError = { text ->  
      logFile.escrever("ERROR: $text")  
      logFile.novaLinha()  
    }  
       
    commit = {  
      imprimir "Adicionado log no resultado"  
      Resultado.arquivo(logFile, 'log.txt')  
    }  
       
    exportar(  
      info: logInfo,  
      erro: logError,  
      salvar: commit  
    )  

Finalmente, o **Script Pai** :

    calculadora = importar "ped.calculadora"  
    contador = importar "ped.contador"  
       
    imprimir "2 + 2 = ${calculadora.somar(2, 2)}"  
    imprimir "2 - 2 = ${calculadora.subtrair(2, 2)}"  
    imprimir "2 * 2 = ${calculadora.multiplicar(2, 2)}"  
    imprimir "2 / 2 = ${calculadora.dividir(2, 2)}"  
       
    imprimir "Inicio: " + contador.atual()  
    imprimir "+1: " + contador.incrementar()  
    imprimir "+10: " + contador.incrementarEm(calculadora.somar(5, 5))  
    imprimir "Zerado: " + contador.zerar()  
       
    //------------------------------------------------  
    log = importar "ped.log"  
       
    log.info("Iniciando execução")  
       
    percorrer(ate: 5) {  
      log.info("Executando passo #$indice")  
    }  
       
    log.erro("Erro na conversão dos valores")  
    log.salvar()  

  * Executando scripts
    * identificador
    * executar(parametros)
    * variaveis(Map)
  * Retorno dos scripts
    * valor
    * vazio
    * variavel(nome)
    * retornar
  * Executando scripts em lotes
  * Agendando scripts
    * identificador
    * agendar(parametros, para)
    * Valores suportados no `para`
    * Regras para o agendamento
    * Sugestões de uso
  * Componentes