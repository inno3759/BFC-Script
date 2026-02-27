---
title: API de SOAP | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-soap
crawled_at: 2026-02-27 13:00:19
---

Pular para o conteúdo principal

Nessa página

A linguagem disponibiliza uma série de funções para para consumo de serviços web no padrão **SOAP**. Essas funções estarão disponíveis ao usuário final apenas através da **Ferramenta de Scripts** , e serão absorvidas plenamente conforme a utilização.

A **API** conta com algumas representações básicas de funcionamento sendo elas: o **serviço** , a **mensagem** e a **resposta**. 

O serviço trata-se de um **_webservice_ SOAP** a ser consumido, cada interação com esse webservice é realizado através de uma mensagem. O produto desta mensagem quando executada é uma resposta, essa resposta pode ser transformada em vários tipos de saídas, sendo elas um **Leitor de XML da API** de arquivo, Uma fonte de arquivo para utilização em conjunto com outras **APIs** (E-mail, Arquivos), O conteúdo **XML** da resposta em si ou simplesmente a impressão da resposta no console do script.

![api soap](/assets/images/bfc14-b99175a97b48b2f1d6ef8bc1d0a121de.png)

## Serviço​

Para criar um novo serviço SOAP a ser consumido deve-se utilizar a função **Soap.servico** , as opções disponíveis para criação e configurações dos serviços serão listadas nos próximos tópicos.

### Soap.servico(url)​

Cria um novo serviço com base na URL informada por parâmetro.

    servico = Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx')  

### Soap.servico(url, namespace, prefixo)​

Cria um novo serviço com base na URL informada por parâmetro. O _namespace_ e prefixo (_target_ _namespace_) informados serão utilizados como padrão na montagem da mensagem e manipulação dos elementos.

    Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx',  
                 'http://ws.cdyne.com/',  
                 'ws')  

### Soap.servico(url, namespace, prefixo, usuario, senha)​

Esta opção dá suporte a criação de serviços que utilizem mecanismos de autenticação HTTP básico permitindo informar também o usuário e senha de conexão como parâmetros.

### Soap.criarNamespace(namespace, prefixo)​

Cria uma representação de um _namespace_ e prefixo para ser reutilizado nas funções da API, desta forma não é necessário informar _namespace_ e prefixo a cada função.

Os valores podem ser acessados através das funções: **namespace()** e **prefixo()** da representação criada.

    namespace = Soap.criarNamespace('http://ws.cdyne.com/', 'ws')  
    servico = Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx', namespacePadrao)  
       
    imprimir namespace.namespace()  
    imprimir namespace.prefixo()  

### cabecalho(nome, valor)​

Adiciona um cabeçalho(header) HTTP na requisição SOAP do serviço.

    servico = Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx')  
    servico.cabecalho('Authorization','Bearer 239e3d8e-1e93-4f2b-beff-c430103b9287')  

### certificado([arquivo, senha])​

Configura a autenticação de certificado de cliente SSL/TLS.

  * `arquivo` \- deve ser um certificado válido, contendo toda a cadeia necessária (formato JKS ou P12).
  * `senha` \- a senha para acessar o certificado, caso o arquivo não possua senha, informar `""`.

    servico.certificado([arquivo: parametros.certificado.valor, senha: parametros.senha.valor])  

### certificado([id])​

Configura a autenticação de certificado de cliente SSL/TLS, utilizando um certificado armazenado na ferramenta de documentos.

###### Exemplo 1​

![Configuração dos parâmetros](/assets/images/bfc15-ca66b10c05987e05b26cdeec8fc7ae61.png)

    // Recebendo o certificado via parametro  
      
    servico.certificado(parametros.certificado)  

###### Exemplo 2​

    // Consulta de certificado utilizando a fonte diretamente no script  
      
    certificado = Dados.plataforma.documentos.v1.certificados  
        .entidade(campos: "id, descricao", primeiro: true)  
      
    servico.certificado(certificado)  

### mensagem()​

Cria uma nova mensagem (envelope) a ser enviado ao serviço.

### mensagem(namespace, prefixo)​

