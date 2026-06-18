# Desafio Back-end :desktop_computer:

> Caso o comando nao responda, confira se a porta ja esta em uso.


Olá! :wave: Este é o primeiro contato com um pedaço do nosso dia a dia. A ideia é que você veja de perto alguns dos problemas que resolvemos por aqui.

## Introdução

O desafio pede três coisas:

* refatorar o trecho de criação de conta, que está complicado demais
* escrever testes para as partes que ficaram sem cobertura
* implementar duas funcionalidades novas

Para participar, clone o repositório e mande o link por e-mail.

Algumas dicas antes de começar:

* leia este arquivo até o fim. Ler código, documentação e tarefa com atenção é metade do trabalho — sair codando costuma criar mais problema do que resolver
* ficou com dúvida em algum ponto? Manda um e-mail
* quebre a entrega em tarefas pequenas, para não cair em paralisia por análise
* dá uma olhada no nosso guia de estilo, lá está explicado como a gente trabalha
* ao entregar, fique à vontade para acrescentar qualquer nota neste arquivo

## Entregáveis

1. Refatoração do código de criação de conta. Avalie o trecho e reescreva buscando reduzir a complexidade atual
2. Alguns trechos ficaram sem teste. Descubra quais são e cubra os casos
3. Duas funcionalidades novas:

    - Hoje criar uma conta também cria os usuários: uma conta tem vários usuários e cada usuário pertence a uma conta. Surgiu um requisito novo — parte dos clientes tem mais de uma empresa e precisa que o mesmo usuário acesse empresas diferentes. Então passa a existir um cadastro único de usuários, ligado às empresas (`entities`), não mais à conta. O diagrama esperado está logo abaixo.
    - Alguns parceiros vão ajudar a trazer clientes novos, e eles usam filas para essa comunicação. É preciso um consumidor que leia as mensagens da fila e siga o fluxo de criação de conta que já existe. O corpo da mensagem é o mesmo JSON que chega pela API. Há uma suíte de exemplo com dois cenários em `spec/workers/new_registation_worker_spec.rb`

![Diagrama do banco](docs/assets/diagram.png)

## Entregável extra

Espalhamos pela aplicação vários pontos que poderiam ser refatorados. Se você identificar e quiser arrumar, conta como bônus. A próxima conversa também passa por esse ponto, então só comentar já vale.

## Setup

Você vai precisar de:

 * docker
 * docker-compose
 * ruby 3.0.2

Para subir o container do banco relacional, rode na raiz do projeto: `docker-compose up`

Crie um arquivo `.env` e preencha as variáveis: `cp .env.example .env`

Para subir a aplicação: `foreman start`

## Testes

A suíte pode rodar em paralelo usando uma gem específica, o que deixa a execução bem mais rápida:

1. Prepare o banco de teste