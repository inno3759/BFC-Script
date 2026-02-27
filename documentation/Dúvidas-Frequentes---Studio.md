---
title: Dúvidas Frequentes | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/faq
crawled_at: 2026-02-27 12:59:00
---

Pular para o conteúdo principal

Nessa página

## Utilização de Mapas​

A primeira coisa é x.getClass, esse parâmetro pode-se ser trabalhado com vários tipos de dados dentro do script, porém esses dados nem sempre são explícitos, pois a linguagem _groovy_ tem uma tipagem dinâmica, onde não é necessário declarar uma variável com tipo **x** e só é possível colocar esse tipo **x** na variável, o desenvolvedor pode criar como booleano, depois uma string, inteiro e assim por diante, é lógico que: o tipo é relevante na hora de fazer uma comparação ou passar algum parâmetro em uma busca, mas dificilmente aparecerá algum erro por estar passando em uma variável, para isso é necessário ter um cenário bem específico. Se mandar executar **x.getClass** é possível pegar o valor de uma variável qualquer e ver qual o tipo de dado dela.

    x = true;  
    imprimir x.getClass();  

![faq](/assets/images/script175-ebda204062818241c4d0f588882ff526.png)  
---  
  
Será testado com os tipos mais utilizados. Observe abaixo:

    x = true;  
    imprimir x.getClass();  
      
    x = 'Silvana'  
    imprimir x.getClass();  
      
    x = 1  
    imprimir x.getClass();  
      
    x = Datas.hoje()  
    imprimir x.getClass();  

![faq](/assets/images/script176-a6d2750ce049bc480d6249c57beb0470.png)  
---  
  
Mas o _groovy_ tem outra categoria de variável chamadas de coleções, tem por exemplo o range, lista e o que é de fato um mapa. Portanto, cada uma dessas variáveis tem suas particularidades e são trabalhadas de maneiras diferentes.

![faq](/assets/images/script177-527ae6edd30e4f50f57374b83bdd94e1.png)  
---  
  
Com **Lista** é possível armazenar uma série de dados dentro de uma variável só, e consegue acessar esses valores através de um índice. No groovy assim que tiver a lista criada, o desenvolvedor consegue inserir itens na lista de modos diferentes. Possivelmente a mais fácil é usando o operador **_Left shift ( <<)_**, logo, é possível colocar o valor que desejar dentro dessa lista é não é obrigatório colocar todos do mesmo tipo de variável, ou seja, pode-se colocar string, inteiro, data, booleano. A partir do momento que alimentar essa lista, é possível trabalhar posteriormente com os dados que tem-se dentro dela. É fácil identificar uma lista pois tem-se colchetes e vários itens dentro dela.

    x = []  
      
    x << "1"  
    x << 23  
    x << true  
      
    imprimir x  

![faq](/assets/images/script178-4251020beba096ae0e31b108e46f6c69.png)  
---  
  
Outra forma de estar atribuindo um valor, é forçando um índice e igualar o índice a tal valor, assim ele também dará o resultado.

    x = []  
      
    x << "1"  
    x << 23  
    x << true  
    x[3] = "Silvana"  
      
    imprimir x  

![faq](/assets/images/script179-dcab5deee72884b58514d39f15d0c8ff.png)  
---  
  
É muito difícil mandar imprimir a lista inteira, o mais comum é querer imprimir apenas um item específico da lista, para isso, passe [] depois do nome da variável e coloque um valor (chamado de índice), ou seja, cada item está em uma posição e essa posição é o índice da lista, lembrando que é sempre começando a contar do 0. No exemplo abaixo será mandado imprimir a posição 2 e como começa a contar do 0 aparecerá a informação que está na terceira posição.

    x = []  
      
    x << "1"  
    x << 23  
    x << true  
    x[3] = "Silvana"  
      
    imprimir x  
      
    imprimir x[2]  

![faq](/assets/images/script180-d98c21402a4f74a4edf577fd65a5ba18.png)  
---  
  
Para trabalhar com todos os valores dela, utilize uma estrutura de repetição "percorrer".

    x = []  
      
    x << "1"  
    x << 23  
    x << true  
    x[3] = "Silvana"  
      
    imprimir x  
      
    imprimir x[2]  
      
    percorrer(x){  
     imprimir item  
    }  

![faq](/assets/images/script181-0d378deddf4678815151dfb12c0bf317.png)  
---  
  
Quando se trabalha com lista, é possível extrair algumas informações propriamente ditas. Tamanho da lista (size), quantidade de itens (IsEmpty).

    x = []  
      
    x << "1"  
    x << 23  
    x << true  
    x[3] = "Silvana"  
      
    imprimir x  
      
    imprimir x[2]  
      
    percorrer(x){  
     imprimir item  
    }  
      
    imprimir x.size()  
    imprimir x.isEmpty()  
    }  