Cria uma nova mensagem (envelope) a ser enviado ao serviço sobrescrevendo o _namespace_ e prefixo padrão informados na criação do serviço.

### mensagem(namespace)​

Cria uma nova mensagem (envelope) a ser enviada ao serviço sobrescrevendo o _namespace_ e prefixo padrão informados na criação do serviço. Esta opção deve ser utilizada com _namespaces_ criados com a função Soap.criarNamespace.

### tempoLimite(valor)​

Define o tempo limite para a execução das requisições. O valor deve ser informado em milissegundos.

### depurar(booleano)​

Quando habilitado exibirá no log de execução o corpo da mensagem SOAP enviado.

## Mensagem​

A representação de uma mensagem é composta basicamente de um cabeçalho e de um corpo. Ambos podem conter diversos elementos que por sua vez podem possuir outros elementos. Esta estrutura de árvore é baseada no padrão XML e é através dela que os parâmetros de entrada da funcionalidade do _webservice_ são informados. Em resumo, uma mensagem destina-se à execução de um método/função de um serviço SOAP.

As opções disponíveis para montagem da mensagem estão listadas nos próximos tópicos.

### namespace(namespace, prefixo)​

Adiciona um _namespace_ a mensagem. Este _namespace_ será adicionado ao envelope SOAP da mensagem e poderá ser utilizado na declaração dos elementos.

### namespace(namespace)​

Adiciona um _namespace_ a mensagem. Este _namespace_ será adicionado ao envelope SOAP da mensagem e poderá ser utilizado na declaração dos elementos.

### namespaces()​

Retorna uma lista com os _namespaces_ declarados na mensagem.

### namespacePadrao()​

Retorna o _namespaces_ definido como padrão da mensagem.

### corpo()​

Retorna o elemento do corpo da mensagem.

### corpo(conteudo)​

Escreve o conteúdo XML no corpo da mensagem. É importante lembrar que o conteúdo deverá ser um XML válido e utilizar os _namespaces_ declarados na mensagem/corpo.** 

    servico.mensagem().corpo('<ws:VerifyEmail><ws:email>teste@test.com</ws:email><ws:LicenseKey>example</ws:LicenseKey></ws:VerifyEmail>')  

### corpo(arquivo)​

Escreve o conteúdo XML no corpo da mensagem com base em uma fonte de arquivo. É importante lembrar que o conteúdo do arquivo deverá ser um XML válido e utilizar os _namespaces_ declarados na mensagem/corpo.

    xml = Arquivo.novo('msg.xml', 'xml')  
    xml.fechar()  
       
    servico.mensagem().corpo(xml)  

### cabecalho()​

Retorna o elemento do cabeçalho da mensagem.

### cabecalho(conteudo)​

Escreve o conteúdo XML no cabeçalho da mensagem. É importante lembrar que o conteúdo deverá ser um XML válido e utilizar os _namespaces_ declarados na mensagem/corpo. 

    servico.mensagem().cabecalho('<ws:VerifyEmail><ws:email>teste@test.com</ws:email><ws:LicenseKey>example</ws:LicenseKey></ws:VerifyEmail>')  

### cabecalho(arquivo)​

Escreve o conteúdo XML no cabeçalho da mensagem com base em uma fonte de arquivo. É importante lembrar que o conteúdo do arquivo deverá ser um XML válido e utilizar os _namespaces_ declarados na mensagem/corpo.

    xml = Arquivo.novo('msg.xml', 'xml')  
    xml.fechar()  
       
    servico.mensagem().cabecalho(xml)  

### operacao(operacao)​

Define a operação/método/função a ser executada no webservice. Este valor será informado no cabeçalho HTTP SOAP Action da mensagem.

### executar()​

Executa a chamada ao método/função do serviço SOAP e retorna uma representação da resposta.

### executar(operacao)​

Executa a chamada ao método/função do serviço SOAP e retorna uma representação da resposta. Esta opção permite que a operação a ser executada seja informada diretamente pela função executar() sem a necessidade de pré-definir o valor através da função operacao().

### requisicao()​

