# MongoDB - Aula 03 - Exercício
autor: Júnior Germani

## Liste todos Pokemons com a altura **menor que** 0.5;
var query = {height: {$lt: 0.5}}

db.pokemon.find(query)
{ 
	"_id" : ObjectId("565c9b9ed9f8ad3b3dc5b3d5"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "electric", 
	"attack" : 55, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("565c9bc5d9f8ad3b3dc5b3d6"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}


## Liste todos Pokemons com a altura **maior ou igual que** 0.5
var query = {height: {$gte: 0.5}}

db.pokemon.find(query)
{ 
	"_id" : ObjectId("565c9bd1d9f8ad3b3dc5b3d7"), 
	"name" : "Charmander", 
	"description" : "Esse é o cão chupando manga de fofinho", 
	"type" : "fogo", 
	"attack" : 52, 
	"height" : 0.6 
}
{ 
	"_id" : ObjectId("565c9bdbd9f8ad3b3dc5b3d8"), 
	"name" : "Squirtle", 
	"description" : "Ejeta água que passarinho não bebe", 
	"type" : "água", 
	"attack" : 48, 
	"height" : 0.5 
}


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}

db.pokemon.find(query)
{ 
	"_id" : ObjectId("565c9bc5d9f8ad3b3dc5b3d6"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
var query = {$or: [{attack: {$lte: 0.5}}, {name: /Pikachu/i}]}

query
{
        "$or" : [
                {
                        "attack" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "name" : /Pikachu/i
                }
        ]
}

db.pokemon.find(query)
{ 
	"_id" : ObjectId("565c9b9ed9f8ad3b3dc5b3d5"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "electric", 
	"attack" : 55, 
	"height" : 0.4 
}

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}

query
{
        "$and" : [
                {
                        "attack" : {
                                "$gte" : 48
                        }
                },
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                }
        ]
}

db.pokemon.find(query)
{ 
	"_id" : ObjectId("565c9b9ed9f8ad3b3dc5b3d5"), 
	"name" : "Pikachu", 
	"description" : "Rato elétrico bem fofinho", 
	"type" : "electric", 
	"attack" : 55, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("565c9bc5d9f8ad3b3dc5b3d6"), 
	"name" : "Bulbassauro", 
	"description" : "Chicote de trepadeira", 
	"type" : "grama", 
	"attack" : 49, 
	"height" : 0.4 
}
{ 
	"_id" : ObjectId("565c9bdbd9f8ad3b3dc5b3d8"), 
	"name" : "Squirtle", 
	"description" : "Ejeta água que passarinho não bebe", 
	"type" : "água", 
	"attack" : 48, 
	"height" : 0.5 
}


