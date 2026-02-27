---
title: Mapas | Studio
url: https://studio.ajuda.betha.cloud/extensoes/scripts/bfc-script/mapas
crawled_at: 2026-02-27 12:59:32
---

Pular para o conteúdo principal

É possível criar mapas simplificados e acessar seus valores de forma explícita.

    pessoa = [nome:'João da Silva', idade:25, profissao: 'Contador']  
       
    imprimir pessoa.nome  
    imprimir pessoa.idade  
    imprimir pessoa.profissao  

Observe o exemplo abaixo, usando uma **lista de mapas** :

    //Declaração da lista. Será composta por um mapa que contém o nome, a idade e a profissão.  
    dadosPessoais = []  
       
    //Adicionando dados à lista  
    dadosPessoais << [nome:'Luca Ingram', idade:25, profissao: 'Process pipeline drafter']  
    dadosPessoais << [nome:'Jack Young', idade:30, profissao: 'Industrial economist']  
    dadosPessoais << [nome:'Jake Sullivan', idade:31, profissao: 'Gastroenterology nurse']  
       
    //Imprimindo os dados...  
    percorrer(dadosPessoais) {  
      imprimir 'Posição: ' + indice + ' -> Dados:' + item   
    }  
       
    //Temos o resultado:  
    Posição: 0 -> Dados:[nome:Luca Ingram, idade:25, profissao:Process pipeline drafter]  
    Posição: 1 -> Dados:[nome:Jack Young, idade:30, profissao:Industrial economist]  
    Posição: 2 -> Dados:[nome:Jake Sullivan, idade:31, profissao:Gastroenterology nurse]  
       
    //Agora, vamos alterar última posição da lista com novos dados.   
    //Jake Sullivan trocou de profissão e precisamos atualizar seu dado profissional. Fazemos isso substituindo um mapa por outro:  
    dadosPessoais[2] = [nome:'Jake Sullivan', idade:31, profissao: 'Administrative leader']  
       
    //Voltamos a imprimir. Resultado:  
    Posição: 0 -> Dados:[nome:Luca Ingram, idade:25, profissao:Process pipeline drafter]  
    Posição: 1 -> Dados:[nome:Jack Young, idade:30, profissao:Industrial economist]  
    Posição: 2 -> Dados:[nome:Jake Sullivan, idade:31, profissao:Administrative leader]  
       
    //Outro exemplo: Preciso saber a idade do segundo profissional da lista, Jack Young:  
    imprimir dadosPessoais[1].idade  
    //Resultado: 30