Retorna uma representação para leitura da requisição SOAP realizada. Este leitor de mensagem contém as mesmas funcionalidades da resposta e poderá ser utilizado para fins de depuração.

## Elementos​

Um elemento pode ser considerado como uma representação baseada em árvore para descrever uma informação na mensagem. Os elementos de uma mensagem (corpo, cabeçalho) **SOAP** utilizam o padrão **XML**.

As opções disponíveis para manipulação dos elementos estão listadas nos próximos tópicos.

### nome()​

Retorna o nome do elemento.

### namespace()​

Retorna o namespace do elemento.

### adicionarElemento(nome)​

Adiciona/cria um novo elemento. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

    elemEnderecos = servico.mensagem()  
                           .corpo()  
                           .adicionarElemento('endereco')  
                                 
    elemEnderecos.adicionarElemento('residencial')      
    elemEnderecos.adicionarElemento('comercial')  

O elemento elemEnderecos irá produzir o seguinte XML na mensagem:

    <endereco>  
        <residencial></residencial>  
        <comercial></comercial>  
    </endereco>  

### adicionarElemento(nome, namespace, prefixo)​

Adiciona/cria um novo elemento informando também o _namespace_ e prefixo de declaração do elemento. É importante lembrar que o _namespace_ utilizado deve estar declarado na mensagem ou elemento pai. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarElemento(nome, namespace)​

Adiciona/cria um novo elemento informando também o _namespace_ de declaração do elemento. É importante lembrar que o _namespace_ utilizado deve estar declarado na mensagem ou elemento pai. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarTexto(texto)​

Adiciona conteúdo do tipo texto a um elemento. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

    elemEnderecos.adicionarElemento('residencial')  
                 .adicionarTexto('Rua geral')  

Produzirá:

    <residencial>Rua geral</residencial>  

### adicionarElementoTexto(nome, texto)​

Adiciona um novo elemento com conteúdo do tipo texto. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

    elemEnderecos.adicionarElementoTexto('residencial', 'Rua geral')  

Produzirá:

    <residencial>Rua geral</residencial>  

### adicionarElementoTexto(nome, texto, namespace, prefixo)​

Adiciona um novo elemento com conteúdo do tipo texto indicando também o _namespace_ e prefixo que o elemento está vinculado. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarElementoTexto(nome, texto, namespace)​

Adiciona um novo elemento com conteúdo do tipo texto indicando também o _namespace_ e prefixo que o elemento está vinculado. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarAtributo(nome, valor)​

Adiciona um novo atributo ao elemento atual. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

    elemEnderecos.adicionarElemento('residencial')  
                 .adicionarAtributo('principal','N')  

Produzirá:

    <residencial principal="N">Rua geral</residencial>  

### adicionarAtributo(nome, valor, namespace, prefixo)​

Adiciona um novo atributo ao elemento atual indicando também o _namespace_ e prefixo ao qual o atributo está vinculado. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarAtributo(nome, valor, namespace)​

Adiciona um novo atributo ao elemento atual indicando também o _namespace_ e prefixo ao qual o atributo está vinculado. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarNamespace(namespace, prefixo)​

Adiciona a declaração de um _namespace_ ao elemento atual. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### adicionarNamespace(namespace)​

Adiciona a declaração de um _namespace_ ao elemento atual. O retorno desta função é a representação do novo elemento criado e poderá ser utilizado para adicionar elementos filhos caso necessário.

### elementoAnterior()​

Utilizado para navegação entre os elementos criados de uma mesma família. Esta opção contém a representação do elemento pai do elemento corrente.

    servico.mensagem()  
           .corpo()  
           .adicionarElemento('pessoas')  
           .adicionarElementoTexto('nome', 'João')  
           .elementoAnterior() //O elemento pai do elemento nome é pessoas  
           .adicionarElementoTexto('nome', 'Maria')  

Produzirá:

    <pessoas>  
        <nome>João</nome>  
        <nome>Maria</nome>  
    </pessoas>  

### contemElementoAnterior()​

Indica se o elemento atual possui um próximo elemento.

### proximoElemento()​

Utilizado para navegação entre os elementos criados de uma mesma família. Esta opção contém a representação do primeiro elemento filho do item corrente.

