# Traefik_proxy_demo

**Dnsmasq**
```
❯ $ head /etc/dnsmasq.conf 
    address=/localhost/172.17.0.1
 
```

WhoAmi Docker images :

```
❯  $ sudo ./traefik --configFile=traefik.toml

```

![traefik_01](https://cloud.githubusercontent.com/assets/7684497/17546778/044d7cac-5ee4-11e6-813b-ee5c9a3e32d4.png)

``` 
❯  $ docker run -d \
     -l traefik.backend=test1 \
     -l traefik.frontend.rule=Host:test.localhost \
     -P --name businessService emilevauge/whoami

   $ docker inspect --format '{{ .NetworkSettings.Ports }}'  businessService

   $ curl $(hostname --all-ip-addresses | awk '{print $1}'):SPECIFIC_PORT
   
```

**Web-UI :** localhost:8081
   
![treafik_02](https://cloud.githubusercontent.com/assets/7684497/17546937/b0a3f8be-5ee4-11e6-9101-4045b87f923f.png)
   
   
   
*Note :* Traefik will reroute **test.localhost:8000** to the right container ( businessService )
   
   
**Load Balancing : Scalable Traffic**

```
❯  $ docker run -d \
     -l traefik.backend=test1 \
     -l traefik.frontend.rule=Host:test.localhost \
     -P emilevauge/whoami
     
```
...

![traefik_03](https://cloud.githubusercontent.com/assets/7684497/17547027/330846de-5ee5-11e6-90bf-7711e9ee1d73.png)


**Rerouting :**
   
Traefik will reroute **test.localhost:8000** to one of the corresponding backend container ( businessService )
   
