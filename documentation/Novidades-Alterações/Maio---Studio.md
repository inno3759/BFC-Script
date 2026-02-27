---
title: Maio | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2023/maio
crawled_at: 2026-02-27 13:02:22
---

Pular para o conteúdo principal

Nessa página

## **11/05/2023**​

### Restrições no API de Cache​

A partir do dia 15/05 a API de Cache que é um recurso do BFC Script, terá um TTL (tempo de expiração) **máximo de 48 horas**. Este cache armazena dados de até 10kb para serem reaproveitados durante as próximas execuções no contexto da entidade e sistema, hoje possui uma configuração padrão de 12h quando não informado no momento da criação.

Solicitamos que observem as devidas mudanças nas implementações para que as extensões continuem a funcionar conforme o esperado. Essa mudança se deve ao alto volume de armazenamentos criados com prazos muito longos, elevando o custo para manter esses dados e causando um impacto no desempenho do recurso. 

Para mais informações sobre os recursos, favor consultar nossa documentação:

<https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-cache>

### Adequação de acesso a usuários administrativos no Studio Extensões​

Em um movimento de adequação do Studio Extensões para um ambiente integrado de desenvolvimento, comunicamos que a partir desta publicação, a regra de acesso para usuários administradores valerá também da validação do contexto.

Desta forma, usuários que apenas são administradores de contextos estendidos (como unidades de ensino ou de saúde, por exemplo) não conseguirão mais acessar a ferramenta. Usuários administrativos ao nível de entidade, continuarão com os acessos conforme regras previamente estabelecidas.

  * **11/05/2023**
    * Restrições no API de Cache
    * Adequação de acesso a usuários administrativos no Studio Extensões