### contemProximoElemento()​

Indica se o elemento atual possui um elemento anterior.

    elemPessoas = servico.mensagem()  
                         .corpo()  
                         .adicionarElemento('pessoas')  
       
    imprimir elemPessoas.contemElementoAnterior() // true pois corpo() e cabecalho() são elementos da mensagem              
    imprimir elemPessoas.contemProximoElemento() // false  
       
    elemPessoas.adicionarElementoTexto('nomePessoa', 'João')  
       
    imprimir elemPessoas.contemProximoElemento() // true  
    elemPessoas.proximoElemento().nome() // nomePessoa  

## Métodos​

Métodos são representações auxiliares para simplificar a montagem dos elementos da mensagem nos casos em que o _webservice_ contém apenas parâmetros simples como entrada.

As opções disponíveis para criação de métodos a partir da mensagem estão listadas nos próximos tópicos.

**metodo(operacao):** Cria um novo método para a operação/função informado no parâmetro.

**metodo(operacao, namespace, prefixo**): Cria um novo método utilizando a operação, _namespace_ e prefixo informados nos parâmetros.

**metodo(operacao, namespace):** Cria um novo método utilizando a operação e _namespaces_ informados nos parâmetros.

    metodoVerificaEmail = servico.mensagem().metodo('VerifyEmail')  

**As funções disponíveis na representação de métodos são:**

**parametro(nome, valor):** Adiciona um parâmetro de entrada ao método atual.

**parametro(nome, valor, namespace):** Adiciona um parâmetro de entrada ao método atual utilizando o namespace informado.

**operacao():** Retorna a operação do método atual.

**namespace():** Retorna o _namespace_ do método atual.

**elemento():** Retorna o elemento que representa o método atual.

**requisicao():** Retorna uma representação para leitura da requisição SOAP realizada. Este leitor de mensagem contém as mesmas funcionalidades da resposta e poderá ser utilizado para fins de depuração.

**executar():** Executa a chamada do método atual e retorna uma representação da resposta.

**mensagem():** Retorna a representação da mensagem em que o método foi criado.

    servico = Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx',  
                           'http://ws.cdyne.com/', 'ws')  
                             
    resposta = servico.mensagem()  
                      .metodo('VerifyEmail')  
                      .parametro('email', parametros.email.valor)  
                      .parametro('LicenseKey', '123')  
                      .executar()  

## Resposta​

Uma mensagem quando executada tem como retorno uma representação de resposta. Esta resposta pode ser processada/lida de maneiras distintas conforme necessidade.

As opções de processamento disponíveis são:

**imprimir():** Imprime o conteúdo XML da resposta no console do editor de scripts.

**conteudo():** Retorna o conteúdo XML da resposta no formato caracter. 

    resposta = servico.metodo('VerifyEmail')  
           .parametro('email', parametros.email.valor)  
           .parametro('LicenseKey', '123')  
           .executar()  
       
    imprimir resposta.conteudo()  

**arquivo():** Retorna uma fonte de arquivo que contém o conteúdo da resposta. Esta opção deverá ser utilizada em conjunto com as demais APIs da engine de scripts.

    resposta = servico.metodo('VerifyEmail')  
           .parametro('email', parametros.email.valor)  
           .parametro('LicenseKey', '123')  
           .executar()  
       
    //Utilizando com a API de arquivos  
    xml = Arquivo.ler(resposta.arquivo(), 'xml')  
       
    //Utilizando o retorno como anexo da API de Email  
    Email.novo()  
         .de('webservice@betha.com.br')  
         .para('usuarios@betha.com.br')  
         .assunto('Arquivo de resposta do webservice!')  
         .anexarArquivo(resposta.arquivo(), 'resposta.xml')  
         .enviar()  

**xml():** Retorna um leitor de arquivos XML da API de Arquivos para o conteúdo da resposta.

    resposta = servico.metodo('VerifyEmail')  
           .parametro('email', parametros.email.valor)  
           .executar()  
       
    xml = resposta.xml()  
    xml.proximoElemento('GoodEmail')  
       
    se(xml.valor() == 'true'){  
      imprimir 'O endereço ' + parametros.email.valor + ' é um e-mail válido!'  
    } senao {  
      imprimir 'O endereço ' + parametros.email.valor + ' é inválido!'  
    }  

