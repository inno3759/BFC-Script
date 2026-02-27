---
title: Tipos de Scripts | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/tipos
crawled_at: 2026-02-27 12:58:38
---

Pular para o conteúdo principal

Nessa página

Será abordado neste tópico a construção dos artefatos através dos itens: **Scripts** , **Componentes** , **Críticas** e **Fontes dinâmicas**. O que muda nesses recursos são suas finalidades e recursos exclusivos para cada artefato. Mas antes de mostrarmos as diferenças e particularidades de cada item, veja para que serve cada ícone da página de Editor de scripts. 

Para iniciar pressione o botão **+SCRIPT** , independente do item escolhido nas outras abas sempre será esse botão que iniciará a construção de um artefato.

![tipos](/assets/images/script57-4bb92a172825f2e05215266605e124a3.png)  
---  
  
Informe o título, no campo **Tipo** são apresentados o tipo que será construído o script. Informe os outros campos caso necessário e pressione o botão **SALVAR**.

![tipos](/assets/images/script58-d52b556f2f0c4a4aef1b7c04ac4e488c.png)  
---  
  
Abrirá a tela de **Editor de scripts**.

![tipos](/assets/images/script59-e7b58b01319189cc92061ef4709897e1.png)  
---  
1| Modo Edição| Alterna do modo de visualização para o modo de edição do script.  
---|---|---  
2| Desfazer| Desfazer a última alteração realizada no script.  
3| Refazer| Refaz a última alteração desfeita do script.  
4| Localizar| Faz a busca de um termo dentro do script disponível;  
5| Localizar e Substituir| Sobrepõe um trecho de texto indicado dentro do script por outro a critério do usuário.  
6| Formatar Script| Realiza uma indentação automática do script  
7| Modo tela cheia| Alterna a janela do editor entre o modo tela cheia e o modo padrão  
8| Descartar rascunho| Retorna o script para a última versão publicada do mesmo  
9| Salvar| Salva a código atual como rascunho  
10| Publicar| Realiza a publicação do script atual, gerando uma nova versão da extensão  
11| Executar Rascunho| Executa a versão de rascunho do script  
12| Visualizar Parâmetros| Abre a janela onde é possível realizar a configuração dos parâmetros utilizados na execução do script  
13| Configurações| Abre a janela de configurações, exibindo uma lista de configuração de comportamentos do script  
14| Visualizar Dependências| Abre uma janela exibindo quais extensões devem estar disponíveis para o script atual ser executado devidamente  
15| Alternar para modo claro/escuro| Altera a cor de exibição da janela entre um conjunto de cores claras e escuras  
16| Explorar fontes de dados| Abre a visualização do catálogo de dados, informando quais as fontes de dados disponíveis para uso pelo script atual  
17| Quebra de Linha| Alterna a opção de quebra de linha, permitindo escolher se o script exibirá ou não uma barra de rolagem horizontal  
18| Console| Essa aba permite visualizar quando há erros de sintaxe ou outros quando de tenta executar ou publicar o script;  
19| Execuções| Retém o histórico de execuções realizadas no modo rascunho do script, permitindo acessar o log ou visualizar eventuais erros de execução.  
  
## Scripts​

Vamos começar pelo primeiro item que é **Scripts** , a partir daqui damos início à construção de um artefato. A linguagem utilizada é chamada de BFC-Script, e é através dela que é possível desenvolver os artefatos. 

O ambiente de desenvolvimento de scripts é simples, suas principais características são a facilidade de manipulação, por tratar-se de um compilador com funções e recursos no idioma português e a possibilidade de desenvolvimento por mais de um usuário.

Os scripts são pequenos programas com capacidade de interagir com os dados de cada sistema dos produtos com tecnologia Cloud, sejam para entrada e/ou saída de dados, podendo gerar resultados de saída como arquivos, e-mails, notificações, além de consumo de serviços dos próprios sistemas e de terceiros.

