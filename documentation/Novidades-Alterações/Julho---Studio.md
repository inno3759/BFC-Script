---
title: Julho | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2025/julho
crawled_at: 2026-02-27 13:01:25
---

Pular para o conteúdo principal

Nessa página

## 23/07/2025​

### Limite de tempo no método `esperar()` em Scripts​

Foi implementado um limite máximo de **10 minutos** (600 000 milissegundos) para o tempo de espera acumulado que pode ser invocado pelo método `esperar()` dentro de um único script. A medida visa otimizar o uso de recursos do servidor, prevenir que scripts fiquem inativos por tempo excessivo e garantir a estabilidade da aplicação. Para não impactar negativamente os scripts existentes, a validação é aplicada de forma distinta para scripts novos e antigos, através de um sistema de **Especificações**.

**Limite de Tempo**

  * O tempo de espera total acumulado por um script não pode exceder **10 minutos** (600 000 ms).

**Sistema de Especificações**

Para evitar a quebra de scripts antigos que dependiam do comportamento anterior, criamos duas especificações:

  * **Especificação 1 (Scripts Legados)**

    * **A quem se aplica:** scripts criados antes da atualização. 
    * **Comportamento:** o limite de 10 minutos **NÃO** é restritivo; o script não falhará. 
    * **Sinalização:** execução marcada com status **Aviso** (amarelo) quando o limite recomendado é excedido.
  * **Especificação 2 (Scripts novos e modificados)**

    * **A quem se aplica:** scripts criados ou editados a partir da atualização. 
    * **Comportamento:** o limite de 10 minutos **É OBRIGATÓRIO**. 
    * **Sinalização:** execução interrompida e registrada com status **Erro** se o limite for excedido.

Impacto

  * **Scripts antigos (Especificação 1):**

    * Continuam funcionando sem falhas. 
    * Recomenda-se monitorar avisos (amarelo) e revisar scripts para otimizar chamadas a `esperar()`.
  * **Scripts novos (Especificação 2):**

    * Devem respeitar o novo limite durante o desenvolvimento. 
    * Lógicas que dependam de pausas longas precisam ser reavaliadas ou divididas em múltiplos scripts.

**Boas Práticas**

  * **Use com moderação:** `esperar()` é para pausas curtas, não controle de fluxo prolongado. 
  * **Cuidado com loops:** evite chamadas a `esperar()` dentro de laços de repetição. 
  * **Revise a lógica:** se precisar “esperar” muito tempo, avalie quebrar o processo ou usar gatilhos alternativos.

  * 23/07/2025
    * Limite de tempo no método `esperar()` em Scripts