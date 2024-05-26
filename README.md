
## Python Flask Application
The application is simple python3 flask-based REST app. Application needs connection for the database for single endpoint and also need a cache server.

You can control the application configuration via ENV variables:
```conf
APP_HOST=127.0.0.1
APP_PORT=5000
REDIS_HOST=127.0.0.1
REDIS_PORT=6379
DATABASE_URI=mysql+pymysql://<user>:<password>@<host>:3306/<db_name>
DATABASE_URI=postgresql+psycopg2://<user>:<password>@<host>:5432/<db_name>
```

> **Note**
>
> For `DATABASE_URI` use only any one of it, depending on which DB you prefer.

**Following commands can be used to operate with database and/or the application:-**
```sh
python app.py         ## Run application
```

```sh
python create_db.py   ## Create DB (Make sure this only run one time.)
python drop_db.py     ## Drop DB
```

**Application endpoints are:**
* `/` - hello world endpoint
* `/status` - status endpoint
* `/palindrom/<text>` - check if the text is palindrom, if true the text is stored in the DB
* `/admin` - admin area
* `/redis-hits` - endpoint for testing redis connection

**Points to remember**
1. The application is ready once the `/status` is responding with `200` message `OK`. Not ready state results in `404` message `Not ready`.
2. When `/redis-hits` endpoint is accessed the return should not be ***No response from redis***.

> **Note**
>
> DB drivers `pymysql` and `psycopg2` are part of the `requirements.txt`, change them in case you have some problem with installation.