**anexos():** Retorna uma lista com os anexos presentes na mensagem de retorno do serviço.** 

    retorno = servico.mensagem().corpo(xml).executar()  
    anexos = retorno.anexos()  
       
    percorrer(anexos) {  
        imprimir item.id()  
        imprimir item.tipo()  
        imprimir item.cabecalho("Content-Type") // mesmo valor do item.tipo()  
          
        arquivo = item.arquivo()  
    }  

**anexo(id):** Localiza e retorna um anexo de acordo com o seu id.

    retorno = servico.mensagem().corpo(xml).executar()  
       
    anexo = retorno.anexo(xmlRetorno.atributo("href").valor());  
    Resultado.arquivo(anexo.arquivo());  

## Base 64​

Base64 é um método para codificação de dados para transferência na Internet. É utilizado frequentemente para transmitir dados binários por meios de transmissão que lidam apenas com texto, como por exemplo para enviar arquivos anexos por e-mail. Uma abordagem muito comum, inclusive praticada por alguns tribunais de contas, é o uso do Base64 para envio de arquivos binários em webservices SOAP.

Segue um exemplo de como utilizar a API provida no BFCScript para este propósito:

    textoCodificado = BaseCodec.padrao64().codifica('Meu texto').texto()  
    textoDecodificado = BaseCodec.padrao64().decodifica(textoCodificado).texto()  

É possível codificar um arquivo zip gerado em um script:

    xml = Arquivo.novo('teste.xml', 'xml', [indentar:'S'])  
       
    xml.escreverInicioDocumento("UTF-8")  
    xml.escreverInicioElemento('root')  
       
    xml.escreverComentario('Nomes dos colaboradores sem setor')  
    xml.escreverInicioElemento('nome')  
    xml.escreverAtributo('completo', 'N')  
    xml.escreverAtributo('composto', 'S')  
    xml.escreverTexto('Marcos da Silva')  
    xml.escreverFimElemento()  
       
    xml.escreverInicioElemento('nome')  
    xml.escreverAtributo('completo', 'S')  
    xml.escreverTexto('Maria Joana Amaral')  
    xml.escreverFimElemento()  
       
    xml.escreverInicioElemento('setor')  
    xml.escreverAtributo('nome', 'Desenvolvimento')  
    xml.escreverInicioElemento('pessoas')  
    xml.escreverElementoTexto('nome', 'Javanildo Soares')  
    xml.escreverFimElemento()  
    xml.escreverFimElemento()  
       
    xml.escreverFimElemento()  
    xml.escreverFimDocumento()  
       
    arquivo = Arquivo.novo('arquivo.zip', 'zip')  
    arquivo.adicionar(xml)  
       
    arquivoCodificado = BaseCodec.padrao64().codifica(arquivo).texto()  
    arquivoDecodificado = BaseCodec.padrao64().decodifica(arquivoCodificado).texto()  

Ou ainda codificar um arquivo recebido por parâmetro:

    arquivoCodificado = BaseCodec.padrao64().codifica(parametros.arquivo.valor).texto()  
    arquivoDecodificado = BaseCodec.padrao64().decodifica(arquivoCodificado).texto()  

É possível ainda definir o encoding para codificação e/ou decodificação:

    textoCodificado = BaseCodec.padrao64().codifica('áé', 'iso-8859-1').texto()  
    textoDecodificado =  BaseCodec.padrao64().decodifica(textoCodificado).texto('iso-8859-1')  

O encoding padrão é UTF-8.

A função BaseCodec está disponível ao usuário final apenas através da **Ferramenta de Scripts**.

**Atenção:** existe um limite cumulativo de **30MB** para codificar/decodificar conteúdo Base64 durante uma execução de script. A soma de todo o conteúdo processado deve ficar sempre abaixo deste limite. Lembrando que este limite incinde sobre a saída gerada pela API, e não sobre as entradas utilizadas.

