# DocuSign Vendor specific Extensions

The Swagger and OpenAPI specifications enable vendor specific extensions throughout Swagger files. 
The extensions must start with the letter x. All DocuSign extensions start with `x-ds-`.

## Categories, Resources, Methods
The OpenAPI specification does not focus on the idea of resources for APIs. 
In particular, the OpenAPI `tags` element can be used to add multiple tags to a method.

DocuSign assigns each method to exactly one **resource**. Resources are usually plural nouns. 
They start with a capital letter.

Methods are verbs. They are lower case.

Resources are grouped together into "categories." Within the documentation, a three level table of contents is used:
Categories, Resources, Methods.

### Categories
Categories are listed in the top level `x-ds-categories` element. It is an array of Category objects. 
Each object includes parameters:

* `name` -- markdown format
* `description` -- markdown format
* `summary` -- markdown format

### Resources
Within the OpenAPI file, a method's resource name is stored in location `tags[0]` within the method's operation definition. 
Only one element of the `tags` array is used.

The top level `tags` array holds the extended descriptions of the resources in markdown format.

Each resource name exactly matchs a definition name. The resource (and definition) names start with a capital letter.

The `description` field in the matching definition entry for the resource holds the resource's summary description, 
also in markdown format.

Definitions that are also resources include the following extensions:

* `x-ds-category` -- the name of the definition's (and resource's) owning category. 
  The value will match a `name` value in the `x-ds-categories` array.
* `x-ds-definition-name` -- the name of the definition as used for generating SDKs
* `x-ds-order` -- an integer for ordering Resources with a Category table of contents entry. Not used.
* `x-ms-summary` -- Not used.

## Methods
The heart of an API specification are the methods.

A Method's Resource name is stored in `tags[0]`

Important parameters for each method:

* `description` -- markdown format.
* `operationId` -- unique throughout the Swagger file.
* `summary` -- markdown format.
* `x-ds-in-sdk` -- is the method included in the SDK? Not used.
* `x-ds-method` -- the method name within the resource's scope. This is the method name used in the API documentation.
* `x-ds-methodname` -- the method name within the category's scope. This method name is used in the SDKs.
* `x-ds-service` -- the owning category for the method.

### Common method names

Most resources include one or more common methods:

| Method name | HTTP method | Description |
| --- | --- | --- |
| create | POST | creates a new resource instance |
| get	| GET	| get a single instance of the resource |
| list | GET	| list current resources |
| delete | DELETE | delete a resource |
| update | PUT | update a resource |
