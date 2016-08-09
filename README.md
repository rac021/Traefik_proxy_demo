# Traefik_proxy_demo


WhoAmi Docker images :

```
❯  $ sudo ./traefik --configFile=traefik.toml

   $ docker run -d \
     -l traefik.backend=test1 \
     -l traefik.frontend.rule=HOST:test.localhost \
     -P --name businessService emilevauge/whoami

   $ docker inspect --format '{{ .NetworkSettings.Ports }}'  businessService

   $ curl $(hostname --all-ip-addresses | awk '{print $1}'):SPECIFIC_PORT
   
```

   http://localhost:8081
   
   
