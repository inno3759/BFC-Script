---
title: API de HTTP | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-http
crawled_at: 2026-02-27 13:00:34
---

Pular para o conteúdo principal

Nessa página

A linguagem disponibiliza uma API para consumo de serviços web HTTP. Essas funções estarão disponíveis ao usuário final apenas por meio da **Ferramenta de Scripts** , e serão absorvidas plenamente conforme a utilização.

A API conta com algumas representações básicas de funcionamento sendo elas a **Requisição** e a **Resposta**.

**A Requisição** trata-se da definição de uma ou várias chamadas à um serviço HTTP comum, cada interação com esse serviço é realizado através dos métodos/verbos padrões do HTTP.

O produto desta interação quando executada é uma **Resposta** , essa resposta pode ser transformada em vários tipos e saídas, sendo elas um **JSON** no formato de Mapa (quando a resposta do serviço for **JSON**), Uma fonte de arquivo para utilização em conjunto com outras APIs (E-mail, Arquivos). O conteúdo da resposta no formato de texto em si ou simplesmente a impressão da resposta no console do script.

![api http](/assets/images/bfc14-b99175a97b48b2f1d6ef8bc1d0a121de.png)

## Requisição​

Para criar uma nova requisição HTTP deve-se utilizar a função **Http.servico** , a função recebe como parâmetro a URL do serviço a ser consumido:

    servico = Http.servico('https://jsonplaceholder.typicode.com/posts')  

A **URL** informada pode conter marcadores, estes marcadores serão substituídos por um determinado valor no momento da execução de um método HTTP.

    servico = Http.servico('https://jsonplaceholder.typicode.com/posts/{ano}/{id}')  

Vejamos a seguir quais as opções disponíveis na API para interagir com um serviço.

### cookie(nome, valor)​

Adiciona um cookie na requisição HTTP.

### cookie(nome, valor, caminho, domínio, versão)​

Adiciona um cookie na requisição HTTP informando também o caminho/path, domínio e versão do cookie.

### cookie(Mapa[nome, valor])​

Adiciona um ou vários cookies (nome/valor) na requisição HTTP com base em um mapa.

    servico = Http.servico('https://jsonplaceholder.typicode.com/posts')  
    servico.cookie('Usuario', 'João da Silva')  
    servico.cookie('Usuario', 'João da Silva', '/usuarios', 'betha.com.br', 1)  
    servico.cookie([ Usuario: 'João da Silva', Accesso: 'sim' ])  

### cabecalho(nome, valor)​

Adiciona um cabeçalho/header na requisição HTTP.

### cabecalho(nome, lista de valores)​

Adiciona um cabeçalho/header com vários valores na requisição HTTP.

### cabecalho(Mapa[nome, valor])​

Adiciona um ou vários cabeçalhos/headers (nome/valor) na requisição HTTP com base em um mapa.

    servico.cabecalho('Authorization', 'Basic ABCF5065FGC==')  
    servico.cabecalho('User', ['murphy', 'luiz.silva'])  
    servico.cabecalho([ User: 'alex.o.leao'])  

### certificado([arquivo, senha])​

Configura a autenticação de certificado de cliente SSL/TLS. 

  * `arquivo` \- deve ser um certificado válido, contendo toda a cadeia necessária (formato PFX ou P12). 
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
      
    imprimir Http.servico('https://<endereço>/')  
                .certificado(certificado)  
                .GET().conteudo()  

### chaveIntegracao([identificador])​

Configura a chave de integração que será utilizada para a geração das credenciais de acesso.

As integrações são cadastradas no gerenciador de acesso do sistema e entidade destino. É possível que um script acesse os dados de várias entidades e sistemas, bastando para isso que cada destino tenha uma integração configurada para o sistema e entidade que está executando o script.

###### Exemplo​

    servico.chaveIntegracao("identificador da integração")  

tip

Recomendamos fortemente a utilização de variáveis de ambiente ou parâmetros para a configuração das chaves de integração.

## Parâmetros e caminhos​

