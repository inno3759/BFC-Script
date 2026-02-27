---
title: Dezembro | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2024/dezembro
crawled_at: 2026-02-27 13:01:45
---

Pular para o conteúdo principal

Nessa página

## 12/12/2024​

### Novo Formato de Segurança para Scripts que utilizam as APIs do Service Layer​

A Betha está promovendo mudanças importantes visando aumentar a segurança na comunicação de Scripts com as APIs do Service Layer. Atualmente, o uso direto de tokens nos scripts gera uma série de desafios, que incluem:

  * **Riscos de segurança** : emissão e configuração dos tokens em scripts, onde o mesmo fica exposto e pode ser usado para outros fins.
  * **Interrupções nos serviços** : falhas em scripts devido a tokens expirados.
  * **Manutenção recorrente** : necessidade de renovação anual dos tokens.

Para resolver estas questões, implementamos um novo modelo de integração baseado em chaves de integração configuradas no Gerenciador de Acessos.

**Guia para Adequação**

Abaixo estão instruções para configurar seus scripts e garantir a continuidade do funcionamento após a data limite para adequação.

**1\. Configurando a integração no gerenciador de acessos**

No **Gerenciador de Acessos** , vá até a aba **Integrações**. Nesta seção, você pode gerenciar integrações existentes ou criar uma nova. Para adicionar uma integração, clique no botão **+INTEGRAÇÃO**.

![novembro](/assets/images/scripts16-3d2e6bbf1a97185c7922cf624139e319.png)  
---  
  
Preencha os campos obrigatórios, **Natureza da Integração** , **Sistema de Origem** e **Entidade de Origem** de acordo com as especificações da integração. Após configurar todos os campos, finalize e salve a integração para que ela esteja disponível para uso nos scripts.

![novembro](/assets/images/scripts17-0267be2d5011651205b9b2cc81447acc.png)  
---  
  
**Dica de preenchimento:**

  * **Natureza da Integração** : integração via Scripts.
  * **Sistema de Origem** : informe o sistema onde o script vai realizar a integração.
  * **Entidade de Origem** : informe a entidade onde o script vai realizar a integração.

Após configurar e salvar a integração, o **Identificador de Integrações** será exibido na listagem da aba de Integrações, ficando disponível para consulta e utilização. A chave de integração só poderá ser utilizada em scripts rodando no sistema e entidade de origem.

![novembro](/assets/images/scripts18-f733241fcdbf2d9fbfc29e71b65b2201.png)  
---  
  
**2\. Configurando o Script para fazer uso da integração**

Para habilitar o novo formato de autenticação para comunicação com o Service Layer a partir de um script é necessário fazer um ajuste pontual no script.

O exemplo abaixo mostra a forma de autenticação atual e que será **descontinuada** em breve:

    Http.servico('https://endereco.betha.cloud/...')   
        .cabecalho('Authorization', "Bearer ${tokenIntegracao}")   
        .[POST|GET...]()  

Abaixo, o **novo modelo** , onde utilizamos uma chave de chave de integração. No exemplo abaixo, estamos passando a chave de integração através de uma variável de ambiente.

    Http.servico('https://endereco.betha.cloud/...')  
        .chaveIntegracao(Variavel.CHAVE_INTEGRACAO)  
        .[POST|GET...]()  

É fortemente recomendado que as chaves de integração sejam configuradas em **variáveis de ambiente** , para facilitar tanto a orquestração de scripts, quanto a parametrização na entidade do cliente.