### Contornando a limitação cumulativa​

Caso seja necessário codificar ou decodificar diversos conteúdos e esteja sendo esbarrado no limite cumulativo, pode-se utilizar métodos que não retornam como o resposta o conteúdo (não alocando no contexto global), e sim disponibilizam ele dentro de uma closure, que acaba liberando a memória alocada mais rapidamente:

    input = 'Meu texto'; //poderia ser um arquivo  
    BaseCodec.padrao64().codifica(input) { conteudo ->  
       imprimir conteudo.texto();  
    }  
       
    inputEncoded = 'YWJjZGVmZ2hp'; //poderia ser um arquivo  
    BaseCodec.padrao64().decodifica(inputEncoded) { conteudo ->  
       imprimir conteudo.texto();  
    }  

Fazendo o uso dessas chamadas, o limite passa a ser de 30mb de forma individual e não descontando do limite cumulativo global.

**É recomendado que não se atribua essa variável interna para um contexto maior, permitindo assim que a memória alocada seja liberada**

## Hash​

Uma função de hash pode ser utilizada para verificar a integridade de arquivos, uma vez que uma hash é gerada com base em um texto ou arquivo, não existe uma maneira de fazer o caminho contrário. Uma abordagem muito comum, inclusive praticada por alguns tribunais de contas, é o uso de verificações de integridade de arquivos binários enviados em webservices SOAP.

Existem alguns algoritmos popularmente utilizados para gerar uma hash de algo, são eles MD5, SHA-1, SHA-256 e SHA-512:

**padraoMD5()**

     hashMD5 = Hash.padraoMD5().codifica("qualquer texto").texto()  

Quando utilizado um texto, é possível definir o charset para codificação (o charset padrão é UTF-8):

    hashMD5 = Hash.padraoMD5().codifica("ë", "iso-8859-1").texto()  

Quando utilizado um arquivo, não é possível definir o charset para codificação, o charset utilizado é o do arquivo:

    xml = Arquivo.novo('teste.xml', 'xml', [indentar:'S'])  
       
    xml.escreverInicioDocumento("UTF-8")  
    xml.escreverInicioElemento('root')  
       
    xml.escreverComentario('Nomes dos colaboradores sem setor')  
    xml.escreverInicioElemento('nome')  
    xml.escreverAtributo('completo', 'N')  
    xml.escreverAtributo('composto', 'S')  
    xml.escreverTexto('Marcos da Silva')  
    xml.escreverFimElemento()  
       
    xml.escreverInicioElemento('nome')  
    xml.escreverAtributo('completo', 'S')  
    xml.escreverTexto('Maria Joana Amaral')  
    xml.escreverFimElemento()  
       
    xml.escreverInicioElemento('setor')  
    xml.escreverAtributo('nome', 'Desenvolvimento')  
    xml.escreverInicioElemento('pessoas')  
    xml.escreverElementoTexto('nome', 'Javanildo Soares')  
    xml.escreverFimElemento()  
    xml.escreverFimElemento()  
       
    xml.escreverFimElemento()  
    xml.escreverFimDocumento()  
       
    hashMD5 = Hash.padraoMD5().codifica(xml).texto()  

**padraoSHA1()**

     hashSHA1 = Hash.padraoSHA1().codifica("qualquer texto").texto()  

Quando utilizado um texto, é possível definir o charset para codificação (o charset padrão é UTF-8):

    hashSHA1 = Hash.padraoSHA1().codifica("ë", "iso-8859-1").texto()  

Quando utilizado um arquivo, não é possível definir o charset para codificação, o charset utilizado é o do arquivo:

    imprimir Hash.padraoSHA1().codifica(parametros.arquivo.valor).texto()  

**padraoSHA256()**

     hashSHA256 = Hash.padraoSHA256().codifica("qualquer texto").texto()  

Quando utilizado um texto, é possível definir o charset para codificação (o charset padrão é UTF-8):

    hashSHA256 = Hash.padraoSHA256().codifica("ë", "iso-8859-1").texto()  