Para permitir que um mesmo serviço atenda as mais diversas situações encontradas em **APIs HTTP** , as funções caminho(), e parametro() possuem um comportamento diferenciado das demais. Estas funções quando executadas criam uma cópia da requisição atual adicionando os respectivos parâmetro(s)/caminho(s). Desta forma a requisição original não é alterada e pode ser reutilizada para outras invocações no mesmo serviço.

    servico = Http.servico('https://jsonplaceholder.typicode.com')  
       
    //Gera uma chamada GET ao endereço https://jsonplaceholder.typicode.com/posts?id=5  
    servico.caminho('posts')  
           .parametro('id', 5)  
           .GET()  
       
    //Gera uma chamada GET ao endereço https://jsonplaceholder.typicode.com/users/admins?id=5  
    servico.caminho('users')  
           .caminho('admins')  
           .parametro('id', 2)  
           .GET()  
       
    //Caso se deseje alterar a requisição original basta associar a cópia ao serviço original, desta forma  
    //todas as requisições criadas à partir deste serviço utilizaram estes caminhos  
    servico = servico.caminho('users')  
                     .caminho('admins')  
       
    //Gera uma chamada GET ao endereço https://jsonplaceholder.typicode.com/users/admins/ativos?id=5  
    servico.caminho('ativos')  
           .parametro('id', 5)  
           .GET()  

### parametro(nome, valor)​

Cria uma cópia da requisição atual adicionando um parâmetro de query.

### parametro(nome, lista de valores)​

Cria uma cópia da requisição atual adicionando um ou mais parâmetros de query na requisição.

### parametro(Mapa[nome, valor])​

Cria uma cópia da requisição atual adicionando um ou mais parâmetros de query na requisição com base no mapa informado no parâmetro.

    servico.parametro('id', '1') //posts?id=1  
    servico.parametro('id', ['1', '2', '5']) //posts?id=1&id=2&id=5  
    servico.parametro([ id: '5', nome: 'joao']) //posts?id=1&nome=joao  
    servico = Http.servico(...)  
    servico.parametro('id', 1)  
    servico.parametro('id', 2)  
       
    imprimir servico.parametros() //[] - Vazio pois como cria uma cópia o serviço original não é alterado  
    servico = servico.parametro('id', 1)  
                     .parametro('id', 2)  
       
    imprimir servico.parametros() //[id : [1,2]] - pois atribuímos a cópia o serviço original  

### caminho(caminho)​

Cria uma cópia da requisição atual adicionando um caminho/path na URL corrente.

    servico = Http.servico('https://jsonplaceholder.typicode.com')  
       
    servico.caminho('posts')  
           .caminho('listar') //URL: https://jsonplaceholder.typicode.com/posts/listar  

### aceitarTipoMidia(midias)​

Informa qual tipo de mídia é aceito pela requisição. O valor padrão é Http.TODOS.

    servico.aceitarTipoMidia('application/json')  

