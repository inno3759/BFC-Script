---
title: Parâmetros de Execução | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/parametros-execucao
crawled_at: 2026-02-27 12:58:42
---

Pular para o conteúdo principal

Nessa página

A ferramenta permite que parâmetros sejam adicionados para que sejam informados dados para execução dos relatórios. Muitos desenvolvedores se confundem com parâmetros e filtros, a diferença é:

**Filtro:** onde pega-se o parâmetro ou um dado fixo e configurar para buscar determinadas informações da fonte;

**Parâmetro:** utilizado para passar os dados para o filtro como também passar internamente uma configuração pessoal de organização ou afins.

Para adicionar um parâmetro, pressione o botão **+PARÂMETROS**.

![Parâmetros de Execução](/assets/images/script80-2ef4b62005cb19d46bbab869f5e8bfe7.png)  
---  
  
O nome deve seguir as regras de nomenclatura de variáveis da linguagem [BFCScript](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/apresentacao-bfc-script), sendo que não podem existir parâmetros com o mesmo nome.

Insira uma descrição e se necessário uma dica de preenchimento (auxilia no preenchimento do campo), essa informação é exibida ao passar o mouse em cima do campo.

![Parâmetros de Execução](/assets/images/script81-4b00aecd5448d70e422b6ba7d9c8b7ad.png)  
---  
  
Logo abaixo há o campo **Tipo do dado** , que é referente a um padrão do parâmetro. Aqui, a ferramenta dispõe de nove opções, acompanhe abaixo os detalhes de cada uma delas: 

![Parâmetros de Execução](/assets/images/script82-7c8d5a54a6b40c4a196726792e44d2fc.png)  
---  
  
## Tipos de Parâmetros​

Consulte o material **API arquivos** onde é detalhado como manipular o resultado/leitura dos parâmetros, para isso clique [aqui](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-arquivos).

### Arquivo​

Realiza upload de um arquivo e exibe no relatório o layout de um arquivo com extensão TXT, CSV e XML; 

![Parâmetros de Execução](/assets/images/script83-5ec4e1c1cfce955071caac5130a99213.png)  
---  
  
### Caracter​

Permite informar um dado do tipo texto, ou seja, é possível digitar uma frase, números, símbolos.

![Parâmetros de Execução](/assets/images/script84-5ba1933a36de396e687b59896d3c5d32.png)  
---  
  
### Data​

Define um valor padrão como uma data específica, exemplo: 30/09/2021 ou variáveis: primeiro dia do mês; 

    parametros.data.valor.format("yyyy-MM-dd")  

![Parâmetros de Execução](/assets/images/script85-a3aee28f3e90a409353f7e1ca7adac6f.png)  
---  
  
### Data e hora​

Semelhante a opção **Data** , porém exibe a hora quando selecionado a opção data específica;

![Parâmetros de Execução](/assets/images/script86-9c5f3720f6ed7ae947623df938cd19ac.png)  
---  
  
### Inteiro​

Permite informar um número do tipo inteiro (sem casas decimais);

![Parâmetros de Execução](/assets/images/script87-3fd1d45520bac152f1bd727baea57ca8.png)  
---  
  
### Lista múltipla​

Apresenta um campo chamado **Opção da lista** contendo as seguintes opções: **Dinâmica** (listagem onde a origem entrega dados a serem alimentados em uma lista dinâmica e exibe informações das fontes de dados proveniente dos sistemas. Permitindo configurá-la e selecioná-las várias opções para que as informações desejadas sejam exibidas no relatório), **Estática** (permite selecionar várias opções) e **Indefinida**(fica a critério do usuário preencher com informações que desejar, formando valores indefinidos); 

  * **Opção da lista - Dinâmica**

![Parâmetros de Execução](/assets/images/script88-55d7ace8a47e9a7a19501713270a41fe.png)  
---  
  
  * **Opção da lista - Estática**

![Parâmetros de Execução](/assets/images/script89-292cd3dfe3c2b1b5fc022074631016ef.png)  
---  
  
  * **Opção da lista - Indefinida**

![Parâmetros de Execução](/assets/images/script90-66cca81c7bf1511532247c300dfc887b.png)  
---  
  
### Lista simples​

Possui as mesmas opções da listas **Dinâmica** , a única diferença é que permite selecionar apenas uma opção e **Estática** permite selecionar apenas um item criado pelo usuário desenvolvedor; 

  * **Opção da lista - Dinâmica**

![Parâmetros de Execução](/assets/images/script91-07437dbec57427c0a50fbc13b39c6607.png)  
---  
  
  * **Opção da lista - Estática**

![Parâmetros de Execução](/assets/images/script92-db5d02f0a6ff2f9a01aec653283b007e.png)  
---  
  
