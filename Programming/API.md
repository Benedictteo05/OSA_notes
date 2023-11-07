### Swagger
- A suite of tools used for documenting and testing web APIs. It provides a standardized way to describe and visualize RESTful APIs, making it easier for developers to understand, interact with, and integrate APIs into their applications.


### API documentation
- Controller
	- A class that defines a set of related endpoints (API actions) for a specific resource of functionality. Controllers handle incoming HTTP requests, process them, and return appropriate responses. Each controller typically corresponds to a specific entity or resource in the application.
	- e.g. User
- Endpoint
	- A specific URL with HTTP method that represents a function in the API controller. It's where clients can make requests to interact with the API.
	- e.g.  POST /User/login
- Schema
	- Refers to the structure and format of data that is exchanged between the client and the API. it defines the data types, properties, and relationship of the data. Schemas can be defined for request bodies, response bodies, and data models.
	- e.g. LoginRequest
- Parameter
	- Used to provide additional data to the server when making a request. Parameters can be included in the URL path or as query parameters.
	- A path parameters is defined in the API endpoint annotation to specify what data is required for an endpoint.
	- A query parameter is added to the URL after a question mark? and follows a key-value format.
	- e.