Para obter mais detalhes sobre o método adicionado à API HTTP do script, consulte a documentação disponível [aqui](https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-http/#chaveintegracaoidentificador).

**3\. Trabalhando com dados de mais de uma entidade**

Para usuários que precisam acessar dados de múltiplas entidades, o script deve ser configurado para gerenciar diferentes chaves de integração. Isso pode ser feito criando uma **variável de ambiente específica para cada entidade**. 

No **Gerenciador de Scripts** , acesse a seção **Variáveis de Ambiente** para realizar as configurações necessárias.

![novembro](/assets/images/scripts19-fc78324d7219f1620f825f25a0adaab7.png)  
---  
  
Utilize o botão **+VARIÁVEL** para inserir novas variáveis. Dessa forma, você pode adicionar várias chaves de integração, cada uma correspondente a uma entidade diferente.

![novembro](/assets/images/scripts20-30f612786332253a1036e498bc159ca9.png)  
---  
  
**Prazos e ajustes**

  * ~~Data limite para adequação: 31/01/2025.~~

  * **Nova data limite para adequação: 14/02/2025**

  * **Scripts a serem ajustados** : será enviada uma lista completa de scripts executados em 2024 por e-mail para cada entidade desenvolvedora (Betha, revendas e parceiros).

**ATENÇÃO!**

Após a data limite, o consumo das APIs do Service Layer via Scripts utilizando tokens será descontinuado e a utilização do header **Authorization** nas comunicações será bloqueado.

Recomendamos a todos os responsáveis que iniciem a adequação o quanto antes, para evitar interrupções nos serviços e garantir a conformidade com as novas diretrizes de segurança.

## 11/12/2024​

### Emissão de Tokens de Conversão e Integração para Revendas​

Prezados,

Recentemente, foi necessário revisar e adequar nossas políticas de segurança relacionadas a _tokens_ de _service layer_ devido a situações envolvendo o uso indevido desses _tokens_ para alteração de dados em bases de clientes. Tais práticas geraram preocupações por parte da Betha, de clientes e até mesmo de algumas revendas.

A camada de serviços conhecida como _service layer_ foi originalmente concebida para atender demandas de conversões e tratamentos de dados. Contudo, ao longo do tempo, passou a ser utilizada também para integrações entre produtos, o que acarretou uma série de problemas, como:

  * Necessidade de renovação periódica dos _tokens_ , gerando indisponibilidades nas integrações;
  * Exposição de _tokens_ com alto impacto nas bases dos clientes;
  * Falta de rastreabilidade, uma vez que os _tokens_ não identificam o usuário que realizou a requisição da API, prejudicando a auditoria e a identificação de ações.

Diante desse cenário, o acesso à funcionalidade de emissão de _tokens_ destinados à integração (emitidos em nome da revenda, com validade de até 1 ano) foi removido de todos os usuários. Foi reforçada a utilização de _tokens_ emitidos em nome do próprio usuário que realizará operações na base de um cliente, promovendo maior segurança e rastreabilidade.

**Solicitações de acesso para integração:**

Entendemos que, no contexto atual, algumas demandas ainda exigem o uso de _tokens_ de integração. Por esse motivo, revendas que necessitarem dessa funcionalidade poderão solicitá-la por meio da abertura de um chamado para o sistema **Admin**. A solicitação deve incluir:

  * Relação dos IDs dos usuários na Central do Usuário que deverão receber o acesso.

![novembro](/assets/images/scripts10-b53b37deb275ee20140e66d2ede14928.png)  
---  
  
Reforçamos a recomendação de utilizar _tokens_ emitidos em nome dos usuários para rotinas de conversão e tratamento de dados conforme o **Comunicado Emissão e Uso de Tokens para Conversão e Tratamento de Dados**. Essa prática permite um controle mais eficaz e a rastreabilidade das ações, enquanto o uso de _tokens_ emitidos em nome da revenda deve ser limitado exclusivamente a integrações.

Agradecemos pela compreensão e colaboração na aplicação dessas medidas.

Atenciosamente,

* * *

## 10/12/2024​

### Novas Diretrizes para Tokens de Conversão e Tratamento de Dados​

A emissão e o uso dos _tokens_ para conversão e tratamento de dados devem seguir algumas novas diretrizes para garantir a segurança e a conformidade dos processos. Cada técnico é responsável por emitir seu próprio _token_ , que é de uso pessoal e intransferível.

IMPORTANTE!

Os _tokens_ **não devem ser compartilhados** com outros usuários. O sistema mantém registros auditáveis de todas as ações realizadas em nome do técnico, garantindo segurança e rastreabilidade.

Os _tokens_ emitidos para técnicos **não devem** ser utilizados para integrações entre sistemas. Isso inclui a **Integração desktop/cloud,** para essa finalidade, a configuração de _tokens_ deve ser solicitada à equipe de suporte técnico, que será responsável pela emissão e gestão dos _tokens_ de integração no Service Layer.

Tokens utilizados para **migração** devem ser emitidos exclusivamente para o técnico responsável por essa tarefa. **Tokens gerados para integração NÃO devem ser usados para migração.**

Para emitir _tokens_ , é necessário que o técnico tenha acesso ao **Admin**. Caso esse acesso não esteja disponível, o técnico deve solicitar a liberação ao gestor responsável. Se o gestor também não possuir acesso ao **Admin** , o **gestor deve abrir um chamado** em <https://atendimento.betha.com.br/> solicitando o acesso.

O usuário deve preencher os itens obrigatórios para abertura do chamado, como orientado na imagem abaixo, deve-se informar também o usuário do gestor cadastrado na **Central do Usuário**.

![novembro](/assets/images/scripts11-7acd80b084ad60dee0cab995ad5f9571.png)  
---  
  
**Acesso ao Admin**

Para emitir um _token_ , o técnico deve ter acesso ao Admin. Caso não tenha, é necessário solicitar ao gestor responsável.

Para ter acesso ao sistema Admin é necessário utilizar o seguinte endereço: [admin.betha.com.br](http://admin.betha.com.br/). Ao acessá-lo, o usuário é direcionado a tela de _login_ , onde deve informar o nome de usuário cadastrado na **Central de Usuário** (Para mais informações clique [aqui](https://suite.ajuda.betha.cloud/suite/central-do-usuario/apresentacao)) e Senha. Logo após é necessário clicar no botão **ENTRAR**.

![novembro](/assets/images/scripts12-7f8d6b0fbe8d21f431a32e756e38e6ef.png)  
---  
  
**Permitindo usuários técnicos por Revenda​**

O gestor deve autorizar o usuário técnico no seguinte local - **Atendimento > Fly e Cloud > Usuários técnicos permitidos por Revenda**.

![novembro](/assets/images/scripts13-4d796a61afcf6027535e0ad09fb5fdce.png)  
---  
  
Ao clicar na opção mencionada acima, uma nova janela é aberta para que o gestor possa conceder acesso. É necessário selecionar a Revenda ao qual o acesso técnico será concedido. É necessário clicar no botão **Adicionar** , inserir o usuário e, logo após, clicar em **Gravar** para salvar as informações. A partir disso, será possível acessar o recurso **Token de Conversão para o usuário,** dentre outras funcionalidades disponíveis aos técnicos. 

Caso o técnico atue em clientes de várias regiões, deve-se conceder acesso ao técnico a revenda **BETHA SISTEMAS - Uso interno** , onde o técnico conseguirá interagir com os clientes de todas as revendas/filiais.

![novembro](/assets/images/scripts14-f781edc7e856ba352cfa5a28341e53a9.png)  
---  
  
IMPORTANTE!

  * Ao remover um usuário da revenda/filial, ele perderá os acessos.

**Emitindo _token_ de conversão**

Para emitir o _token_ de conversão, o técnico deve acessar o menu **Atendimento > Conversões > Token de Conversão para o usuário**.

![novembro](/assets/images/scripts15-984bf5bf98b8030101cb54981ac51129.png)  
---  
  
  * 12/12/2024
    * Novo Formato de Segurança para Scripts que utilizam as APIs do Service Layer
  * 11/12/2024
    * Emissão de Tokens de Conversão e Integração para Revendas
  * 10/12/2024
    * Novas Diretrizes para Tokens de Conversão e Tratamento de Dados