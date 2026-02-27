---
title: API padrão | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/api-padrao
crawled_at: 2026-02-27 12:59:55
---

Pular para o conteúdo principal

Nessa página

A _engine_ padrão disponibiliza uma API com várias funções utilitárias para manipulação de datas, caracteres e números. As funções são separadas por classes e são invocadas como métodos. Alguns métodos para manipulação de datas e caracteres podem ser utilizados de maneira direta, invocando o método a partir do próprio elemento, não necessitando a invocação através da classe. 

Este capítulo abordará detalhes de cada função da API padrão. Essas funções estarão disponíveis ao usuário final e serão absorvidas plenamente conforme a utilização.

## Funções para manipulação de caracteres​

A seguir são descritas todas as funções disponíveis para a manipulação de caracteres. Da mesma forma que para as funções de manipulação de números, serão apresentadas as funções, sua descrição e sintaxe em uma tabela, a fim de facilitar o entendimento.

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**| **SINTAXE**  
---|---|---  
**capitaliza**|  Por meio desta função é possível colocar a primeira letra de cada palavra de um texto em maiúsculo e as outras letras para minúsculo.| Caracteres.capitaliza(texto)OUtexto.capitaliza  
**direita**|  Obtém uma quantidade específica de caracteres iniciados da direita para esquerda.| Caracteres.direita(texto, quantidade)OUtexto.direita(quantidade)  
**dividir**|  Esta função divide um texto de acordo com a expressão regular informada.| Caracteres.dividir(boa-tarde~/|/) //OUvalor.dividir(~/|/)  
**equivalente**|  Verifica se uma expressão está contida em um texto.| Caracteres.equivalente(texto, expressao)OUtexto.equivalente(expressao)  
**esquerda**|  Obtém uma quantidade específica de caracteres iniciados da esquerda para direita.| Caracteres.esquerda(texto, quantidade)OUtexto.esquerda(quantidade)  
**maiusculo**|  Converte todos os caracteres de um texto em maiúsculo.| Caracteres.maiusculo(texto)OUtexto.maiusculo  
**minusculo**|  Converte todos os caracteres de um texto em minúsculo.| Caracteres.minusculo(texto)OUtexto.minusculo  
**posicao**|  Obtém a posição onde um caracter se encontra em uma texto.| Caracteres.posicao(texto, expressao, posicaoInicio)OUtexto.posicao(expressao, posicaoInicio)  
**posicaoFinal**|  Obtem a posição final de uma expressão regular em um texto.| Caracteres.posicaoFinal(texto, expressao regular, posicaoInicio)OUtexto.posicaoFinal(expressao regular, posicaoInicio)  
**removeEspacos**|  Remove o excesso de espaços de um texto.| Caracteres.removeEspacos(texto)OUtexto.removeEspacos  
**removeEspacosDireita**|  Remove o excesso de espaços de um texto a esquerda.| Caracteres.removeEspacosDireita(texto)OUtexto.removeEspacosDireita  
**removeEspacosEsquerda**|  Remove o excesso de espaços de um texto à direita.| Caracteres.removeEspacosEsquerda(texto)OUtexto.removeEspacosEsquerda  
**sobrepor**|  Sobrepõe um texto em outro em uma determinada posição e com uma quantidade específica de caracteres.| Caracteres.sobrepor(texto, posicaoInicial, quantidadeSobrepor, textoSobrepor)OUtexto.sobrepor(posicaoInicial, quantidadeSobrepor, textoSobrepor)  
**substituir**|  Substitui as ocorrências de uma expressão localizada em um texto por outra expressão.| Caracteres.substituir(texto, textoLocalizar, textoSubstituir)OUtexto.substituir(textoLocalizar, textoSubstituir)  
**subTexto**|  Obtém um número específico de caracteres de uma posição específica de um texto.| Caracteres.subTexto(texto, inicio, tamanho)OUtexto.subTexto(inicio, tamanho)  
**tamanho**|  Obtém o tamanho de um texto.| Caracteres.tamanho(texto)OUtexto.tamanho  
**vazio**|  Verifica se uma palavra está vazia.| Caracteres.vazio(valor)OUvalor.vazio  
**repetir**|  Repete um texto especificado de acordo com uma quantidade definida.| Caracteres.repetir(texto, repeticao)OUtexto.repetir(repeticao)  
  
