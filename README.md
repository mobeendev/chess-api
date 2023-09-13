## PHP Chess API

API using [Chess Data](https://github.com/chesslablab/chess-data).

### Documentation

Read the latest docs [here](https://chess-api.readthedocs.io/en/latest/).

### Demo

Check out [this demo](https://www.chesslablab.com).

### Installation

Install the Composer packages:
```
composer install
```

Create an `.env` file:

```
cp .env.example .env
```

Finally, you may want to add the following entry to your `/etc/hosts` file if running the PHP chess API on your localhost along with [React Chess](https://github.com/chesslablab/react-chess) as per the `REACT_APP_API_HOST` variable defined in the [react-chess/.env.example](https://github.com/chesslablab/react-chess/blob/master/.env.example) file.

### Run the Chess API

There is an easy quick way to get the Chess API up and running without an SSL certificate for when testing endpoints that don't require a database connection, e.g., `POST /api/download/image`. In such cases use [PHP's built-in web server](https://www.php.net/manual/en/features.commandline.webserver.php) as described next.

```
cd public
```
```
php -S localhost:8000
```

### Run the Chess API on a Docker Container

Before starting the Chess API for the first time, make sure to have created the `certificate.crt` and `private.key` files into the `docker/nginx/ssl` folder.

#### Development

This will allow the `HOST` website running on `PORT` as defined in [react-chess/.env.example](https://github.com/chesslablab/react-chess/blob/master/.env.example) to send requests to the Chess API server.

```
docker compose -f docker-compose.dev.yml up -d
```

#### Production

This will allow any origin to send requests to the Chess API server.

```
docker compose -f docker-compose.prod.yml up -d
```

### File Permissions Setup

Make sure the `var` directory exists:

```
mkdir var
```

And set up the following permissions:

```
sudo chown www-data:standard -R var
sudo chmod 775 -R var
```

Finally, set up the following permissions for the `storage` directory:

```
sudo chown www-data:standard -R storage
sudo chmod 775 -R storage
```

### Contributions

See the [contributing guidelines](https://github.com/chesslablab/chess-api/blob/main/CONTRIBUTING.md).

Happy learning and coding!