### Mês/Ano​

Define um valor padrão como mês/ano específico (09/2021) ou variáveis (próximo mês); 

![Parâmetros de Execução](/assets/images/script93-79d327cf863c2a542933e420a1760712.png)  
---  
  
### Valor​

Exibe um número fracionário de casas decimais.

![Parâmetros de Execução](/assets/images/script94-f5930fccfd3f1a3bb8eaff24408a64bc.png)  
---  
  
É possível definir se o parâmetro será de preenchimento obrigatório ou opcional, também inserir mais de um parâmetro para o mesmo script. 

Pode-se especificar um valor padrão, ou seja, ao abrir a tela já vem com o campo do parâmetro cadastrado preenchido quando os campos **Visível e Habilitado** estiverem marcados como **SIM**. 

Preencha as informações do formulário e ao final, clique em **SALVAR** ,**SALVAR NOVO** ou**CANCELAR**.

![Parâmetros de Execução](/assets/images/script95-a94c2ce9972975eb69190099751c0cff.png)  
---  
  
Todos os itens criados ficam na tela de definição de parâmetros, podendo editá-los ou excluí-los.

![Parâmetros de Execução](/assets/images/script96-0360a8ad18b92af92d73181ef76e6384.png)  
---  
  
### Senha​

É possível criar parâmetros com o tipo “Senha”, das quais possuem um comportamento semelhante aos parâmetros do tipo caracter, porém os mesmos não tem seu valor armazenado após a execução, ou exibidos no detalhamento de execuções após a finalização.

![Parâmetros de Execução](/assets/images/script224-d5e0ab29fb5f99efe77ecb3d88172b0e.png)  
---  
![Parâmetros de Execução](/assets/images/script225-22cc9053ceaa8d3c6ae761087ca7d4e0.png)  
---  
  
Detalhamentos sobre esse tipo de parâmetro:

  * Não é possível atribuir um valor padrão para parâmetros do tipo “Senha”;
  * O valor do parâmetro não é preenchido na reexecução;
  * Parâmetros do tipo senha não são convertidos para marcadores automaticamente;
  * Parâmetros do tipo senha não são exibidos na consulta de execuções.

ATENÇÃO! 

Em tempo de execução, esse tipo de parâmetro se comporta de forma idêntica a parâmetros do tipo **caracter** , de forma que o desenvolvedor tem liberdade na utilização do mesmo, porém, sugere-se atenção na hora de exportar o valor do parâmetro no log ou impressão do relatório, a fim de evitar o vazamento de informações sensíveis.

## Definindo layout dos parâmetros nos relatórios​

Ao cadastrar os parâmetros é possível definir o layout de forma avançada, ou seja, melhorando o preenchimento no momento da execução, possibilitando também a estilização como posição e tamanho dos parâmetros. Após a criação dos parâmetros, acesse **Editar > Parâmetros > Definir layout**, logo, realize as mudanças desejadas. Quando o usuário realizar a execução do relatório no **Gerenciador de Relatórios** ou no **F4** aparecerá todos os parâmetros com o _layout_ previamente configurados desde que as alterações estejam publicadas. 

![Parâmetros de Execução](/assets/images/gifparametros-3cc73ae7267a448c3136d8db71ea7158.gif)  
---  
  
É permitido ainda definir o tamanho da janela dos parâmetros. As opções são: **Padrão** , **Média** ou **Grande**.

![Parâmetros de Execução](/assets/images/script196-d5f36525be36fb5b54004297c837b5f8.png)  
---  
  
Consequentemente, a configuração estabelecida ficará disponível no **Assistente F4**.

  * **Padrão**

![Parâmetros de Execução](/assets/images/script197-a1cebe543991c7c3549c3a27142ca10e.png)  
---  
  
  * **Média**

![Parâmetros de Execução](/assets/images/script198-fb608605218c8e9450f8d819613a8de8.png)  
---  
  
  * **Grande**

![Parâmetros de Execução](/assets/images/script199-0cd7e0f540265c88b43e54b61ed3fe0f.png)  
---  
  
## Visualizando marcadores​

É possível definir um parâmetro como um marcador, assim o valor utilizado neste parâmetro será utilizado para identificar as execuções realizadas em um Script na tela de execuções da ferramenta. Ao clicar em uma extensão visualiza-se os marcadores na tela da listagem das execuções dos artefatos, porém só aparecem quando preenchidos na hora da execução e que sejam habilitados na tela de parâmetros.

![Parâmetros de Execução](/assets/images/script97-97127e95a0e0e8bd58b1b23b331cdde7.png)  
---  
  
