---
title: API de fonte de dados | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-fonte-dados
crawled_at: 2026-02-27 13:00:24
---

Pular para o conteúdo principal

Nessa página

A linguagem disponibiliza uma série de funções para das fontes de dados registradas pelas aplicações no catálogo de dados da Betha Sistemas. Essas funções estarão disponíveis ao usuário final apenas através da **Ferramenta de Scripts** e serão absorvidas plenamente conforme a utilização.

Uma fonte de dados é composta por um **ativo** , um **tema** , e as **operações** propriamente ditas.

A API de script utiliza a seguinte estrutura para representar estes componentes:

**Dados.ativo.tema.versao.operacao()**

## Ativo​

Um **ativo** pode ser considerado como a fonte/origem das informações. É nele que as operações de busca e manipulação de dados serão executadas.

## Tema​

Um **tema** pertence a um ativo e representa um grupo de informação em comum. Exemplos de possíveis temas do ativo folha seriam funcionários, feriados, etc.

## Operações​

Operações são funções de busca/manipulação de dados disponibilizadas através de um tema. Considerando o exemplo do tema funcionário do ativo, folha, teríamos como possíveis operações a criação de um funcionário, busca dos registros, cálculo da folha, etc.

As operações básicas de um tema são:

  * **Operação de busca**
  * **Operação de criação**
  * **Operação de atualização**
  * **Operação de exclusão**

A disponibilidade de cada operação depende do ativo e tema utilizado.

### Operação de busca​

A operação de busca padrão conta com os seguintes parâmetros:

  * **criterio:** Parâmetro utilizado para filtrar os dados da busca.

    tema.busca(criterio:"nome = 'Maria' and idade > 18")  

  * **ordernacao:** Parâmetro utilizado para informar a ordem do resultado da busca. O valor deste parâmetro deve ser preenchido com o nome dos campos separados por vírgula seguido da orientação (asc - Ascendente, desc - Descendente).

    tema.busca(ordenacao:"nome,sobrenome asc, cidade desc")  

  * **campos** : Parâmetro utilizado para informar quais campos do registro devem estar no resultado da busca.

    tema.busca(campos:"nome, sobrenome, cidade(nome, uf)")  

**parâmetros:** Utilizado para informar os valores dos parâmetros da operação. O nome dos parâmetros pode variar conforme ativo, tema e operação utilizada.

    ativo.telefones.busca(parametros:[codigoFuncionario:15]))  
    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    percorrer(dadosFuncionarios.busca(ordenacao:"rg desc", campos:"nome, rg, id, dataAdmissao, dataNascimento")){   
        imprimir "##Funcionario"   
        imprimir item.dataNascimento  
        imprimir item  
          
        imprimir "##Telefones: "     
        percorrer(dadosFuncionarios.telefones.busca(parametros:[codigoFuncionario:item.id])){   
            imprimir item  
        }    
    }  

Para retornar um único item, deve-se utilizar o parâmetro primeiro:true na operação de busca.

    dadosFuncionarios.busca(ordenacao:"rg desc", campos:"nome, rg, id, dataAdmissao, dataNascimento", primeiro:true)  

**valorPadrao:** Parâmetro utilizado para ativar/desativar o valor padrão dos campos quando nulos. Caso este parâmetro seja verdadeiro os registros das fontes de dados poderão conter propriedades nulas que deverão ser tratadas pelo próprio script.

    tema.busca(valorPadrao: falso)  

### Operação de criação​

A operação de criação padrão conta com os seguintes parâmetros:

**parâmetros:** Utilizado para informar os valores dos parâmetros da operação. O nome dos parâmetros pode variar conforme ativo, tema e operação utilizada. **conteúdo:** Dados do registro a ser criado.

    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    telefone = [  
      sequencial: 10,  
      telefone: '488817858',  
      tipo: 'OUTRO',  
      tipoNumero: 'CELULAR',  
      descricao: "Outro Celular"  
    ]  
       
    telefoneCriado = dadosFuncionarios.telefones.cria(parametros: [codigoFuncionario:12], conteudo: telefone)  

### Operação de atualização​

A operação de atualização padrão conta com os seguintes parâmetros:

  * **parâmetros:** Utilizado para informar os valores dos parâmetros da operação. O nome dos parâmetros pode variar conforme ativo, tema e operação utilizada.
  * **conteúdo:** Dados do registro a ser atualizado.

    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    telefone = [  
      telefone: '488817858'  
    ]  
       
    telefoneAlterado = dadosFuncionarios.telefones.atualiza(parametros: [codigoFuncionario: 12, codigoTelefone: 15], conteudo: telefone)  

### Operação de exclusão​

A operação de exclusão padrão conta com os seguintes parâmetros:

  * **parâmetros:** Utilizado para informar os valores dos parâmetros da operação. O nome dos parâmetros pode variar conforme ativo, tema e operação utilizada.

    dadosFuncionarios.telefones.exclui(parametros: [codigoFuncionario: 12, codigoTelefone: 15])  

  * Ativo
  * Tema
  * Operações
    * Operação de busca
    * Operação de criação
    * Operação de atualização
    * Operação de exclusão