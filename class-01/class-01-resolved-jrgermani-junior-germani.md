# MongoDB - Aula 01 - Exercício
autor: Júnior Germani

## Importando os restaurantes
mongoimport --db be-mean --collection restaurantes --drop --host=127.0.0.1 --file restaurantes.json
2015-11-30T13:08:34.715-0300    connected to: 127.0.0.1
2015-11-30T13:08:34.719-0300    dropping: be-mean.restaurantes
2015-11-30T13:08:37.608-0300    imported 25359 documents
    
## Contando os restaurantes
db.restaurantes.find({}).count()
25359