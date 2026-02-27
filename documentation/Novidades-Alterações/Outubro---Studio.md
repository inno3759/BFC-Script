---
title: Outubro | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2024/outubro
crawled_at: 2026-02-27 13:01:50
---

Pular para o conteúdo principal

Nessa página

## 10/10/2024​

### Novos Parâmetros na API de Assinaturas e Gerenciador de Scripts​

A partir de agora, é possível configurar a natureza e os marcadores ao enviar documentos para assinatura através da API de Assinaturas. Essa funcionalidade permite que os documentos enviados sigam um padrão definido pela sua organização, garantindo maior padronização. Além disso, os marcadores auxiliam na categorização e localização rápida dos documentos dentro do sistema.

Agora, ao enviar um relatório pelo **Gerenciador de Scripts** , você pode adicionar novos parâmetros de configuração, permitindo controle sobre o processo de assinatura de documentos. Essas opções proporcionam maior padronização na gestão dos documentos.

Novos Parâmetros Disponíveis:

  * `naturezaQualificadora`: Define a natureza do documento.
  * `marcadores`: Permite atribuir valores aos marcadores do documento, informados no formato JSON. Esses - marcadores podem ser usados posteriormente para pesquisar documentos dentro da Ferramenta de Assinatura.
  * `expiraEm`: Estabelece a data e hora limite para a conclusão do processo de assinatura. Após esse prazo, o processo é concluído com a situação "Expirado".
  * `permiteAdicionarNovosAssinantes`: Enquanto o processo de assinatura estiver aberto, será possível - adicionar novos assinantes.
  * `publico`: Define a visibilidade das informações do processo. Se definido como público, qualquer usuário com o hash do documento pode consultar as informações através do Verificador. Se privado, apenas usuários logados e participantes do processo podem acessar as informações de assinatura.
  * `bloqueiaCertificadoCorporativo`: Quando definido como true, indica que o documento não deve ser assinado por um certificado corporativo.
  * `permiteCertificadoAvancadoParaUsuarioVerificado`: Quando true, permite que o documento seja assinado por um certificado do tipo Avançado, desde que o usuário tenha sua identidade verificada.
  * `assinarComCampoInvisivel`: Aplicável somente a documentos do tipo PDF. Quando true, o processo de plotagem não é realizado, mantendo o conteúdo original do documento e evitando a corrupção de assinaturas já realizadas ou futuras.

![Outubro](/assets/images/scripts9-3816d7f62606b05b81369c938fe7eac3.png)  
---  
  
Dessa forma, é possível personalizar a natureza e os marcadores dos documentos, assegurando conformidade com os padrões da sua organização, gerenciar os prazos, adicionamento de assinantes e visibilidade das informações conforme a necessidade do seu fluxo de trabalho e controlar quais tipos de certificados podem ser utilizados na assinatura dos documentos, aumentando a segurança dos processos.

Para isso, você deve ajustar seus scripts no **Gerenciador de Scripts** para incluir os novos parâmetros conforme necessário, assim, você pode incorporar os novos parâmetros em seus processos de envio de documentos para assinatura. Você pode também realizar testes com os novos parâmetros para garantir que as configurações atendem às suas expectativas e necessidades operacionais.

  * 10/10/2024
    * Novos Parâmetros na API de Assinaturas e Gerenciador de Scripts