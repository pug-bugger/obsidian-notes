Back-end consist of the main server.js file. This file has access to config file, loads the necessary libraries, such as express and mongoDB connector, and also the routes of order and chat.

Routes are used to handle requests for each collection separately.

• /:id → Параметр передается **в URL-пути** (пример: /api/orders/123).
`req.params.id`
• ?id=... → Параметр передается **в строке запроса (query params)** (пример: /api/orders?id=123).
`req.query.id