**Mapas** é uma coleção do groovy, que forma uma estrutura de dados podendo ser do tipo de dado inteiro, string, lista e etc. Porém um mapa armazena as informações de um modo diferente, ou seja, ele armazena em forma de pares (chave e valor) e é possível colocar a quantidade de itens que desejar.

    x = [:]  
      
    x = [nome: "Silvana", idade: 40]  
      
    imprimir x  

![faq](/assets/images/script182-1526af85bf059c0814a0daeb545b5a00.png)  
---  
  
Quando se tem os dados organizados da forma de um mapa, é possível visualizar as informações um pouco diferente. Exemplo: quero ver o mapa x e o valor do campo nome, para isso, a ferramenta possibilita realizar a atribuição de níveis para acessar um valor específico dentro do mapa.

    x = [:]  
      
    x = [nome: "Silvana", idade: 40]  
      
    imprimir x.nome  

![faq](/assets/images/script183-b2fb1630e16be133e70cf3e24ea3a5a2.png)  
---  
  
O que torna um mapa interessante é a possibilidade de um índice ser uma string ou qualquer outro tipo, também quando criado o mapa a ferramenta possibilita visualizar apenas uma informação.

    meuMapa = [:]  
      
    meuMapa['Silvana'] = [idade: 40]  
    meuMapa['Maria'] = [idade: 25]  
      
    imprimir meuMapa['Silvana'].idade  

![faq](/assets/images/script184-8415a84fd30dd8e3c41a392742546389.png)  
---  
  
Para visualizar mais de uma informação acrescente o imprimir e os dados do mapa desejado.

    meuMapa = [:]  
      
    meuMapa['Silvana'] = [idade: 40]  
    meuMapa['Maria'] = [idade: 25]  
      
    imprimir meuMapa['Silvana'].idade  
    imprimir meuMapa['Maria'].idade  

![faq](/assets/images/script185-c4ac0ec7ce17db3b88f2b70be41cd01e.png)  
---  
  
## Existe algum problema conhecido, referente a versão do Jaspersoft, para edição dos arquivos .jrxml?​

A questão do Jaspersoft é importantíssima, pois a versão recomendada é 6.3, é um pouco mais antiga mas funciona bem e não dá problema na utilização. Quando usado uma versão mais atual, dará um erro de compatibilidade, ou seja, informa que um jrxml está com uma tag inválida, isso acontece na hora de salvar o relatório na ferramenta de Relatórios. Caso tenha instalado uma versão mais recente em seu computador não há a necessidade de desinstalar, a ferramenta consegue alterar a versão do arquivo como sendo uma versão a ser reconhecida na ferramenta de Relatórios. Para isso acesse o **Window > Preferences**, digite no campo de busca **Compatibility** e escolha uma versão 6.3, assim ele gerará arquivos compatíveis com a ferramenta de Relatórios.

![faq](/assets/images/script186-6258de4a8f522ce3d270b1996fe45623.png)  
---  
  
## Quando saber se devo ou não usar um componente?​

A **vantagem** é o reaproveitamento de códigos, imagina um código que é utilizado com frequência (exemplo: CPF), é possível componentizar e reaproveitar em outras extensões. Outra vantagem é alterar informações ou até mesmo corrigir um bug de apenas um componente e automaticamente todos os artefatos que o utilizam são atualizados. 

A **desvantagem** de usar um componente é ter que manter uma extensão a mais, ou seja, quando compartilhado um script tem que garantir que ele está sendo compartilhando componente, porque se for gerado uma chave de um scripts por exemplo, e importar apenas o script e não o componente em qualquer base, não será possível executar o script, vai apresentar um erro por faltar um componente com identificador X.

## Em caso de descontinuidade de uma fonte, ao exportar o relatório de um cliente para outro, as fontes funcionarão corretamente, principalmente se estiverem sendo usadas em uma lista dinâmica com parâmetros?​

Se isso acontecer a fonte vai dar erro e o relatório não irá funcionar. Essa questão de descontinuidade de uma fonte não recorrente e quando isso acontece é avisado com bastante antecedência para que todos possam realizar as ações necessárias para que tudo continue funcionando corretamente.

## Como construir um script?​