Para voltar a listagem normal, ou seja, que **não** apareçam os marcadores, clique no ícone representado por um olho e desabilite a opção **Marcadores**. Por padrão este item vem desabilitado e essa configuração não é resetada, ou seja, quando fechada a tela e retornar, a ferramenta mantém a configuração anterior.

![Parâmetros de Execução](/assets/images/script98-d3ab6f59299ebef4ef71cb726f2f999a.png)  
---  
  
Para que os marcadores sejam apresentados como mencionado anteriormente, é necessário habilitar a opção **Utilizar como marcador** onde pode-se adicionar e/ou editar um parâmetro. Porém, quando nenhum marcador for selecionado, os três primeiros parâmetros serão utilizados como marcadores. Observa-se, ainda, que parâmetros do tipo “arquivo” não suportam marcadores. 

![Parâmetros de Execução](/assets/images/script99-d79d59630d2e7720041b4e83e6fd6289.png)  
---  
  
Habilitando o parâmetro mostrado no parágrafo anterior, na tela de definição dos parâmetros é apresentado um ícone em forma de lista antes do nome. 

![Parâmetros de Execução](/assets/images/script100-879d2d027171ca8dbe0fe83fb574528d.png)  
---  
  
## Recursos importantes da lista Dinâmica​

Os parâmetros dinâmicos consistem nos parâmetros do tipo **Lista simples** ou **Lista múltipla** que filtram informações de acordo com uma fonte de dados pré-definidos, a única diferença entre esses tipos é que: a simples aceita apenas uma opção e a múltipla permite selecionar várias, como mostrado anteriormente.

A listagem dinâmica é uma origem que entrega dados a serem alimentados dinamicamente, as informações apresentadas vêm dos catálogos de dados fornecidos pelos sistemas. 

É necessário selecionar a categoria da fonte para que as fontes sejam exibidas. 

![Parâmetros de Execução](/assets/images/script101-f9a5642571f3b5463992fa16bb3453a0.png)  
---  
  
A fonte de dados é uma API e possui diversos campos/atributos como uma tabela no banco de dados, portanto, ao selecionar uma API para ser a origem da listagem é necessário fornecer algumas informações, pois quando selecionado o valor da listagem essa seleção retorna um dado, com essa informação será enviado para a execução do relatório.

O campo **Valor** será considerado quando selecionar o valor da listagem, para isso, se faz necessário definir o atributo da fonte de dados que representará o valor para filtrar o relatório. 

No campo **Descrição** deve ser informado o que aparecerá como descrição na listagem. Abaixo desse campo a ferramenta traz alguns dados, isso acontece porque nem tudo que se pode visualizar poderá ser filtrado. Neste item é possível inserir mais de uma informação. 

No campo **Filtro** a ferramenta sugere o que pode ser filtrado, deixa inserir mais de uma informação e será apresentado apenas o que foi informado. 

![Parâmetros de Execução](/assets/images/script102-1590823488b81f034f45ca90ee860c4d.png)  
---  
  
Veja abaixo como aparecem as informações inseridas anteriormente.

![Parâmetros de Execução](/assets/images/script103-91fa9c159abf82bf4382f12bc230580c.png)  
---  
  
Quando inserido o nome do banco irá trazer a informação, pois foi especificado para filtrar esse parâmetro.

![Parâmetros de Execução](/assets/images/script104-b2fa4ed5bb10f69d00b7e3bb95594f73.png)  
---  
  
Na mesma linha da **Descrição** tem o nível, esse recurso mostra a quantidade de níveis da fonte de dados para compor a descrição, ou seja, as fontes tem uma espécie de hierarquia. Exemplo: dentro da fonte agências bancárias tem objetos, na expressão **bairro.municipio.codigoibge** possui 3 níveis, porém podem ter expressões contendo vários níveis. 

A ferramenta suporta dados de grande complexidade, porém é o usuário desenvolvedor que informa a quantidade de níveis através dos símbolos de **-** e **+** que serão exibidos neste campo. Dessa forma a ferramenta vai adentrar na hierarquia dos dados dessa fonte. 

![Parâmetros de Execução](/assets/images/script105-8a70324bff01fa53903f23801b94515b.png)  
---  
  
Na tela **Definindo parâmetros** encontra-se a ordenação das informações disponíveis através dos pontos do lado esquerdo, apenas arraste para a posição que desejar. 

![Parâmetros de Execução](/assets/images/script106-677feae215d3623cbbe5b99559296d61.png)  
---  
  
Nessa tela estão presentes também os recursos de edição e exclusão dos parâmetros criados. Para dar início à ação desejada, pressione em um dos dois ícones mostrados na imagem abaixo.

![Parâmetros de Execução](/assets/images/script107-ee1f8d6ae9680d0d60c0e916741739ff.png)  
---  
  
