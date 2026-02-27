---
title: Dezembro | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2025/dezembro
crawled_at: 2026-02-27 13:01:20
---

Pular para o conteúdo principal

Nessa página

## 18/12/2025​

### Novo parâmetro de visibilidade para verificação de documentos assinados​

Foi implementado um novo parâmetro que permite indicar o modo de visibilidade (público ou privado) para a verificação de documentos assinados digitalmente gerados via script ou integração. Esta melhoria permite que desenvolvedores e integradores definem se a execução de um relatório integrado deve resultar em um documento público, facilitando a validação externa da assinatura.

Anteriormente, a opção de definir a visibilidade do documento estava disponível apenas na execução manual em tela. Execuções via script (integrações) não possuíam essa opção e geram documentos privados por padrão, o que causava problemas na hora de validar a assinatura, especialmente em contextos como o sistema Saúde.

Com esta alteração, o comportamento da geração via script equipara-se às opções de tela, permitindo flexibilidade na definição de acesso ao documento assinado.

![scripts](/assets/images/scripts238-c352b8fa54c1101061b373013adde2d8.png)  
---  
  
Ao configurar a execução de um script que chama um relatório com assinatura digital:

  * Identifique o novo parâmetro de visibilidade disponível na chamada da função ou requisição.
  * Defina o parâmetro para indicar se o documento será Público ou Privado.
  * Ao optar pelo modo "Público", a validação da assinatura do documento poderá ser realizada sem as restrições de acesso que ocorriam quando o documento era gerado automaticamente como privado.

  * 18/12/2025
    * Novo parâmetro de visibilidade para verificação de documentos assinados