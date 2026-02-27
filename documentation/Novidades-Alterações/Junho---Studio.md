---
title: Junho | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/novidades/2022/junho
crawled_at: 2026-02-27 13:02:59
---

Pular para o conteúdo principal

Nessa página

## **13/06/2022**​

### Credenciais para e-mails do gmail​

O Google disponibilizou em seu canal de [ajuda](https://support.google.com/accounts/answer/6010255?hl=pt-BR) a seguinte informação:

"_A partir de 30 de maio de 2022, o Google não autorizará mais o uso de apps ou dispositivos de terceiros que exigem apenas nome de usuário e senha para fazer login na Conta do Google. Essa mudança tem como objetivo proteger sua conta…_ "

Isso significa que a autenticação precisará ser realizada em duas etapas, ou seja, é necessário ter a configuração em dois fatores ativados. Antes desse prazo era possível enviar e-mail mesmo que essa configuração estivesse desabilitada utilizando usuário e senha para enviar e-mail por exemplo, agora, não é mais possível. Ao habilitar a autenticação de dois fatores o Google permite cadastrar senha para aplicativos, permitindo cadastrar informações, logo é gerado uma senha para ser utilizada no lugar da senha principal do usuário no envio do e-mail. Para habilitar essa funcionalidade clique em **Gerenciar sua conta > Segurança > Verificação em duas etapas**. 

![Junho](/assets/images/script13-3dbc6afb0e6075affd4c1d384adeb1b7.png)  
---  
  
Siga os próximos passos conforme solicitado, a partir do momento que que a configuração é habilitada aparece na tela. Clique em **Senha de app** para cadastrar uma senha para um determinado aplicativo.

![Junho](/assets/images/script14-4f40dee8a08db5ff6c5fc65545e3e674.png)  
---  
  
Escolha o app e o dispositivo e pressione o botão **GERAR**.

![Junho](/assets/images/scrip15-04f166494324a3ef6971581ed02b3877.png)  
---  
![Junho](/assets/images/script15-065f75ec7d79ce6bf822c9ca650f2f5f.png)  
---  
  
Ao clicar no botão mencionado, a senha gerada é apresentada na tela.

![Junho](/assets/images/script16-bf12726ae5a2bd44a7b6ef4297c5b455.png)  
---  
  
IMPORTANTE!

Essa senha será utilizada no lugar da senha principal do seu email no ambiente de scripts.

Para maiores informações consulte nossa documentação existente, clicando [aqui](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-email/#exemplos).

Exclua a(s) senha(s) no ícone de lixeira ou adicione outras senhas caso desejar. 

![Junho](/assets/images/script17-9cd815917c8b16e67001068ade10f94a.png)  
---  
  
* * *

### Agendando scripts de forma programática​

Foi disponibilizada a funcionalidade de agendamentos automáticos nos scripts, sendo assim, agora existe uma forma programática de realizar os agendamentos. Portanto, agora há duas maneiras de realizar um agendamento: de forma [visual](https://docs.plataforma.betha.cloud/docs/extensoes/scrip-ts/executando-script#agendando-scripts) e [programática](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-script#agendando-scripts).

As sugestões de uso dessa funcionalidade são:

  * Esperar o processamento de um lote enviado para algum serviço;
    * No lugar de parar a execução atual, utilizando o método **esperar** , basta agendar o mesmo ou outro script passando os parâmetros necessários para a consulta;
  * Executar um processo incremental sem a necessidade de fazer um agendamento customizado;
  * De forma geral, em todos os lugares onde hoje se utiliza o **esperar**.

**Como realizar um agendamento?**

Utilizando o comando _Script.identificador.agendar('1m')_ onde o **Script** é palavra reservada, seguida do **identificador** do script a ser agendado e o método **agendar()** , que pode receber os paramentos da execução, juntamente com o tempo de agendamento, ou simplesmente o tempo. 

![Junho](/assets/images/script18-5f723212e4cd9aee6f907425f0bdb212.png)  
---  
![Junho](/assets/images/script19-10a6e1f9ee4962cc0b7769d0dd5940ab.png)  
---  
  
Acesse [aqui](https://docs.plataforma.betha.cloud/docs/extensoes/bfc-script/api-script#agendarparametros-para) para ter acesso ao material sobre essa melhoria.

* * *

### Executando Relatórios e Scripts no contexto de outra entidade no modo rascunho​

Agora as ferramentas **Relatórios** e **Scripts** permitem executar artefatos no contexto de outra entidade no modo rascunho, agilizando assim o processo de desenvolvimento dos artefatos sem necessidade de publicar para só depois visualizar as execuções realizadas.

Para tornar visíveis as execuções habilite o parâmetro **Rascunho** , localizado no ícone simbolizado por um olho no lado direito da tela.

![Junho](/assets/images/script20-034154a6c89901746d732653c7ae892f.png)  
---  
  
Logo, todas as execuções são apresentadas inclusive em formato de rascunho.

![Junho](/assets/images/script21-766152de27ee488545442d16076be61e.png)  
---  
  
  * **Relatórios**

![Junho](/assets/images/script22-ccdf89b9c5435d8a15269b010b4f8144.png)  
---  
  
  * **Scripts**

![Junho](/assets/images/script23-e7c12a3d558ea0e6fc6eca2774d2c275.png)  
---  
  
* * *

### Visualizando tags na listagem de extensões​

Foi implementado nas ferramentas Relatórios e Scripts a possibilidade de visualizar as **Tags** de extensões diferenciando-as mesmo que tenham nomes iguais. Esse recurso está localizado em **Visualizar > Tags**.

![Junho](/assets/images/script24-81c8ca716fc41b37770bc57f3a939fec.png)  
---  
  
Todas as **Tags** são mostradas na cor cinza, logo, os **Atributos** na cor branca.

![Junho](/assets/images/script25-9f32f35fbd3711417f48a5a49ecdc1f6.png)  
---  
  
LEMBRE-SE!

Mesmo atualizando ou saindo da página, será mantida a última configuração, ou seja, se a opção Tags estiver habilitada continuará aparecendo as informações na tela. Não aparecerá quando o parâmetro for desabilitado.

* * *

### Acessando opções de execução quando necessário​

Nas ferramentas Assistente F4, Relatórios e Scripts as opções de execução ficam ocultas podendo ser acessadas quando desejado pelo usuário, essa melhoria tem o intuito de diminuir as informações apresentadas na tela de execução. Para visualizar as opções de execução pressione o botão **OPÇÕES**.

![Junho](/assets/images/script26-a6f45182daa25c2befd200fae0fd9126.png)  
---  
![Junho](/assets/images/script27-6e5771242c8b2ab2ace9af445aab30e5.png)  
---  
  
Marcando as opções desejadas, aparece um indicador de campo quando as informações estão ocultas.

![Junho](/assets/images/script28-bd7a9af092b262711ae07c3f27a59470.png)  
---  
  
Quando as opções estiverem ocultas e houver opções com campos obrigatórios não preenchidos é exibido uma indicação de alerta.

![Junho](/assets/images/script29-1a70ff0bae3341becf0323ed10150ab4.png)  
---  
  
  * **13/06/2022**
    * Credenciais para e-mails do gmail
    * Agendando scripts de forma programática
    * Executando Relatórios e Scripts no contexto de outra entidade no modo rascunho
    * Visualizando tags na listagem de extensões
    * Acessando opções de execução quando necessário