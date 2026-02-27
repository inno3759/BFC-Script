---
title: Executando um script | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/executando-script
crawled_at: 2026-02-27 12:58:47
---

Pular para o conteúdo principal

Nessa página

Sabemos que um script pode ter várias versões, pois são artefatos que passaram por modificações, alterações por algum motivo. Para visualizar como ficou determinada alteração, é necessário pressionar o botão **EXECUTAR**.

![executando](/assets/images/script114-ce5cf5cfa06a2f3a95a4d00aa34722d1.png)  
---  
  
IMPORTANTE!

Scripts são executados no servidor da Betha e não localmente, portanto se faltar energia na hora da execução por exemplo, continuará executando normalmente.

Ao clicar no botão mencionado acima abrirá a tela de execução de um script. Existem duas opções de execuções que podem ser habilitadas, a primeira delas denomina-se como **Pública** , ao executar o artefato com esse item marcado serão exibidos para todos os usuários que possuem esse script. Habilitando a opção **Enviar por e-mail** , é enviado o artefato via e-mail para os usuários inseridos logo abaixo do item mencionado.

Para executar marque as opções desejadas e pressione o botão **EXECUTAR**.

![executando](/assets/images/script115-198ec44619802dd2e67beaf3531fc478.png)  
---  
  
As opções de execução ficam ocultas podendo ser acessadas quando desejado pelo usuário, essa melhoria tem o intuito de diminuir as informações apresentadas na tela de execução. Para visualizar as opções de execução pressione o botão **OPÇÕES**.

![executando](/assets/images/script209-96e7269863ba95e8fef679a40111d769.png)  
---  
![executando](/assets/images/script210-46e29979f81483810ed1c415a8c80bc5.png)  
---  
  
Marcando as opções desejadas, aparece um indicador de campo quando as informações estão ocultas.

![executando](/assets/images/script211-68722b54a9b8bc704743e382ace548af.png)  
---  
  
Quando as opções estiverem ocultas e houver opções com campos obrigatórios não preenchidos é exibido uma indicação de alerta.

![executando](/assets/images/script212-06593a757c335bdbd21dac80da0c2a3c.png)  
---  
  
Todas as execuções são apresentadas na tela central e as informações são distribuídas em colunas.

![executando](/assets/images/script116-110496b396a063867c8bff966d856dd6.png)  
---  
  
No ícone de engrenagem são apresentadas outras ações disponíveis no que diz respeito ao script executado. 

![executando](/assets/images/script117-5707564f66cb6b2273c1faa640c82496.png)  
---  
  
É possível indicar o modo de visibilidade (público ou privado) para a verificação de documentos assinados digitalmente gerados via script ou integração através das configurações. Esta opção permite que desenvolvedores e integradores definam se a execução de um relatório integrado deve resultar em um documento público, facilitando a validação externa da assinatura.

![scripts](/assets/images/scripts238-c352b8fa54c1101061b373013adde2d8.png)  
---  
  
Ao configurar a execução de um script que chama um relatório com assinatura digital:

  * Identifique o novo parâmetro de visibilidade disponível na chamada da função ou requisição.
  * Defina o parâmetro para indicar se o documento será Público ou Privado.
  * Ao optar pelo modo "Público", a validação da assinatura do documento poderá ser realizada sem as restrições de acesso que ocorriam quando o documento era gerado automaticamente como privado.
  * Por padrão a opção "Público" está selecionada. 

  * **Reexecutar**

Todas as reexecuções de extensões passam a considerar sempre a última versão da mesma. Quando a reexecução é solicitada a partir de uma versão desatualizada, é apresentada uma mensagem informativa para o usuário, conforme imagem abaixo. 

![executando](/assets/images/script118-220b45bd862f6b5604a813eb7cdbc2b7.png)  
---  
  
Caso algum parâmetro não possa ser preenchido da execução devido incompatibilidade de tipos entre as versões, é exibido uma notificação na tela.

![executando](data:image/png;base64,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)  
---  
  
  * **Parâmetros**

Possibilita a visualização dos parâmetros criados pelo usuário desenvolvedor.

![executando](/assets/images/script119-380c19276da00ab056e7fd3a78840e23.png)  
---  
  
  * **Métricas**

