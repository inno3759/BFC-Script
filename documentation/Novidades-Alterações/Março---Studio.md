---
title: Março | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2023/marco
crawled_at: 2026-02-27 13:02:27
---

Pular para o conteúdo principal

Nessa página

## **27/03/2023**​

### Monitorando em tempo real as execuções​

Dando continuidade às melhorias de desempenho e escalabilidade no monitoramento das execuções de relatórios e scripts, estamos disponibilizando uma opção para monitoramento em tempo real, o qual possibilita a visualização dos logs* e métricas antes do término da execução.

* disponível somente para scripts.

![Março](/assets/images/script8-b378cdf294ae8dc5e70946a6c63218bc.png)  
---  
  
O monitoramento em tempo real, propicia o acompanhamento dos logs e métricas no decorrer da execução.

Caso seja necessário habilitar o monitoramento para uma execução que já esteja em andamento, é possível selecionar a opção de mesmo nome, que está disponível no ícone representado por uma engrenagem. 

Ao selecionar a opção monitoramento em tempo real para uma execução que já esteja em andamento, os logs e métricas pararão a ser sincronizados e disponibilizados para consulta após alguns instantes.

![Março](/assets/images/script9-8c2add915cb05904088d487aeeb45f6f.png)  
---  
  
### Executando no contexto de outra entidade​

Seguindo com as evoluções na execução de scripts e relatórios, a partir dessa liberação a opção de “executar em outro contexto” foi deslocada para o início da tela e a entidade selecionada será usada no momento da busca nos campos de seleção com dados dinâmicos.

Ainda, no caso dos campos de seleção terem seus valores preenchidos e a entidade de execução ser alterada, estes serão limpos, evitando que valores inválidos sejam enviados para processamento.

![Março](/assets/images/gif1-b6faa310e46b32ad9deefa35531a2d28.gif)  
---  
  
**Exemplificando:** partindo do cenário onde temos para seleção uma lista de obras da entidade, ao selecionar para executar em outro contexto e selecionado outra entidade, a lista de obras terá seu valor selecionado limpo e serão dispostos apenas as obras que pertencerem à entidade selecionada.

LEMBRE-SE!

  * Somente será exibido a opção de execução em outro contexto para usuários técnicos e somente serão listadas as entidades que o usuário é administrador e possui acesso técnico;
  * Execuções em outro contexto serão automaticamente classificadas como execuções privadas.

* * *

## **10/03/2023**​

### Log de execução de Scripts​

Informamos que o log de execução dos scripts passaram por mudanças, agora a execução de scripts no Studio Extensões conta com a opção de execução “**Log de execução em tempo real** ”.

![Março](/assets/images/script7-4237a49b3318c0c9835aecdcd0bf693d.png)  
---  
  
Quando selecionada, é possível visualizar os registros do log de processamento dos scripts atualizados frequentemente via a opção já existente de “Log de execução” ou para download do usuário. Nos casos onde não for selecionada, esses mesmos registros de log ficarão disponíveis somente após o término do processamento e em formato de arquivo para download. 

Por padrão, a opção virá desmarcada e processos como agendamentos não disponibilizarão a opção. Esse comportamento se adequa ao intuito da funcionalidade de servir como uma saída para validações de lógica e fluxo em ambiente de desenvolvimento ou validação.

IMPORTANTE!

O período de disponibilidade do arquivo se manterá, permanecendo disponível para download e acesso durante o período de 30 dias.

  * **27/03/2023**
    * Monitorando em tempo real as execuções
    * Executando no contexto de outra entidade
  * **10/03/2023**
    * Log de execução de Scripts