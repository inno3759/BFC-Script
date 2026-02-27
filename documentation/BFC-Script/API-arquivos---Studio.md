---
title: API arquivos | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-arquivos
crawled_at: 2026-02-27 12:59:59
---

Pular para o conteúdo principal

Nessa página

O bfc-script disponibiliza uma API para leitura e escrita de arquivos. As funções são separadas por tipo de arquivo e são invocadas como métodos. Esta sessão abordará o uso de cada função da API de arquivos e os detalhes de cada implementação. Essas funções estarão disponíveis ao usuário final apenas através do CloudJob, e serão absorvidas plenamente conforme a utilização.

## Leitura de arquivos​

A leitura de arquivos está disponível através da função **Arquivo.ler()**. Esta função irá retornar uma implementação específica com operações distintas para realizar a leitura do arquivo conforme tipo. Esta função contém algumas variações para permitir diferentes origens e a passagem de parâmetros para as implementações:

**Arquivo.ler(arquivo ou conteúdo):** Realiza a leitura do arquivo utilizando a implementação padrão para arquivos texto.

**Arquivo.ler(arquivo ou conteúdo, tipo do arquivo):** Realiza a leitura do arquivo utilizando a implementação própria para o tipo de arquivo informado.

**Arquivo.ler(arquivo ou conteúdo, tipo do arquivo, parametros):** Realiza a leitura de arquivo utilizando a implementação própria para o tipo do arquivo informado permitindo a passagem de parâmetros específicos da implementação.

Exemplo de utilização:

    arquivoTxt = Arquivo.ler(origem, 'txt');  
    arquivoCsv = Arquivo.ler('Bob|Esponja', 'csv', [delimitador:'|']);  

### Escrita de arquivos​

A criação de um novo arquivo está disponível através da função **novo**. Esta função irá retornar uma implementação específica com operações distintas para realizar a escrita do arquivo conforme tipo. A função novo contém algumas variações:

**Arquivo.novo(nome do arquivo, tipo do arquivo, parâmetros):** Cria um novo arquivo utilizando a implementação padrão para arquivos texto.

**Parâmetros de escrita:**

_delimitador_ : Caracter para delimitar os valores do arquivo CSV. Por padrão utiliza-se virgula.

_entreAspas_ : Indica se os valores escritos no arquivo deverão estar entre aspas duplas. Utilizar _S_ para Sim e _N_ para Não.

_encoding_ : Determina o encoding a ser usado na criação do arquivo. Por padrão utiliza UTF-8.

### Download​

Por padrão a API de arquivos não disponibiliza para download os arquivos criados pelas implementações. Para que os mesmos sejam incluídos no arquivo zip de resultado da execução de um script através da **Ferramenta de Scripts** é necessário adicionar estes arquivos ao resultado.

    txt = Arquivo.novo('teste.txt', 'txt')  
       
    //Adiciona o arquivo txt no zip do resultado  
    Resultado.arquivo(txt)  
       
    //Personaliza o nome do arquivo no zip do resultado  
    Resultado.arquivo(txt, 'meu_arquivo.txt')  
       
    //Personaliza o nome do arquivo e do diretório no zip do resultado  
    Resultado.arquivo(txt, 'meu_arquivo.txt', 'Arquivos texto')  

### Arquivos Texto (txt)​

#### Leitura​

**Arquivo.ler(nome do arquivo, tipo do arquivo):** Cria um novo arquivo utilizando a implementação própria para o tipo de arquivo informado.

    arquivo = Arquivo.ler(arquivo, 'txt')  

**Arquivo.ler(nome do arquivo, tipo do arquivo, parâmetros):** Cria um novo arquivo utilizando a implementação própria para o tipo de arquivo informado permitindo a passagem de parâmetros específicos da implementação.

    arquivo = Arquivo.ler(arquivo, 'txt', [ encoding: 'iso-8859-1' ]);  

#### lerLinha()​

Realiza a leitura de uma linha do arquivo e retorna o conteúdo lido.

    texto = arquivo.lerLinha()  

