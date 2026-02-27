---
title: Suporte a variáveis de ambiente | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/variaveis-ambiente
crawled_at: 2026-02-27 13:01:11
---

Pular para o conteúdo principal

Nessa página

Existe um ambiente para configuração de variáveis de ambiente que podem ser utilizadas dentro de um script _._

Este recurso é interessante para que dados como credenciais, endereços dentre outros, não sejam definidos diretamente dentro de um script. Através do recurso de variáveis de ambiente é possível que estas variáveis sejam inclusive configuradas para cada cliente.* Para utilizar uma variável de ambiente basta configurá-la no menu específico e referenciá-la dentro de um script, o que deve ser alinhado com o desenvolvedor do mesmo.

É possível definir variáveis de ambientes no gerenciador de extensões acessando o menu **Utilitários > Gerenciador de extensões** ou clicando **F4** no seu teclado.

![variaveis de ambiente](/assets/images/bfc4-f53885147e70aa0e120a2c9a15e32432.png)

Uma janela será aberta, a seguir clique em **VARIÁVEIS DE AMBIENTE**.

![variaveis de ambiente](/assets/images/bfc5-e112c6c3850936acb4840d99f9317c99.png)

Para inserir novas variáveis, pressione o botão **\+ VARIÁVEL**.

![variaveis de ambiente](/assets/images/bfc6-796132a7f600794c10f769ad25868225.png)

Insira uma chave e um valor. É possível ainda deixar a chave secreta ou padrão, para isso basta clicar no ícone de cadeado. 

Em seguida clique no botão **SALVAR** para gravar as informações.

![variaveis de ambiente](/assets/images/bfc7-bd2b904d01a3c126b16251c06100e17b.png)

O usuário tem a possibilidade de editar ou excluir uma variável por meio dos ícones de lápis e lixeira.

![variaveis de ambiente](/assets/images/bfc8-7e0e7b1221cd78a54ef06df5df231e0f.png)

Algumas restrições são apresentadas caso o usuário não siga as orientações adequadas no cadastramento das variáveis, uma mensagem aparecerá no topo da tela informando quais os requisitos precisa ter. Observe na imagem abaixo o que deve conter para se tornar válido uma variável.

![variaveis de ambiente](/assets/images/bfc9-a56f245202a30029b2da9d0bdf047112.png)

IMPORTANTE!

Todas as variáveis cadastradas podem ser visualizadas e utilizadas por todos os usuários da mesma entidade que utilizam um determinado sistema.

Quando um script é flexibilizado para um cliente, é necessário configurar as variáveis de ambiente utilizadas pelo script dentro do **Gerenciador de extensões > VARIÁVEIS DE AMBIENTE**.

![variaveis de ambiente](/assets/images/bfc10-5d8da3504c5b913cdd370d766cae645e.png)

![variaveis de ambiente](/assets/images/bfc11-95f32016973c3304fe53685df07de160.png)

![variaveis de ambiente](/assets/images/bfc12-feba8d5fedf086671ca209930a3fbac4.png)

## Utilização da chave nos scripts​

Perceba na imagem abaixo que em todas as linhas são apresentados a palavra **Variável** e após **sua chave**. Isso significa que cada vez que chamar um valor dessa lista de variável será inserido da seguinte maneira:

'Variavel.' + a chave cadastrada.

![variaveis de ambiente](/assets/images/bfc13-46c16312ba9cf81050d9546b2851e58c.png)

É dessa forma que são inseridas as variáves nos scripts.

  * Utilização da chave nos scripts