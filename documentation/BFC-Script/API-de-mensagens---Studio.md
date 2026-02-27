---
title: API de mensagens | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-mensagens
crawled_at: 2026-02-27 13:00:14
---

Pular para o conteúdo principal

O bfc-script disponibiliza uma API para envio de mensagens de diversas naturezas, aos usuários dos sistemas. Essas funções estarão disponíveis ao usuário final apenas através da **Ferramenta de Eventos** , e serão absorvidas plenamente conforme a utilização.

A seguir são descritas todas as funções disponíveis para mensagens

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**erro(mensagem)**|  Adiciona uma nova mensagem de erro a ser apresentada ao usuário.  
**aviso(mensagem)**|  Adiciona uma nova mensagem de aviso a ser apresentada ao usuário.  
**info(mensagem)**|  Adiciona uma nova mensagem de informação a ser apresentada ao usuário.  
**sucesso(mensagem)**|  Adiciona uma nova mensagem de sucesso a ser apresentada ao usuário.  

    Mensagens.erro('Mensagem de erro')  
    Mensagens.aviso('Mensagem de aviso')  
    Mensagens.info('Mensagem de informação')  
    Mensagens.sucesso('Mensagem de sucesso')  

É possível ainda adicionar mensagens parametrizadas:

    Mensagens.erro('Mensagem de %s %s', 'erro', 'parametrizada')