## Componentes​

Um componente nada mais é que um script criado para ser utilizado dentro de outros scripts. Existem situações em que é necessário realizar algo muito repetitivo, para que o usuário desenvolvedor não precise criar uma função dentro de cada script, é feito um componente para ser usado dentro de outros scripts. Esse conjunto de códigos serão importados para dentro de um outro script, sem necessidade de declarar tudo novamente.

A vantagem de realizar um componente é: 

  * Reaproveitamento dos códigos em diversos scripts;
  * Manutenção simplificada, pois será necessário atualizar apenas um artefato.

**Mas como isso funciona?**

Será informado um nome da função, no exemplo abaixo será **arquivoPlanoContabil** , logo, serão inseridos um conjunto de códigos passando pelos parâmetros de execução e por último terá o código **Scripts.exportar** seguido do nome da função que será exportado.

    // função que retorna o arquivo  
      
    arquivoPlanoContabil = { exercicio, entidade, mes, idPessoa,tipoEnvio ->  
      
      //Natureza do Saldo(*)  
     mascaras_mistas = ["237000000","237100000","237110000","237110100","237110200","237110300","237110400","237120000",                    "237120100","237120200","237120300","237120400","237130000","237130100","237130200","237130300",                    "237130400","237140000","237140100","237140200","237140300","237140400","237150000","237150100",                    "237150200","237150300","237150400","237200000","237210000","237210100","237210200","237210300",                   "237210400","237210500","237210600","237220000","237220100","237220200","237220300","237220400",                    "237220500","237220600","237230000","237230100","237230200","237230300","237230400","237230500",                    "237230600","237240000","237240100","237240200","237240300","237240400","237240500","237240600",                "237250000","237250100","237250200","237250300","237250400","237250500","237250600","511200000",                    "521200000","522139900","522190000","522190100","522190200","522190300","522210300","522220000",                   "522220100","522220200","522220300","622210900","622220900","821110100","234000000","234100000",                    "234110000","234200000","234210000","621100000","821000000","821100000","821110000","821110101"];  
     mascaras_devedoras = ["1","4","6","8"];     
     mascaras_credoras  = ["2","3","5","7"];   
     mascaras_orcamentarias = ["5","6"];  
     mascaras_controle = ["7","8"];  
     mascaras_patrimoniais = ["1","2","3","4"];   
        
     imprimir "Iniciando Geração do Arquivo planocontabil.txt " + Datas.hoje().formatar('HH:mm:ss');   
      listaArquivo = [];  
     separador = "|";  
     arquivoTxt  = Arquivo.novo('planocontabil.txt');  
      /*************************************************************************************  
     Identifica a configuração do plano de contas  
     *************************************************************************************/  
     identificaParametro = Dados.contabilidade.v1.parametroEscrituracao.busca(criterio: "entidade.id ="+ entidade + " and exercicio.ano = " + exercicio, campos: "configuracao.id");         
     percorrer(identificaParametro){item2 ->  
       configuracaoPlanoContasId = item2.configuracao.id  
     }  
     /************************************************************************************/  
      se(tipoEnvio =="ABERTURA"){  
       criteriosBusca = "configuracao.id = $configuracaoPlanoContasId";  
     }senao{  
       se(tipoEnvio == "DIARIO"){  
           criteriosBusca = "configuracao.id = $configuracaoPlanoContasId";  
       }senao{ // mensal  
           dataAux = (Datas.data(Integer.valueOf(exercicio),(Integer.valueOf(mes)+1),1) - 1).formatar('yyyy-MM-dd')  
           dataAux2 = Datas.data(Integer.valueOf(exercicio),(Integer.valueOf(mes)),1).formatar('yyyy-MM-dd')  
           criteriosBusca = "configuracao.id = $configuracaoPlanoContasId and dataVigenciaInicial <= $dataAux and dataVigenciaInicial >= $dataAux2 ";  
       }  
     }   
     camposBusca = "mascara,descricao,tipo"  
     ordenacaoBusca = "mascara asc";  
      r = Dados.contabilidade.v1.contaContabil.busca(criterio: criteriosBusca, campos: camposBusca, ordenacao: ordenacaoBusca);  
      percorrer(r){ item ->  
        
       //#Identificador da Pessoa Jurídica junto ao TCE(*)..7  
       idPessoa = idPessoa;  
        
       //Classe,Grupo....19  
       conta = item.mascara  
        
       //Ano de Aplicação do Plano...4  
       ano = exercicio  
        
       //Título ...250  
       titulo = item.descricao  
              
       se(mascaras_mistas.find{it == item.mascara.subTexto(0,9)} != nulo){  
         naturezaSaldo = "X"  
       }senao{  
         se(mascaras_devedoras.find{it == item.mascara.subTexto(0,1)} != nulo) {  
           naturezaSaldo = "D"  
         }senao{  
           se(mascaras_credoras.find{it == item.mascara.subTexto(0,1)} != nulo){  
             naturezaSaldo = "C"  
           }senao{  
             naturezaSaldo = ""  
           }       
         }  
       }  
          
         //Escrituração(*)  
         se (item.tipo == "A") {  
             escrituracao = "S"  
         } senao {  
             escrituracao = "N"  
         }  
        
         //Natureza da Informação(*)       
         se(mascaras_orcamentarias.find{it == item.mascara.subTexto(0,1)} != nulo) {  
           naturezaInfo = "O"  
         }senao{  
           se(mascaras_controle.find{it == item.mascara.subTexto(0,1)} != nulo) {   
              naturezaInfo = "C"  
           }senao{  
             se(mascaras_patrimoniais.find{it == item.mascara.subTexto(0,1)} != nulo) {  
              naturezaInfo = "P"  
             }senao{  
               naturezaInfo = ""  
              }   
            }   
          }  
        
        //Indicador de Superávit Financeiro(*)  
     /*  
     F Financeiro  
     P Patrimonial  
     X Mista/Hibrida  
     O Outros Controles*/  
        //Tipo de Controle da Conta(*)  
     /*tpControleConta dsTipoControleConta  
     O Obrigatória  
     F Facultativa  
     T Obrigatória – TCE/PR  
     P Próprio da Entidade*/  
      
     // Escreve os dados gerados no arquivo txt.  
         
       arquivoTxt.escrever(idPessoa + separador);  
       arquivoTxt.escrever(conta + separador);  
       arquivoTxt.escrever(ano + separador);  
       arquivoTxt.escrever(titulo + separador);  
       arquivoTxt.escrever(naturezaSaldo);      
       arquivoTxt.novaLinha()     
     }  
        
     imprimir "Finalizando Geração do Arquivo planocontabil.txt " + Datas.hoje().formatar('HH:mm:ss');   
     retornar arquivoTxt  
    }  
      
    Scripts.exportar(  
     arquivoPlanoContabil : arquivoPlanoContabil  
    )  

