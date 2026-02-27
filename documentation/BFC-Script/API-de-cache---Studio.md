---
title: API de cache | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-cache
crawled_at: 2026-02-27 13:01:02
---

Pular para o conteúdo principal

Nessa página

O bfc-script disponibiliza uma API para armazenar valores pequenos em cache (máximo de 10kb), como dados de autenticação de serviços externos. O valor é armazenado usando o contexto de sistema, database e entidade.

## Cache.adicionar(chave, valor)​

Adiciona um novo valor no cache, com a chave informada e o tempo de expiração (TTL) padrão de 12 horas. Tempo máximo de 48 horas.

    Cache.adicionar('meu-token', 'aaabbbccc')  

## Cache.adicionar(chave, valor, expirarEm)​

Adiciona um novo valor no cache, com a chave informada e o tempo de expiração (opcional).

    Cache.adicionar('meu-token', 'aaabbbccc', 2.horas)  

## Cache.recuperar(chave, valorPadrao)​

Recupera-se um valor colocado previamente no cache, ou retorna o valor padrão.

    Cache.recuperar('meu-token', '')  

## Cache.contem(chave)​

Verifica se o cache contém algum valor para a chave informada.

## Cache.remover(chave)​

Remove o valor para a chave informada.

  * Cache.adicionar(chave, valor)
  * Cache.adicionar(chave, valor, expirarEm)
  * Cache.recuperar(chave, valorPadrao)
  * Cache.contem(chave)
  * Cache.remover(chave)