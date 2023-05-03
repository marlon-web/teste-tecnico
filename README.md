# Teste técnico Adgency Digital

Primeiramente, obrigado pelo seu interesse em trabalhar conosco.
Abaixo você encontrará todos as informações necessárias para iniciar o seu teste.

## Avisos antes de começar

- Crie um repositório no seu GitHub.
- Faça seus commits no seu repositório.
- Envie o link do seu repositório para o recrutador responsável.
- Você poderá consultar o Google, Stackoverflow ou algum projeto particular na sua máquina.
- Fique à vontade para perguntar qualquer dúvida aos recrutadores.
- Fique tranquilo, respire, assim como você, também já passamos por essa etapa. Boa sorte! :)


### Sobre o ambiente da aplicação:

- O framework que usamos atualmente é o Laravel, por isso é necessário que o teste seja feito com o framework Laravel.

## Objetivo: Deployer Service


Atualmente temos uma base de 400 clientes usando um produto ([sistema de rifas](https://rifasonline.me)), e temos novos clientes adquirindo esse produto constantemente, por isso sempre que esse produto receber uma atualização, é necessário que todos os clientes sejam atualizados. Todos os clientes estão no [forge](https://forge.laravel.com), um serviço de gerenciamento de servidores criado pela equipe do Laravel.

O [forge](https://forge.laravel.com) tem um mecanismo de deploy automático que funciona da seguinte forma, o habilitar o deploy automatico em um site dentro do forge, o forge irá: 
- Adicionar um webhook ao repositório em que esse site está sendo versionado (GitHub, GitLab, BitBucket e etc...)

E toda vez que houver um push na master/main desse repositório, o webhook será o responsavel por contactar a API do forge para fazer o deploy.



### Problema
Os serviços de versionamento de código (GitHub, GitLab, BitBucket e etc...) tem um limite de webhooks por respositório, logo, ao exceder esse limite, o forge não irá conseguir mais adicionar webhooks ao repositório, impedindo novos clientes de receber as atualizações.


### Solução

Criar um(a) serviço/API com um endpoint  que irá intermédiar entre o repositório e o forge, com as seguintes caracteristicas:
- Quando houver um push na main/master do repositorio, todos os clientes devem ser atualizados.
- Deve-se considerar um limite de 60 requisições por minuto a API forge.

Para isso o forge disponibiliza uma API REST com varios endpoints, por agora iremos últilizar somente dois

`/servers`

`/servers/{server_id}/sites`

O retorno do endpoint `/servers` é um JSON contendo uma lista de servidores, cada um contendo:
- id
- name
- ip

O retorno do endpoint `/servers/{server_id}/sites` é um JSON contendo uma lista de sites, cada um contendo:
- id
- name
- url
- server_id
- deployment_url
- repository

Onde o campo `deployment_url` é uma url disponibilizada pelo forge, que ao receber um POST, irá executar o deploy da aplicação.

Você deve criar uma fake API/mock para simular a API do forge com os dois endpoints acima citados.

## O que será avaliado e valorizamos :heart:
- Código limpo e organizado (nomenclatura, etc)
- Conhecimento de padrões (PSRs, design patterns, SOLID)
- Ser consistente e saber argumentar suas escolhas
- Apresentar soluções que domina
- Modelagem de Dados
- Manutenibilidade do Código
- Tratamento de erros
- Cuidado com itens de segurança
- Arquitetura (estruturar o pensamento antes de escrever)
- Carinho em desacoplar componentes (outras camadas, service, repository)

De acordo com os critérios acima, iremos avaliar seu teste para avançarmos para a entrevista técnica.
Caso não tenha atingido aceitavelmente o que estamos propondo acima, não iremos prosseguir com o processo.

## O que será um Diferencial
- Testes de integração.
- Testes unitários.
- Uso de Design Patterns.
