# Traefik_proxy_demo


WhoAmi Docker images :

```
❯  $ docker run -d -l \
     traefik.backend=test1 -l traefik.frontend.rule=HOST:test.localhost \
    -p 8080:8080 --name whoami -t jwilder/whoami
    
   $ curl $(hostname --all-ip-addresses | awk '{print $1}'):8080
   I'm 736ab83847bb
```
