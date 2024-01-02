# Postman Practice - Beginners

Complete the tasks below in Postman, using the online JSONPlaceholder API created for practicing purposes: 

> https://jsonplaceholder.typicode.com/

Note that any `POST`/`DELETE`/etc. will not actually update the database for JSONPlaceholder ‘s API - an expected response will be given, but its database is actually static.

Note that JSONPlaceholder’s API has no required credentials, and uses JSON for its request bodies.

Please checkout the JSONPlaceholders’s [guide](https://jsonplaceholder.typicode.com/guide/) for additional info on its API setup and usage.

## Practice
**Collection Setup**
- [ ] Create a new collection in Postman (name it whatever you wish)
- [ ] Add a variable for the API’s base URL `https://jsonplaceholder.typicode.com/`  (use this variable for the base URL when creating the requests below)

**Create Requests**
Note that, as JSONPlaceholder expects any `POST`/`DELETE`/etc. requests to have an included JSON body, `Content-Type` must be set appropriately in the request Headers tab. The request body will also need to be set to `raw/json`.
- [ ] Add a ‘List all albums’ request to the collection
- [ ] Add a ‘Get album by id’ request to the collection, and issue the request for `id = 2`
- [ ] Add a ‘Search albums’ request to the collection, and issue the request searching for `userId = 1`
- [ ] Add a ‘List all photos for album with id’ request to the collection, and issue the request with `albumId = 3`
- [ ] Add a ‘Search for photos within album’ request to the collection, and issue the request with `albumId = 1` and `photoId = 3` 

**Run the collection**
- [ ] Run the collections of requests you made manually (using Postman’s `Run collection`, not one-by-one by hand), setting `Persist responses for a session` to `true`

## Next Steps
Check out the rest of the resources (see the beginner's setup/resources file that is in the same folder as this file).
