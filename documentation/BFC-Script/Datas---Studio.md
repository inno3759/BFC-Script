---
title: Datas | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/datas
crawled_at: 2026-02-27 12:59:41
---

Pular para o conteúdo principal

A linguagem permite trabalhar com datas de forma simplificada. Várias funções estão embutidas nos elementos de data facilitando muito o uso, além de tornar as implementações intuitivas. Os exemplos abaixo demonstram o uso de algumas funções para manipulação de datas, além de demonstrar formas nativas para somar datas/horas/etc.

    //Funções para obter-se uma data/dataHora  
    hoje = Datas.hoje()  
    primeiroDiaDoAno = Datas.data(hoje.ano,1 ,1 )  
    ultimoDiaDoAno = Datas.dataHora(hoje.ano, 12, 31, 23, 59)  
       
    imprimir Datas.adicionaSegundos(hoje, 10)  
    imprimir hoje + 10.segundos  
       
    imprimir Datas.adicionaMinutos(hoje, 10)  
    imprimir hoje + 10.minutos  
       
    imprimir Datas.adicionaHoras(hoje, 10)  
    imprimir hoje + 10.horas  
       
    imprimir Datas.adicionaDias(hoje, 10)  
    imprimir hoje + 10.dias  
       
    imprimir Datas.adicionaMeses(hoje, 10)  
    imprimir hoje + 10.meses  
       
    imprimir hoje + 1.segundo  
    imprimir hoje + 1.minuto  
    imprimir hoje + 1.hora  
    imprimir hoje + 1.dia  
    imprimir hoje + 1.mes  
       
    imprimir hoje + 10.anos + 9.meses + 8.semanas + 7.dias + 6.horas + 5.minutos + 4.segundos + 3.milesegundos  
       
    imprimir Datas.ano(hoje)  
    imprimir hoje.ano  
    imprimir Datas.mes(hoje)  
    imprimir hoje.mes  
    imprimir Datas.dia(hoje)  
    imprimir hoje.dia  
    imprimir Datas.hora(hoje)  
    imprimir hoje.hora  
    imprimir Datas.minuto(hoje)  
    imprimir hoje.minuto  
    imprimir Datas.segundo(hoje)  
    imprimir hoje.segundo  
       
    imprimir Datas.diaSemana(hoje)  
    imprimir hoje.diaSemana  
       
    imprimir Datas.removeDias(hoje, 10)  
    imprimir hoje - 10.dias  
      
    imprimir Datas.removeMeses(hoje, 10)  
    // imprimir Datas.removeMeses(hoje, 10, true)  
    // Ao informar o parâmetro `true` a função aplicará ajustes necessários na subtração dos meses.  
    imprimir hoje - 10.meses  
       
    imprimir Datas.extenso(hoje)  
    imprimir hoje.extenso  
       
    imprimir Datas.nomeDiaSemana(hoje)  
    imprimir hoje.nomeDiaSemana  
       
    imprimir Datas.nomeMes(hoje)  
    imprimir hoje.nomeMes  
       
    imprimir Datas.ehData('01/01/2010')  
      
    imprimir Datas.diferencaAnos(primeiroDiaDoAno, ultimoDiaDoAno)  
    // imprimir Datas.diferencaAnos(primeiroDiaDoAno, ultimoDiaDoAno, true)  
    // Ao informar o parâmetro `true` a função aplicará ajustes para considerar anos parciais corretamente, ajustando a diferença se as datas ainda não alcançaram o mesmo mês e dia.  
      
    imprimir Datas.diferencaDias(primeiroDiaDoAno, ultimoDiaDoAno)  
    imprimir Datas.diferencaHoras(primeiroDiaDoAno, ultimoDiaDoAno)  
    imprimir Datas.diferencaMeses(primeiroDiaDoAno, ultimoDiaDoAno)  
    imprimir Datas.diferencaMinutos(primeiroDiaDoAno, ultimoDiaDoAno)  
    imprimir Datas.diferencaSegundos(primeiroDiaDoAno, ultimoDiaDoAno)  
       
    amanha = hoje + 1.dia  
       
    //Podemos criar intervalos com datas  
    percorrer(hoje..amanha){  
        imprimir item.extenso  
    }  
       
    percorrer(hoje+1.semana..<amanha+2.semanas){  
        imprimir item.extenso  
    }  
       
    //Podemos obter uma data a partir de uma expressão como esta  
    semanaQueVem = 7.dias.apartirDe.hoje  
       
    imprimir semanaQueVem + 5.dias  

É importante notar que os valores numéricos informados nas funções de data para representar ano, mês, dias, horas e segundos, diferentemente da formatação Brasileira, não devem conter zeros à esquerda:

    //Correto  
    Datas.data(2017, 8, 5)  
       
    //Incorreto (Erro de compilação)  
    Datas.data(2017, 08, 05)  

Observa-se que os métodos `Datas.diferencaAnos` e `Datas.removeMeses` possuem um parâmetro booleano opcional. Quando informado como `true`, o método aplica ajustes no cálculo, particularmente válidos para anos parciais, bissextos e afins.