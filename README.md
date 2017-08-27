## Perdi e agora?
O projeto sugir com uma demanda pessoal com alguns documento perdidos, objetivo é que pessoal possa cadastrar documento, objetos e etc perdidos ou encontrados e informar o que foi feito com esse documento.

### Exemplo:

> Um dia encontrei um cartão de debido no Caixa Eletrônico, no outro dia fui na agencia e entreguei o cartão para o gerente, por sorte encontrei a pessoa no facebook, ela não tinha um sobrenome muito comum foi fácil encontrar, avisei que tinha deixado no banco ela foi lá e retirou o cartão. Já Pensou se nome fosse João da Silva. :(

## Docker
Se você deseja ultilizar Docker, primeiro crie o arquivo _database.yml_:


 ```yaml
 default: &default
  adapter: postgresql
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  host: postgres
  user: postgres

 development:
   <<: *default
   database: perdi-e-agora_development 

 test:
   <<: *default
   database: perdi-e-agora_test 

 ```
depois execute os comandos abaixo::
 
 ```sh
 docker-compose build
 docker-compose run --rm website bundle install
 docker-compose run --rm website bundle exec rails db:create
 docker-compose run --rm website bundle exec rails db:migrate
 docker-compose up
 ```