Um exemplo prático de utilização do **Repetir** é para completar os caracteres de um campo de um leiaute bancário. Por exemplo, no leiaute tem o campo nome com 100 caracteres, porém, se o nome não tiver 100 caracteres, então, o campo deve ser preenchido com espaços em branco à direita.

Segue um exemplo de preenchimento de um campo do tipo String:

    //Script convencional  
    arquivo = Arquivo.novo('arq.txt', 'txt', [encoding: 'iso-8859-1']);  
       
    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    percorrer(dadosFuncionarios.busca()){  
      arquivo.escrever(item.nome)  
      arquivo.escrever(Caracteres.repetir(" ", 100 - item.nome.tamanho()))  
      arquivo.escrever(item.rg)  
      arquivo.escrever(Caracteres.repetir(" ", 10 - item.rg.tamanho()))  
      arquivo.escrever('ABCDE')  
      arquivo.novaLinha()  
    }  
       
    Resultado.arquivo(arquivo)  

    //Script otimizado  
    preencherComEspacos = { texto, tamanho ->   
       texto + Caracteres.repetir(" ", tamanho - texto.tamanho())  
    }  
       
    arquivo = Arquivo.novo('arq.txt', 'txt', [encoding: 'iso-8859-1']);  
       
    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    percorrer(dadosFuncionarios.busca()){  
      arquivo.escrever(preencherComEspacos(item.nome,100))  
      arquivo.escrever(preencherComEspacos(item.rg, 10))  
      arquivo.escrever('ABCDE')  
      arquivo.novaLinha()  
    }  
       
    Resultado.arquivo(arquivo)  

Segue um outro exemplo, utilizando o mesmo leiaute bancário, de preenchimento com zeros à esquerda para um determinado campo do tipo numérico:

    //Função para preencher os espaços do número  
    formatarNumero = { numero, tamanho ->  
       
      numeroTxt = "$item.id"  
       
      //Observe que o preenchimento do campo está à esquerda, no caso, antes do Código.  
      Caracteres.repetir('X', tamanho - numeroTxt.tamanho()) + numeroTxt  
        
      //Observe que o preenchimento do campo está à direita, no caso, depois do Código.  
      // numeroTxt + Caracteres.repetir('X', tamanho - numeroTxt.tamanho())  
    }  
       
    arquivo = Arquivo.novo('arq.txt', 'txt', [encoding: 'iso-8859-1']);  
       
    dadosFuncionarios = Dados.dubai.v1.funcionarios  
       
    percorrer(dadosFuncionarios.busca()){  
      idString = "$item.id"  
      //Aqui os números são preenchidos com os caracteres desejados sem utilizar a função formatarNumero()  
      imprimir item.nome + Caracteres.repetir(" ", 100 - item.nome.tamanho()) +   
        Caracteres.repetir("X", 10 - idString.tamanho()) + item.id + '-ABCDE'  

      arquivo.escrever(item.nome)  
      arquivo.escrever(Caracteres.repetir(" ", 100 - item.nome.tamanho()))  
      //Aqui é utilizado o recurso da função de preenchimento dos espaços - formatarNumero(a,b)  
      arquivo.escrever(formatarNumero(item.id,10))  
      arquivo.escrever('-ABCDE')  
      arquivo.novaLinha()  
    }  
       
    Resultado.arquivo(arquivo)  

### Expressões regulares​

As funções de Caracteres suporta o uso de expressões regulares para realizar diversas operações baseadas em um padrão em textos.

    Caracteres.expressao(texto, expressao)  
    //ou  
    "texto".expressao(expressao)  

