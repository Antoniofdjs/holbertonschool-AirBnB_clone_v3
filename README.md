# AirBnB Clone - The Console

The console is the first segment of the AirBnB project at Holberton School that will collectively cover fundamental concepts of higher level programming. The goal of AirBnB project is to eventually deploy our server a simple copy of the AirBnB Website(HBnB). A command interpreter is created in this segment to manage objects for the AirBnB(HBnB) website.
New AUTHORS SOON JUAN AND ANTONIO

#### Functionalities of this command interpreter:

- Create a new object (ex: a new User or a new Place)
- Retrieve an object from a file, a database etc...
- Do operations on objects (count, compute stats, etc...)
- Update attributes of an object
- Destroy an object

## Table of Content

- [Environment](#environment)
- [Installation](#installation)
- [File Descriptions](#file-descriptions)
- [Usage](#usage)
- [Examples of use](#examples-of-use)
- [Bugs](#bugs)
- [Authors](#authors)
- [Contributors](#contributors)
- [License](#license)

## Environment

This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## Installation

- Clone this repository: `git clone "https://github.com/alexaorrico/AirBnB_clone.git"`
- Access AirBnb directory: `cd AirBnB_clone`
- Run hbnb(interactively): `./console` and enter command
- Run hbnb(non-interactively): `echo "<command>" | ./console.py`

## File Descriptions

[console.py](console.py) - the console contains the entry point of the command interpreter.
List of commands this console current supports:

- `EOF` - exits console
- `quit` - exits console
- `<emptyline>` - overwrites default emptyline method and does nothing
- `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
- `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file).
- `show` - Prints the string representation of an instance based on the class name and id.
- `all` - Prints all string representation of all instances based or not on the class name.
- `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file).

#### `models/` directory contains classes used for this project:

[base_model.py](/models/base_model.py) - The BaseModel class from which future classes will be derived

- `def __init__(self, *args, **kwargs)` - Initialization of the base model
- `def __str__(self)` - String representation of the BaseModel class
- `def save(self)` - Updates the attribute `updated_at` with the current datetime
- `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

Classes inherited from Base Model:

- [amenity.py](/models/amenity.py)
- [city.py](/models/city.py)
- [place.py](/models/place.py)
- [review.py](/models/review.py)
- [state.py](/models/state.py)
- [user.py](/models/user.py)

#### `/api/v1` Directory contains the app.py and the blueprints for handling RESTFUL API actions

[app.py](/api/v1/app.py) - This Flask app serves as the backend for an Airbnb clone project. It provides RESTful API endpoints for managing objects related to the Airbnb project.

#### `/api/v1/views Blueprints for the RESFTFUL API endpoints for each class

[amenities.py](/api/v1/views/amenities.py)  Flask blueprint for handling RESTful API actions related to Amenity objects

- `def get_amenities` - Retrieves a list of all amenities
-  `def get_amenity` - Retrieves an Amenity object
-  `def delete_amenity` - Deletes an Amenity object
-  `def post_amenity` - Creates an Amenity object
-  `def put_amenity` - Updates an Amenity object

[cities.py](/api/v1/views/cities.py) Flask blueprint for handling RESTful API actions related to City objects

- `get_cities_by_state` - Retrieves a list of all cities by state
- `def get_city` - Retrieves a City object
- `def delete_city` - Deletes a City object
- `def create_city` - Creates a City object
- `def update_city` - Updates a City object

[index.py](/api/v1/views/index.py) Endpoints to retrieve the status of the API and statistics about different types of objects managed by the application.

- `def api_status` - Endpoint that return the status of the API
- `def get_stats` - Endpoint to retrieve stats of objects by type

[places_reviews.py](/api/v1/views/places_reviews.py) Flask blueprint for handling RESTful API actions related to Reviews objects

- `def get_reviews_by_place` - Retrieves the list of all Review objects of a Place
-  `def get_review` - Retrieves a Review object
-  `def delete_review` - Deletes a Review object
-  `def create_review` - Creates a Review object
-  `def update_review` - Updates a Review object

[places.py](/api/v1/views/places.py) Flask blueprint for handling RESTful API actions related to Place objects

- `def get_places_by_city` - Retrieves the list of all Place objects of a City
- `def get_place` - Retrieves a Place object
- `def delete_place` - Deletes a Place object
- `def create_place` - Creates a Place object
- `def update_place` - Updates a Place object

[states.py](/api/v1/views/states.py) Flask blueprint for handling RESTful API actions related to State objects

- `def get_states` - Get all objects from State
- `def get_state` - Gets a State object
-  `def delete_state` - Deletes a State Object
-  `def post_state` - Creates a State
-  `def put_state` - Updates a State

[users.py](/api/v1/views/users.py) Flask blueprint for handling RESTful API actions related to User objects

- `def get_users` - Get all objects from Users
- `def get_user` - Gets a User object
-  `def delete_user` - Deletes a User Object
-  `def post_user` - Creates a User object
-  `def put_user` - Updates a User object

#### `/models/engine` directory contains File Storage class that handles JASON serialization and deserialization :

[file_storage.py](/models/engine/file_storage.py) - serializes instances to a JSON file & deserializes back to instances

- `def all(self)` - returns the dictionary \_\_objects
- `def new(self, obj)` - sets in \_\_objects the obj with key <obj class name>.id
- `def save(self)` - serializes **objects to the JSON file (path: **file_path)
- ` def reload(self)` - deserializes the JSON file to \_\_objects

#### `/tests` directory contains all unit test cases for this project:

[/test_models/test_base_model.py](/tests/test_models/test_base_model.py) - Contains the TestBaseModel and TestBaseModelDocs classes
TestBaseModelDocs class:

- `def setUpClass(cls)`- Set up for the doc tests
- `def test_pep8_conformance_base_model(self)` - Test that models/base_model.py conforms to PEP8
- `def test_pep8_conformance_test_base_model(self)` - Test that tests/test_models/test_base_model.py conforms to PEP8
- `def test_bm_module_docstring(self)` - Test for the base_model.py module docstring
- `def test_bm_class_docstring(self)` - Test for the BaseModel class docstring
- `def test_bm_func_docstrings(self)` - Test for the presence of docstrings in BaseModel methods

TestBaseModel class:

- `def test_is_base_model(self)` - Test that the instatiation of a BaseModel works
- `def test_created_at_instantiation(self)` - Test created_at is a pub. instance attribute of type datetime
- `def test_updated_at_instantiation(self)` - Test updated_at is a pub. instance attribute of type datetime
- `def test_diff_datetime_objs(self)` - Test that two BaseModel instances have different datetime objects

[/test_models/test_amenity.py](/tests/test_models/test_amenity.py) - Contains the TestAmenityDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_amenity(self)` - Test that models/amenity.py conforms to PEP8
- `def test_pep8_conformance_test_amenity(self)` - Test that tests/test_models/test_amenity.py conforms to PEP8
- `def test_amenity_module_docstring(self)` - Test for the amenity.py module docstring
- `def test_amenity_class_docstring(self)` - Test for the Amenity class docstring

[/test_models/test_city.py](/tests/test_models/test_city.py) - Contains the TestCityDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_city(self)` - Test that models/city.py conforms to PEP8
- `def test_pep8_conformance_test_city(self)` - Test that tests/test_models/test_city.py conforms to PEP8
- `def test_city_module_docstring(self)` - Test for the city.py module docstring
- `def test_city_class_docstring(self)` - Test for the City class docstring

[/test_models/test_file_storage.py](/tests/test_models/test_file_storage.py) - Contains the TestFileStorageDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_file_storage(self)` - Test that models/file_storage.py conforms to PEP8
- `def test_pep8_conformance_test_file_storage(self)` - Test that tests/test_models/test_file_storage.py conforms to PEP8
- `def test_file_storage_module_docstring(self)` - Test for the file_storage.py module docstring
- `def test_file_storage_class_docstring(self)` - Test for the FileStorage class docstring

[/test_models/test_place.py](/tests/test_models/test_place.py) - Contains the TestPlaceDoc class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_place(self)` - Test that models/place.py conforms to PEP8.
- `def test_pep8_conformance_test_place(self)` - Test that tests/test_models/test_place.py conforms to PEP8.
- `def test_place_module_docstring(self)` - Test for the place.py module docstring
- `def test_place_class_docstring(self)` - Test for the Place class docstring

[/test_models/test_review.py](/tests/test_models/test_review.py) - Contains the TestReviewDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_review(self)` - Test that models/review.py conforms to PEP8
- `def test_pep8_conformance_test_review(self)` - Test that tests/test_models/test_review.py conforms to PEP8
- `def test_review_module_docstring(self)` - Test for the review.py module docstring
- `def test_review_class_docstring(self)` - Test for the Review class docstring

[/test_models/state.py](/tests/test_models/test_state.py) - Contains the TestStateDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_state(self)` - Test that models/state.py conforms to PEP8
- `def test_pep8_conformance_test_state(self)` - Test that tests/test_models/test_state.py conforms to PEP8
- `def test_state_module_docstring(self)` - Test for the state.py module docstring
- `def test_state_class_docstring(self)` - Test for the State class docstring

[/test_models/user.py](/tests/test_models/test_user.py) - Contains the TestUserDocs class:

- `def setUpClass(cls)` - Set up for the doc tests
- `def test_pep8_conformance_user(self)` - Test that models/user.py conforms to PEP8
- `def test_pep8_conformance_test_user(self)` - Test that tests/test_models/test_user.py conforms to PEP8
- `def test_user_module_docstring(self)` - Test for the user.py module docstring
- `def test_user_class_docstring(self)` - Test for the User class docstring

## Examples of use

```
vagrantAirBnB_clone$./console.py
(hbnb) help
	@@ -151,12 +174,16 @@ EOF  all  create  destroy  help  quit  show  update
```

## Bugs

No known bugs at this time.

## Authors

Alexa Orrico - [Github](https://github.com/alexaorrico) / [Twitter](https://twitter.com/alexa_orrico)  
Jennifer Huang - [Github](https://github.com/jhuang10123) / [Twitter](https://twitter.com/earthtojhuang)

Second part of Airbnb: Joann Vuong

## Contributors

Antonia De Jesus - [Github](https://github.com/Antoniofdjs)
Juan C Lopez - [Github](https://github.com/juancalpz23)

## License

Public Domain. No copy write protection.
