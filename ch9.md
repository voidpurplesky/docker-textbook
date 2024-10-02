## 9.1
200
```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": true,
  "insecure-registries": [
    "registry.local:5000"
  ],
  "metrics-addr": "127.0.0.1:9323"
}
```

http://localhost:9323/metrics


`$hostIP=$(Get-NetIPConfiguration | Where-Object {$_.IPv4DefaultGateway -ne $null}).IP4Address.IPAddress`
리눅스 
`hostIP=$(ip route get 1 | awk '{print $NF;exit}')`
MAC 
`hostIP-$(ifconfig en0 | grep -e 'inet\s' | awk '{print $2})`
`docker container run -e DOCKER_HOST=$hostIP -d -p 9090:9090 diamol/prometheus:2.13.1`

```
PS D:\cmj\workspaces\docker> docker network create nat
a94904017304b129f88b89b6b64263186e3f4a6e3242f5da18d132a994c8d580

docker-compose up -d
```
http://localhost:8010/

http://localhost:8011/actuator/prometheus

## 9.2
`for ($i=1; $i -le 5; $i++) { iwr -useb http://localhost:8010 | Out-Null }`
http://localhost:8012/metrics
access_log_total{hostname="5349f228faab"} 32
5씩증가

http://localhost:9090/targets

```
PS D:\cmj\workspaces\docker\080258\ch09\exercises> docker-compose -f docker-compose-scale.yml up -d --scale accesslog=3
time="2024-10-01T16:34:01+09:00" level=warning msg="The \"HOST_IP\" variable is not set. Defaulting to a blank string."
time="2024-10-01T16:34:01+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch09\\exercises\\docker-compose-scale.yml: the attribute `version` is obsolete, it will be ignored
, please remove it to avoid potential confusion"
time="2024-10-01T16:34:01+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 6/6
 ✔ Container exercises-prometheus-1     Running                                                                                                                                       0.0s 
 ✔ Container exercises-accesslog-3      Started                                                                                                                                      12.4s 
 ✔ Container exercises-accesslog-1      Started                                                                                                                                      12.0s 
 ✔ Container exercises-accesslog-2      Started                                                                                                                                      12.7s 
 ✔ Container exercises-iotd-1           Running                                                                                                                                       0.0s 
 ✔ Container exercises-image-gallery-1  Started                                                                                                                                       2.2s 

PS D:\cmj\workspaces\docker\080258\ch09\exercises> for ($i=1; $i -le 10; $i++) { iwr -useb http://localhost:8010 | Out-Null }
```
## 9.6 연습문제 225
```
PS D:\cmj\workspaces\docker> docker container run -d -p 8050:80 diamol/ch09-todo-list
Unable to find image 'diamol/ch09-todo-list:latest' locally
latest: Pulling from diamol/ch09-todo-list
641667054481: Download complete
3bc5282286b7: Download complete
e936bd534ffb: Download complete
caf64655bcbb: Download complete
d1927dbcbcab: Download complete
e9d8a968b003: Download complete
68ced04f60ab: Download complete
Digest: sha256:401c93647463079bdc35e06d274d8c56758c18ebeb156c6ea3ff2cb5fc74ce9f
Status: Downloaded newer image for diamol/ch09-todo-list:latest
19e9a7c40ca68eddd0abe38da277786040be3ef52628df1c4b395e37c56948e2
```
http://localhost:8050

http://localhost:8050/metrics

cd 080258\ch09\lab
container rm

`docker-compose up -d`
```
PS D:\cmj\workspaces\docker\080258\ch09\lab> docker-compose up -d
time="2024-10-02T09:34:35+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch09\\lab\\docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid 
potential confusion"
time="2024-10-02T09:34:35+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 4/4
 ✔ prometheus Pulled                                                                                                                                                                                  4.4s 
   ✔ e8bb6249c6de Download complete                                                                                                                                                                   0.9s 
 ✔ grafana Pulled                                                                                                                                                                                     5.2s 
   ✔ bd8566134b91 Download complete                                                                                                                                                                   0.4s 
[+] Running 3/3
 ✔ Container lab-prometheus-1  Started                                                                                                                                                                1.4s 
 ✔ Container lab-todo-list-1   Started                                                                                                                                                                1.3s 
 ✔ Container lab-grafana-1     Started
```
https://github.com/gilbutITbook/080258/tree/main/ch09/lab
http://localhost:8050
http://localhost:3000