Quando utilizado um arquivo, não é possível definir o charset para codificação, o charset utilizado é o do arquivo:

    zip = Arquivo.novo('arquivos.zip', 'zip');  
       
    zip.adicionar(parametros.arquivo.valor, 'teste.xml');  
       
    imprimir Hash.padraoSHA256().codifica(zip).texto()  

**padraoHex()**

     hexadecimal = Hash.padraoHex().codifica("qualquer texto").texto()  

Quando utilizado um texto, é possível definir o charset para codificação (o charset padrão é UTF-8):

    hexadecimal = Hash.padraoHex().codifica("ë", "iso-8859-1").texto()  

Quando utilizado um arquivo, não é possível definir o charset para codificação, o charset utilizado é o do arquivo:

    zip = Arquivo.novo('arquivos.zip', 'zip');  
       
    zip.adicionar(parametros.arquivo.valor, 'teste.xml');  
       
    imprimir Hash.padraoHex().codifica(zip).texto()  

## Exemplos​

Exemplo 1:

    servico = Soap.servico('http://ws.cdyne.com/emailverify/Emailvernotestemail.asmx',  
                           'http://ws.cdyne.com/', 'ws')  
       
    resposta = servico.mensagem()  
                      .metodo('VerifyEmail')  
                      .parametro('email', parametros.email.valor)  
                      .parametro('LicenseKey', '123')  
                      .executar()  
       
    xml = resposta.xml()  
    xml.proximoElemento('GoodEmail')  
       
    se(xml.valor() == 'true'){  
      imprimir 'O endereço ' + parametros.email.valor + ' é um e-mail válido!'  
    } senao {  
      imprimir 'O endereço ' + parametros.email.valor + ' é inválido!'  
    }  

Exemplo 2:

    servico = Soap.servico('https://www3.bcb.gov.br/wssgs/services/FachadaWSSGS',  
                           'http://publico.ws.casosdeuso.sgs.pec.bcb.gov.br', 'ws')  
       
    resposta = servico.mensagem()  
                      .metodo('getUltimoValorVO')  
                      .parametro('in0', '1')  
                      .executar()  
       
    xml = resposta.xml()  
    xml.proximoElemento('svalor')  
       
    notificacao = 'A cotação do dolar para hoje é de R$ ' + Caracteres.substituir(xml.valor(), '.', ',')  
       
    Notificacao.nova()  
               .mensagem(notificacao)  
               .para('usuario')  
               .enviar()  

Exemplo 3:

    servico = Soap.servico('https://demo.voxtecnologia.com.br/servicos/ws-consulta-previa-localizacao',  
                           'https://demo.voxtecnologia.com.br/servicos/ws-consulta-previa-localizacao', 'ws')  
       
    mensagem = servico.mensagem()  
    elemDadosConsulta = mensagem.corpo().adicionarElemento('dadosConsultaPreviaLocalizacao')  
    elemMensagem = elemDadosConsulta.adicionarElemento('mensagem')  
       
    elemMensagem.adicionarElemento('controle')    
                .adicionarElementoTexto('hash', '6cd61adb859800aa565d97290f798e01')  
                .elementoAnterior()  
                .adicionarElementoTexto('categMens', 'dadosConsultaPreviaLocalizacao')  
                .elementoAnterior()  
                .adicionarElementoTexto('data', '2015-10-28 09:54:44')  
                .elementoAnterior()  
                .adicionarElementoTexto('versao', '1.0')  
              
    elemMensagem.adicionarElemento('dadosConsultaPreviaLocalizacao')  
                .adicionarElementoTexto('co_protocolo', 'PRP1512623548')  
                .elementoAnterior()  
                .adicionarElementoTexto('dt_evento', '2016-05-23 12:00:00')  
                .elementoAnterior()  
                .adicionarElementoTexto('is_indeferido', 'false')  
              
    resposta = mensagem.executar()  
       
    email = Email.novo()  
                 .de('remetente@betha.com.br')  
                 .para('destinatario@betha.com.br')  
                 .assunto('Arquivo de resposta do webservice!')  
                 .mensagem('Segue arquivo em anexo do retorno do webservice')  
                 .anexarArquivo(mensagem.requisicao().arquivo(), 'envio.xml')  
                 .anexarArquivo(resposta.arquivo(), 'resposta.xml')  
                 .enviar()  