Não existe uma forma exata de como começar a construção de um script que tenha que ser seguida, mas separamos algumas dicas:

  1. Planeje o _layout_ que será apresentado no relatório, fazendo isso ajuda a entender quais as informações serão necessárias mostrar;
  2. Tenha em mente quais os parâmetros de missão do artefato tanto para relatório quanto para script; 
  3. Só agora comece a codificar;
  4. Deixe as regras concentrada em um único lugar (script), facilitando assim imprimir os valores no relatório, facilitando a edição, manuseio e a customização em um único só lugar; 
  5. Leve em consideração a quantidade de fontes a ser utilizada para optar entre fonte padrão ou dinâmica a ser utilizada. Se for utilizada mais que 5 buscas, realizar tratamentos de dados grande ou aplicar muitas regras opte pela fonte dinâmica, mas quando o relatório for mais simples como imprimir uma listagem opte pela fonte padrão;
  6. Realize quantos testes achar necessários, até ficar seguro que tudo está funcionando corretamente;
  7. Existe muita reutilização de fontes dinâmicas em contextos diferentes e os dados que são utilizados são bem diferentes e distintos, quando feito um reparo carrega muito, portanto, verifique se cada fonte dinâmica seja específica para cada contexto facilitando **muito** na performance de um script. 

## Qual a forma mais ágil para testar um script desenvolvido?​

Utilize bases de testes disponíveis com alguns dados, porém sabemos que nem todas as bases tem um cenário perfeito com todas as informações disponíveis para realizar os testes de forma eficaz. Portanto, quando realizado um teste na base de algum cliente é extremamente necessário tomar uma série de cuidados, principalmente quando precisa realizar alterações de dados. Deve-se avaliar até onde vale a pena realizar esses testes na base do cliente, porém a forma mais ágil é setar eles dentro das variáveis que está pegando os valores dos parametros.exercicio, parametros.valor, coloca-se um valor fixo apenas para fazer o teste e ao término da validação é a hora da disponibilização de fato. Mas dependendo do script levará um tempo considerável para testar e disponibilizar. 

**Dicas para validação:**

  1. Valide todos os parâmetros independente da quantidade que tiver, evitando chamados; 
  2. Teste os parâmetros mesmo não setados como obrigatórios, imprima com 1, 2, 3 ou mais valores, tentando abranger todas possibilidades, porque o script quando codificado apresenta 3 comportamentos diferentes: filtrar múltiplas opções, filtrar nulo ou filtrar apenas uma. 

## Qual a melhor prática para desenvolver uma nova versão de uma extensão que já tem versão em uso no cliente?​

Se o usuário desenvolvedor precisa realizar uma customização em um determinado relatório e ele já foi orquestrado, não há possibilidade de editar nele, pois o botão fica desabilitado. É necessário duplicar o artefato (pode ser na base do solicitante), realizar todas as alterações necessárias, testar e quando estiver tudo funcionando corretamente entre na base do artefato original, atualize os dados e realize a nova orquestração para o cliente utilizar. Não esqueça de excluir o artefato duplicado para não ficar "sujeira" e não ficar nada duplicado gerando confusão nas alterações futuras na base do cliente. 

Existe uma exceção, não pode ficar desenvolvendo críticas e testando esse tipo de artefato diretamente na base do cliente, isso pode invalidar o fluxo. Segue abaixo como realizar uma validação de uma crítica sem interferir no fluxo dos clientes de uma entidade.

  1. Crie um novo script na base do cliente;
  2. Executando o comando "Imprimir usuario.id" o artefato apresentará o usuário logado no sistema, realizando isso o desenvolvedor consegue forçar um controle de execução apenas para ele mesmo.

![faq](/assets/images/script187-5fb43caba3b8f06142f5563ecceb0275.png)  
---  
  
  3. Feito isso, o desenvolvedor pode encapsular todo o código da crítica dentro do if + usuario.id em uma crítica na base do cliente, ou seja, assim é possível testar com os dados cadastrados na base sem mexer no fluxo das pessoas que estão trabalhando nessa entidade. Ao forçar a regra da crítica e ao publicar, essa crítica vai funcionar única e exclusivamente para o usuário logado dentro do cadastro. 

![faq](/assets/images/script174-df3ac43121571d6b62682c2030f17361.png)  
---  
  
  * Utilização de Mapas
  * Existe algum problema conhecido, referente a versão do Jaspersoft, para edição dos arquivos .jrxml?
  * Quando saber se devo ou não usar um componente?
  * Em caso de descontinuidade de uma fonte, ao exportar o relatório de um cliente para outro, as fontes funcionarão corretamente, principalmente se estiverem sendo usadas em uma lista dinâmica com parâmetros?
  * Como construir um script?
  * Qual a forma mais ágil para testar um script desenvolvido?
  * Qual a melhor prática para desenvolver uma nova versão de uma extensão que já tem versão em uso no cliente?