Quando o usuário precisar fazer uso desse componente dentro de um script é essencial informar o nome do componente para que possa trazer todas as informações. 

Na página de informações existe a funcionalidade **Identificador** , neste local é configurado o nome do artefato, e é através dele que será possível importar os dados para dentro de um script. Para cadastrá-lo ou editá-lo clique no identificador e digite um nome, logo pressione o botão **SALVAR**. 

![tipos](/assets/images/script60-42545aeaa11e7afb5c692d443264c828.png)  
---  
  
Um detalhe importante, quando não aparece a informação da cor azul significa que esse artefato foi flexibilizado e está sendo usado por outras entidades tornando-o inviável a edição.

![tipos](/assets/images/script61-ed0424784c2ec6631fd4ab2417fb6bd7.png)  
---  
  
Como foi visto nos parágrafos anteriores os componentes têm suas particularidades, além do que foi apresentado perceba que na tela de informações não é apresentado o histórico de execuções, pois um componente é feito para ser utilizado dentro de outros scripts e não para ser executado sozinho. Na tela que contém as informações do script é apresentado apenas o histórico de atualizações.

![tipos](/assets/images/script62-415cb9303b01703deecaf3532bb653a0.png)  
---  
  
Quando um componente estiver sendo importado para um script ele aparecerá da seguinte maneira: na primeira linha é informado o nome do identificador do componente e na linha de baixo é informado o nome que foi exportado. Ao inserir essas informações dentro de um script já estará usando a função declarada dentro do Componente. 

    MeuComponente = importar("simam_planejamento_programa")  
      
    MeuComponente.arquivoPlanoContabil()  

