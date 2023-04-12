# Simple axum todo app

A todo list app built with [Axum](https://crates.io/crates/axum). It serves as an  introduction to backend development in [rust](https://www.rust-lang.org/). It is based on the [todo example](https://github.com/tokio-rs/axum/tree/main/examples/todos) from axum's [examples](https://github.com/tokio-rs/axum/tree/main/examples).

## Usage 

Run the following command to get started:

```bash
git clone https://github.com/EteimZ/axum-todo.git
cd axum-todo
cargo run
```

## Endpoints

The application has the following endpoints.

- `POST` **/todos**: This endpoint creates a new todo.
- `GET` **/todos**: This endpoint gets all of todos in the server.
- `GET` **/todos/:id**: This endpoint gets a particular todo.
- `PATCH` **/todos/:id**: This endpoint updates an existing todo.
- `DELETE` **/todos/:id**: This endpoint deletes a particular todo.

Using curl client we can make requests to the running application.

### Create todo

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"text": "Buy groceries"}' \
  http://127.0.0.1:3000/todos
```

Response:
```json
{"id":"0d98604c-237f-4ae6-b9a4-d6eecdee5020",
"text":"Buy groceries",
"completed":false}
```

### List todos

```bash
curl -X GET http://127.0.0.1:3000/todos
```

Response:

```json
[
  {
    "id": "ec2553b0-6f91-4c48-a8b1-39bffc41b46a",
    "text": "Complete axum todo.",
    "completed": false
  },
  {
    "id": "0d98604c-237f-4ae6-b9a4-d6eecdee5020",
    "text": "Buy groceries",
    "completed": false
  }
]
```

### Get todo

```bash
curl -X GET http://127.0.0.1:3000/todos/ec2553b0-6f91-4c48-a8b1-39bffc41b46a
```

Response:

```json
{
  "id": "ec2553b0-6f91-4c48-a8b1-39bffc41b46a",
  "text": "Complete axum todo",
  "completed": false
}
```

### Update todo

```bash
 curl -X PATCH  \
   -H "Content-Type: application/json"
   -d '{ "completed": true}'  
    http://127.0.0.1:3000/todos/ec2553b0-6f91-4c48-a8b1-39bffc41b46a
```

Response: 

```json
{
  "id": "ec2553b0-6f91-4c48-a8b1-39bffc41b46a",
  "text": "Complete axum todo",
  "completed": true
}
```

### Remove todo

```bash
curl -X DELETE http://127.0.0.1:3000/todos/ec2553b0-6f91-4c48-a8b1-39bffc41b46a
```


