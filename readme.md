# Geofront docker

Runs a [Geofront](https://github.com/spoqa/geofront) Server. More information on their [documentation](https://geofront.readthedocs.io)

## Usage

You must create a geofront config file named `geofront.cfg.py`

```
docker run -d -p 80:8080 -v /path/to/config:/config --name geofront sett/geofront
```

### Redis

If you want to use redis for caching you can link it:

```
docker run -d --name redis redis
docker run -d -p 80:8080 -v /path/to/config:/config --link redis:redis --name geofront sett/geofront
```

Point your config to use the host `redis` e.g.
```
TOKEN_STORE = RedisCache(host='redis', db=0)
```