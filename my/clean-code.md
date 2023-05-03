---
tags:
- programming
- clean-code
---

# Código Limpo - Habilidades Práticas do Agile Software

### Os fundamentos do Lean, fundamentos 5S.

- **Seiri**, ou organização (pense em “ordenar”). Saber onde estão as coisas - usar abordagens como nomes adequados - é crucial.
- **Seiton**, ou arrumação (pense em “sistematizar”). Há um antigo ditado americano que diz: “Um lugar para tudo, e tudo em seu lugar”. Um pedaço de código deve estar onde você espera encontrá-lo - caso não esteja, refatore e coloque lá.
- **Seiso**, ou limpeza (pense em “polir”): manter o local de trabalho livre de fios pendurados, gordura, migalha e lixo.
- **Seiketsu**, ou padronização: a equipe concorda em manter o local de trabalho limpo.
- **Shutsuke**, ou disciplina (autodisciplina). Isto significa ter disciplina para seguir as práticas e refletir frequentemente isso no trabalho e estar disposto a mudar.

## 1 - Código Limpo

### O que é um Código Limpo?

**Bjarne Stroustrup, criador do C++ e autor do livro A linguagem de programação C++**

#### Página 7

> Gosto do meu código elegante e eficiente. A lógica deve ser direta para dificultar o encobrimento de bugs, as dependências mínimas para facilitar a manutenção, o tratamento de erro completo de acordo com uma estratégia clara e o desempenho próximo do mais eficiente de modo a não incitar as pessoas a tornarem o código confuso com otimizações sorrateiras. O código limpo faz bem apenas uma coisa.
  **Grady Booch, autor do livro Object Oriented Analysis and Design with Applications**

#### Página 8

> Um código limpo é simples e direto. Ele é tão bem legível quanto uma prosa bem escrita. Ele jamais torna confuso o objetivo do desenvolvedor, em vez disso, ele está repleto de abstrações claras e linhas de controle objetivas.
> **O “grande” Dave Thomas, fundador da OTI, o padrinho da estratégia Eclipse**

#### Página 9

> Além de seu criador, um desenvolvedor pode ler e melhorar um código limpo. Ele tem testes unitários e de aceitação, nomes significativos; ele oferece apenas uma maneira, e não várias, de se fazer uma tarefa; possui poucas dependências, as quais são explicitamente declaradas e oferecem um API mínimo e claro. O código deve ser inteligível já que dependendo da linguagem, nem toda informação necessária pode ser expressa no código em si.
> **Michael Feathers, autor de WOrking Effectively with Legacy Code**

#### Página 10

> Eu poderia listar todas as qualidades que vejo em um código limpo, mas há uma predominante que leva a todas as outras. Um código limpo sempre parece que foi escrito por alguém que se importava. Não há nada de óbvio no que se pode fazer para torná-lo melhor. Tudo foi pensado pelo autor do código, e se tentar pensar em algumas melhoras, você voltará ao início, ou seja, apreciando o código deixado para você por alguém que se importa bastante com essa tarefa.
> **Ron Jeffries, autor de Extreme Programming Installed and Extreme Programming Adventures in C#**

#### Página 10

> Nestes anos recentes, comecei, e quase finalizei, com as regras de Beck sobre código simples. Em ordem de prioridade, são:
> Efetue todos os teste;
> Sem duplicação de código;
> Expressa todas as ideias do projeto que estão no sistema;
> Minimiza o número de entidades, como classes, métodos, funções e outras do tipo;
>
>  **Ward Cunningham, criador do conceito de “Wiki”, criador do Fit, co criador da Programação Extrema (eXtreme Programming). Incentivador dos Padrões de Projeto. Líder da Smalltalk e da OO. Pai de todos aqueles que se importam com o código.**

#### Página 11

Você sabe que está criando um código limpo quando cada rotina que você lê se mostra como o que você esperava. Você pode chamar de código belo quando ele também faz parecer que a linguagem foi feita para o problema.

### Conclusão

Livros sobre arte não prometem lhe tornar um artista. Tudo o que podem fazer é oferecer algumas ferramentas, técnicas e linhas de pensamentos que outros artistas usaram. Portanto, este livro não pode prometer lhe tornar um bom programador. Ou lhe dar a “sensibilidade ao código”. Tudo o que ele pode fazer é lhe mostrar a linha de pensamentos de bons programadores e os truques, técnicas e ferramentas que eles usam.

Assim como um livro sobre arte, este está cheio de detalhes. Há muitos códigos. Você verá códigos bons e ruins; código ruim sendo transformado em bom; listas de heurísticas, orientações e técnicas; e também exemplo após exemplo. Depois disso, é por sua conta.

## 2 - Nomes significativos

Evite informações erradas
Faça distinções significativas
Use nomes pronunciáveis (generationTimestamp, modificationTimestamp)
Use nomes passíveis de busca (WORK_DAYS_PER_WEEK)
Evite codificações
Evite o mapeamento mental (i, j, k, …)
Não dê uma de espertinho
Selecione uma Palavra por Conceito
Não faça trocadilhos
Use nomes a partir do Domínio da Solução
Use nomes de Domínio do Problema
Adicione um contexto significativo (GuessStatisticsMessage)
Não adicione contexto desnecessários (GSD)