#### contemProximaLinha()​

Verificar se o arquivo sendo lido contém uma próxima linha.

    percorrer(enquanto: { arquivo.contemProximaLinha() }) {  
        imprimir arquivo.lerLinha()  
    }  

#### Escrita​

    arquivo = Arquivo.novo('FendaDoBiquine.txt')  

Criando um novo arquivo com um Encoding específico (por padrão utiliza UTF-8):

    arquivo = Arquivo.novo('FendaDoBiquine.txt', 'txt', [ encoding: 'iso-8859-1' ]);  

Criando um novo arquivo com a especificação do caractere de quebra de linha (por padrão será Unix). Método permite selecionar dentre as seguintes opções: Unix, MacOS ou Windows.

    arquivo = Arquivo.novo('FendaDoBiquine-ANSI.txt', 'txt', [encoding: 'windows-1252', lineSeparator: 'Windows']);  

#### escrever(texto)​

Realiza a escrita de um conteúdo no arquivo

    arquivo.escrever('Jonathan Peters')  

#### novaLinha()​

Realiza a escrita de uma quebra de linha no arquivo

    arquivo.escrever('Jonathan Peters')  
    arquivo.novaLinha()  
    arquivo.escrever('Oscar Randall')  

#### Quebra de linha e retorno de carro padrão Windows​

Deve-se usar o escrever("\r\n") em vez do padrão novaLinha()

### Arquivos CSV (csv)​

#### Leitura​

    arquivo = Arquivo.ler(arquivo, 'csv')  

Lendo um arquivo com um Encoding específico (Por padrão utiliza UTF-8):

    texto = arquivo.lerLinha()  

Parâmetros de leitura:

delimitador: Caracter que delimita os valores do arquivo CSV. Por padrão utiliza uma vírgula.

encoding: Determina o encoding a ser usado na leitura do arquivo. Por padrão utiliza UTF-8.

#### lerLinha()​

Realiza a leitura de uma linha do arquivo e retorna o conteúdo lido.

    texto = arquivo.lerLinha()  

#### contemProximaLinha()​

Verificar se o arquivo sendo lido contém uma próxima linha.

    percorrer(enquanto: { arquivo.contemProximaLinha() }) {  
        imprimir arquivo.lerLinha()  
    }  

#### pularLinhas(int linhas)​

Ignora a leitura da quantidade de linhas informado no parâmetro com base na linha atual

    arquivo = Arquivo.ler('Nome,Endereco\nBob,Fenda do biquine', 'csv')  
    arquivo.pularLinhas(1)  
    imprimir arquivo.lerLinha() //Bob,Fenda do biquini  

#### lerProximoValor()​

Realiza a leitura do próximo valor do arquivo considerando o delimitador. Esta função realiza a leitura de todo o arquivo e não somente da linha atual.

    arquivo = Arquivo.ler('Plancton,Mar\nBob,Fenda do Biquine', 'csv')  
    arquivo.lerProximoValor() //Plancton  
    arquivo.lerProximoValor() //Mar  
    arquivo.lerProximoValor() //Bob  

#### contemProximoValor()​

Indica se existe um próximo valor a ser lido no arquivo atual.

    se(arquivo.contemProximoValor()){  
        arquivo.lerProximoValor()  
    }  

#### Escrita​

    arquivo = Arquivo.novo('FendaDoBiquine.csv', 'csv')  

Criando um novo arquivo com um Encoding específico (Por padrão utiliza UTF-8):

    arquivo = Arquivo.novo('FendaDoBiquine.csv', 'csv', [ encoding: 'iso-8859-1' ]);  

**Parâmetros de escrita:**

_delimitador_ : Caracter para delimitar os valores do arquivo CSV. Por padrão utiliza uma virgula.

_entreAspas_ : Indica se os valores escritos no arquivo deverão estar entre aspas duplas. Utilizar _S_ para Sim e _N_ para Não.

_encoding_ : Determina o encoding a ser usado na criação do arquivo. Por padrão utiliza UTF-8.

