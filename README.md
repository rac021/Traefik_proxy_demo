# Traefik_proxy_demo


WhoAmi Docker images :

```
❯  $ docker run -d \
     -l traefik.backend=test1 \
     -l traefik.frontend.rule=HOST:test.localhost \
     -P --name businessService emilevauge/whoami

   $ docker inspect --format '{{ .NetworkSettings.Ports }}'  businessService

```