As expressões são representadas na linguagem de scripts utilizando o seguinte padrão: **~/expressão/**

     expNumeros = ~/\d+/  
    expLetras = ~/(?i)[a-z]/  
       
    Caracteres.expressao("1235", ~/[a-z]/)  
    "1235".expressao(~/[a-z]/)  

As operações disponíveis em uma expressão estão listadas nos tópicos a seguir:

### equivalente()​

Verifica se o texto é totalmente equivalente à expressão.

    //verdadeiro pois todo o texto equivale a expressão regular informada  
    Caracteres.expressao("123", ~/\d+/).equivalente()  
       
    //falso pois apesar do texto conter números o valor não é totalmente equivalente à expressão.  
    "123AB".expressao(~/\d+/).equivalente()  

### totalGrupos()​

Retorna o total de grupos da expressão regular.

    expBoasVindas = "boa-tarde".expressao(~/boa-(tarde|noite)/)  
    imprimir expBoasVindas.totalGrupos() // 1  

### dividir()​

Esta função divide um texto de acordo com a expressão regular informada retornando uma lista com os valores separados.

    partes = "boa|tarde".expressao(~/\|/).dividir()  
    percorrer(partes){  
       imprimir item  
    }  
       
    //Saída:  
    //boa  
    //tarde  

### substituirPor(valor)​

Realiza a substituição de todos os valores da expressão encontrados no texto pelo valor informado no parâmetro.

    valor = "A1B2".expressao(~/[0-9]+/).substituirPor("*")  
    imprimir valor // A*B*  

### substituirPrimeiroPor(valor)​

Realiza a substituição do primeiro valor da expressão encontrado no texto pelo valor informado no parâmetro.

    valor = "A1B2".expressao(~/[0-9]+/).substituirPrimeiroPor("*")  
    imprimir valor // A*B2  

### encontrouPadrao()​

Indica se o padrão da expressão foi encontrado no texto.

    encontrouAlgo = "1235A".expressao(~/[0-9]+/).encontrouPadrao()  
    imprimir encontrouAlgo // true  

### concatenarValoresEncontrados()​

Retorna todos os valores encontrados no texto pela expressão concatenados.

    imprimir "B30th45".expressao(~/[0-9]+/).concatenarValoresEncontrados() // 3045  

### concatenarValoresEncontrados(separador)​

Retorna todos os valores encontrados no texto pela expressão concatenados com o separador informado no parâmetro.

    imprimir "B30th45".expressao(~/[0-9]+/).concatenarValoresEncontrados(",") // 30,45  

### Caractere de escape​

    imprimir "These "names" sets apply to this country: American"  
       
    //Resultado:  
    Há um erro de sintaxe. (1:18)  

Isto ocorre, porque o compilador interpreta os caracteres de aspas duplas dentro da cadeia de caracteres como delimitadores. Para eliminar o problema emprega-se o caractere de escape \ (barra contrária, ou backslash) antes das aspas:

    imprimir "These \"names\" sets apply to this country: American"  
       
    //Resultado:  
    These "names" sets apply to this country: American  

Veja este caso:

    imprimir "C:\Temp\PDF\Leitura"  
       
    //Resultado:  
    Há um erro de sintaxe. (1:13)   

Isso ocorre porque o compilador interpreta as barras contrárias como caracteres de escape. Mas não é o que queremos. Queremos imprimir um caminho de pastas usando, literalmente, as barras contrárias:

    //Adicione mais um caractere de escape em cada barra  
    imprimir "C:\\Temp\\PDF\\Leitura"  
       
    //Resultado:  
    C:\Temp\PDF\Leitura  

Dentro das expressões regulares, é necessário inserir, no caractere de escape, um **til** entre as barras contrárias:

    ~\caractere de escape aqui~\  

Veja abaixo um exemplo usando caracteres de escape. Repare que, dentro do último comando "expressao", há uma solicitação de substituir uma barra por uma string vazia.

    //O código abaixo remove caracteres especiais  
    caracteres = "Caráctéres\$  Es\$,pêc-i_a*i/s. fôrám removídós\$: !@#¨&*^´()\n"  
       
    caracteres.expressao(~/[à|á|ã]/).substituirPor("a")  
              .expressao(~/[Á|Ã|À]/).substituirPor("A")  
              .expressao(~/[é|ê]/).substituirPor("e")  
              .expressao(~/[É|É]/).substituirPor("E")  
              .expressao(~/[É|É]/).substituirPor("")  
              .expressao(~/[í]/).substituirPor("i")    
              .expressao(~/[Í]/).substituirPor("I")    
              .expressao(~/[õ|ó|ô]/).substituirPor("o")    
              .expressao(~/[Õ|Ó|Ô]/).substituirPor("O")  
              .expressao(~/[ü|ú]/).substituirPor("u")  
              .expressao(~/[Ú|Ü]/).substituirPor("U")  
              .expressao(~/[ç]/).substituirPor("c")  
              .expressao(~/[Ç]/).substituirPor("C")  
              .expressao(~/  /).substituirPor(" ")  
              .expressao(~/[,|~\\n~\|~\/~\|-|_|*|.|!|@|#|$|%|¨|&|*|^|´|.|~|:|;|)|(|%|~\-|]/).substituirPor("")  
       
    //Resultado:  
    Caracteres Especiais foram removidos   

## Múltiplas ocorrências e grupos​

Uma expressão pode encontrar diversas ocorrências de um padrão em um texto. Estes valores podem ser organizados por grupos ou simplesmente por valor localizado.

Percorrendo todas as ocorrências encontradas em um texto:

    achaNumeros = "B30th45".expressao(~/[0-9]+/)  
    percorrer(achaNumeros){  
      imprimir item.valorEncontrado()  
    }  
    //Saída:  
    // 30  
    // 45  

### posicaoInicial()​

Retorna a posição inicial do texto que coincida com a expressão localizada. Caso o padrão não seja encontrado retorna -1.

### posicaoFinal()​

Retorna a posição final do texto que coincida com a expressão localizada. Caso o padrão não seja encontrado retorna -1.

    achaNumeros = "B30th45".expressao(~/[0-9]+/)  
    percorrer(achaNumeros){  
      valor = item.valorEncontrado()  
      inicio = item.posicaoInicial()  
      fim = item.posicaoFinal()  
      imprimir "O valor $valor inicia na posição $inicio e termina na posição $fim"  
    }  
       
    // Saída:  
    //O valor 30 inicia na posição 1 e termina na posição 3  
    //O valor 45 inicia na posição 5 e termina na posição 7  

### posicaoFinal()​

Retorna a posição final do texto que coincida totalmente com a expressão utilizada. Caso não encontrado retorna -1.

    imprimir "B30th".expressao(~/\d+/).posicaoFinal() //3  

### valoresGrupos()​

Retorna uma lista com todos os valores encontrados pelos grupos especificados na expressão.

    exp = "boa-tarde".expressao(~/boa-(tarde|noite)/)  
    percorrer(exp){  
      imprimir item.valoresGrupos() // [tarde]  
    }  

### valorGrupo(indice)​

Retorna ao valor do grupo encontrado conforme índice e expressão.

    exp = "bom-dia".expressao(~/(boa|bom)-(dia|tarde|noite)/)  
    percorrer(exp){  
      imprimir item.valorGrupo(0) //bom  
      imprimir item.valorGrupo(1) //dia  
    }  
       
    exp2 = "boa-tarde".expressao(~/(boa|bom)-(dia|tarde|noite)/)  
    percorrer(exp2){  
      imprimir item.valorGrupo(0) //boa  
      imprimir item.valorGrupo(1) //tarde  
    }  

### valorEncontrado()​

Retorna o conteúdo do texto encontrado de acordo com a expressão/grupo utilizado.

    exp = "Muito boa-tarde respeitável público.. Ops, acho que seria boa-noite!".expressao(~/(boa|bom)-(dia|tarde|noite)/)  
    percorrer(exp){  
        imprimir item.valorEncontrado()  
    }  
       
    //Saída:  
    // boa-tarde  
    // boa-noite  

### concatenarValoresGrupos()​

Retorna os valores dos grupos da expressão concatenados.

    exp = "boa-Tarde".expressao(~/(boa|bom)-(dia|(t|T)arde|noite)/)  
    percorrer(exp){  
      imprimir item.concatenarValoresGrupos() // boaTardeT  
    }  

### concatenarValoresGrupos(separador)​

Retorna os valores dos grupos da expressão concatenados com o separador informado no parâmetro.

    exp = "boa-Tarde".expressao(~/(boa|bom)-(dia|(t|T)arde|noite)/)  
    percorrer(exp){  
      imprimir item.concatenarValoresGrupos("-") // boa-Tarde-T  
    }  

## Datas​

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**| **SINTAXE**  
---|---|---  
**adicionaDias**|  Adiciona uma quantidade especificada de dias à uma data.| Datas.adicionaDias(data, quantidadeDias)OUdata.adicionaDias(quantidadeDias)  
**adicionaHoras**|  Adiciona uma quantidade especificada de horas em uma data/hora| Datas.adicionaHoras(data, quantidadeHoras)  
**adicionaMeses**|  Adiciona uma quantidade especificada de meses em uma data. Caso o dia da data especificada não seja um dia válido para o mês resultante, Ex: 31/10/2011, adiciona 1 mês, valor inválido para nova data 31/11/2011, a diferença de dias será acrescentada na nova data, Ex:31/10/2011, adiciona 1 mês fica 01/12/2011.| Datas.adicionaMeses(data, quantidadeMeses)OUdata.adicionaMeses(quantidadeMeses)  
**adicionaMinutos**|  Adiciona uma quantidade especificada de minutos em uma data/hora.| Datas.adicionaMinutos(data, quantidadeMinutos)OUdata.adicionaMinutos (quantidadeMinutos)  
**adicionaSegundos**|  Adiciona uma quantidade especificada de segundos em uma data/hora.| Datas.adicionaSegundos(data, quantidadeMinutos)OUdata.adicionaSegundos(quantidadeMinutos)  
**ano**|  Obtém o ano em que se encontra uma determinada data| Datas.ano(data)OUdata.ano  
**data**|  Gera uma data sem hora de acordo com o dia, mês e ano passados por parâmetro.| Datas.data(ano, mês, dia)OUano.data(mês, dia)  
**dataHora**|  Gera uma data com a hora de acordo com o dia, mês, ano, hora e minuto passados por parâmetro| Datas.dataHora (ano, mês, dia, hora, minuto)OUano.dataHora (mês, dia, hora minuto)  
**dia**|  Obtém o dia em que se encontra uma determinada data.| Datas.dia(data)OUdata.dia  
**diaSemana**|  Obtem o dia da semana em que se encontra uma determinada data, considerando-se o domingo comoprimeiro dia e o sábado como o sétimo dia.| Datas.diaSemana(data)OUdata.diaSemana  
**diferencaAnos**|  Calcula a diferença em anos entre duas datas.| Datas.diferencaAnos(menorData, maiorData)OUmenorData.diferencaAnos (maiorData)  
**diferencaDias**|  Calcula a diferença em dias entre duas datas.| Datas.diferencaDias(menorData, maiorData)OUmenorData.diferencaDias(maiorData)  
**diferencaHoras**|  Calcula a diferença em horas entre duas datas.| Datas.diferencaHoras(menorData, maiorData)OUmenorData.diferencaHoras(maiorData)  
**diferencaMeses**|  Calcula a diferença em meses entre duas datas| Datas.diferencaMeses(menorData, maiorData)OUmenorData.diferencaMeses(maiorData)  
**diferencaMinutos**|  Calcula a diferença em minutos entre duas datas/hora.| Datas.diferencaMinutos(menorData, maiorData)OUmenorData.diferencaMinutos(maiorData)  
**diferencaSegundos**|  Calcula a diferença em segundos entre duas datas/hora| Datas.diferencaSegundos (menorData, maiordata)OUmenorData.diferencaSegundos(maiorData)  
**ehData**|  Verifica se um texto é uma hora válida.| Datas.ehData(texto)OUtexto.ehdata  
**extenso**|  Obtém a data por extenso.| Datas.extenso(data)OUdata.extenso  
**hoje**|  Obtém a data e hora do sistema operacional| Datas.hoje()OUDatas.hoje(data)  
**hora**|  Obtém a hora em que se encontra uma determinada data/hora.| Datas.hora(data)OUData.hora  
**mês**|  Obtém o mês em que se encontra uma determinada data.| Datas.mes(data)OUdata.mes  
**minuto**|  Obtém os minutos referentes a uma determinada data/hora.| Datas.minuto(data)OUdata.minuto  
**nomeDiaSemana**|  Obtém o nome do dia da semana.| Datas.nomeDiaSemana(data)OUdata.nomeDiaSemana  
**nomeMes**|  Obtém o nome do mês de uma data,| Datas.nomeMes(data)OUdata.nomeMes  
**periodo**|  Cria um período com data inicial e final.| Datas.periodo(dataInicial, dataFinal)  
**removeDias**|  Remove uma quantidade especificada de dias de uma data.| Datas.removeDias(data, quantidadeOUdata.removeDias(quantidadeDias)  
**removeMeses**|  Remove uma quantidade especificada de meses de uma data. Caso o dia da data especificada não seja um dia válido para o mês resultante, Ex: 31/12/2011, remove 1 mês, valor inválido para nova data 31/11/2011, a diferença de dias será acrescentada da nova data, Ex: 31/12/2011,remove 1 mês fica 01/12/2011.| Datas.removeMeses(data, quantidadeMeses)OUdata.removeMeses(quantidadeMeses)  
**Segundo**|  Obtém os segundos referentes a uma determinada data/hora.| Datas.segundo(data)OUdata.segundo  
**formatar**|  Obtém o valor de uma data formatado de acordo com um padrão especificado.| Datas.formatar(data, formato)EXEMPLO://data definida como dia 26/05/2017imprimir data.formatar('yyyy-MM-dd') // 2017-05-26imprimir data.formatar('MM/yyyy') // 05/2017imprimir data.formatar('EEEE') // Sexta-feira  
  
Padrões para formatação:

**Letra**| **Descrição**|  Exemplos  
---|---|---  
y| Ano| 2009; 09  
M| Mês do ano| Julho; Jul; 07  
w| Semana no ano| 27  
W| Semana no mês| 2  
D| Dia no ano| 189  
d| Dia no mês| 10  
F| Dia da semana no mês| 2  
E| Nome do dia da semana| Segunda-feira, Seg  
u| Número do dia da semana (1=Segunda.7=Domingo)| 1  
a| Indicador de AM/PM| AM  
H| Hora no dia (0-23)| 0  
k| Hora no dia (1-24)| 24  
K| Hora no dia (0-11)| 0  
h| Hora no dia (1-12)| 12  
m| Minuto na hora| 55  
s| Segundos no minuto| 30  
S| Milissegundo| 978  
  
## Funções para manipulação de números​

A API padrão provê uma série de funções para a manipulação de números. Sendo assim o quadro a seguir exibe todas as funções disponíveis de maneira prática. Além da função propriamente dita, informa a sua descrição ou objetivo dela, bem como a sintaxe de cada função.

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**| **SINTAXE**  
---|---|---  
**absoluto**|  Calcula o valor absoluto de um número.| Numeros.absoluto(valor)  
**arredonda**|  Arredonda um valor| Numeros.arredonda(valor, casasDecimais)  
**coseno**|  Calcula o cosseno de um ângulo.| Numeros.coseno(valor)  
**decimal**|  Converte o valor de um texto em um número decimal de alta precisão.| Numeros.decimal(texto)  
**ehNumero**|  Verifica se um texto é um número válido.| Numeros.ehNumero(texto)  
**exponencial**|  Obtém o exponencial de um número específico.| Numeros.exponencial(numero)  
**fatorial**|  Obtém o fatorial de um número.| Numeros.fatorial(numero)  
**inteiro**|  Converte o valor de um texto em um número inteiro. Caso o texto represente um número decimal, este será truncado para um inteiro, ou seja, a parte decimal será descartada.| Numeros.inteiro(texto)  
**logaritmo**|  Informa o logaritmo natural de um número.| Numeros.logaritmo(valor)  
**logaritmo10**|  Informa logaritmo de base 10 de um número.| Numeros.logaritmo10(valor)  
**maximo**|  Obtém o maior valor entre dois números.| Numeros.maximo(valor1, valor2)  
**minimo**|  Obtém o menor valor entre dois números.| Numeros.minimo(valor1, valor2)  
**numero**|  Converte o valor de um texto em um número, retornando o tipo Long para números inteiros e Double para números decimais.**IMPORTANTE!** Esta função NÃO deve ser utilizada para trabalhar com valores monetários. O tipo Double não é adequado para esse fim e vai resultar em imprecisões que ao longo de um cálculo podem alterar de forma significativa o resultado. A função adequada para este fim é a Numeros.decimal.| Numeros.numero(texto)  
**pi**|  Multiplica o valor de PI pelo número especificado.| Numeros.pi(valorMultiplicar)  
**piso**|  Obtém o maior número que é menor ou igual ao número especificado, sendo este número inteiro.| Numeros.piso(valor)  
**raiz**|  Calcula a raiz quadrada de um número.| Numeros.raiz(valor)  
**randomico**|  Obtém um número aleatório entre 1 a um valor limite especificado.| Numeros.randomico(numeroDelimitador)  
**resto**|  Retorna o resto da divisão realizada entre o dividendo e o divisor, que são passados por parâmetro.| Numeros.resto(valorDividendo, valorDivisor)  
**seno**|  Calcula o seno de um ângulo.| Numeros.seno(valor)  
**seZero**|  Testa os valores passados como parâmetro e retorna o primeiro diferente de zero.| Numeros.seZero(valor1, valor2, valorN)  
**tangente**|  Calcula a tangente de um ângulo.| Numeros.tangente(valor)  
**teto**|  Obtém o menor número que é maior ou igual ao número especificado, sendo este número inteiro.| Numeros.teto(valor)  
**trunca**|  Trunca um valor de acordo com o número de casas decimais especificadas.| Numeros.trunca(valor, casasDecimais)  
  
## JSON​

**FUNÇÃO**| **DESCRIÇÃO / OBJETIVO**| **SINTAXE**  
---|---|---  
**ler**|  Converte um json em um mapa| pessoa = JSON.ler('{"nome":"João da Silva"}')imprimir pessoa.nome // imprimie João da Silva  
**escrever**|  Converte um objeto em json| json = JSON.escrever([nome: "João da Silva"])imprimir json // imprimie {"nome":"João da Silva"}  
  
  * Funções para manipulação de caracteres
    * Expressões regulares
    * equivalente()
    * totalGrupos()
    * dividir()
    * substituirPor(valor)
    * substituirPrimeiroPor(valor)
    * encontrouPadrao()
    * concatenarValoresEncontrados()
    * concatenarValoresEncontrados(separador)
    * Caractere de escape
  * Múltiplas ocorrências e grupos
    * posicaoInicial()
    * posicaoFinal()
    * posicaoFinal()
    * valoresGrupos()
    * valorGrupo(indice)
    * valorEncontrado()
    * concatenarValoresGrupos()
    * concatenarValoresGrupos(separador)
  * Datas
  * Funções para manipulação de números
  * JSON