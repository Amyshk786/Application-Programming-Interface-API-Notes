A REST API (Representational State Transfer Application Programming Interface) is a way for different software systems to communicate with each other over the internet using standard HTTP methods.

It is one of the most common approaches used to build web services.





# REST is a Design Principles which helps an Application or Service to Access a Resource within another Application, Service or Database. 


All API requests for the same resource should look the same, no matter where the request comes from. The REST API should ensure that the same piece of data, such as the name or email address of a user, belongs to only one uniform resource identifier (URI).


It defines a set of principles for designing networked applications.

REST is:

Stateless
Client-server based
Cacheable
Uses standard HTTP methods
Resource-based




-> BODY - Body is a Payload where we can Put All Our Data


-> HEADERS - If we want to Send Any Extra Data in our Request which are Key Value Pairs


-> PATH - /users  /products














# REST APIs use standard HTTP Methods (Verbs) 



| Method | Purpose                   | Example             |
| ------ | ------------------------- | ------------------- |
| GET    | Retrieve data             | Get all users       |
| POST   | Create new resource       | Create a new user   |
| PUT    | Update entire resource    | Update user details |
| PATCH  | Partially update resource | Update user email   |
| DELETE | Remove resource           | Delete user         |










-> GET /users  - Will Return All the Users


-> GET /users/:id  - Will Return a Particular User by ID


-> POST /users  - Will Create a New User


-> DELETE /users/:id  - Will Delete a Particular User by ID


-> PUT /users/:id - 	 Updates (replaces) the entire user by ID


-> PATCH /users/:id  - Will Update a Particular User by ID





# Status Codes

REST APIs use HTTP status codes to indicate success or failure.



| Code | Meaning               |
| ---- | --------------------- |
| 200  | OK                    |
| 201  | Created               |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 404  | Not Found             |
| 500  | Internal Server Error |
