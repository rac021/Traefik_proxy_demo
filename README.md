# Traefik_proxy_demo

**Dnsmasq**
```
❯ $ head /etc/dnsmasq.conf 
    address=/localhost/172.17.0.1
 
```

WhoAmi Docker images :

```
❯  $ sudo ./traefik --configFile=traefik.toml

   $ docker run -d \
     -l traefik.backend=test1 \
     -l traefik.frontend.rule=Host:test.localhost \
     -P --name businessService emilevauge/whoami

   $ docker inspect --format '{{ .NetworkSettings.Ports }}'  businessService

   $ curl $(hostname --all-ip-addresses | awk '{print $1}'):SPECIFIC_PORT
   
```

   **Web-UI** : localhost:8081
   
   **Rerouting :**
   
   Traefik will reroute **test.localhost:8000** to the right container ( businessService )
   