Através das **Ações disponíveis > Trace execução**, é a forma onde é possível visualizar as informações e principalmente a duração da execução do componente. 

![tipos](/assets/images/script63-eb5d0de2f27c3bb3061a4df6f3ea681c.png)  
---  
  
Clicando em **Trace execução** , aparecem as informações mostradas abaixo.

    {  
     "id" : 3770586,  
     "revisao" : 8740551,  
     "versao" : 1,  
     "titulo" : "Teste",  
     "porIdentificador" : false,  
     "inicio" : "2022-02-24T09:59:14.357",  
     "termino" : "2022-02-24T09:59:14.539",  
     "duracao" : 0.182000000  
    }  

### Definir dependências​

Através da funcionalidade definir dependências a ferramenta de scripts consegue vincular um componente, para isso clique no ícone mostrado na imagem abaixo.

![tipos](/assets/images/script64-8beacdc9fa4e79b01b29d0ae9b05930e.png)  
---  
  
Na sequência, uma nova tela é aberta para que seja cadastrada a dependência, para tanto pressione o botão **+DEPENDÊNCIA**. Preencha com campos solicitados e salve as informações. Sendo assim, o script ficará com uma dependência cadastrada. 

![tipos](/assets/images/script65-583de38df77311c98f3b838bdb991bbf.png)  
---  
  
## Fontes dinâmicas​

Fontes dinâmicas são categorias de scripts que são utilizadas para gerar o conjunto de dados que serão utilizados posteriormente para a geração de um relatório. As fontes dinâmicas devem ser utilizadas em conjunto com a ferramenta de relatórios, porém são criadas e mantidas através da ferramenta de scripts. A mesma fonte dinâmica pode ser consumida por 1 ou mais relatórios diferentes, e para isso, a fonte deve estar disponível na mesma entidade que o relatório desejado.

Para gerar uma nova fonte dinâmica, deve-se acessar a ferramenta de scripts, clicar sobre o botão **+SCRIPT** , na janela que se abrirá, deve-se selecionar a opção **Fonte Dinâmica** no campo **Tipo** , conforme imagem a seguir.

![tipos](/assets/images/script66-4c2196dde643ed0a783d6dda1a671b16.png)  
---  
  
Uma vez que a fonte foi criada, após a primeira publicação da mesma, ela ficará disponível para visualização/edição na aba **Fontes Dinâmicas** da ferramenta de script. 

### Editor de Scripts​

Quando se está criando fontes dinâmicas, a primeira coisa a se fazer é definir a estrutura. Primeiramente é necessário criar uma variável, geralmente é criada com o nome de esquema e definir quais os campos que aparecerão quando gerado um relatório.

Para cada campo criado na fonte de dados, é necessário informar qual o tipo, ou seja, se será um texto, número e etc. Neste exemplo serão usados os tipos numero e caracter e é possível colocar a quantidade de campos desejados, neste caso usaremos apenas três para exemplificar.

**Exemplo:**

     esquema = [  
     id: Esquema.numero,  
     nome: Esquema.caracter,  
     idade: Esquema.numero  
    ]  

