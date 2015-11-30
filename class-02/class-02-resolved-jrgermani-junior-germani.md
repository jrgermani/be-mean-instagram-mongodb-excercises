# MongoDB - Aula 02 - Exercício
autor: Júnior Germani

## Listagem das databases (passo 2)
show dbs
be-mean  0.078GB
local    0.078GB

## Listagem das coleções (passo 3)
show collections

## Cadastro dos pokemons (passo 4)
var pokemons = [{'name':'Mewtwo','description':'Não exerce nenhuma função pois não foi criado por Arceus','type':'Psíquico','attack': 60,'height': 0.6},{'name':'Latias','description':'Junto com Latios, são guardiões do infinito','type':'Dragão/Psíquico','attack': 52,'height': 0.5},{'name':'Rayquaza','description':'É a estrela dos desejos','type':'Psíquico/Metal','attack': 53,'height': 0.3},{'name':'Zygarde','description':'Diz-se para monitorar o ecossistema, e se o ecossistema cai em desordem, ele aparece e revela o seu poder. Zygarde é o único Pokémon capaz de aprender Wrath do Land (Ira da Terra)','type':'Dragão/Terra','attack': 48,'height': 0.5}]

pokemons
[
        {
                "name" : "Mewtwo",
                "description" : "Não exerce nenhuma função pois não foi criado por Arceus",
                "type" : "Psíquico",
                "attack" : 60,
                "height" : 0.6
        },
        {
                "name" : "Latias",
                "description" : "Junto com Latios, são guardiões do infinito",
                "type" : "Dragão/Psíquico",
                "attack" : 52,
                "height" : 0.5
        },
        {
                "name" : "Rayquaza",
                "description" : "É a estrela dos desejos",
                "type" : "Psíquico/Metal",
                "attack" : 53,
                "height" : 0.3
        },
        {
                "name" : "Zygarde",
                "description" : "Diz-se para monitorar o ecossistema, e se o ecossistema cai em desordem, ele aparece e revela o seu poder. Zygarde é o único Pokémon capaz de aprender Wrath do Land (Ira da Terra)",
                "type" : "Dragão/Terra",
                "attack" : 48,
                "height" : 0.5
        }
]

db.pokemons.insert(pokemons)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 4,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})


## Lista dos pokemons (passo 5)
db.pokemons.find()
{ "_id" : ObjectId("565ca6519db49f842867e44b"), "name" : "Mewtwo", "description" : "Não exerce nenhuma função pois não foi criado por Arceus", "type" : "Psíquico", "attack" : 60, "height" : 0.6 }
{ "_id" : ObjectId("565ca6519db49f842867e44c"), "name" : "Latias", "description" : "Junto com Latios, são guardiões do infinito", "type" : "Dragão/Psíquico", "attack" : 52, "height" : 0.5 }
{ "_id" : ObjectId("565ca6519db49f842867e44d"), "name" : "Rayquaza", "description" : "É a estrela dos desejos", "type" : "Psíquico/Metal", "attack" : 53, "height" : 0.3 }
{ "_id" : ObjectId("565ca6519db49f842867e44e"), "name" : "Zygarde", "description" : "Diz-se para monitorar o ecossistema, e se o ecossistema cai em desordem, ele aparece e revela o seu poder. Zygarde é o único Pokémon capaz de aprender Wrath do Land (Ira da Terra)", "type" : "Dragão/Terra", "attack" : 48, "height" : 0.5 }

## Pokemon (passo 6)
var query = {'name':'Mewtwo'}
var poke = db.pokemons.findOne(query)
poke
{
        "_id" : ObjectId("565ca6519db49f842867e44b"),
        "name" : "Mewtwo",
        "description" : "Não exerce nenhuma função pois não foi criado por Arceus",
        "type" : "Psíquico",
        "attack" : 60,
        "height" : 0.6
}

## Atualização do Pokemon (passo 7)
var query = {'name':'Mewtwo'}
var poke = db.pokemons.findOne(query)
poke
{
        "_id" : ObjectId("565ca6519db49f842867e44b"),
        "name" : "Mewtwo",
        "description" : "Não exerce nenhuma função pois não foi criado por Arceus",
        "type" : "Psíquico",
        "attack" : 60,
        "height" : 0.6
}

poke.description
Não exerce nenhuma função pois não foi criado por Arceus
poke.description = "Pokemon psíquico mais foda que existe"
Pokemon psíquico mais foda que existe
db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
db.pokemons.findOne(query)
{
        "_id" : ObjectId("565ca6519db49f842867e44b"),
        "name" : "Mewtwo",
        "description" : "Pokemon psíquico mais foda que existe",
        "type" : "Psíquico",
        "attack" : 60,
        "height" : 0.6
}

