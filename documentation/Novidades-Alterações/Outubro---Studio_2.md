---
title: Outubro | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2022/outubro
crawled_at: 2026-02-27 13:02:46
---

Pular para o conteúdo principal

Nessa página

## **05/10/2022**​

### Adicionado propriedade para recuperar a lista de e-mails configurados para serem notificados na execução de um Script​

Adicionado a propriedade “**emailsNotificacao** ” ao contexto do script. Esta propriedade retornará a lista de e-mails configurados na etapa de "**Opções de execução** ". No caso de não haver sido configurado nenhum e-mail, será retornado um objeto nulo.

Na prática, a propriedade permitirá, por exemplo, que o desenvolvedor crie regras onde ao ocorrer falha de validação ou de execução, os usuários configurados para receberem a notificação poderão ser informados via programação conforme o desejado. 

**Exemplo:**

     if (contextoExecucao.emailsNotificacao != null) {  
       remetente = "ped@betha.com.br"  
       
       contextoExecucao.emailsNotificacao.each {  
           email = Email.novo()  
           email.de(remetente, "Email de ${remetente}")  
                .para(it, "Para ${it}")  
                .assunto("Execução de Script")  
               .mensagem("Você está recebendo este e-mail, pois está configurado nas opções de execução do agendamento")  
                .enviar()  
       }  
    }  

* * *

### Alteração no painel principal de listagem do Gerenciador de Scripts​

Implementada melhorias no painel principal de listagem do Gerenciador de Scripts. Agora, em prol de um maior alinhamento da ferramenta ao que se destina — desenvolvimento de scripts — a listagem trará informações mais relevantes ao desenvolvimento, como data de criação, data da última modificação, versão e descrição. Todas essas colunas são ordenáveis e estão dispostas conforme disponibilidade para as listagens filtradas de: rascunhos, favoritos, flexibilizados e naturezas.

OBSERVAÇÃO! 

Os arquivos e dados das execuções, que eram anteriormente exibidos, encontram-se disponíveis ainda via F4 das aplicações. Através de filtros e da navegação para a sessão desejada, terá acesso aos artefatos gerados, bem como demais informações.

![Outubro](/assets/images/script6-40c4946c8753cf8324e9ccb50a9f0f98.png)  
---  
  
* * *

### Flexibilização de Tags​

Implementado melhoria no controle das tags flexibilizadas ao cliente, onde o sistema conduzirá uma “mescla” das tags previamente configuradas pelo cliente (ou outras entidades) com a enviada pela entidade atual.

Dessa forma, problemas enfrentados anteriormente de sobrescrita ou perda de tags ao efetuar novas orquestrações não mais ocorrerão.

  * **05/10/2022**
    * Adicionado propriedade para recuperar a lista de e-mails configurados para serem notificados na execução de um Script
    * Alteração no painel principal de listagem do Gerenciador de Scripts
    * Flexibilização de Tags