A API conta com algumas constantes para os tipos de mídia comuns:

  * **Http.JSON: application/json**
  * **Http.XML: application/xml**
  * **Http.TEXTO _XML: text/xml**
  * **Http.XHTML: application/xhtml+xml**
  * **Http.TEXTO _HTML: text/html**
  * **Http.TEXTO: text/plain**
  * **Http.FORMULARIO: application/x-www-form-urlencoded**
  * **Http.MULTIPART: multipart/form-data**
  * **Http.ARQUIVO: application/octet-stream**
  * **Http.TODOS: */***

    servico.aceitarTipoMidia(Http.JSON)  
    servico.aceitarTipoMidia([Http.JSON, Http.XML])  

### credenciais(usuario, senha)​

Configura a autenticação básica HTTP no serviço.

    servico.credenciais('user', '123')  

### tempoLimite(valor)​

Define o tempo limite para requisições executadas a partir do serviço. O valor deve ser informado em milissegundos.

    // define timeout de 30 segundos  
    servico.tempoLimite(30000)  

### GET (Mapa[marcadores])​

Executa uma chamada do tipo GET ao serviço retornando uma representação de resposta.

    resposta = Http.servico('https://www.betha.com.br/users').GET()  
       
    svcUsuarios = Http.servico('https://www.betha.com.br/usuarios/{uf}/{nome}')  
    svcUsuarios.GET([uf: 'SC', nome: 'joao'])  
    svcUsuarios.GET([uf: 'SP', nome: 'maria'])  

### OPTIONS (Mapa[marcadores])​

Executa uma chamada do tipo **OPTIONS** ao serviço retornando uma representação de resposta.

    resposta = Http.servico('https://www.betha.com.br/users').OPTIONS()  

### HEAD (Mapa[marcadores])​

Executa uma chamada do tipo **HEAD** ao serviço retornando uma representação de resposta.

    resposta = Http.servico('https://www.betha.com.br/users').HEAD()  

### TRACE (Mapa[marcadores])​

Executa uma chamada do tipo **TRACE** ao serviço retornando uma representação de resposta.

    resposta = Http.servico('https://www.betha.com.br/users').TRACE()  

### DELETE​

  * **DELETE ()**
  * **DELETE (Mapa[marcadores])**
  * **DELETE (dados, Mapa[marcadores])**
  * **DELETE (dados, Tipo de mídia)**
  * **DELETE (dados, Tipo de mídia, Mapa[marcadores])**

Executa uma chamada do tipo DELETE ao serviço retornando uma representação de [resposta](http://test.betha.com.br/documentacao/bfc-script/2.10.X/#apiHttpResposta). Os dados da requisição são enviados conforme tipo de mídia informado no parâmetro sendo Http.JSON (_application/json_) o valor padrão.

    dados = [  
        id: "5",  
        author: "Uncle Bob",  
    ]  
       
    resposta = Http.servico('https://www.betha.com.br/users').DELETE()  
    resposta = Http.servico('https://www.betha.com.br/users/{id}').DELETE([id: '5'])  
    resposta = Http.servico('https://www.betha.com.br/users/{id}').DELETE(dados, [id: '5'])  
    resposta = Http.servico('https://www.betha.com.br/users/{id}').DELETE(dados, Http.JSON)  
    resposta = Http.servico('https://www.betha.com.br/users/{id}').DELETE(dados, Http.JSON, [id: '5'])  

### POST​

  * **POST (dados)**
  * **POST (dados, Mapa[marcadores])**
  * **POST (dados, Tipo de mídia)**
  * **POST (dados, Tipo de mídia, Mapa[marcadores])**
  * **POST (formulário)**
  * **POST (formulário, Mapa[marcadores])**

Executa uma chamada do tipo POST ao serviço retornando uma representação de resposta. Os dados/formulário da requisição são enviados conforme tipo de mídia informado no parâmetro sendo Http.JSON _(application/json)_ o valor padrão.

    conteudo = [  
        title: "The rabbit in the topper",  
        author: "Mr. M",  
    ]  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .POST(conteudo, Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .POST('{"nome":"Test"}', Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users/{id}')  
                   .POST(conteudo, Http.JSON, [id: 5])  

### PUT​

  * PUT (dados)
  * PUT (dados, Mapa[marcadores])
  * PUT (dados, Tipo de mídia)
  * PUT (dados, Tipo de mídia, Mapa[marcadores])
  * PUT (formulário)
  * PUT (formulário, Mapa[marcadores])

Executa uma chamada do tipo PUT ao serviço retornando uma representação de resposta. Os dados/formulário da requisição são enviados conforme tipo de mídia informado no parâmetro sendo Http.JSON _(application/json)_ o valor padrão.

    conteudo = [  
        title: "The rabbit in the topper",  
        author: "Mr. M",  
    ]  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .PUT(conteudo, Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .PUT('{"nome":"Test"}', Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users/{id}')  
                   .PUT(conteudo, Http.JSON, [id: 5])  

### PATCH​

  * PATCH (dados)
  * PATCH (dados, Mapa[marcadores])
  * PATCH (dados, Tipo de mídia)
  * PATCH (dados, Tipo de mídia, Mapa[marcadores])
  * PATCH (formulário)
  * PATCH (formulário, Mapa[marcadores])

Executa uma chamada do tipo **PATCH** ao serviço retornando uma representação de [resposta](http://test.betha.com.br/documentacao/bfc-script/2.7.X/index.html#apiHttpResposta). Os dados/formulário da requisição são enviados conforme tipo de mídia informado no parâmetro sendo Http.JSON (_application/json_) o valor padrão.

    conteudo = [  
        title: "The rabbit in the topper",  
        author: "Mr. M",  
    ]  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .PATCH(conteudo, Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users')  
                   .PATCH('{"nome":"Test"}', Http.JSON)  
       
    resposta = Http.servico('https://www.betha.com.br/users/{id}')  
                   .PATCH(conteudo, Http.JSON, [id: 5])  

### METODO​

  * METODO (método)
  * METODO (Mapa[marcadores], método)
  * METODO (método, dados)
  * METODO (método, dados, Mapa[marcadores])
  * METODO (método, tipo de mídia)
  * METODO (método, dados, tipo de mídia)
  * METODO (método, dados, tipo de mídia, Mapa[marcadores])
  * METODO (formulário)
  * METODO (formulário, Mapa[marcadores]

A função **METODO** é utilizada para realizar chamadas utilizando métodos personalizados. Tem como retorno uma representação de resposta. Os dados/formulário da requisição quando existentes são enviados conforme tipo de mídia informado no parâmetro sendo Http.JSON _(application/json)_ o valor padrão.

    dados = [  
        title: "The rabbit in the topper",  
        author: "Mr. M",  
    ]  
       
    resp = Http.servico('https://www.betha.com.br/users')  
               .METODO('GET'); //GET sem corpo  
       
    resp = Http.servico('https://www.betha.com.br/users/{id}')  
               .METODO([id: 'joao'], 'GET'); //Marcadores de URL  
       
    resp = Http.servico('https://www.betha.com.br/users')  
               .METODO('POST', dados)  

## Formulários​

Para permitir o uso de serviços web onde os dados são recebidos no formato de formulários (form), a API conta com alguns facilitadores. Vejamos quais são as seções a seguir.

### formulario​

Para criar um novo formulário de dados deve-se utilizar as funções **criarFormulario()** ou **criarFormulario(tipo de mídia formulário).** Estas funções criam um novo formulário utilizando como tipo de mídia o valor Http.FORMULARIO (application/x-www-form-urlencoded). A mídia pode ser alterada informando no parâmetro da função o tipo de mídia desejada.

    servico = Http.servico('https://www.betha.com.br/users')  
    formulario = servico.criarFormulario()  

### parametro(nome, valor)​

Adiciona um parâmetro ao formulário atual.

    formulario = servico.criarFormulario()  
                        .parametro("nome", "Betha")  

### parametro(Mapa[nome, valor])​

Adiciona um ou mais parâmetros ao formulário atual com base em uma mapa.

    parametros = [nome: "Betha", site: "www.betha.com.br"]  
       
    formulario = servico.criarFormulario()  
                        .parametro(parametros)  

### POST() - POST(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo POST.

    parametros = [nome: "Betha", site: "www.betha.com.br"]  
       
    resposta  = servico.criarFormulario()  
                        .parametro(parametros)  
                        .POST()  

### PUT() - PUT(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo PUT.

    resposta  = servico.criarFormulario().PUT()  

### PATCH() - PATCH(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo PATCH.

    resposta  = servico.criarFormulario().PATCH()  

### METODO(método) - METODO(método, Mapa[marcadores])​

Envia o formulário utilizando como tipo de método um valor personalizado.

    resposta  = servico.criarFormulario().METODO('POST')  

## Formulario Multipart​

Para criar um novo formulário multipart deve-se utilizar as funções **criarFormularioMultipart()** ou **criarFormularioMultipart(tipo de mídia formulário).** Estas funções criam um novo formulário multipart utilizando como tipo de mídia o valor Http.MULTIPART (multipart/form-data). A mídia padrão pode ser alterada informando no parâmetro da função o tipo de mídia desejada.

Formulários multipart geralmente são utilizados para envio de dados e arquivos (upload) em um requisição.

    servico = Http.servico('https://www.betha.com.br/users')  
    formulário = serviço.criarFormularioMultipart()  

### parametro​

**parametro (nome, valor)**

**parametro (nome, valor, tipo de mídia)**

**parametro (Mapa[nome:valor])**

**parametro (Mapa[nome:valor])**

Adiciona um ou mais parâmetros ao formulário atual. Este parâmetro pode conter um tipo de mídia diferente ao do formulário.

### POST() - POST(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo **POST**.

    resposta  = servico.criarFormularioMultipart().POST()  

### PUT() - PUT(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo **PUT**.

    resposta  = servico.criarFormularioMultipart().PUT()  

### PATCH() - PATCH(Mapa[marcadores])​

Envia o formulário utilizando como tipo de método o verbo **PATCH**.

    resposta  = servico.criarFormularioMultipart().PATCH()  

### METODO(método) - METODO(método, Mapa[marcadores])​

Envia o formulário utilizando como tipo de método um valor personalizado.

    resposta  = servico.criarFormularioMultipart().METODO('POST')  

## Resposta​

Uma chamada a um serviço web quando executada tem como retorno uma representação de resposta. Esta resposta pode ser processada/lida de maneiras distintas conforme necessidade.

Existem algumas opções de resposta disponíveis, as quais veremos nas seções a seguir.

### codigo()​

Retorna o código HTTP da resposta.

    resposta = ...  
       
    se (resposta.codigo() == 404) {  
        imprimir 'Servidor não encontrado';  
    }  

### tipoMidia()​

Retorna o tipo de mídia da resposta.

    imprimir 'A resposta é do tipo ' + resposta.tipoMidia()  

### ehJson()​

Indica se o tipo de mídia da resposta é do tipo JSON.

    se (resposta.ehJson()){  
        imprimir 'A resposta é um JSON'  
    }  

#### **sucesso()**​

Indica se o código resposta é considerado como sucesso segundo o padrão HTTP.

    se (resposta.sucesso()){  
        imprimir 'Tudo OK com a chamada HTTP'  
    }  

### tamanho()​

Retorna o tamanho do conteúdo segundo o cabeçalho da resposta (Content-Length) recebido. Caso o valor não seja retornado pelo servidor ou seja inválido retorna -1.

### contemResultado()​

Indica se a requisição retornou algum resultado. Esta verificação é realizada com base no conteudo() e no tamanho() da mensagem e pode ou não estar presente dependendo de cada serviço utilizado.

### ultimaModificacao()​

Retorna a data da última modificação do resultado. Este valor é obtido do resultado da requisição e pode ou não estar presente dependendo de cada serviço utilizado.

### cookie(nome)​

Recupera um cookie da resposta com base no nome. Um cookie pode conter as seguintes informações:

  * **nome():** Nome do cookie
  * **valor():** Valor do cookie
  * **valorCodificado():** Valor do cookie codificado no padrão URL
  * **valorDecodificado():** Valor do cookie no padrão URL decodificado
  * **caminho():** Caminho/Path do cookie
  * **dominio():** Domínio do cookie
  * **versao():** Versão do cookie (número)
  * **comentario():** Comentário do cookie
  * **idadeLimite():** Idade limite/tempo de duração do cookie (maxAge)
  * **expira():** Data de expiração do cookie
  * **ehSeguro():** Indica se é seguro
  * **ehSomenteHttp():** Indica se é somente HTTP

    usaEnterComoTab = resposta.cookie('UsaEnterComoTab')  
    imprimir 'O usuário utiliza enter como TAB: ' + usaEnterComoTab.valor()  

### contemCookie(nome)​

Indica se a resposta contém um cookie com o nome informado no parâmetro.

### cookies()​

Recupera uma lista contendo os cookies retornados na resposta.

    percorrer(resposta.cookies()){  
        imprimir item.nome() + ':' + item.valor()  
    }  

### cabecalho(nome)​

Recupera um cabeçalho(Header) da resposta com base no nome. Um cabeçalho poder conter as seguintes informações:

  * **nome():** Nome do cabeçalho
  * **valores():** Uma lista contendo todos os valores do cabeçalho
  * **valor():** O primeiro valor encontrado do cabeçalho

    imprimir resposta.cabecalho('Authorization').valor() //  

### contemCabecalho(nome)​

Indica se a resposta contém um cabeçalho (Header) com o nome informado no parâmetro.

### cabecalhos()​

Recupera uma lista contendo os cabeçalhos retornados na resposta.

    percorrer(resposta.cabecalhos()){  
        imprimir item.nome() + ':' + item.valor()  
    }  

### imprimir()​

Imprime o conteúdo da resposta no console do editor de scripts.

### conteudo()​

Retorna o conteúdo da resposta no formato de caracteres.

    resposta = Http.servico('https://www.betha.com.br/users').GET()  
    imprimir resposta.conteudo()  

### arquivo([nome])​

Retorna uma fonte de arquivo que contém o conteúdo da resposta. O parâmetro nome é opcional, e deve ser passado quando a origem não retorna o 'filename' no cabeçalho 'Content-Disposition' e for necessário que o arquivo tenha uma extensão específica.

    //Utilizando com a API de arquivos  
    resposta = Http.servico('https://www.betha.com.br/users').GET()  
    texto = Arquivo.ler(resposta.arquivo(), 'txt')  
       
    //Utilizando o retorno como anexo da API de Email  
    resposta = Http.servico('https://www.betha.com.br/users').GET()  
    Email.novo()  
         .de('webservice@betha.com.br')  
         .para('usuarios@betha.com.br')  
         .assunto('Arquivo de resposta do webservice!')  
         .anexarArquivo(resposta.arquivo('resposta.txt'))  
         .enviar()  
      
    // Fazendo o download e envio de um arquivo  
    resposta = Http.servico("http://sample.com/sample.pdf").GET()  
    arquivo = resposta.arquivo("sample.pdf")  
    tipo = resposta.cabecalho("Content-Type").valor()  
    resultado = Http.servico("http://sample.com/file/upload")  
        .criarFormularioMultipart('multipart/form-data')  
        .parametro('file', arquivo, tipo)  
        .POST()  
    imprimir resultado.conteudo()  

### json()​

Retorna o resultado de um serviço JSON como Mapa/Lista de mapa.

    resposta = Http.servico('https://www.betha.com.br/users/5').GET()  
       
    json = resposta.json()  
       
    imprimir json.id  
    imprimir json.nome  

### fechar()​

Fecha a resposta e libera todos os recursos utilizados.

  * Requisição
    * cookie(nome, valor)
    * cookie(nome, valor, caminho, domínio, versão)
    * cookie(Mapanome, valor)
    * cabecalho(nome, valor)
    * cabecalho(nome, lista de valores)
    * cabecalho(Mapanome, valor)
    * certificado(arquivo, senha)
    * certificado(id)
    * chaveIntegracao(identificador)
  * Parâmetros e caminhos
    * parametro(nome, valor)
    * parametro(nome, lista de valores)
    * parametro(Mapanome, valor)
    * caminho(caminho)
    * aceitarTipoMidia(midias)
    * credenciais(usuario, senha)
    * tempoLimite(valor)
    * GET (Mapamarcadores)
    * OPTIONS (Mapamarcadores)
    * HEAD (Mapamarcadores)
    * TRACE (Mapamarcadores)
    * DELETE
    * POST
    * PUT
    * PATCH
    * METODO
  * Formulários
    * formulario
    * parametro(nome, valor)
    * parametro(Mapanome, valor)
    * POST() - POST(Mapamarcadores)
    * PUT() - PUT(Mapamarcadores)
    * PATCH() - PATCH(Mapamarcadores)
    * METODO(método) - METODO(método, Mapamarcadores)
  * Formulario Multipart
    * parametro
    * POST() - POST(Mapamarcadores)
    * PUT() - PUT(Mapamarcadores)
    * PATCH() - PATCH(Mapamarcadores)
    * METODO(método) - METODO(método, Mapamarcadores)
  * Resposta
    * codigo()
    * tipoMidia()
    * ehJson()
    * tamanho()
    * contemResultado()
    * ultimaModificacao()
    * cookie(nome)
    * contemCookie(nome)
    * cookies()
    * cabecalho(nome)
    * contemCabecalho(nome)
    * cabecalhos()
    * imprimir()
    * conteudo()
    * arquivo(nome)
    * json()
    * fechar()