Após gerar o esquema da fonte é instanciado o objeto das fontes de dados e abaixo é acrescentado o retorno da fonte, ou seja, por essa expressão será apresentado as informações.

    fonte = Dados.dinamico.v2.novo(esquema)  
    retornar fonte;  

Mas, para que sejam retornados dados é preciso informar o que será mostrado, é necessário inserir as informações porque até aqui foi realizada apenas a estrutura. Para isso, descreva entre as duas linhas mencionadas acima as informações que serão apresentadas no relatório. Perceba que foram inseridas o **id** , **nome** e **idade** em cada linha como definido no esquema apresentado anteriormente.

    esquema = [  
     id: Esquema.numero,  
     nome: Esquema.caracter,  
     idade: Esquema.numero  
    ]  
      
    fonte = Dados.dinamico.v2.novo(esquema)  
      
    fonte.inserirLinha([id: 1, nome: "Artur", idade:29])  
    fonte.inserirLinha([id: 2, nome: "Mateus", idade:35])  
    fonte.inserirLinha([id: 3, nome: "Sabrina", idade:25])  
    fonte.inserirLinha([id: 4, nome: "Fernando", idade:42])  
      
    retornar fonte;  

![tipos](/assets/images/script67-4445bbd3a8346302d22de14504826411.png)  
---  
  
Neste exemplo foi escrito as informações, mas nada impede de fazer buscas em outras fontes de dados localizado no lado direito da tela. Com essas fontes é possível realizar cálculos, tratar dados entre outros, realizando algo mais elaborado.

![tipos](/assets/images/script68-9831d0064a34413f0e8573e0d2ee3d8b.png)  
---  
![tipos](/assets/images/script69-772b0b4a5589d9bc4d8501081dbd413f.png)  
---  
  
Clicando no ícone de executar a ferramenta mostrará se houve algum erro ou se foi publicado corretamente, essa informação é visível abaixo da tela. Neste exemplo não apresentou nenhum erro, ou seja, temos uma fonte de dados válida. 

![tipos](/assets/images/script70-361b67641403d35b073ae37de21e5f96.png)  
---  
  
IMPORTANTE!

É possível simular a execução da fonte dinâmica através do rascunho, sem a necessidade de realizar um vínculo com o relatório. Recomenda-se utilizar a função “imprimir” da ferramenta de scripts para visualizar os dados inseridos na fonte, e iniciar o desenvolvimento do relatório somente após esses dados terem sido validados.

Ao executar um rascunho no editor de Scripts a ferramenta permite que o mesmo seja cancelado através da opção mostrada na imagem abaixo.

![tipos](/assets/images/script220-30d50bd0460881984a498974d9e7bab9.png)  
---  
  
Clicando na opção mencionada aparecerá que o rascunho do script está sendo cancelado.

![tipos](/assets/images/script221-bca8988a0772914d79de838962d8f376.png)  
---  
  
### Criando código da fonte dinâmica​

Segue abaixo um exemplo funcional de fonte dinâmica, contendo o mínimo necessário para se publicar um script executável de fonte dinâmica:

![tipos](data:image/png;base64,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)  
---  
Linhas 1-3| Definição da estrutura de dados que serão passados para o relatório. O conjunto de dados está sendo passado dentro de uma variável tipo Mapa (LinkedHashMap) chamada “estrutura”, e dentro desse mapa existe uma propriedade “id”, que está configurada para o tipo “Esquema.inteiro”, indicando que o jasper deverá receber o campo “id” no formato de dados “Integer” ou “Long”;  
---|---  
Linha 4| Instanciando a fonte de dados propriamente dita através de uma variável chamada “fonte”, qual recebe como parâmetro a variável “estrutura”, indicando quais os campos esperados ao se alimentar os dados na mesma.  
Linha 5| Exemplo de chamada da função “inserirLinha” de nossa fonte, onde a mesma recebe uma linha de dados informando “[id: 1]” que posteriormente será lida pelo relatório.  
Linha 6| Toda finalização de um script de fonte dinâmica deve retornar a fonte que foi criada e alimentada no decorrer do script.  
  