Um script quando executado pode ter mais de um ativo no banco de dados, possibilitando visualizar os ativos/recursos do script que foram acionados, **Número de execuções** , **Duração da execução** , **Tamanho do payload** (pacote de dados de envio ou entrega por uma API) e **[APDEX](https://en.wikipedia.org/wiki/Apdex)** (métrica que mede a performance de uma API).

![executando](/assets/images/script120-04cd4aa4d47d8ad0eb0cf064f3cfb2e5.png)  
---  
  
Clicando sobre o ícone mostrado na imagem abaixo são apresentadas as informações da **Duração** , **Tamanho do payload** e**APDEX**.

![executando](/assets/images/script121-f7f2eaad9a232283dd6e69dc591e9d99.png)  
---  
  
Clicando na engrenagem, a ferramenta disponibiliza uma amostragem da execução do campo exibindo detalhadamente todos os dados.

![executando](/assets/images/script122-c7edd9c2d3d55b1f276601e9c6c2fc12.png)  
---  
![executando](/assets/images/script123-d1ed45af7d014acd818c04d642e95d98.png)  
---  
  
  * **Log execução**

Neste item é possível visualizar todo o conteúdo do log de execução de um script. 

![executando](/assets/images/script124-e89a3a824fba3a316bde046bfacfa7a0.png)  
---  
  
  * **Trace execução**

O trace basicamente expõem algumas informações da execução de uma extensão, sendo particularmente útil em extensões que tem muitas dependências (um script que chama outro, ou faz uso de componentes, por exemplo), pois permite entender o passo a passo da execução de uma extensão.

![executando](/assets/images/script125-feb0a1ae9af7fd2ae768e0dfc707da3b.png)  
---  
  
  * **Execução pública**

Marcando o parâmetro, a execução pública é exibida para todos os usuários que possuem acesso a esse script. Caso esteja desmarcado, apenas o usuário logado que executou o script pode visualizar o resultado da execução.

![executando](/assets/images/script126-29216509623445f1844930e8ab09813c.png)  
---  
  
  * **Número de protocolo**

De acordo com o número de protocolo os usuários conseguem obter detalhes da execução através de um ambiente público <https://consulta-execucoes.cloud.betha.com.br/#/>. Para visualizar todos os detalhes, copie o número do protocolo e acesse o link.

![executando](/assets/images/script127-c02067c47b1d54d235de6c3153b383f5.png)  
---  
![executando](/assets/images/script128-cb1b47e4d6b03bef8e3302e3e50ad379.png)  
---  
  
Insira o número do protocolo para obter todos os detalhes da execução. 

![executando](/assets/images/script129-e71f9a69839aa4e955ecbaadc8b80510.png)  
---  
  
É possível consultar o protocolo da execução para obter informações importantes e relevantes acerca da execução realizada através do botão CONSULTAR localizado em **Execuções > Ações disponíveis > Protocolo**.

![executando](/assets/images/script130-f5833ea3fba94c8d54ac9af87f0db597.png)  
---  
  
Ao clicar no botão mencionado é possível visualizar todos os detalhes da execução, inclusive as opções **APDEX** de uma execução, proporcionando melhor visualização do desempenho das ferramentas da empresa através de uma legenda com cores diferenciadas e o **Trace** , que visa facilitar a observação do tempo gasto nas execuções, obtendo assim maior controle da qualidade do código executado.

![executando](/assets/images/script218-5e85f383236f253dece93ece9c067f09.png)  
---  
![executando](/assets/images/script119-380c19276da00ab056e7fd3a78840e23.png)  
---  
![executando](/assets/images/script193-c8547144a320f2a1fcde9e980cb9725b.png)  
---  
  
Na opção **MARCADORES** , são apresentadas informações dos marcadores customizados na aplicação. Logo abaixo, são mostradas informações relacionadas ao contexto da execução: **Sistema** e **Entidade**.

![executando](/assets/images/script213-41d4f91c99bb6ec2c4993ea384f58806.png)  
---  
  
É possível também visualizar todos os eventos realizados durante a execução de um script, exemplo: o usuário que executou, data e hora de início e fim do mesmo.

![executando](/assets/images/script226-0777947f25759a72fd1fdad83d3b210f.png)  
---  
  
Segue abaixo a lista dos eventos.

![executando](/assets/images/script227-eb87b2a128cbd4616fb3b42a385079c4.png)  
---  
  
Além das informações apresentadas acima, há também a opção **Agendado por** , que mostra a identificação do [agendamento de forma programática](https://docs.plataforma.betha.cloud/docs/extensoes/scrip-ts/executando-script#agendando-scripts-de-forma-program%C3%A1tica). 

![executando](/assets/images/script214-8124db8b1b4f2d4034ef339c8549f416.png)  
---  
  
Todas as execuções recentes ficam disponíveis em uma aba específica do lado esquerdo da tela, para visualizá-las basta clicar no local mencionado.

![executando](/assets/images/script200-4c026ee30b2c201809e5d14238ee1425.png)  
---  
![executando](/assets/images/script201-1b68f626ac9dcef29d1d09ebdfc9f9a4.png)  
---  
  
## Salvando parâmetros mais utilizados​

Na tela de **execução de script** o usuário encontra os parâmetros cadastrados para que sejam preenchidos. Ao término do preenchimento dos itens desejados, é possível salvar os parâmetros. Para isso, pressione a flecha no botão **EXECUTAR** , facilitando assim, a visualização dos parâmetros mais utilizados. 

![executando](/assets/images/script131-6fa92bda6f20cff7689e77ed23deb480.png)  
---  
  
Insira uma descrição e clique em **SALVAR** ou **SALVAR E EXECUTAR** para gravar e executar o script. para anular a ação, pressione **CANCELAR**.

![executando](/assets/images/script132-0f608d8c9a5d95dca6225b784358d159.png)  
---  
  
Os parâmetros salvos ficam disponíveis no lado esquerdo da tela. Para visualizá-los clique em **Parâmetros salvos** e para carregá-los clique no parâmetro desejado. 

Com esse recurso, a ferramenta possibilita que o usuário possua uma lista de parâmetros com informações salvas para quando desejar **reexecutar** o script. Também é possível editar as informações já cadastradas, basta alterar as informações e salvar novamente.

![executando](/assets/images/script133-8f4c90fc2d7c07ede7685a9f4e460a87.png)  
---  
  
Os parâmetros salvos não estão vinculados a uma versão específica da extensão, portanto, se o usuário editar e publicar uma nova, nada será modificado. A única alteração que terá é ao incluir um campo novo, a informação aparecerá na ferramenta sem informação nenhuma, ou seja, em branco. Para que a informação seja apresentada é necessário inserir o conteúdo no campo e salvar novamente.

![executando](/assets/images/script134-639c9274d3ccac2861a004ad1b87aa1d.png)  
---  
  
## Agendando scripts​

A ferramenta dispõe de um recurso facilitador para os usuários, são os agendamentos, possibilitando que seja programada uma execução para um determinado script. Clicando em **Ações disponíveis** no botão **EXECUTAR** existe a possibilidade de **Agendar** os Scripts.

![executando](/assets/images/script135-0e7f6d0eef9005f1d3eb264adb6db2a4.png)  
---  
  
São apresentados 4 abas a serem preenchidas para que o agendamento se concretize, veja em detalhes abaixo. 

![executando](/assets/images/script136-06c2c6322f7de264b194906f4d286c8e.png)  
---  
  
### Configurando opções​

Na primeira aba **Configurar opções** encontram-se as opções de execuções e se algum parâmetro for cadastrado aparecerá nessa tela para preenchimento.

![executando](/assets/images/script137-86a6dfaa55b4463ba2f930b5ef4da3f1.png)  
---  
  
### Definindo recorrência​

Na segunda aba **Definir recorrência** são apresentados as informações referentes às repetições que esse script será executado. Perceba que todos os campos são de preenchimento obrigatórios e os campos comuns são **Recorrência** , **Início** e **Termina**.

No campo **Recorrência** , as opções de escolha são: diária, semanal, mensal, anual ou personalizada.

![executando](/assets/images/script138-6880dd912b06e1c69203e3f3c67a6106.png)  
---  
  
No campo Início, informe uma data que dará início a execução e o envio do mesmo. 

![executando](/assets/images/script139-76678a6e7d23216d02d5b28912c78289.png)  
---  
  
No campo **Termina** o usuário precisa escolher entre as opções **Nunca** (não tem fim), **Após algumas ocorrências** (um novo campo é aberto para que seja informado a quantidade de ocorrências) e **Em uma data específica** (necessário informar a data de término).

![executando](/assets/images/script140-ade0be49c2efa9bb6f377daef2db6209.png)  
---  
  
Dependendo da opção escolhida no campo **Recorrência** , outros campos são apresentados. Confira abaixo os detalhes de cada item: 

**Diária:** optando por essa recorrência, o campo **Repete a cada (dias)** é exibido, é necessário que o usuário insira a quantidade de dias em que será repetido a execução do script.

![executando](/assets/images/script141-248e7908a9639659a2356504ec11fdb0.png)  
---  
  
**Semanal:** informe os dias da semana que será executado e enviado o script. 

![executando](/assets/images/script142-bb38b6e6542b1341fe35fd26ac0879c5.png)  
---  
  
**Mensal:** neste item, dois novos campos são apresentados, onde o usuário informará os dias do mês e o(s) mês(es) de envio do script.

![executando](/assets/images/script143-75057e1a713f722e8d3a9903e1dab841.png)  
---  
  
**Anual:** escolhendo essa opção aparecerá apenas campos comuns a todas as opções, porém será executado e enviado o script 1 vez ao ano na data e hora estipulados no campo Início e terá um fim marcando o campo **Termina**.

![executando](/assets/images/script144-49377fda9d753395db75a348c09dcdbb.png)  
---  
  
**Personalizado:** optando por essa recorrência, o campo **Expressão de agendamento CRON** é exibido, a expressão CRON é uma expressão que determina um agendamento que pode ser horários, datas, repetições periódicas, intervalos fixos ou apenas um agendamento para uma determinada data.

Atualmente os agendamentos suportados são de expressões no formato CRON Quartz e com intervalo mínimo entre execuções de 15 minutos. No exemplo a seguir, está especificado uma CRON de repetição para cada hora:

![executando](/assets/images/script145-3aa1aa63e1c5037e43678952f75a2212.png)  
---  
  
Para facilitar a construção dessas expressões, existem diversas ferramentas e documentações na internet, como por exemplo o site [Cron Maker,](http://www.cronmaker.com/) que permite montar de acordo com grupos de horário e dias da semana. Abaixo seguem alguns exemplos de expressões Cron e seus significados.

**Condição**| **Expressão**  
---|---  
Executar a cada 30 minutos| 0 0/30 * 1/1 * ? *  
Executar a cada 12 horas| 0 0 0/12 1/1 * ? *  
Executar todo dia da semana às 18h| 0 0 18 ? * MON-FRI *  
Somente nas sextas-feiras e sábados, às 8h| 0 0 8 ? * FRI,SAT *  
Primeiro dia a cada 2 meses, às 13h| 0 0 13 1 1/2 ? *  
Primeira segunda feira de Maio às 12h| 0 0 12 ? 5 MON#1 *  
  
### Gerenciando notificações​

O recurso **Gerenciar notificações** , administra os avisos de execuções dos relatórios, controlando o que será possível visualizar e para quem irá enviar as notificações. Quando o parâmetro **Omitir notificações** está **desabilitado** é possível inserir os usuários que receberão as notificações.

![executando](/assets/images/script215-d50985efb91505d8fae5f34484df1dd9.png)  
---  
  
Quando o parâmetro está **habilitado** , o campo **Notificar usuários do sistema** desaparece, ou seja, ao executar um artefato não será enviado nenhum tipo de notificação para os usuários. 

![executando](/assets/images/script216-56a0a879c90207f495ddc0023feedd2d.png)  
---  
  
### Resumo​

Esta guia mostra o resumo de todas as informações inseridas nas guias anteriores, através do campo **Título** é inserido um nome para o agendamento e ainda é possível realizar um agendamentos sistêmico que tem por objetivo agendar execuções vinculadas ao sistema e não a um usuário específico.

![executando](/assets/images/script217-8d42c54f94555b72d472b3a0ccad61b6.png)  
---  
  
**IMPORTANTE!**

É necessário que o usuário seja administrador da entidade para realizar os **Agendamentos sistêmicos**. 

A ferramenta permite que seja realizado o cancelamento de uma execução sistêmica por um administrador. Esta funcionalidade está disponível através da engrenagem Mais opções > Cancelar, porém só aparecerá a opção de cancelar quando o script estiver sendo executado, caso contrário não aparece essa alternativa.

![executando](/assets/images/script222-9c760cd8e23912c325b20eaee9ef3779.png)  
---  
  
### Agendando scripts de forma programática​

É possível realizar agendamentos automáticos nos scripts, ou seja, de forma programática. Portanto, agora há duas maneiras de realizar um agendamento: de forma [visual](https://docs.plataforma.betha.cloud/docs/extensoes/scrip-ts/executando-script#agendando-scripts) e [programática](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-script#agendando-scripts).

As sugestões de uso dessa funcionalidade são:

  * Esperar o processamento de um lote enviado para algum serviço;
    * No lugar de parar a execução atual, utilizando o método **esperar** , basta agendar o mesmo ou outro script passando os parâmetros necessários para a consulta;
  * Executar um processo incremental sem a necessidade de fazer um agendamento customizado;
  * De forma geral, em todos os lugares onde hoje se utiliza o **esperar**.

**Como realizar um agendamento?**

Utilizando o comando _Script.identificador.agendar('1m')_ onde o **Script** é palavra reservada, seguida do **identificador** do script a ser agendado e o método **agendar()** , que pode receber os paramentos da execução, juntamente com o tempo de agendamento, ou simplesmente o tempo. 

![executando](/assets/images/script202-5f723212e4cd9aee6f907425f0bdb212.png)  
---  
![executando](/assets/images/script203-93ca51996d25a1748657e639e838b41d.png)  
---  
  
Todos os agendamentos ficam em uma guia exclusiva no Gerenciador de Scripts facilitando a visualização e realizando possíveis alterações. No lado direito da tela na opção **Ações disponíveis** é permitido **Editar** , **Excluir** ou **Desativar** quando o script estiver ativado.

![executando](/assets/images/script223-04b5d295e38617aef5fa304a3de34161.png)  
---  
  
### Visualização de Motivos de Cancelamento de Agendamentos​

Você pode visualizar o motivo do cancelamento de um agendamento diretamente na interface de agendamentos. Para acessar essa informação, siga os passos abaixo:

  1. Acesse o menu **"Studio Extensões"**.
  2. Escolha a **entidade** e o **sistema** desejado.
  3. Vá para a aba **"Script"** e selecione o script desejado.
  4. Na aba **"Agendamentos"** , ao passar o mouse sobre o ícone de informação ao lado do status do agendamento, o motivo será exibido.

![executando](/assets/images/scripts237-88bd79806bdb0c7b9792161cc7a31955.png)  
---  
  
Os motivos pelos quais um agendamento pode ser cancelado incluem:

  * **Solicitação do usuário** : Cancelamento manual realizado por um usuário.
  * **Término** : O agendamento expirou devido à data de validade.
  * **Exclusão da extensão** : A extensão vinculada ao agendamento foi removida.
  * **Desatualizado** : Se o script foi editado e o parâmetro mudou, o agendamento se torna inconsistente e, assim, é desativado automaticamente, necessitando reconfiguração.
  * **Sem dono** : A pessoa responsável pela extensão foi desligada da entidade.

## Executando uma extensão utilizando dados de outras entidades​

Os **usuários técnicos** podem executar uma extensão dentro do ambiente de desenvolvimento de outras entidades, facilitando o fluxo de desenvolvimento. Porém, esse usuário precisa ter acesso a outra entidade destino (necessário ser administrador) para que seja realizada essa execução. 

Esse recurso está disponível nas ferramentas de **Relatórios** e **Scripts** através da opção**Executar no contexto de outra entidade**. Habilitando essa opção, o usuário necessita selecionar a entidade. Para isso, basta clicar no espaço abaixo que logo, será mostrado as alternativas. 

![executando](/assets/images/script146-93bb98752f02fdbe51036baf1bb1c048.png)  
---  
  
A entidade selecionada será usada no momento da busca nos campos de seleção com dados dinâmicos.

Ainda, no caso dos campos de seleção terem seus valores preenchidos e a entidade de execução ser alterada, estes serão limpos, evitando que valores inválidos sejam enviados para processamento.

![executando](/assets/images/entidades-b6faa310e46b32ad9deefa35531a2d28.gif)  
---  
  
**Exemplificando:** partindo do cenário onde temos para seleção uma lista de obras da entidade, ao selecionar para executar em outro contexto e selecionado outra entidade, a lista de obras terá seu valor selecionado limpo e serão dispostos apenas as obras que pertencerem à entidade selecionada.

IMPORTANTE!

  * Somente será exibido a opção de execução em outro contexto para usuários técnicos e somente serão listadas as entidades que o usuário é administrador e possui acesso técnico;
  * Execuções em outro contexto serão automaticamente classificadas como execuções privadas.

## Monitorando em tempo real as execuções​

Ao executar um artefato na ferramenta Scripts, existe um recurso de feedback informando aos usuários se a opção de monitoramento em tempo real está ativada. Proporcionando mais clareza durante a execução. 

**Opção habilitada:** ao clicar em **Ações disponíveis** , é possível visualizar a opção **Log execução** com a informação **Tempo real**. Clicando nessa opção, uma tela é aberta para que o usuário possa acompanhar e atualizar a execução em tempo real até que ela seja concluída, mostrando as informações do log. 

Na opção Ações disponíveis > Métricas, também aparecerá a opção de atualizar até o final da execução.

![executando](/assets/images/script228-a54fe2bc89fa07a02605a993beff10b9.png)  
---  
![executando](/assets/images/script229-be5fb7d1a2ff42b4b3a34f46e601967c.png)  
---  
![executando](/assets/images/script234-d0b83a37b39fe2b2334b373831379f49.png)  
---  
  
**Monitoramento em tempo real desabilitado:** as informações do log dos dados serão apresentadas apenas ao final da execução, com a opção **Log execução** aparecendo desabilitada durante a execução e sendo habilitada no momento da conclusão. Ao clicar em **Métricas** , é mostrado que a execução está em andamento e exibidas informações adicionais no link **Saber mais**.

![executando](/assets/images/script235-cf466df2a6a42248040168c28a28ff0e.png)  
---  
![executando](/assets/images/script236-84906e8073cdf301fabab71ca937a23f.png)  
---  
  
## Adicionado propriedade para recuperar a lista de e-mails configurados para serem notificados na execução de um Script​

Adicionado a propriedade “**emailsNotificacao** ” ao contexto do script. Esta propriedade retornará a lista de e-mails configurados na etapa de "**Opções de execução** ". No caso de não haver sido configurado nenhum e-mail, será retornado um objeto nulo.

Na prática, a propriedade permitirá, por exemplo, que o desenvolvedor crie regras onde ao ocorrer falha de validação ou de execução, os usuários configurados para receberem a notificação poderão ser informados via programação conforme o desejado. 

Exemplo:

    if (contextoExecucao.emailsNotificacao != null) {  
       remetente = "ped@betha.com.br"  
       contextoExecucao.emailsNotificacao.each {  
           email = Email.novo()  
           email.de (remetente, "Email de ${remetente}")  
                .para(it, "Para ${it}")  
                .assunto("Execução de Script")  
               .mensagem("Você está recebendo este e-mail, pois está configurado nas opções de execução do agendamento")  
                .enviar()  
       }  
    }  

  * Salvando parâmetros mais utilizados
  * Agendando scripts
    * Configurando opções
    * Definindo recorrência
    * Gerenciando notificações
    * Resumo
    * Agendando scripts de forma programática
    * Visualização de Motivos de Cancelamento de Agendamentos
  * Executando uma extensão utilizando dados de outras entidades
  * Monitorando em tempo real as execuções
  * Adicionado propriedade para recuperar a lista de e-mails configurados para serem notificados na execução de um Script