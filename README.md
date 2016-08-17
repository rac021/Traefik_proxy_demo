# Traefik_proxy_demo

**Dnsmasq**
```
❯ $ head /etc/dnsmasq.conf 
    address=/localhost/172.17.0.1
 
  $ sudo service dnsmasq restart
    
```
*     *for more help : https://davejamesmiller.com/blog/installing-dnsmasq-wildcard-local-domains-debian*


**Traefik commande**

```
❯  $ sudo ./traefik --configFile=traefik.toml

```

![traefuk_01](https://cloud.githubusercontent.com/assets/7684497/17548330/b323b51e-5eeb-11e6-9fdf-9aee7816767d.png)


**WhoAmi Docker images :**

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
   