_lineSeparator_ : Determina a especificação do caractere de quebra de linha (por padrão será Unix). Método permite selecionar dentre as seguintes opções: Unix, MacOS ou Windows.

#### escrever(texto)​

Realiza a escrita de um conteúdo no arquivo utilizando o delimitador parametrizado.

    arquivo.escrever('Jonathan Peters')  

#### novaLinha()​

Realiza a escrita de uma quebra de linha no arquivo.

    arquivo.escrever('Jonathan Peters')  
    arquivo.novaLinha()  
    arquivo.escrever('Oscar Randall')  

### Arquivos XML (xml)​

Os documentos **XML** são lidos e escritos por item/evento. Cada parte do documento é considerado um item e possui características diferentes. No exemplo abaixo podemos afirmar que o documento XML possui 5 itens/eventos:

    <pessoa completo="N">João da Silva</pessoa>  

dos quais:

    Início de documento  
    <pessoa: Início do elemento. Este tipo de item contém um nome(pessoa), pode conter atributos, namespaces etc.  
    João da Silva: Texto do elemento. Este é um tipo de item considerado TEXTO. Diferente de um início de elemento ele não possui um nome e nem atributos.  
    </pessoa> : Fim do elemento  
    Fim de documento  

#### Leitura​

    arquivo = Arquivo.ler(arquivo, 'xml')  

##### tipo()​

Retorna o tipo do item sendo lido. Os valores disponíveis são:

INICIO_DOCUMENTO

FIM_DOCUMENTO

INICIO_ELEMENTO

FIM_ELEMENTO

ATRIBUTO

DTD

CDATA

NAMESPACE

TEXTO

COMENTARIO

ESPACO

DECLARACAO_NOTACAO

DECLARACAO_ENTIDADE

REFERENCIA_ENTIDADE

##### valor()​

Retorna o valor texto do item corrente. Caso o item seja um elemento complexo irá retornar em branco.

Tipos Suportados:

_INICIO _ELEMENTO_, _FIM _ELEMENTO_, _ATRIBUTO_ , _REFERENCIA _ENTIDADE_, _DECLARACAO _ENTIDADE_.

##### contemValor()​

Indica se o item atual contém um valor do tipo texto e se o mesmo é diferente de vazio.

    se(arquivo.contemValor()){  
        imprimir arquivo.valor()  
    }  

##### contemNome()​

Indica se o item atual contém um nome e se o mesmo é diferente de vazio.

##### nome()​

Retorna o nome do item atual. Caso o item não seja suportado irá retornar em branco. Tipos suportados: INICIO_ELEMENTO, FIM_ELEMENTO, ATRIBUTO, REFERENCIA_ENTIDADE, DECLARACAO_ENTIDADE.

##### xml()​

Retorna o item atual no formato XML.

##### namespaces()​

Retorna uma lista contendo os namespaces presentes no item atual. Tipos suportados:

INICIO_ELEMENTO, FIM_ELEMENTO, ATRIBUTO, NAMESPACE

Um Namespace contém as seguintes informações:

prefixo(): Prefixo do namespace

namespace(): Valor do namespace

##### contemNamespace(namespace)​

Indica se o item atual contém um namespace declarado igual ao informado por parâmetro.

##### contemNamespace(namespace, prefixo)​

Indica se o item atual contém um namespace declarado com valor e prefixo igual aos parâmetros.

##### atributos()​

Retorna uma lista contendo os atributos presentes no item atual. Tipos suportados: _INICIO _ELEMENTO_

Um Atributo contem as seguintes informações:

prefixo(): Prefixo do namespace

namespace(): Namespace do atributo

nome(): nome do atributo

valor(): valor do atributo

    percorrer(arquivo.atributos()){  
        imprimir item.nome()  
    }  

##### contemAtributo(nome)​

Indica se o elemento atual contém um atributo com o nome informado no parâmetro. Tipos suportados: _INICIO _ELEMENTO_, _ATRIBUTO_

##### contemAtributo(nome, namespace)​

