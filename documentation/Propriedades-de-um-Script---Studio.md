---
title: Propriedades de um Script | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/propriedades
crawled_at: 2026-02-27 12:58:29
---

Pular para o conteúdo principal

Nessa página

Realizada a publicação, o usuário pode clicar sobre o artefato na tela inicial do gerenciador de Scripts, através dela é possível visualizar outras informações importantes.

Nos itens **Tipo** e **Natureza** são escolhidos pelo usuário ao cadastrar um novo script, a informações **Criado em** e**Atualizado em** mostra data e hora e quem criou/atualizou o script, em **Versão atual** é atualizada automaticamente pelo próprio gerenciador conforme as execuções realizadas. Em **Reexecução automática** reestarta a execução da extensão no caso dela ter sido interrompida por alguma questão do ambiente.

As opções **Identificador** , **_Tag_(s)**, **Exportações** e**Atributos** estão marcados em azul, pois, a ferramenta possibilita que sejam inseridas informações clicando nelas. O detalhamento de cada uma está descrito abaixo.

![propriedades](/assets/images/script32-70029a3ebf2b7e12b249f5a5fce30ec2.png)  
---  
  
Quando um artefato tenha sido flexibilizado para a entidade do usuário logado, o item **Flexibilizado por** é mostrado na tela, aqui é possível visualizar a entidade que flexibilizou o script e nesses casos o botão de **EDITAR** fica desabilitado, ou seja, apenas pessoas com acesso a entidade que flexibilizou o artefato terão acesso e poderão atualizá-lo.

![propriedades](/assets/images/script33-8d457703e0a585d73f1e9637e33268f0.png)  
---  
  
## Identificadores​

Esse recurso traz flexibilidade para a ferramenta durante o processo de desenvolvimento, com ele é possível flexibilizar scripts com o mesmo identificador para clientes, ou seja, é permitido esta duplicidade somente para quem desenvolve extensões (revendas, filiais, etc). 

Para configurar um identificador clique sobre a palavra **Configurar** , logo é aberta a tela **Alterando identificador** , insira um identificador e pressione o botão **SALVAR**. 

![propriedades](/assets/images/script34-36013530652b65e25a7fdd685e12af20.png)  
---  
  
Clicando em **Ações disponíveis > Copiar** o usuário desenvolvedor cria uma cópia da extensão na base, dessa forma o desenvolvedor consegue fazer edições e testes sem alterar a extensão original. Isso é importante também quando deseja-se customizar uma extensão flexibilizada, porque não é possível editar uma extensão que está instalada através do orquestrador, mas pode-se criar uma cópia dela e editá-la.

![propriedades](/assets/images/script35-9cc108b7834d31200c42423e75fb17bf.png)  
---  
  
## Inserindo _tags_​

Ao clicar na opção **Ainda não há tags** , uma janela será aberta para inserir novos dados. Digite o nome da tag e pressione Enter para adicionar a informação, é possível adicionar quantas tags achar necessário. Em seguida, clique em salvar para gravar as informações. As tags cadastradas são exibidas na tela principal junto com as demais informações do artefato.

![propriedades](/assets/images/script36-f2694ac0ad10a946d4d68c63063c7d5e.png)  
---  
  
Usuários administradores podem criar e associar tags aos artefatos através do **Assistente F4**. Ao clicar em **Ver detalhes** ao lado do nome, uma nova janela será aberta, permitindo o cadastro de novas tags.

![propriedades](/assets/images/script37-9a35f4d5f0246623fefdf3bb6f46f445.png)  
---  
![propriedades](/assets/images/script38-5eac69172084f008af1e652ab02bef38.png)  
---  
  
### Visualizando tags na listagem de extensões​

Existe a possibilidade de visualizar as **Tags** de extensões diferenciando-as mesmo que tenham nomes iguais. Esse recurso está localizado em **Visualizar > Tags**.

![propriedades](/assets/images/script207-ec2e97dde6745655ad84f3adeca41c9a.png)  
---  
  
Todas as **Tags** são mostradas na cor cinza, logo, os **Atributos** na cor branca.

![propriedades](/assets/images/script208-8322589c42cd35768bba85dbce996331.png)  
---  
  
IMPORTANTE!

Mesmo atualizando ou saindo da página, será mantida a última configuração, ou seja, se a opção Tags estiver habilitada continuará aparecendo as informações na tela. Não aparecerá quando o parâmetro for desabilitado.

## Exportando Scripts​

Clicando em **Adicionar** ao lado da opção **Exportações** , a ferramenta possibilita a criação de chaves para exportação. Esse recurso serve basicamente para um desenvolvedor exportar um artefato para que outro desenvolvedor importe as informações através de uma chave de acesso.

![propriedades](/assets/images/script40-df8b95cad4010c901c6728e9b54e5f90.png)  
---  
  
Pressione o botão **+EXPORTAR** para gerar uma chave, insira uma data de validade e pressione o botão **GERAR**.

![propriedades](/assets/images/script41-563e19ccdf0a0dd9bb6f1eb1e063de4b.png)  
---  
  
