# Architecture Decision Record (ADR)

[Instagram Video](https://www.instagram.com/p/DaLxmjUCEB3/)

Você já entrou num projeto e se perguntou o porquê de algumas escolhas?
Tipo, por que escolheram Postgres em vez de MongoDB?
Ou, por que funções serverless em vez de uma API REST?

Se essas respostas dependem da memória de alguém, então você já encontrou um problema que os ADRs resolvem.

**Práticas de engenharia de software que todo dev deveria saber.**

ADR significa Archtecture Decision Record (Registro de Decisão Arquitetural).
Ele é um documento simples que registra decisões importantes sobre a arquitetura do sistema, mas principalmente o motivo pelo qual elas foram tomadas.
Porque a decisõa em si é importante, mas o contexto que levou até ela é mais importante ainda.

Por exemplo, digamos que um time decidiu usar RabbitMQ para comunicação entre microserviços.
Daqui um ano, alguém novo entra e sugere trocar tudo por Kafka.
Se ninguém registrou o motivo pelo qual RabbitMQ foi escolhido, a discussão vai começar do zero.
Agora, se existir um ADR, basta abrir o documento para entender o contexto, as restrições e as alternativas que já foram avaliadas na época.

Na prática, um ADR costuma ser bem curto.
Primeiro vem os metadados, como status, data e pessoas envolvidas na decisão.
Em seguida, o título, por exemplo "Comunicação assincrona entre microserviços".
Depois, o contexto, explicando qual problema precisava ser resolvido.
Essa parte pode ser decomposta em uma pergunta, como por exemplo, como por exemplo "Como notificar outros serviços ...".
E decision drivers, ou seja, as necessidades que motivaram essa decisão.
Por fim, vem a decisão tomada, que o ideal é de que venha acompanhada de consequências, como vantagens, desvantagens e impactos futuros.
Alguns times também registram as alternativas consideradas antes da escolha final.
No meu caso, poderiamos dizer: Kafka, RabbitMQ, SQS, Azure Service Bus, enfim.

```markdown
---
status: Accepted
date: 2022-11-22
deciders: Sofia
---

# Comunicação assincrona entre microserviços

## Context and Problem Statement

Como notificar outros serviços sem aumentar o tempo de requisição?

## Decision Drivers

* Motivador 1
* Motivador 2

## Decision Outcome

Usaremos o RabbitMQ, porque ..., mesmo que ...

```


E o mais legal é que você nem precisa se preocupar com decorar tudo isso que eu falei, porque já existem templates prontos, e inclusive extensões do VS Code que te ajudam a fazer um ADR.

O ADR manager, por exemplo, ele até já prevê o local do arquivo, que geralmente fica em docs/decisions/ do repositório e inclusive cria o arquivo com o identificador correto.

E uma coisa importante é que o ADR não serve para impedir mudanças, mas para justificá-las.
Se no futuro o contexto mudar, você cria um novo ADR registrando a nova decisão.
Assim o projeto mantém o histórico da evolução da arquitetura.
Agora, quando alguém perguntar porque que a gente fez deste jeito, a resposta vai deixar de ser "não sei, já estava assim", e vai passar a estar documentada.

## Brain Storm

* Registro de Decisão - Decision registry
* Carderno de Laboratório: Laboratórios experimentais precisam manter um registro de tudo o que foi feito, quais resultados foram obtivos, que problemas foram solucionados, como foram solucionados e porquê.
