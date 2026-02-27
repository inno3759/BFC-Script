---
title: Fevereiro | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2023/fevereiro
crawled_at: 2026-02-27 13:02:32
---

Pular para o conteúdo principal

Nessa página

## **22/02/2023**​

### Disponibilizado criação de parâmetro do tipo “Senha”​

Durante o desenvolvimento de relatórios/scripts, agora é possível criar parâmetros com o tipo “Senha”, das quais possuem um comportamento semelhante aos parâmetros do tipo caracter, porém os mesmos não tem seu valor armazenado após a execução, ou exibidos no detalhamento de execuções após a finalização.

![Fevereiro](/assets/images/script1-d5e0ab29fb5f99efe77ecb3d88172b0e.png)  
---  
![Fevereiro](/assets/images/script2-22cc9053ceaa8d3c6ae761087ca7d4e0.png)  
---  
  
Detalhamentos sobre esse tipo de parâmetro:

  * Não é possível atribuir um valor padrão para parâmetros do tipo “Senha”;
  * O valor do parâmetro não é preenchido na reexecução;
  * Parâmetros do tipo senha não são convertidos para marcadores automaticamente;
  * Parâmetros do tipo senha não são exibidos na consulta de execuções.

ATENÇÃO! 

Em tempo de execução, esse tipo de parâmetro se comporta de forma idêntica a parâmetros do tipo **caracter** , de forma que o desenvolvedor tem liberdade na utilização do mesmo, porém, sugere-se atenção na hora de exportar o valor do parâmetro no log ou impressão do relatório, a fim de evitar o vazamento de informações sensíveis.

* * *

### Exibindo título do script na tela do editor​

Visando atender as necessidades dos nossos usuários, informamos que agora é possível visualizar o nome do artefato no editor de Scripts, para isso basta clicar no botão editar. 

![Fevereiro](/assets/images/script3-2a415bc4f7c77bb3268c57c26f977a43.png)  
---  
  
* * *

### Visualizando Eventos na consulta de relatórios e scripts​

Ao consultar uma execução de um artefato (relatório e/ou script), o usuário consegue visualizar todos os eventos realizados durante a execução de um relatório e/ou script, como por exemplo: o usuário que executou, data e hora de início e fim do mesmo.

![Fevereiro](/assets/images/script4-1ce7a926dd97454d0f33e4c902ca6017.png)  
---  
![Fevereiro](/assets/images/script5-0777947f25759a72fd1fdad83d3b210f.png)  
---  
  
Segue abaixo a lista dos eventos.

![Fevereiro](/assets/images/script6-eb87b2a128cbd4616fb3b42a385079c4.png)  
---  
  
* * *

### Permitido compartilhamento de extensões por representantes técnicos​

Informamos que foi removida a permissão de importação e exportação de scripts/relatórios entre clientes. Será suportada apenas a importação de scripts/relatórios da entidade do cliente para a entidade de um representante técnico. Essa ação tem por objetivo realizar a rastreabilidade da distribuição de extensões. Portanto, os compartilhamentos serão distribuídos sempre por um representante técnico.

* * *

### Atributos flexibilizados​

Implementado ao mecanismo de orquestração a capacidade de flexibilizar atributos. A partir desta publicação, atributos presentes no artefato de origem serão enviados para as entidades de destino, a observar as seguintes características.

Ao efetuar a orquestração, os atributos do artefato da entidade de origem serão flexibilizados. No caso do artefato possuir no destino um atributo com o mesmo nome, o seu valor será sobrescrito com o valor proveniente da orquestração. 

Se o destino possuir atributos com diferentes chaves no destino, a lista de atributos será combinada com os provenientes da origem.

Caso um atributo seja removido da entidade de origem, o mesmo não será removido da entidade destino. Tal comportamento visa manter o correto funcionamento caso alguma funcionalidade use o atributo.

  * **22/02/2023**
    * Disponibilizado criação de parâmetro do tipo “Senha”
    * Exibindo título do script na tela do editor
    * Visualizando Eventos na consulta de relatórios e scripts
    * Permitido compartilhamento de extensões por representantes técnicos
    * Atributos flexibilizados