Indica se o elemento atual contém um atributo com o nome e namespace informado no parâmetro. Tipos suportados: _INICIO _ELEMENTO_, _ATRIBUTO_

##### contemAtributo(nome, namespace, prefixo)​

Indica se o elemento atual contém um atributo com o prefixo, nome e namespace informado no parâmetro. Tipos suportados: _INICIO _ELEMENTO_, _ATRIBUTO_

##### atributo(nome)​

Retorna o [atributo](http://test.betha.com.br/documentacao/bfc-script/2.7.X/index.html#apiArquivosImplementacoesXmlTiposAtributo) do elemento com base no nome informado no parâmetro. Tipos suportados: INICIO_ELEMENTO, ATRIBUTO

##### atributo(nome, namespace)​

Retorna o [atributo](http://test.betha.com.br/documentacao/bfc-script/2.7.X/index.html#apiArquivosImplementacoesXmlTiposAtributo) do elemento com base no namespace e nome informado nos parâmetros. Tipos suportados: INICIO_ELEMENTO, ATRIBUTO

##### atributo(nome, namespace, prefixo)​

Retorna o [atributo](http://test.betha.com.br/documentacao/bfc-script/2.7.X/index.html#apiArquivosImplementacoesXmlTiposAtributo) do elemento com base no prefixo, namespace e nome informado nos parâmetros. Tipos suportados: INICIO_ELEMENTO, ATRIBUTO

##### ehTipoInicioDocumento​

Indica se o tipo do item atual é igual a INICIO_DOCUMENTO

##### ehTipoFimDocumento​

Indica se o tipo do item atual é igual a FIM_DOCUMENTO

##### ehTipoTexto​

Indica se o tipo do item atual é igual a TEXTO

##### ehTipoComentario​

Indica se o tipo do item atual é igual a COMENTARIO

##### ehTipoFimElemento​

Indica se o tipo do item atual é igual a FIM_ELEMENTO

##### ehTipoInicioElemento​

Indica se o tipo do item atual é igual a INICIO_ELEMENTO

##### ehTipoEspaco​

Indica se o tipo do item atual é igual a ESPACO

##### ehTipoCData​

Indica se o tipo do item atual é igual a CDATA

##### ehTipoAtributo​

Indica se o tipo do item atual é igual a ATRIBUTO

##### ehTipoNamespace​

Indica se o tipo do item atual é igual a NAMESPACE

##### contemProximo()​

Indica se o documento atual contém um próximo item a ser lido.

##### tipoProximo()​

Retorna o tipo do próximo item caso a leitura do documento não tenha sido finalizada.

##### proximo()​

Itera no documento passando a leitura para o próximo item. Tem como retorno o tipo do novo item.

    percorrer(enquanto: { xml.contemProximo() }) {  
      xml.proximo()  
        
      imprimir '#Dados do elemento: ' + conta  
      imprimir 'Tipo: ' + xml.tipo()  
                    
      se(xml.contemValor()){  
         imprimir 'Valor: ' + xml.valor()  
      }  
        
      se(xml.contemProximo()){  
        imprimir 'Tipo do proximo elemento: ' + xml.tipoProximo()  
      }  
        
      se(xml.ehTipoInicioElemento()){   
          imprimir 'Nome: ' + xml.nome()     
          percorrer(xml.atributos()){  
            imprimir 'Atributo: ' + item.nome() + '=' + item.valor()  
        }  
      }  
    }  

##### proximaTag()​

Itera no documento passando a leitura para o próxima tag encontrada (INICIO_ELEMENTO ou FIM_ELEMENTO). Tem como retorno o tipo do novo item atual.

##### contemProximoElemento()​

Indica se o documento atual contém um próximo elemento a ser lido.

##### proximoElemento()​

No documento passando a leitura para o próximo elemento (INICIO_ELEMENTO) tem como retorno um valor booleano indicando se a leitura do próximo elemento foi realizada ou se o documento chegou ao fim.

    xml = Arquivo.ler('<root><!-- Nomes dos colaboradores --><nome completo="N" composto="S">Marcos da Silva</nome><nome completo="S">Maria Joana Amaral</nome></root>', 'xml');  
       
    //Leitura baseada em elementos  
    percorrer(enquanto: { xml.proximoElemento() }) {   
       
      imprimir '#Dados do elemento:'  
      imprimir 'Tipo: ' + xml.tipo()  
      imprimir 'Nome: ' + xml.nome()     
      imprimir 'Valor: ' + xml.valor()  
       
      percorrer(xml.atributos()){  
        imprimir 'Atributo: ' + item.nome() + '=' + item.valor()  
      }  
    }  

##### proximoElemento(nome)​

Itera no documento passando a leitura para o próximo elemento cujo nome seja igual ao valor informado no parâmetro. Tem como retorno um valor booleano indicando se a leitura do elemento foi realizada ou se o documento chegou ao fim e o mesmo não foi encontrado.

##### proximoElemento(nome, namespace)​

Itera no documento passando a leitura para o próximo elemento cujo nome e namespace sejam iguais aos valores informados nos parâmetros. Tem como retorno um valor booleano indicando se a leitura do elemento foi realizada ou se o documento chegou ao fim e o mesmo não foi encontrado.

#### Escrita​

    arquivo = Arquivo.novo('FendaDoBiquine.xml', 'xml')  

Parâmetros de escrita:

_encoding_ : Encoding do documento XML. Por padrão utiliza UTF-8.

_indentar_ : Indica se o documento será escrito indentado ou de forma linear. Utilizar _S_ para Sim e _N_ para Não.

##### namespacePadrao(namespace)​

Define o namespace padrão do elemento XML.

##### prefixo(prefixo, uri)​

Define o prefixo de uma URI.

##### escreverAtributo(nome, valor)​

Escreve um novo atributo no elemento atual.

    xml.escreverInicioElemento('pessoa')  
    xml.escreverAtributo('idade', '18')  
    //Saída: <pessoa idade="18">  

##### escreverAtributo(nome, valor, namespace)​

Escreve um novo atributo no elemento atual informando também o namespace.

##### escreverAtributo(nome, valor, namespace, prefixo)​

Escreve um novo atributo no elemento atual informando também o namespace.

##### escreverCData(data)​

Escreve uma área com conteúdo CDATA no documento XML.

##### escreverTexto(texto)​

Escreve texto no item atual.

    xml.escreverInicioElemento('pessoa')  
    xml.escreverTexto('João')  
    xml.escreverFimElemento()  
    //Saída: <pessoa>João</pessoa>  

##### escreverComentario(comentario)​

Escreve um comentário no documento XML.

    <!-- comentário -->  

##### escreverNamespace(namespace)​

Escreve um namespace no elemento atual.

##### escreverNamespace(namespace, prefixo)​

Escreve um namespace com prefixo no elemento atual.

##### escreverDTD(dtd)​

Escreve um DTD no documento XML.

##### escreverElementoVazio(elemento)​

Escreve um elemento vazio no documento XML:

    xml.escreverElementoVazio('vazio')  
    //Saída: <vazio />  

##### escreverElementoVazio(elemento, namespace)​

Escreve um elemento vazio e namespace no documento XML.

##### escreverElementoVazio(elemento, namespace, prefixo)​

Escreve um elemento vazio e namespace com prefixo no documento XML.

##### 10.6.2.15 escreverInicioDocumento()​

Escreve a declaração de um documento XML.

##### escreverInicioDocumento(encoding)​

Escreve a declaração de um documento XML informando o encoding.

##### escreverInicioDocumento(encoding, versao)​

Escreve a declaração de um documento XML informando o encoding e versão.

    xml.escreverInicioDocumento('UTF-8', '1.0')  
    //Saída: <?xml version='1.0' encoding='UTF-8'?>  

##### escreverInicioDocumento(encoding, versao, standalone)​

Escreve a declaração de um documento XML informando o encoding, versão e standalone.

##### escreverFimDocumento()​

Escreve o fim do documento XML.

##### escreverInicioElemento(nome)​

Escreve o início de um elemento no documento XML.

    xml.escreverInicioElemento('pessoa')     
    //Saída: <pessoa>  

##### escreverInicioElemento(nome, namespace)​

Escreve o início de um elemento com namespace no documento XML.

##### escreverInicioElemento(nome, namespace, prefixo)​

Escreve o início de um elemento com namespace e prefixo no documento XML.

##### escreverFimElemento()​

Escreve o fim do elemento atual.

##### nomeElementoAtual()​

Retorna o nome do elemento sendo editado.

    xml.escreverInicioElemento('pessoa')  
    xml.escreverInicioElemento('endereco')  
    imprimir xml.nomeElementoAtual() //Saída: endereco  
    xml.escreverFimElemento()  
    imprimir xml.nomeElementoAtual() //Saída: pessoa  

##### escreverFimElementos()​

Escreve o fim de todos os elementos atualmente abertos.

    xml.escreverInicioElemento('pessoa')  
    xml.escreverInicioElemento('endereco')  
    xml.escreverFimElementos()  
    //Saída: <pessoa><endereco></endereco></pessoa>  

##### escreverFimElementos(elementoParar)​

Escreve o fim de todos os elementos abertos abaixo do elemento informado no parâmetro.

    xml.escreverInicioElemento('pessoa')  
    xml.escreverInicioElemento('endereco')  
    xml.escreverInicioElemento('cidade')  
    xml.escreverInicioElemento('bairro')  
      
    xml.escreverFimElementos('endereco')  
    //Saída: <pessoa><endereco><cidade><bairro></bairro></cidade></endereco>  

##### escreverElementoTexto(nome, valor)​

Escreve um elemento texto no documento XML.

    xml.escreverElementoTexto('nome', 'Maria')  
    //Saída: <nome>Maria</nome>  

##### escreverElementoTexto(nome, valor, namespace)​

Escreve um elemento texto com namespace.

##### 10.6.2.29 escreverElementoTexto(nome, valor, namespace, prefixo)​

Escreve um elemento texto com namespace e prefixo.

##### escrever(xml)​

Escreve um bloco XML no arquivo atual.

    xml.escrever('<nome>José</nome>')  

##### contemElementoAberto()​

Indica se o documento atual contém algum início de elemento sem um fim declarado.

##### escreverReferencia(nome, id, valor)​

Escreve a referência à uma entidade no documento XML.

##### escreverInstrucaoProcessamento(target, conteudo)​

Escreve as instruções de processamento no documento.

##### escreverEspaco(conteudo)​

Escreve um item texto do tipo ESPACO

##### escreverEspacoIgnoravel(conteudo)​

Escreve um item de texto do tipo ESPACO ignorável.

### Arquivos ZIP (zip)​

#### Leitura​

A leitura de arquivos .zip está disponível através da seguinte chamada:

    zip = Arquivo.ler('arquivo.zip', 'zip')  

Onde iterando, é possível navegar entre os arquivos:

    percorrer(zip) {  
          
        //Imprime o nome do arquivo, sem considerar extensão  
        imprimir item.nome;  
       
        imprimir item.extensao;  
          
        //Imprime o nome inteiro do arquivo, incluindo extensão e a sua estrutura de pastas  
        imprimir item.nomeAbsoluto;  
          
        //É possivel identificar se o item em questão representa um diretório  
        imprimir item.ehDiretorio();  
          
        //Recupera uma referência de um arquivo ao conteúdo do zip.  
        arquivo = item.arquivo;  
          
        //Pode ser utilizado outras apis para trabalhar no arquivo descompactado...  
        Arquivo.ler(arquivo, 'txt');  
    }  

**Obs:** Caso durante a geração do zip, seja utilizado um encoding diferente do UTF-8, o valor deve ser informado. Por exemplo:

    zip = Arquivo.ler('arquivo.zip', 'zip', [encoding: 'CP437'])  

#### Escrita​

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  

##### criarDiretorio​

Realiza a criação de um diretório em branco no arquivo zip.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.criarDiretorio('2016')  
    relatorios.zip  
    └─ 2016  

##### adicionar(Arquivo)​

Adiciona um arquivo no diretório raiz do arquivo zip.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar(parametros.arquivo.valor)  

##### adicionar(Arquivo, Nome do arquivo no zip)​

Adiciona um arquivo no diretório raiz do arquivo zip utilizando o nome informado no segundo parâmetro.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar(parametros.arquivo.valor, 'despesas.pdf')  
    relatorios.zip  
    └─ despesas.pdf  

##### adicionar(Arquivo, Nome do arquivo no zip, Diretório)​

Adiciona um arquivo em um determinado diretório do arquivo zip utilizando o nome informado como parâmetro. Caso o diretório não exista no arquivo zip o mesmo será criado.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar(parametros.arquivo.valor, 'despesas.pdf', '2016')  
    relatorios.zip  
    └─ 2016  
        └─ despesas.pdf  

É possível criar subdiretórios utilizando o separador **/** no nome do diretório:

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar(parametros.arquivo.valor, 'despesas.pdf', '2016/Despesas')  
    relatorios.zip  
    └─ 2016  
        └─ Despesas  
            └─ despesas.pdf  

##### adicionar(Lista de arquivos)​

Adiciona um ou mais arquivos no diretório raiz do arquivo zip.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar([parametros.despesas.valor, parametros.receitas.valor])  
    relatorios.zip  
    ├─ Despesas.pdf  
    └─ Receitas.pdf  

##### adicionar(Lista de arquivos, Diretório)​

Adiciona um ou mais arquivos no diretório informado no parâmetro do arquivo zip. Caso o diretório não exista o mesmo será criado.

    arquivo = Arquivo.novo('relatorios.zip', 'zip')  
    arquivo.adicionar([parametros.despesas.valor, parametros.receitas.valor], 'Arquivos')  
    relatorios.zip  
    └─ Arquivos  
       ├─ Despesas.xml  
       └─ Receitas.xml  

##### comentario(Comentário)​

Adiciona um comentário às informações do arquivo zip.

    Arquivo.novo('relatorios.zip', 'zip').comentario('Arquivo contendo os relatórios')  

### Arquivos JSON (json)​

Os documentos JSON são lidos e escritos por item/evento. Cada parte do documento é considerado um item e possui características diferentes. No exemplo abaixo podemos afirmar que o documento JSON possui 4 itens:

    {  
       "nome": "João da Silva"  
    }  

dos quais:

{ : Início do objeto. Este tipo de item pode conter propriedades.

"nome": Nome do campo. Este é um tipo de item considerado TEXTO.

"João da Silva"" : Valor do campo

} Fim de objeto

#### Leitura​

    json = Arquivo.ler('''  
    {  
       "nome": "João da Silva",  
       "telefones": [  
               "4899999999999",  
               "4899999999992"  
       ]  
    }  
    ''', 'json')  
       
    json.proximo() // inicio do objeto  
    json.proximo() // nome do primeiro campo  
      
    nomePessoa = ""  
    telefonesPessoa = []  
       
    percorrer(enquanto: { !json.ehFimObjeto() }) {  
       
       nomeCampo = json.texto()  
       
       se(nomeCampo == "nome"){  
           nomePessoa = json.proximo().texto()  
       }  
       
       se(nomeCampo == "telefones"){  
       
           json.proximo() // inicio do array  
           json.proximo() // primero item do array  
       
           telefones = []  
           percorrer(enquanto: { !json.ehFimMatriz() }) {  
               telefonesPessoa<<json.texto()  
               json.proximo() // proximo item  
           }  
       }  
       
       json.proximo() // avança para o proximo campo  
    }  
       
    pessoa = [nome: nomePessoa, telefones: telefonesPessoa]  

##### proximo()​

Avança a leitura para o próximo item.

##### ehInicioObjeto()​

Retorna um valor booleano indicando se o item atual é o início de um objeto.

##### ehInicioMatriz()​

Retorna um valor booleano indicando se o item atual é o início de uma matriz (array).

##### ehFimObjeto()​

Retorna um valor booleano indicando se o item atual é o fim de um objeto.

##### ehFimMatriz()​

Retorna um valor booleano indicando se o item atual é o fim de uma matriz (array).

##### ehNomeCampo()​

Retorna um valor booleano indicando se o item atual é o nome de um campo.

##### ehTexto()​

Retorna um valor booleano indicando se o item atual é um texto.

##### ehNumero()​

Retorna um valor booleano indicando se o item atual é um número.

##### ehBooleano()​

Retorna um valor booleano indicando se o item atual é um booleano.

##### ehNulo()​

Retorna um valor booleano indicando se o item atual é nulo.

##### texto()​

Retorna o valor do item atual como texto.

##### numero()​

Retorna o valor do item atual como número.

##### booleano()​

Retorna o valor do item atual como booleano.

##### jsonParser()​

Retorna a implementação nativa do parse que está sendo usado, para possibilitar implementações avançadas, clique [aqui](https://fasterxml.github.io/jackson-core/javadoc/2.5/com/fasterxml/jackson/core/JsonParser.html) para mais informações.

### Escrita​

    json = Arquivo.novo('pessoa.json', 'json')  
      
    json.escreverInicioObjeto()  
    json.escreverNomeCampo("nome")  
    json.escreverTexto("João da Silva")  
      
    json.escreverNomeCampo("telefones")  
    json.escreverInicioMatriz()  
      
    json.escreverTexto("4899999999999")  
    json.escreverTexto("4899999999992")  
      
    json.escreverFimMatriz()  
    json.escreverFimObjeto()  

##### escreverInicioMatriz()​

Escreve o início de uma matriz (array)

##### escreverFimMatriz()​

Escreve o fim de uma matriz (array)

##### escreverInicioObjeto()​

Escreve o início de um objeto

##### escreverFimObjeto()​

Escreve o fim de um objeto

##### escreverNomeCampo(nome)​

Escreve o nome do campo

    {  
        "valor": ""  
    }  

##### escreverTexto(texto)​

Escreve um texto

    {  
        "valor": "abc"  
    }  

##### escreverNumero(numero)​

Escreve um número

    {  
        "valor": 123  
    }  

##### escreverBooleano(booleano)​

Escreve um booleano

    {  
        "valor": true  
    }  

##### escreverNulo()​

Escreve o valor nulo

    {  
        "valor": null  
    }  

##### escreverObjeto()​

Escreve um objeto completo

    json.escreverObjeto([nome: "AAA"])  
    {  
        "valor": {  
            "nome": "AAA"  
        }  
    }  

##### escreverCampoTexto(nome,texto)​

Escreve o nome e o valor de campo do tipo texto

##### escreverCampoBooleano(nome,booleano)​

Escreve o nome e o valor de campo do tipo booleano

##### escreverCampoNulo(nome)​

Escreve o nome e o valor de campo nulo

##### escreverCampoNumero(nome,numero)​

Escreve o nome e o valor de campo do tipo numero

##### escreverCampoInicioMatriz(nome)​

Escreve o nome e o início de um campo do tipo matriz (array)

##### escreverCampoInicioObjeto(nome)​

Escreve o nome e o início de um campo do tipo objeto

##### escreverCampoObjeto(nome,objeto)​

Escreve o nome e o valor de um campo do tipo objeto

##### sonGenerator()​

Retorna a implementação nativa do jsonGenerator que está sendo utilizado, para mais informações acesse o [link](https://fasterxml.github.io/jackson-core/javadoc/2.8/com/fasterxml/jackson/core/JsonGenerator.html).

  * Leitura de arquivos
    * Escrita de arquivos
    * Download
    * Arquivos Texto (txt)
    * Arquivos CSV (csv)
    * Arquivos XML (xml)
    * Arquivos ZIP (zip)
    * Arquivos JSON (json)
    * Escrita