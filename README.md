# Atlas Pokémon

Welcome to Atlas-Pokémon! Here you can find a lot of info about first-gen pokémon, and even create your own team!!

You can access here: https://atlas-poke.herokuapp.com/

![pokedex-1](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.03.07.png?raw=true)


## Front: basic usage

In our webpage, you will find a navigation bar at the top, where you can access to three sections: trainers, teams, and pokedex. Let's talk more in depth about them!

![image-general-trainer](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.06.40.png?raw=true)

### Trainers

By clicking the "+" sign in the bottom-right corner, you can create a new trainer. You can choose its name, age, hobby and even a photo, from a wide range of gifs we have selected for you (yayyy!!!)

![list-trainers](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.06.24.png?raw=true)
![add-trainers](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.03.41.png?raw=true)

If you click on the image of a trainer, it's details will appear on the top of the page, so you can check them whenever you want ^^

![image-trainer-details](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.07.13.png?raw=true)

### Teams

Here you can check the details from the pokémon of a specific team. The only thing you have to do is
1. Select a trainer from the selector on the top
2. Click on a trainer's pokémon :D

![details-team](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.08.31.png?raw=true)

![teams](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.07.42.png?raw=true)

Also, if the team size is less than 7, you can add a pokémon. Click on the card, write a name and voilà! 

![add-pokemon](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.07.52.png?raw=true)

![details](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.08.17.png?raw=true)

\* Remember: we only allow first-gen pokèmon


### Pokedex

A full list of first-gen pokèmon!! yayyyy!! Click on any of the pictures and details will be shown :D
Will you be able to find the hidden pokemon? :P

![pokedex-2](https://github.com/C-Inherited/atlas-pokemon/blob/main/Images%20Pokemon%20Atlas/Captura%20de%20pantalla%202021-03-05%20a%20las%2014.09.29.png?raw=true)

\* Additional notes: due to some problems in the original api (PokeApi), some pokèmon can be missing when trying to find them by Id. This can cause them to not appear on the pokèdex. During the development of this project, we found that pokèmon 27 and 110 were missing.


## Back

The proyect have swagger, when you turn on the server you can see all endpoints in this URL:

http://localhost:8080/swagger-ui.html#

## List of our endpoints that u need to know 

- Trainer Endpoints

| PETITION | ROUTE | DESCRIPTION | RESPONSE CODES  
| ------------- | ------------- | ------------- | ------------- |
|GET | /trainers | Retrieve all trainers details without their pokemon team | 
|GET | /trainers/pokemon | Retrieve all trainers details with their pokemon team | 
|GET | /trainer/{id} | Retrieve a trainer by id without their pokemon team | 404 Not found if trainer not present
|GET | /trainer/{id}/pokemon | Retrieve a trainer by id with their pokemon team | 404 Not found if trainer not present
|POST | /trainer | Create a trainer , id is not necessary!| 
|DELETE | /trainer/{id}  | Delete a trainer by id | 404 Not found if trainer not present

- Pokemon Endpoints

| PETITION | ROUTE | DESCRIPTION | RESPONSE CODES
| ------------- | ------------- | ------------- | ------------- |
|POST | /pokemon | Add a pokemon to a trainer team | 404 Not found if trainer not present OR 412 Precondition Failed if trainer have 7 or more pokemon in their team
|DELETE | /pokemon/{id} | Delete pokemon by id from a team | 404 Not found if pokemon not present


## Examples

CREATE A TRAINER

POST /trainer/
Request 
```
{
  "age": 31,
  "hobby": "jugar futbol",
  "imageUrl": "https://www.seekpng.com/png/detail/242-2421423_pokemon-trainer-sprite-png-pixel-pokemon-trainer-sprites.png",
  "name": "Paul"
}
```
Response
```
{
  "id": 5,
  "name": "Paul",
  "hobby": "jugar futbol",
  "age": 31,
  "imageUrl": "https://www.seekpng.com/png/detail/242-2421423_pokemon-trainer-sprite-png-pixel-pokemon-trainer-sprites.png"
}
```

GET /trainer/1/pokemon
Response
```
{
  "id": 1,
  "name": "Nerea",
  "hobby": "jugar futbol",
  "age": 18,
  "imageUrl": "https://www.seekpng.com/png/detail/242-2421423_pokemon-trainer-sprite-png-pixel-pokemon-trainer-sprites.png",
  "team": [
    {
      "id": 1,
      "pokemonId": 1
    },
    {
      "id": 2,
      "pokemonId": 2
    },
    {
      "id": 3,
      "pokemonId": 3
    },
    {
      "id": 4,
      "pokemonId": 4
    },
    {
      "id": 5,
      "pokemonId": 5
    },
    {
      "id": 6,
      "pokemonId": 6
    },
    {
      "id": 8,
      "pokemonId": 8
    }
  ]
}
```

POST /pokemon/
REQUEST
```
{
"pokemonId": 19,
"trainerId": 4
}
```
RESPONSE
```
{
"id": 15,
"pokemonId": 19
}```

