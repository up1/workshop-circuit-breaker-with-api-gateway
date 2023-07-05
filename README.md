# Workshop Circuit Breaker with API Gateway
* [Apache APISIX API Gateway](https://apisix.apache.org/)

## Step 1 :: Build
```
$docker compose build
```

## Step 2 :: Start service with nodejs port = 3000
```
$docker compose up -d service_a
$docker compose ps
$docker compose logs --follow
```

Access with url = http://localhost:3000/demo

## Step 3 :: Start etcd
```
$docker compose up -d etcd
$docker compose ps
$docker compose logs --follow
```

## Step 4 :: Start APISIX server and Dashboard
```
$docker compose up -d apisix
$docker compose up -d apisix-dashboard

$docker compose ps
$docker compose logs --follow
```
See all containers
```
$docker compose ps
NAME                            IMAGE                     COMMAND                  SERVICE             CREATED              STATUS              PORTS
cb-gateway-apisix-1             apache/apisix             "/docker-entrypoint.…"   apisix              About a minute ago   Up About a minute   0.0.0.0:9080->9080/tcp, 0.0.0.0:9091-9092->9091-9092/tcp, 0.0.0.0:9443->9443/tcp
cb-gateway-apisix-dashboard-1   apache/apisix-dashboard   "/usr/local/apisix-d…"   apisix-dashboard    About a minute ago   Up About a minute   0.0.0.0:9000->9000/tcp
cb-gateway-etcd-1               bitnami/etcd              "/opt/bitnami/script…"   etcd                About a minute ago   Up About a minute   0.0.0.0:2379->2379/tcp, 2380/tcp
cb-gateway-service_a-1          cb-gateway-service_a      "docker-entrypoint.s…"   service_a           About a minute ago   Up About a minute   0.0.0.0:3000->3000/tcp
```

Go to dashboard at url = http://localhost:9000/
* user=admin
* password=admin

### Tasks
* Create stream
* Create route
* Create service
* Enable API breaker plugin


