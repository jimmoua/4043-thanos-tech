<h1>API Endpoints</h1>

These are the docs for Bams Barber Shop's API endpoints. Some endpoints will require a JWT token. This token is being stored in a session and a cookie is stored on the client's computer.

| Type  |      Endpoint       |                          Description                          |
| :---: | :-----------------: | :-----------------------------------------------------------: |
|  GET  |    `/api/styles`    |           retrieves a list of styles in JSON format           |
| POST  | `/api/appointments` | sends JSON body data to server containing appointment details |
| POST  |    `/api/login`     |         Logins a client in when provided credentials          |
| POST  |      `/logout`      |    Logs a client out and deletes their session from the db    |
