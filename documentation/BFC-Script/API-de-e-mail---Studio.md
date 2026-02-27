---
title: API de e-mail | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-email
crawled_at: 2026-02-27 13:00:05
---

Pular para o conteúdo principal

Nessa página

A linguagem disponibiliza uma série de funções para envio de mensagens de e-mails. Essas funções estarão disponíveis ao usuário final apenas através da **Ferramenta de Scripts** , e serão absorvidas plenamente conforme a utilização.

Para criar uma nova mensagem de e-mail a ser enviada deve-se utilizar a função **E-mail.novo()**

     msg = Email.novo()  

Uma mensagem contém diversas características que serão apresentadas a seguir, uma vez configurada a mensagem, o envio é realizado através da função **enviar()** da mensagem.

    msg = Email.novo()  
    //configurações da mensagem  
    msg.enviar()  

## Mensagem​

A seguir são descritas todas as funções disponíveis para mensagem de e-mails.

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**de(email)**|  Define o e-mail do remetente da mensagem.  
**de(email, nome)**|  Define o e-mail e nome do remetente da mensagem.  
**para(email)**|  Adiciona um e-mail de destinatário na mensagem.  
**para(email, nome)**|  Adiciona um e-mail e nome de destinatário na mensagem.  
**copiaPara(email)**|  Adiciona um e-mail de cópia na mensagem.  
**copiaPara(email, nome)**|  Adiciona um e-mail e nome de cópia na mensagem.  
**copiaOcultaPara(email)**|  Adiciona um e-mail de cópia oculta na mensagem.  
**copiaOcultaPara(email, nome)**|  Adiciona um e-mail e nome de cópia oculta na mensagem.  
**responderPara(email)**|  Adiciona um e-mail no qual a mensagem deverá ser respondia pelos destinatários.  
**responderPara(email, nome)**|  Adiciona um e-mail e nome no qual a mensagem deverá ser respondia pelos destinatários.  
**mensagem(mensagem)**|  Define o conteúdo da mensagem.  
**mensagemHtml(mensagem)**|  Define o conteúdo da mensagem como HTML.  
**assunto(assunto)**|  Define o assunto da mensagem.  
**cabecalho(nome, valor)**|  Adiciona um cabeçalho no e-mail.  
**autenticacao([usuário, senha, porta, host])**| Autentica o envio do email. Exemplo de uso:.autenticacao([ usuario: joao, senha: joao, porta: 587, host: smtp.live.com])  
**enviar()**|  Envia a mensagem de e-mail.  
  
## Anexos​

A API conta com 2 tipos de anexos disponíveis, sendo um baseado em fonte de arquivos e outro em URL. Exemplos de fonte de arquivos são os parâmetros do script do tipo Arquivo e artefatos gerados pela API de arquivos.

**Criando anexos:**

A criação de anexos pode ser realizada através de funções específicas da API ou de forma simplificada pela mensagem. Anexos criados pelas funções da API devem ser manualmente adicionados à mensagem. Por motivo de performance, caso o mesmo anexo do tipo Arquivo tenha que ser enviado para vários destinatários em mensagens diferentes, este deverá ser criado pela API uma única vez no processo.