IMPORTANTE!

É possível simular a execução da fonte dinâmica através do rascunho, sem a necessidade de realizar um vínculo com o relatório. Recomenda-se utilizar a função “imprimir” da ferramenta de scripts para visualizar os dados inseridos na fonte, e iniciar o desenvolvimento do relatório somente após esses dados terem sido validados.

### Definindo estrutura de uma fonte dinâmica​

A estrutura dos dados definidos para o esquema da fonte deve ser criada conforme a necessidade do relatório, e fica a cargo do desenvolvedor/analista definir os campos e tipos mais adequados. A nomenclatura dos campos segue as mesmas regras de nomenclatura de variáveis, e os tipos de dados disponíveis, assim como seus equivalentes no TIBCO podem ser conferidos na tabela a seguir:

**Configuração Esquema**| **Configuração Jasper**  
---|---  
Esquema.caracter| java.lang.String  
Esquema.inteiro| java.lang.Long  
Esquema.numero| java.math.BigDecimal  
Esquema.data| java.util.Date  
Esquema.objeto| java.util.Object  
Esquema.lista| java.util.List  
  
Segue exemplo de configuração adequada entre o script e o arquivo do TIBCO, conforme tabela anterior:

![tipos](/assets/images/script72-7c2e3386a43c29fa7ca5c1543dcfc411.png)  
---  
  
Vinculando o relatório com a fonte dinâmica   
Alterando a fonte vinculada ao relatório   
Vinculando os parâmetros do relatório com a fonte

Naturezas de relatórios   
Orquestrando relatórios do tipo fonte dinâmica

Exemplo de script fonte dinâmica 1 (Simples)   
Exemplo de script fonte dinâmica 2 (Intermediários)   
Exemplo de script fonte dinâmica 3 (Complexo)

## Críticas​

As críticas de usuários representam uma validação aplicada a registros específicos. Ao criar uma crítica, é exibida a opção 'Evento(s)' na tela de informações. Somente após a seleção de um evento é que o campo **Natureza** se torna habilitado.

No campo **Evento(s)** , é necessário escolher o tipo de alteração que acionará a crítica. A ferramenta permite a seleção de apenas uma opção ou de todas. A opção **Criação** dispara a crítica ao criar um novo empenho, **Alteração** ao editar um empenho já cadastrado e salvar, e 'Excluir' ao deletar um empenho.

Quando se trata da **Natureza** de uma crítica, ela tem um significado um tanto distinto dos demais. Neste contexto, a **Natureza** implica uma adição de significado adicional. Ao abrir as opções desse campo, são exibidos alguns registros do sistema selecionado. Quando um desses registros é escolhido, o usuário está especificando que a crítica será acionada ao realizar ações relacionadas aos cadastros de empenhos no sistema Contábil.

![tipos](/assets/images/script73-ae218699aae95c614dd519c96ea2efe2.png)  
---  
  
IMPORTANTE!

Cada sistema tem sua própria listagem para selecionar no campo Natureza.

A finalidade da crítica é estabelecer regras específicas que impeçam que um usuário edite determinado empenho, a menos que ele passe nas validações previamente definidas. Essa restrição se aplica a situações em que o usuário não está autorizado a criar o empenho, a menos que atenda a essas validações e assim por diante.

A mensagem descrita abaixo é eficaz somente quando o tipo de script é uma **Crítica de Usuário**. Se for tentado executá-la como uma **Fonte Dinâmica** ou **Script Normal** , ocorrerá um erro.

    Mensagens.erro("Teste")  

Perceba que no editor de scripts do tipo crítica, mesmo sendo publicado o conteúdo não existe o botão de play para simular o modo rascunho, é necessário que seja realizado por dentro dos sistemas.