Exemplo 4:

Armazenar o retorno em formato de anexo de um serviço.

    xml = """  
          <ser:entregarManifestacaoProcessual>  
             <tip:idManifestante></tip:idManifestante>  
             <tip:senhaManifestante></tip:senhaManifestante>  
             <tip:numeroProcesso></tip:numeroProcesso>           
         <tip:documento idDocumento="27" tipoDocumento="13" mimetype="application/pdf" descricao="Petição Inicial" tipoDocumentoLocal="14">  
            <int:conteudo></int:conteudo>  
         </tip:documento>  
            <tip:documento idDocumento="28" tipoDocumento="14" mimetype="application/pdf" descricao="Petição Inicial" tipoDocumentoLocal="14">  
            <int:conteudo></int:conteudo>  
            </tip:documento>  
             <tip:dataEnvio></tip:dataEnvio>  
          </ser:entregarManifestacaoProcessual>  
    """;  
       
    imprimir xml;  
       
    servico = Soap.servico("https://eproc1ghml.tjsc.jus.br/homologa1g/ws/controlador_ws.php?srv=intercomunicacao2.2",  
                "http://www.cnj.jus.br/servico-intercomunicacao-2.2.2/", "ser")  
       
    retorno = servico.mensagem()  
                    .namespace("http://www.cnj.jus.br/tipos-servico-intercomunicacao-2.2.2", "tip")  
                    .namespace("http://www.cnj.jus.br/servico-intercomunicacao-2.2.2/", "ser")  
                    .namespace("http://www.cnj.jus.br/servico-intercomunicacao-2.2.2/", "int")  
                    .corpo(xml)  
                    .executar()  
       
    xmlRetorno = retorno.xml()  
       
    se (xmlRetorno.proximoElemento("Body") && xmlRetorno.proximoElemento("entregarManifestacaoProcessualResposta") && xmlRetorno.proximoElemento("recibo") && xmlRetorno.proximoElemento("Include")) {  
      anexo = retorno.anexo(xmlRetorno.atributo("href").valor());  
      Resultado.arquivo(anexo.arquivo());  
    }  
       
    imprimir retorno.conteudo()  

  * Serviço
    * Soap.servico(url)
    * Soap.servico(url, namespace, prefixo)
    * Soap.servico(url, namespace, prefixo, usuario, senha)
    * Soap.criarNamespace(namespace, prefixo)
    * cabecalho(nome, valor)
    * certificado(arquivo, senha)
    * certificado(id)
    * mensagem()
    * mensagem(namespace, prefixo)
    * mensagem(namespace)
    * tempoLimite(valor)
    * depurar(booleano)
  * Mensagem
    * namespace(namespace, prefixo)
    * namespace(namespace)
    * namespaces()
    * namespacePadrao()
    * corpo()
    * corpo(conteudo)
    * corpo(arquivo)
    * cabecalho()
    * cabecalho(conteudo)
    * cabecalho(arquivo)
    * operacao(operacao)
    * executar()
    * executar(operacao)
    * requisicao()
  * Elementos
    * nome()
    * namespace()
    * adicionarElemento(nome)
    * adicionarElemento(nome, namespace, prefixo)
    * adicionarElemento(nome, namespace)
    * adicionarTexto(texto)
    * adicionarElementoTexto(nome, texto)
    * adicionarElementoTexto(nome, texto, namespace, prefixo)
    * adicionarElementoTexto(nome, texto, namespace)
    * adicionarAtributo(nome, valor)
    * adicionarAtributo(nome, valor, namespace, prefixo)
    * adicionarAtributo(nome, valor, namespace)
    * adicionarNamespace(namespace, prefixo)
    * adicionarNamespace(namespace)
    * elementoAnterior()
    * contemElementoAnterior()
    * proximoElemento()
    * contemProximoElemento()
  * Métodos
  * Resposta
  * Base 64
    * Contornando a limitação cumulativa
  * Hash
  * Exemplos