Os campos serão visualizados na **PRÉ-VISUALIZAÇÃO** a partir da ordem estabelecida na tela de definição de parâmetros.

![Parâmetros de Execução](/assets/images/script108-ba7ac04e271fe06e8342e480b4251039.png)  
---  
  
### Ordenação​

Definir a ordem das colunas através do botão **ORDENAÇÃO**.

![Parâmetros de Execução](/assets/images/script109-e34344c9d7fe28841f2090676428cbfa.png)  
---  
  
Pressionando o botão mencionado anteriormente, uma tela é aberta para que sejam definidas as colunas. Ao marcar os itens, elas aparecem no lado direito em forma de colunas facilitando a visualização. Na coluna **Classificação** o usuário pode optar por apresentar as informações de forma crescente ou decrescente. 

![Parâmetros de Execução](/assets/images/script110-c78cb1702610a4b1396046d75502c311.png)  
---  
  
### Filtros avançados​

Filtros avançados é uma ferramenta que permite com que o usuário filtre informações de acordo com critérios. Para realizar esses filtros é necessário clicar no botão **FILTROS AVANÇADOS**.

![Parâmetros de Execução](/assets/images/script111-daa36be822d19b368dc5b407e10e737d.png)  
---  
  
Uma nova janela é aberta onde é possível editar (parte central da tela) os filtros de maneira codificada através do BFC-Script, possibilitando um nível mais avançado de filtragem de dados. No canto superior direito exibe os critérios através da expressão **Como utilizar**. 

![Parâmetros de Execução](/assets/images/script112-1e617ee08c713325d778a642d39d21b6.png)  
---  
  
Clicando em **Veja aqui como utilizar** , a ferramenta possibilita customizar e detalhar os filtros.

![Parâmetros de Execução](/assets/images/script113-ca0e257ca22a000d0d4140dc23acf238.png)  
---  
  
### Acesso ao contexto da aplicação nos filtros avançados​

Para melhorar a usabilidade das extensões evitando que o usuário precise informar um valor que já está no contexto da aplicação, foi disponibilizado o acesso programático a essas informações.

Nos filtros avançados de parâmetros os valores do contexto da aplicação estão disponíveis no objeto **contextoAplicacao**.

Exemplo utilizando o contexto do sistema educação:

![Parâmetros de Execução](/assets/images/script189-628145e3b13b91ab0badaacb11d880ea.png)  
---  
![Parâmetros de Execução](/assets/images/script190-52e05f7d352dade0f2da395b7e2556e9.png)  
---  
  
No gerenciador de scripts é possível acessar os valores do contexto da aplicação no seguinte objeto **contextoExecucao.contextoAplicacao**.

As informações só estarão disponíveis quando a extensão for executada por dentro do sistema que possui o contexto de aplicação, caso for executada através de outro meio, por exemplo, via gerenciador de scripts/relatórios, o objeto que contém a informação estará vazia.

Exemplo utilizando o contexto do sistema educação:

![Parâmetros de Execução](/assets/images/script191-21590ab8fdc9634331706120f8549ac0.png)  
---  
![Parâmetros de Execução](/assets/images/script192-b324f4d0fb98f90f75018767c460f896.png)  
---  
  
## Interagindo com parâmetros no script​

Para interagir com os parâmetros nos scripts, comece digitando o nome de uma variável, a seguir é necessário inserir um objeto chamado "parametros", depois inclua no nome declarado no parâmetro.

**Tipo de Parâmetro**| **Nome Variável**| **Acessando Valor(es)**  
---|---|---  
Arquivo| meuArquivo| parametros.meuArquivo.valor  
Caracter| meuCaracter| parametros.meuCaracter.valor  
Data| minhaData| parametros.minhaData.valor  
Data e Hora| minhaDataHora| parametros.meuValor.valor  
Inteiro| meuInt| parametros.meuInt.valor  
Lista Múltipla| minhaListaMult| parametros.minhaListaMult.**selecionados**.valor  
Lista Simples| minhaListaSim| parametros.minhaListaSim.**selecionado**.valor  
MesAno| meuMesAno| parametros.meuMesAno.valor  
Valor| meuValor| parametros.meuValor.valor  
  
  * Tipos de Parâmetros
    * Arquivo
    * Caracter
    * Data
    * Data e hora
    * Inteiro
    * Lista múltipla
    * Lista simples
    * Mês/Ano
    * Valor
    * Senha
  * Definindo layout dos parâmetros nos relatórios
  * Visualizando marcadores
  * Recursos importantes da lista Dinâmica
    * Ordenação
    * Filtros avançados
    * Acesso ao contexto da aplicação nos filtros avançados
  * Interagindo com parâmetros no script