Todas as chaves geradas ficam disponíveis na tela **Chaves de exportação** e são apresentadas em colunas para melhor visualização. Ainda é possível ativá-las ou desativá-las a qualquer momento.

![propriedades](/assets/images/script42-68ce2ecfe5616d2c636a69002170fa5e.png)  
---  
  
Na aba **EXPIRADAS** são exibidas as chaves que já passaram do prazo de validade. 

![propriedades](/assets/images/script43-2c5094b51b1ce5eb7e45c731de512af1.png)  
---  
  
Essas chaves são fornecidas para outros parceiros (revendas/filiais) que tenham interesse no script. 

![propriedades](/assets/images/script44-a494fd5520b556f35d60979bbdae2f87.png)  
---  
  
Copie a chave cole no campo chave na tela de importação. Perceba que há a possibilidade de realizar uma importação em lote, para isso habilite a opção **Importação em lote** , a seguir clique em **CONTINUAR**.

![propriedades](/assets/images/script45-4d6e0a9f73a99c728870073fdaa425ee.png)  
---  
  
Na próxima tela são apresentadas todas as informações da importação e para confirmar a ação pressione o botão IMPORTAR. 

![propriedades](/assets/images/script46-3b8349db27529ef6932857a0f604c7c2.png)  
---  
  
## Inserindo Atributos​

O recurso **Atributos** visa organizar, visualizar e flexibilizar as extensões com mais agilidade. Para inserir um novo atributo clique em **Adicionar** como mostrado na imagem abaixo. 

![propriedades](/assets/images/script47-8c442ee348e07ad2739fe67fb1008c96.png)  
---  
  
Pressionar o botão **+ATRIBUTO** na janela **Gerenciando atributos** para cadastrar um atributo.

![propriedades](/assets/images/script48-73dd0fed954f95dd729f6d9ef8e645ee.png)  
---  
  
Insira a quantidade desejada de chaves e valores e clique em **SALVAR**.

![propriedades](/assets/images/script49-4956ab77add54a1788f2b87856817559.png)  
---  
  
Logo, os atributos ficam visíveis na tela de informações do artefato. 

![propriedades](/assets/images/script50-ac7b14e6275b86a28a90ff9b86ca39d8.png)  
---  
  
IMPORTANTE!

Este recurso está disponível apenas para usuários com acesso a ferramenta Gerenciador de Scripts.

Ao adicionar um atributo é possível buscar no campo de pesquisa da ferramenta, para isso, insira no campo de pesquisa exatamente como cadastrado no atributo. 

**Exemplo:** Um atributo cadastrado com a Chave: Encerramento e Valor: 2021, deve ser digitado no campo de busca da seguinte maneira: **Encerramento:2021** ou com letras minúsculas **encerramento:2021**. Os dois pontos entre a chave e o valor são essenciais para que a busca seja realizada de maneira correta.

**Atributo cadastrado:**

![propriedades](/assets/images/script51-139fdabdeb7f60f63ae3cabcd72163fa.png)  
---  
  
**Busca pelo Atributo:**

![propriedades](/assets/images/script52-1f8d0ec2f4097703a377038a1f0817ab.png)  
---  
  
**Artefato mostrado na tela:**

![propriedades](/assets/images/script53-c7d0de27907170be62bf65af3bcbde4e.png)  
---  
  
### Atributos flexibilizados​

A ferramenta possui um mecanismo capaz de flexibilizar atributos através da orquestração, ou seja, atributos presentes no artefato de origem serão enviados para as entidades de destino.

Ao efetuar a orquestração, os atributos do artefato da entidade de origem serão flexibilizados. No caso do artefato possuir no destino um atributo com o mesmo nome, o seu valor será sobrescrito com o valor proveniente da orquestração. 

Se o destino possuir atributos com diferentes chaves no destino, a lista de atributos será combinada com os provenientes da origem.

Caso um atributo seja removido da entidade de origem, o mesmo não será removido da entidade destino. Tal comportamento visa manter o correto funcionamento caso alguma funcionalidade use o atributo.

## Controle de Licenças​

A ferramenta permite o controle de licença das extensões, possibilitando a configuração do tipo de licença de uma extensão. Com isso, o desenvolvedor pode configurar a extensão como **Livre** ou Proprietária (opção padrão).

**Livre:** Ao selecionar esta opção, os usuários podem visualizar e copiar o código-fonte da extensão na entidade de destino.

**Proprietária:** Ao optar por esta configuração, o acesso às informações é restrito, permitindo apenas a execução da extensão.

Essas configurações estão vinculadas à versão da extensão, exigindo que uma nova versão devidamente configurada seja lançada através da ferramenta de Orquestração para que as alterações sejam aplicadas às entidades de destino.

A definição da licença é exclusiva para a entidade de origem da extensão. No entanto, os usuários administradores nesta entidade podem copiar e visualizar o código-fonte normalmente, independentemente da licença aplicada.

![propriedades](/assets/images/gif1-7a23f08ec54db16ba2dccd2089ce95b4.gif)  
---  
  
  * Identificadores
  * Inserindo _tags_
    * Visualizando tags na listagem de extensões
  * Exportando Scripts
  * Inserindo Atributos
    * Atributos flexibilizados
  * Controle de Licenças