Laravel simple api rest crud

Una api simple donde se puede gestionar alumnos en base de datos.
Getting Started

solo clona el repositorio -> https://github.com/metallive/laravel-api.git

requirements:
1.- laravel 11
2.- php >= 8.2 
3.- XAMMP(optional)
5.- thunder client addon or Postman 

Give examples

Installing

1.- Configura tu base de datos en ".env" 
    DB_CONNECTION=mysql ->(cualquiera que gustes)
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=laravel
    DB_USERNAME=root
    DB_PASSWORD=
2.- crea tu base de datos
3.- "php artisan migrate" en terminal 
4.- "php artisan serve" en terminal


routes

Route::get('/students', [studentController::class, 'index']);

Route::get('/students/{id}',[studentController::class, 'show']);

Route::post('/students', [studentController::class,'store']);

Route::put('/students/{id}', [studentController::class,'update']);

Route::patch('/students/{id}', [studentController::class,'updatePartial']);

Route::delete('/students/{id}', [studentController::class,'destroy']);



Ejemplos:
get all students
    http://127.0.0.1:8000/api/students/
        {
        "students": [
            {
                "id": 3,
                "name": "pablito toledo",
                "email": "pablotesttledo@gmail.com",
                "phone": "56965954581",
                "language": "English",
                "created_at": "2024-05-27T01:51:34.000000Z",
                "updated_at": "2024-05-27T04:07:32.000000Z"
            },
            {
                "id": 4,
                "name": "hernan",
                "email": "hernaneduardofigueroadelgado@gmail.com",
                "phone": "56965954573",
                "language": "Spanish",
                "created_at": "2024-05-27T01:52:41.000000Z",
                "updated_at": "2024-05-27T01:52:41.000000Z"
            }
        ],
        "status": 200
    }

get{id}
    http://127.0.0.1:8000/api/students/3

    output:
    {
        "student": {
            "id": 3,
            "name": "pablito toledo",
            "email": "pablotesttledo@gmail.com",
            "phone": "56965954581",
            "language": "English",
            "created_at": "2024-05-27T01:51:34.000000Z",
            "updated_at": "2024-05-27T04:07:32.000000Z"
        },
        "status": 200
    }

delete
    http://127.0.0.1:8000/api/students/2



post
    http://127.0.0.1:8000/api/students/

    input:
    {   
            "name": "nicolas",
            "email": "nicolas@gmail.com",
            "phone": "53965244581",
            "language": "Spanish"
    }

    output:
    {
        "students": {
            "name": "nicolas",
            "email": "nicolas@gmail.com",
            "phone": "53965244581",
            "language": "Spanish",
            "updated_at": "2024-05-28T16:48:15.000000Z",
            "created_at": "2024-05-28T16:48:15.000000Z",
            "id": 5
        },
        "status": 201
    }
put
    http://127.0.0.1:8000/api/students/5
    input:
    {   
            "name": "nicolas cage",
            "email": "nicolascage@gmail.com",
            "phone": "53965244581",
            "language": "Spanish"
    }

    output:

    {
        "message": "estudiante actualizado",
        "students": {
            "id": 5,
            "name": "nicolas cage",
            "email": "nicolascage@gmail.com",
            "phone": "53965244581",
            "language": "Spanish",
            "created_at": "2024-05-28T16:48:15.000000Z",
            "updated_at": "2024-05-28T16:52:41.000000Z"
        },
        "status": 200
    }