![tipos](/assets/images/script75-fe37bbc858664504742c9db043946f52.png)  
---  
  
Neste exemplo a crítica está configurada na natureza **Cadastro de empenhos** com evento de **criação** , **alteração** ou **exclusão** , isso significa que ao tentar realizar qualquer um dos eventos a ferramenta não deixará realizar nenhuma ação e mostrará erro cadastrado no script. 

![tipos](/assets/images/script76-2a10349a78f5ea8eb19a04c06a212de8.png)  
---  
  
Na imagem abaixo mostra a mensagem de erro ao tentar salvar uma informação, com isso é perceptível que o script do tipo crítica cadastrado anteriormente funcionou perfeitamente, pois foi mandado dar erro de qualquer maneira ao realizar as ações mencionadas sem validar nada.

![tipos](/assets/images/script77-47e1cacd2c85822e8bb670baff112bef.png)  
---  
  
IMPORTANTE!

Tome muito cuidado ao cadastrar os códigos no script, atente-se para que as regras cadastradas sejam válidas e que façam sentido para a realidade dele, pois ao cadastrar uma regra errada o cliente vai estar impedido de seguir um fluxo normal de trabalho.

É possível alterar os eventos, ou seja, insira ou retire a opção que desejar. Para isso, clique em **Eventos** , logo, uma tela é aberta para que de fato as ações sejam realizadas. A seguir aperte o botão **SALVAR**. 

![tipos](/assets/images/script78-a0aad47425731efe9ceb0d6d4ea4cf3c.png)  
---  
  
Na tela de informações não é apresentado o histórico de execuções, pois um componente é feito para ser utilizado dentro dos sistemas. Na tela que contém as informações do script é apresentado o histórico de atualizações e agendamentos.

![tipos](/assets/images/script79-6913dbb20a808994c7c52f3c17c57d9f.png)  
---  
  
Ao clicar no botão na opção 'Habilitado', uma janela será exibida solicitando a confirmação. 

Para que isso seja viável, é necessário observar algumas questões: 

  * Críticas flexibilizadas poderão ser somente desabilitadas/habilitadas por usuários técnicos.
  * Críticas de propriedade da entidade poderão ser desabilitadas/habilitadas por usuários administradores.

![tipos](/assets/images/script233-d7d11967698d774a49758878d36119b5.png)  
---  
  
Além da mensagem de erro, existem também:

**Aviso:** que não impede uma ação, apenas avisa sobre algo mas não impede de realizar uma ação;

    Mensagens.erro("Teste")   

**Info:** aparece uma janela azul sem dar a impressão que algo aconteceu de errado, é uma informação simples para chamar atenção do cliente mas não é impeditivo caso o usuário execute uma ação;

    Mensagens.info("Teste")  

**Registro.novo:** mostra todos os campos que é possível ler dentro da crítica, com isso mostra uma lista gigante de informações. Para mostrar todos os campos de um cadastro insira como no exemplo abaixo. A variável registro.novo mostra de onde estão vindo todos os campos cadastrados ou modificados na crítica. 

    Mensagens.aviso(registro.novo)  

Para determinar um único campo se faz necessário acrescentar o nome do campo que deseja, assim é possível ver todos os níveis para acessar determinada informação. Observe no exemplo abaixo. 

    Mensagens.aviso(registro.novo.recurso.numero)  

Quando há muitas informações o sistema apresenta um erro, para que isso não aconteça limite a quantidade de texto mostrado na tela. No exemplo exibido abaixo foi limitado para que apareça 500 caracteres, portanto o desenvolvedor do script pode inserir a quantidade que achar necessário. 

    Mensagens.aviso((""registro.novo).esquerda(500)  

  * Scripts
  * Componentes
    * Definir dependências
  * Fontes dinâmicas
    * Editor de Scripts
    * Criando código da fonte dinâmica
    * Definindo estrutura de uma fonte dinâmica
  * Críticas