## 3 - Funções

### Conclusão

As funções são os verbos dessa linguagem, e classes os substantivos.

Programadores experientes vêem os sistemas como histórias a serem contadas em vez de programas a serem escritos. Eles usam os recursos da linguagem de programação que escolhem para construir uma linguagem muito mais rica e expressiva do que a usada para contar a história. Parte da linguagem específica a um domínio é a hierarquia de funções que descreve todas as ações que ocorrem dentro daquele sistema. Em um ato engenhoso, escrevem-se essas funções para usar a mesma linguagem específica a um domínio que eles criaram para contar sua própria parte da história.

Este capítulo fala sobre a mecânica de se escrever bem funções. Se seguir as regras aqui descritas, suas funções serão curtas, bem nomeadas e bem organizadas. Mas jamais se esqueça de que seu objetivo verdadeiro é contar a história do sistema, e que as funções que você escrever precisam estar em perfeita sincronia e formar uma linguagem clara e precisa para lhe ajudar na narração.

## 4 - Comentários

## 5 - Formatação

## 6 - Objetos e Estruturas de Dados

### Conclusão

Os objetos expõem as ações e ocultam os dados. Isso facilita a adição de novos tipos de objetos sem precisar modificar as ações existentes e dificulta a inclusão de novas atividades em objetos existentes. As estruturas de dados expõem os dados e não possuem ações significativas. Isso facilita a adição de novas ações às estruturas de dados existentes e dificulta a inclusão de novas estruturas de dados em funções existentes.

Em um dado sistema, às vezes, desejamos flexibilidade para adicionar novos tipos de dados, e, portanto, optamos por tipos de dados e procedimentos. Bons desenvolvedores de software entendem essas questões sem preconceito e selecionam a abordagem que melhor se aplica no momento.

## 7 - Tratamento de Erro

### Conclusão

Um código limpo é legível, mas também precisa ser robusto. Esses objetivos não são conflitantes. Podemos criar programas limpos e robustos se enxergarmos o tratamento de erro como uma preocupação à parte, algo que seja visível independentemente de nossa lógica principal. Na medida em que somos capazes de fazer isso, podemos pensar nisso de forma independente e dar um grande passo na capacidade de manutenção de nosso código.

## 8 - Limites

### Limites limpos

Coisas interessantes ocorrem nos limites. A alteração é uma delas. Bons projetos de software acomodam modificações sem muito investimento ou trabalho. Quando usamos códigos que estão fora de controle, deve-se dar uma atenção especial ao nosso investimento e garantir que uma mudança futura não seja muito custosa.

O código nos limites precisa de uma divisão clara e testes que definem o que se deve esperar. Devemos evitar que grande parte de nosso código enxergue as particularidades dos de terceiros. É melhor depender de algo que você controle do que pegar algo que acabe controlando você.

Lidamos com os limites de códigos externos através de alguns poucos lugares em nosso código que fazem referência a elas. Podemos os empacotar como fizemos com o Map, ou talvez usar um adapter para converter nossa interface perfeita na que nos for fornecida. De qualquer forma, nosso código se comunica melhor conosco, provê uso consistente interno pelo limite e possui poucos pontos para serem mexidos quando o código externo sofrer alterações.

## 9 - Testes de Unidade

### As três leis do TDD:

1. Não se deve escrever o código de produção até criar um teste de unidade de falhas.
2. Não se deve escrever mais de um teste de unidade do que o necessário para falhar, e não compilar e falhar.
3. Não se deve escrever mais códigos de produção do que o necessário para aplicar o teste de falha atual.

### Testes limpos

- Padrão construir - operar - verificar (make, do, check)

### Uma afirmação por teste

- Padrão dado - quando - então (given, when, then)

### F.I.R.S.T. (Fast, Independent, Repeatable, Self-validating, Timely)

- Rapidez: os testes devem ser rápidos. Quando os testes rodam devagar, você não desejará executá-los.
- Independência: os testes não devem depender uns dos outros. Quando eles dependem uns dos outros, se o primeiro falhar, causará um efeito dominó de falhas, dificultando o diagnóstico e ocultando os defeitos abaixo dele.
- Repetitividade: deve-se poder repetir os testes em qualquer ambiente. Caso eles não sejam, você terá uma desculpa para o motivo das falhas.
- Autovalidação: os testes devem ter uma saída booleana.
- Pontualidade: os testes precisam ser escritos em tempo hábil.

### Conclusão

Os testes são mais importantes para a saúde de um projeto que o código de produção, pois eles preservam e aumentam a flexibilidade, capacidade de manutenção e reutilização do código de produção. Portanto, mantenha seus testes sempre limpos. Trabalhe para torná-los sucintos e expressivos. Invente APIS de teste que funcionem como uma linguagem específica a uma dominio que lhe ajude a criar seus testes.

## 10 - Classes

Última página lida: 149

## 11 - Sistemas

