---
title: Maio | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2022/maio
crawled_at: 2026-02-27 13:03:04
---

Pular para o conteúdo principal

Nessa página

## **19/05/2022**​

### Definindo _layout_ dos parâmetros nos scripts​

Foi implementado na ferramenta **Scripts** um recurso que vai facilitar muito o dia a dia dos usuários.

Agora, ao cadastrar os parâmetros é possível definir o layout de forma avançada, ou seja, melhorando o preenchimento no momento da execução, possibilitando também a estilização como posição e tamanho dos parâmetros. Após a criação dos parâmetros, acesse **Editar > Parâmetros > Definir layout**, logo, realize as mudanças desejadas. Quando o usuário realizar a execução do script no **Gerenciador de Scripts** ou no **F4** aparecerá todos os parâmetros com o _layout_ previamente configurados desde que as alterações estejam publicadas. 

![Maio](/assets/images/gif1-3cc73ae7267a448c3136d8db71ea7158.gif)  
---  
  
LEMBRE-SE!

Essa melhoria já se encontra disponível no Gerenciador de Relatórios.

* * *

### Permitido de definir o tamanho da janela dos parâmetros​

Foi implementado nas ferramentas de Relatórios e Scripts a possibilidade de definir o tamanho da janela dos parâmetros. As opções são: **Padrão** , **Média** ou **Grande**.

![Maio](/assets/images/script30-d5f36525be36fb5b54004297c837b5f8.png)  
---  
  
Consequentemente, a configuração estabelecida ficará disponível no **Assistente F4**.

  * **Padrão**

![Maio](/assets/images/script31-71d3bcd6acb0d63442734d9a933abc19.png)  
---  
  
  * **Média**

![Maio](/assets/images/script32-ebba499b6efdbe5b728c9322e3befe44.png)  
---  
  
  * **Grande**

![Maio](/assets/images/script33-8ea9038c450f830ef2ef1eebcb9c0c41.png)  
---  
  
* * *

### Reaproveitando execuções realizadas nos Relatórios, Scripts e Assistente F4​

A partir dessa liberação, é possível de uma maneira simples acessar os resultados das execuções recentes diretamente na tela de parâmetros. Esse recurso está disponível **Execuções recentes > ABRIR**.

![Maio](/assets/images/script34-1b68f626ac9dcef29d1d09ebdfc9f9a4.png)  
---  
  
* * *

## **04/05/2022**​

### Visualizando informações das execuções recentes de Relatórios e Scripts através do Assistente F4​

Para que os usuários possam acompanhar o andamento da sua execução e não ter que reexecutar relatórios ou scripts para acessar seus resultados, foi implementado no **Assistente F4** o recurso **Execuções recentes** , a opção é exibida do lado direito ao passar o mouse em cada artefato.

![Maio](/assets/images/script35-b0e77c4bf0d811d661e5d0fee6bd57b9.png)  
---  
  
Clicando no recurso, é possível visualizar todas as execuções recentes com todas as informações disponíveis através de colunas. Pressionando o botão **ABRIR** , é apresentado o artefato executado. Para facilitar a pesquisa das execuções filtre por: Minhas execuções, Todas execuções ou utilize o campo de busca.

![Maio](/assets/images/script36-17946d00c6903fa7dae828ed13d28606.png)  
---  
  
Clicando no ícone representado por um olho e habilitando a opção **Detalhes da execução** , é mostrado todas as informações relacionadas às execuções. É possível também visualizar essas informações das execuções pressionando o item **ver detalhes da execução** , porém, será direcionado para outra página. 

![Maio](/assets/images/script37-454397b534385cd516a4cf5a5d54ea26.png)  
---  
  
Por meio da opção **Ações disponíveis** , estão disponibilizadas as opções: Reexeutar, enviar para assinatura, visualizar parâmetros, métricas e metadados, habilitar e/ou desabilitar a execução informando se será pública ou não e ainda consultar o artefato através do protocolo.

![Maio](/assets/images/script38-4da967ca9df71271c87dd7792c94e651.png)  
---  
  
Quando pressionado o item **Gerenciador de extensões** , localizado no canto superior da tela. A ferramenta possibilita a visualização das execuções, agendamentos, compartilhamentos e as variáveis de ambiente do artefato, e nos últimos itens pode-se inserir novos compartilhamentos e novas variáveis. 

![Maio](/assets/images/script39-b20607b109ab08c8b83fc4cc3e09560b.png)  
---  
  
* * *

### Visualizando artefatos por Lista ou Pastas no Assistente F4​

Agora no Assistente F4 é possível visualizar relatórios e/ou scripts através de lista ou pastas, facilitando na organização visual e adaptação dos usuários.

  * **Lista**

![Maio](/assets/images/script40-f11db065f256953d4d15c9562abb079d.png)  
---  
  
  * **Pastas**

![Maio](/assets/images/script41-4b3e57d78a4412f2a399f37a2a1c29f4.png)  
---  
  
* * *

### Acesso ao contexto da aplicação nos scripts​

No gerenciador de scripts é possível acessar os valores do contexto da aplicação no seguinte objeto **contextoExecucao.contextoAplicacao**.

LEMBRE-SE!

As informações só estarão disponíveis quando a extensão for executada por dentro do sistema que possui o contexto de aplicação, caso for executada através de outro meio, por exemplo, via gerenciador de scripts/relatórios, o objeto que contém a informação estará vazia.

![Maio](/assets/images/script42-2b5f54993fad5f7a3d0ef6b05e207489.png)  
---  
  
Exemplo utilizando o contexto do sistema educação:

![Maio](/assets/images/script43-b324f4d0fb98f90f75018767c460f896.png)  
---  
  
* * *

### Visualizando Trace na consulta de relatórios e scripts​

Ao consultar uma execução de um artefato (relatório e/ou script), o usuário consegue visualizar todas as métricas, inclusive a opção **Trace**. Essa melhoria visa facilitar a observação do tempo gasto nas execuções, obtendo assim maior controle da qualidade do código executado.

![Maio](/assets/images/script44-cc58ab0b65a919f6daeafd701e1ffaa2.png)  
---  
![Maio](/assets/images/script45-97e48852ac29eb1696b8f25a7dec1887.png)  
---  
  
  * **19/05/2022**
    * Definindo _layout_ dos parâmetros nos scripts
    * Permitido de definir o tamanho da janela dos parâmetros
    * Reaproveitando execuções realizadas nos Relatórios, Scripts e Assistente F4
  * **04/05/2022**
    * Visualizando informações das execuções recentes de Relatórios e Scripts através do Assistente F4
    * Visualizando artefatos por Lista ou Pastas no Assistente F4
    * Acesso ao contexto da aplicação nos scripts
    * Visualizando Trace na consulta de relatórios e scripts