A seguir são descritas todas as funções disponíveis para anexos de e-mails.

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**Email.criarAnexoUrl()**|  Cria um novo anexo do tipo URL.  
**Email.criarAnexoUrl(url)**|  Cria um novo anexo do tipo URL informando o endereço.  
**Email.criarAnexoUrl(url, nome)**|  Cria um novo anexo do tipo URL informando o endereço e o nome a ser utilizado na mensagem.  
**Email.criarAnexoArquivo()**|  Cria um novo anexo do tipo arquivo.  
**Email.criarAnexoArquivo(arquivo)**|  Cria um anexo do tipo arquivo com base em uma fonte de arquivos.  

    csv = Arquivo.novo('teste.csv', 'csv')  
     csv.escrever('Valor')  
     csv.fechar()  
       
     //Arquivo criado pela API de arquivos  
     anexoArquivo = Email.criarAnexoArquivo(csv)  
       
     //Parâmetro do script tipo Arquivo  
     anexoParametro = Email.criarAnexoArquivo(parametros.xml.valor)  
       
     Email.novo()  
        .anexar(anexoArquivo)  
        .anexar(anexoParametro)  

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**Email.criarAnexoArquivo(arquivo, nome)**|  Cria um anexo do tipo arquivo com base em uma fonte de arquivos. O nome do anexo será o mesmo informado no parâmetro nome.  
**nome(nome)**|  Nome do anexo.  
**descricao(descricao)**|  Descrição do anexo.  
**dispostoParaVisualizacao()**|  Define a disposição do anexo para visualização INLINE no corpo do e-mail.  
**dispostoComoAnexo()**|  Define a disposição do anexo como ATTACHMENT (arquivo anexado).  
**incorporado()**|  Define o anexo como incorporado. Esta opção irá gerar um CID com base no nome do anexo e poderá ser utilizado no corpo da mensagem para referenciar o anexo.  
**naoIncorporado()**|  Define o anexo como não incorporado. Por padrão todos os anexos criados não são incorporados.  
**url(url)**|  Define a url para anexos do tipo URL.  
**arquivo(arquivo)**|  Define a fonte do arquivo para anexos do tipo Arquivo.  
**anexar(anexo)**|  Adiciona um anexo criado a partir das funções E-mail.criarAnexoXX() à mensagem.  

    anexo = Email.criarAnexoUrl('http://cnd.fgv.br/sites/cnd.fgv.br/files/teste_2.pdf', 'Nome do arquivo.pdf')  
     msg.anexar(msg)  

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**anexarArquivo(origem)**|  Adiciona um anexo à mensagem com base em uma fonte de arquivo. Exemplos de fontes são o valor de um parâmetro do script do tipo arquivo e um arquivo criado pela API de arquivos.  

    csv = Arquivo.novo('teste.csv', 'csv')  
     csv.escrever('Valor')  
     csv.fechar()  
       
     //Arquivo criado pela API de arquivos  
     msg.anexarArquivo(csv)  
       
     //Parâmetro do script tipo Arquivo  
     msg.anexarArquivo(parametros.xml.valor)   

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**anexarArquivo(origem, nome)**|  Adiciona um anexo à mensagem com base em uma fonte de arquivo. O nome do anexo na mensagem será o mesmo informado no parâmetro nome.  
**anexarArquivo(anexoArquivo)**|  Adiciona um anexo criado a partir da função E-mail.criarAnexoArquivo à mensagem.  
**anexarUrl(url)**|  Adiciona um anexo à mensagem com base em uma URL. O _download_ do anexo será realizado e adicionado a mensagem.  
**anexarUrl(url, nome)**|  Adiciona um anexo à mensagem com base em uma URL. O _download_ do anexo será realizado e um anexo com o nome parametrizado será adicionado.  

    msg.anexarUrl('http://cnd.fgv.br/sites/cnd.fgv.br/files/teste_2.pdf', 'Nome do arquivo.pdf')  

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**  
---|---  
**anexarUrl(anexoUrl)**|  Adiciona um anexo criado a partir da função Email.criarAnexoUrl à mensagem.  
  
## Exemplos​

    Email.novo()  
        .autenticacao([ usuario: 'usuario', senha: 'senha', porta: 'porta', host: 'smtp.live.com' ])  
        .de('betha@betha.com.br','Betha Sistemas')  
        para(destinatario, 'Destinatário')  
        .mensagem('Testando envio de email')  
        .assunto('Envio cloud job')  
        .enviar();  

