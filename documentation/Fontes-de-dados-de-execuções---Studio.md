---
title: Fontes de dados de execuções | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/fontes-dados-execucao
crawled_at: 2026-02-27 12:58:51
---

Pular para o conteúdo principal

Nessa página

Dentre todas as fontes de dados existentes, a ferramenta de **Scripts** conta com quatro delas destinadas às execuções dos artefatos, sejam eles de relatórios ou scripts. Essas fontes estão disponíveis no explorador de fonte de dados, dentro do grupo Fontes de dados da **Plataforma para Dados de Execuções**.

![fontes-dados](/assets/images/script163-a093acaf80423e92cedc0ea56cc3ad08.png)  
---  
  
Cada uma das fontes possui sua função específica, sendo:

  * **execucoes.busca:** busca todas as execuções passando alguns filtros;
  * **execuções.movimentacoes:** retorna as movimentaçẽos de uma execução dado um protocolo de execução;
  * **execucoes.propriedades:** retorna as propriedades de uma execução dado um protocolo de execução;
  * **parametros.busca:** busca as execuções a partir dos dados de seus parâmetros.

## Consulta execuções​

É uma fonte que consulta as execuções de scripts e relatórios, permitindo visualizar algumas propriedades, como: dados do agendamento, usuário, status, mensagens de inconsistência, endereço dos arquivos gerados e no caso de relatórios, endereços dos arquivos assinados digitalmente. 

A fonte disponibiliza uma série de campos para visualização, ordenação e filtros, que estão dispostas nas abas de mesmo nome.

**Exemplificando:** execução de integração com outro sistema, onde seja necessário enviar os relatórios assinados digitalmente dentro de um período. Essa fonte lhe fornecerá os endereços dos relatórios e demais funcionalidades do script que lhe proverão o restante.

No exemplo abaixo é exibido um script utilizando a fonte mencionada: 

![fontes-dados](/assets/images/script164-ecb4527fdb9cc0361287e52cea5cb4ed.png)  
---  
  
## Consulta de propriedades de execução​

Essa é uma fonte de dados que retorna as propriedades de uma execução, como o formato de exportação do arquivo gerado. Nessa consulta é obrigatório informar o código do protocolo, sendo esse o único filtro disponível. 

**Exemplificando:** determinar o formato de exportação de um determinado arquivo ou se o mesmo foi enviado por e-mail. 

No código abaixo é demonstrado um exemplo de uso:

![fontes-dados](/assets/images/script165-a6d6fe7c3e23d3b698c8669d54078b12.png)  
---  
  
## Consulta de movimentações de execução​

Essa fonte é semelhante a fonte de consulta de propriedades de execução, porém exibe informações relacionadas aos passos de execução do artefato, bem como métricas de tempo de execução em cada um.

**Exemplificando:** determinar o tempo que uma execução levou para ocorrer, desde o momento que foi requisitado até ser finalizado.

No código abaixo é demonstrado um exemplo de uso:

![fontes-dados](/assets/images/script166-550c48b6a9cbaf4f8e65b9f6e384999a.png)  
---  
  
## Consulta de execuções por parâmetros​

Essa fonte é semelhante à fonte de consulta de execuções, porém o retorno das execuções se dará a partir dos parâmetros usados para execução da mesma. 

A fonte disponibiliza uma série de campos para visualização, ordenação e filtros, que estão dispostas nas abas de mesmo nome.

**Exemplificando:** determinar as execuções onde fora fornecido um valor para um parâmetro e o valor seja igual ao desejado. 

No código abaixo é demonstrado um exemplo de uso:

![fontes-dados](/assets/images/script167-52b87d131872e5159f02de330126985e.png)  
---  
  
### API de Gerenciamento de Acessos, Bloqueios e Permissões de Usuários​

Esta documentação detalha uma API e fontes de dados projetada para automatizar o gerenciamento de acessos de usuários. Elas possibilitam que sistemas, como o de Folha de Pagamento, possam desativar e gerenciar programaticamente os acessos de um servidor em todos os sistemas licenciados, especialmente em um cenário  
de rescisão de contrato. 

As funcionalidades permitem:

  1. Listar todos os acessos de um usuário em uma entidade. 
  2. Bloquear (com data de término ou indefinidamente) e desbloquear o acesso de um usuário. 
  3. Gerenciar permissões granulares, alterando o acesso a funcionalidades específicas (via PageMappings) e a grupos de permissão, sem a necessidade de bloquear o usuário por completo. 

Estes recursos estão disponíveis tanto via Endpoints de API (para integrações sistema-a-sistema) quanto via Fontes de Dados no Gerenciador de Scripts. 

Para entender a API, imagine o seguinte fluxo de trabalho automatizado quando um funcionário é desligado da organização:

  1. **Identificação:** O sistema de RH identifica o `userId` do funcionário a ser desligado. 
  2. **Listagem de Acessos:** O sistema consome a API para listar todos os `accessId` associados àquele `userId` na entidade. 
  3. **Remoção de Permissões (Opcional):** Para cada `accessId`, o sistema pode remover o acesso a grupos específicos ou revogar permissões de módulos sensíveis (como o "Minha Folha"). 
  4. **Bloqueio Total:** Como passo final, o sistema realiza uma chamada para bloquear permanentemente o `userId`, garantindo que ele não possa mais acessar nenhum sistema da entidade. 

Para acessar a configuração e autenticação (Pré-requisitos) e o Guia de Endpoints, clique [aqui](https://plataforma-wiki.betha.cloud/pt-br/aplicacoes/autorizacoes/fonte-bloqueio-acessos-por-usuario)

  * Consulta execuções
  * Consulta de propriedades de execução
  * Consulta de movimentações de execução
  * Consulta de execuções por parâmetros
    * API de Gerenciamento de Acessos, Bloqueios e Permissões de Usuários