Envio de e-mail com anexos:

    email = Email.novo()  
         
    imagemAssinatura = Email.criarAnexoUrl('http://www.betha.com.br/site/images/betha-2.png', 'logo.png')  
                            .dispostoParaVisualizacao()  
                            .incorporado()  
         
    destinatario = 'destinatario@betha.com.br'  
         
    email.de('betha@betha.com.br','Betha Sistemas')  
         .para(destinatario, 'Destinatário')  
         .copiaPara(destinatario, 'Destinatário de cópia')  
         .copiaOcultaPara(destinatario)  
         .responderPara(destinatario, 'Nome para Resposta')  
         .assunto('Teste de e-mail')  
         .mensagemHtml('Este é um teste de e-mail. <br/><br/>' +  
                          'Att, <br/><br/>' +  
                          'Betha Sistemas <p/><p/>' +   
                          '<img src="cid:logo.png" width="319" height="51" />')  
         .anexar(imagemAssinatura)  
         .anexarUrl('http://cnd.fgv.br/sites/cnd.fgv.br/files/teste_2.pdf', 'Nome do arquivo.pdf')  
         .enviar()  

    imprimir 'E-mail enviado com sucesso!'  

Enviar arquivos dos parâmetros do script e API de Arquivos:

    csv = Arquivo.novo('teste.csv', 'csv')  
    csv.escrever('Valor')  
       
    anexoCsv = Email.criarAnexoArquivo(csv, 'teste.csv')  
       
    Email.novo()  
         .de('betha@betha.com.br','Betha Sistemas')  
         .para('destinatario@betha.com.br', 'Destinatário')  
         .assunto('Teste de e-mail')  
         .mensagem('Novo arquivo enviado.')  
         .anexar(anexoCsv)  
         .anexarArquivo(parametros.arquivo.valor, 'Arquivo.xml')  
         .enviar()  

## Credenciais de e-mail do cliente​

Para que os e-mails e que não caiam em listas de spam, é necessário configurar o servidor de e-mail e credenciais do próprio cliente para os e-mails enviados por scripts. O envio de e-mail através dos scripts foi atualizado e alterado para que sejam utilizadas as credenciais cadastradas nas variáveis de ambiente.

Atualmente os e-mails podem ser enviados de três modos: 

  * Autenticação com dados nos Script;
  * E quando não se tem autenticação no script, ele busca das variáveis cadastradas no menu **Configurando > Geral > Variáveis de ambiente** (para editores de scripts) ou através do menu **Executando > Artefatos > Relatórios F4** (que não possuem acesso a criação de script) mencionado no item anterior. 

Essa autenticação via script tem prioridade sobre as variáveis de ambiente e o mesmo buscará as informações caso não tenha sido especificado como mostrado na linha 6 do exemplo.

![api email](/assets/images/bfc1-c31f8208f26e905d3de86b6f9662da78.png)

IMPORTANTE!

A partir do dia 01 de junho de 2021 (quinta-feira), os e-mails enviados a partir dos sistemas Cloud da Betha Sistemas passam a ser encaminhados por um servidor de e-mail configurado por cada cliente, necessitando que sejam alterados os scripts para que todos os e-mails possam ser enviados corretamente.

Com isso, é de suma importância acrescentar a linha de códigos com as variáveis: **IP** , **porta** , **usuário** e **senha** , sendo que usuário e senha são opcionais.

![api email](/assets/images/bfc2-ec89ee8aaebc1d88990e870cc4ed775f.png)

Ou, inserir as informações através da configuração no ambiente de variáveis, para que o script possa inseri-las automaticamente, porém, essas variáveis devem manter o padrão **BTH _EMAIL_HOST**, **BTH _EMAIL_PORTA**, **BTH _EMAIL_SENHA** e **BTH _EMAIL_USUÁRIO**, para que o script possa localizar os valores.

![api email](/assets/images/bfc3-899e91ec736d75abf0951cc5a3447038.png)

IMPORTANTE!

O provedor de e-mail deve estar configurado para aceitar esse tipo de envio, caso contrário o email não será enviado.

Um exemplo no gmail: essa configuração está no link <https://myaccount.google.com/lesssecureapps>, onde a opção Permitir aplicativos menos seguros deve estar ativada.

  * Mensagem
  * Anexos
  * Exemplos
  * Credenciais de e-mail do cliente