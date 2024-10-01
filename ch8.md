## 8.1 헬스 체크를 지원하는 도커 이미지 빌드하기
```
PS D:\cmj\workspaces\docker> docker container run -d -p 8090:80 diamol/ch08-numbers-api
Unable to find image 'diamol/ch08-numbers-api:latest' locally
latest: Pulling from diamol/ch08-numbers-api
73eb2212f65e: Download complete
e26e4cba9e8c: Download complete
Digest: sha256:0dcd49f3ecd0d050c0a8cc6c5f516ea37d316b620c5c6839c53b523bc2f5fb7a
Status: Downloaded newer image for diamol/ch08-numbers-api:latest
dad97868e788b0a23f121ba350d79f950aec2aee68b610994ba85ecd458069a0
PS D:\cmj\workspaces\docker> curl http://localhost:8090/rng


StatusCode        : 200
StatusDescription : OK
Content           : 88
RawContent        : HTTP/1.1 200 OK
                    Content-Type: application/json; charset=utf-8
                    Date: Tue, 01 Oct 2024 03:59:29 GMT
                    Server: Kestrel

                    88
Forms             : {}
Headers           : {[Transfer-Encoding, chunked], [Content-Type, application/json; charset=utf-8], [Date, Tue, 01 Oct 2024 03:59:29 GMT], [Server, Kestrel]}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 2



PS D:\cmj\workspaces\docker> curl http://localhost:8090/rng


StatusCode        : 200
StatusDescription : OK
Content           : 45
RawContent        : HTTP/1.1 200 OK
                    Content-Type: application/json; charset=utf-8
                    Date: Tue, 01 Oct 2024 03:59:31 GMT
                    Server: Kestrel

                    45
Forms             : {}
Headers           : {[Transfer-Encoding, chunked], [Content-Type, application/json; charset=utf-8], [Date, Tue, 01 Oct 2024 03:59:31 GMT], [Server, Kestrel]}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 2



PS D:\cmj\workspaces\docker> curl http://localhost:8090/rng


StatusCode        : 200
StatusDescription : OK
Content           : 70
RawContent        : HTTP/1.1 200 OK
                    Content-Type: application/json; charset=utf-8
                    Date: Tue, 01 Oct 2024 03:59:32 GMT
                    Server: Kestrel

                    70
Forms             : {}
Headers           : {[Transfer-Encoding, chunked], [Content-Type, application/json; charset=utf-8], [Date, Tue, 01 Oct 2024 03:59:32 GMT], [Server, Kestrel]}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 2



PS D:\cmj\workspaces\docker> curl http://localhost:8090/rng
curl : 원격 서버에서 (500) 내부 서버 오류 오류를 반환했습니다.
위치 줄:1 문자:1
+ curl http://localhost:8090/rng
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (System.Net.HttpWebRequest:HttpWebRequest) [Invoke-WebRequest], WebException
    + FullyQualifiedErrorId : WebCmdletWebResponseException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand
 
PS D:\cmj\workspaces\docker> docker container ls
CONTAINER ID   IMAGE                          COMMAND                   CREATED          STATUS          PORTS                    NAMES
dad97868e788   diamol/ch08-numbers-api        "dotnet /app/Numbers…"   38 seconds ago   Up 37 seconds   0.0.0.0:8090->80/tcp     kind_galois
e4ab292fd248   diamol/ch06-todo-list          "dotnet ToDoList.dll"     12 minutes ago   Up 12 minutes   0.0.0.0:8050->80/tcp     lab-todo-web-1
5b57b5d363d1   diamol/postgres:11.5           "docker-entrypoint.s…"   12 minutes ago   Up 12 minutes   5432/tcp                 lab-todo-db-1
dede45c6393a   diamol/ch06-todo-list          "dotnet ToDoList.dll"     24 minutes ago   Up 24 minutes   0.0.0.0:8030->80/tcp     todo-list-postgres-todo-web-1
d00100c283bb   diamol/postgres:11.5           "docker-entrypoint.s…"   24 minutes ago   Up 24 minutes   0.0.0.0:5433->5432/tcp   todo-list-postgres-todo-db-1
28434dd4b276   diamol/ch04-access-log         "docker-entrypoint.s…"   30 minutes ago   Up 30 minutes   80/tcp                   image-of-the-day-accesslog-1
8cdea69d25f8   diamol/ch04-image-of-the-day   "java -jar /app/iotd…"   36 minutes ago   Up 36 minutes   0.0.0.0:13826->80/tcp    image-of-the-day-iotd-2
a89a112797a9   diamol/ch04-image-of-the-day   "java -jar /app/iotd…"   36 minutes ago   Up 36 minutes   0.0.0.0:13828->80/tcp    image-of-the-day-iotd-3
c763d857dd7c   diamol/ch04-image-gallery      "/web/server"             57 minutes ago   Up 57 minutes   0.0.0.0:8010->80/tcp     image-of-the-day-image-gallery-1
34dbd5422913   diamol/ch04-image-of-the-day   "java -jar /app/iotd…"   57 minutes ago   Up 57 minutes   0.0.0.0:13722->80/tcp    image-of-the-day-iotd-1
```
\080258\ch08\exercises\numbers\numbers-api\Dockerfile.v2
`HEALTHCHECK CMD curl --fail http://localhost/health`

cd ./ch08/exercises/numbers
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker image build -t diamol/ch08-numbers-api:v2 -f ./numbers-api/Dockerfile.v2 .
[+] Building 142.8s (17/17) FINISHED                                                                                                                                                  docker:desktop-linux 
 => [internal] load build definition from Dockerfile.v2                                                                                                                                               0.1s 
 => => transferring dockerfile: 428B                                                                                                                                                                  0.0s 
 => [internal] load metadata for docker.io/diamol/dotnet-aspnet:latest                                                                                                                                7.4s 
 => [internal] load metadata for docker.io/diamol/dotnet-sdk:latest                                                                                                                                   4.2s 
 => [auth] diamol/dotnet-sdk:pull token for registry-1.docker.io                                                                                                                                      0.0s 
 => [auth] diamol/dotnet-aspnet:pull token for registry-1.docker.io                                                                                                                                   0.0s 
 => [internal] load .dockerignore                                                                                                                                                                     0.1s 
 => => transferring context: 2B                                                                                                                                                                       0.0s 
 => [builder 1/6] FROM docker.io/diamol/dotnet-sdk:latest@sha256:a78173a9dbd3e6b3b2af1eadad3edd6e8ef7b2801f3cda405928e5da155c7039                                                                   123.2s 
 => => resolve docker.io/diamol/dotnet-sdk:latest@sha256:a78173a9dbd3e6b3b2af1eadad3edd6e8ef7b2801f3cda405928e5da155c7039                                                                             0.1s 
 => => sha256:460e7bb4980298c8d51ffc08a56e3287127742d4536b351673153ea463880a22 6.31kB / 6.31kB                                                                                                        0.9s
 => => sha256:475935cb0b6d0d3f088b6637b4685a6c18050de45a68c3e9ab53dd5b0cf9c53f 12.40MB / 12.40MB                                                                                                     15.8s
 => => sha256:9deb21478e67b8ff1256de3e2639cefcab485f4fd5e25355d45cfd21597e22f4 116.09MB / 116.09MB                                                                                                  116.2s
 => => sha256:efefb401e9dccd3e703e80b80fb9bbd3847f66c6d7c64d51845e0d121ae00776 13.70MB / 13.70MB                                                                                                     22.3s
 => => sha256:667692510b7038b74e221f92eb33610e4968b669c8a718378ecb1f78739c3713 51.77MB / 51.77MB                                                                                                     75.5s
 => => sha256:1128949d0793d2435bb1f0640a777f32feee88b71d4fe234121c3cfb345a80c4 10.00MB / 10.00MB                                                                                                     13.1s
 => => sha256:b7a128769df1909f91b589d0a4a2e1c1671aebc047a9f46b4b30dfeb7308ea6a 7.81MB / 7.81MB                                                                                                       15.2s 
 => => sha256:c7b7d16361e00faca0e9393f3f43923f25ceb1210face87839dfc5de988905c1 50.38MB / 50.38MB                                                                                                     67.2s 
 => => extracting sha256:c7b7d16361e00faca0e9393f3f43923f25ceb1210face87839dfc5de988905c1                                                                                                             2.3s 
 => => extracting sha256:b7a128769df1909f91b589d0a4a2e1c1671aebc047a9f46b4b30dfeb7308ea6a                                                                                                             0.4s 
 => => extracting sha256:1128949d0793d2435bb1f0640a777f32feee88b71d4fe234121c3cfb345a80c4                                                                                                             0.3s 
 => => extracting sha256:667692510b7038b74e221f92eb33610e4968b669c8a718378ecb1f78739c3713                                                                                                             2.4s 
 => => extracting sha256:efefb401e9dccd3e703e80b80fb9bbd3847f66c6d7c64d51845e0d121ae00776                                                                                                             1.6s 
 => => extracting sha256:9deb21478e67b8ff1256de3e2639cefcab485f4fd5e25355d45cfd21597e22f4                                                                                                             5.0s 
 => => extracting sha256:460e7bb4980298c8d51ffc08a56e3287127742d4536b351673153ea463880a22                                                                                                             0.1s 
 => => extracting sha256:475935cb0b6d0d3f088b6637b4685a6c18050de45a68c3e9ab53dd5b0cf9c53f                                                                                                             0.4s 
 => [internal] load build context                                                                                                                                                                     0.3s 
 => => transferring context: 4.42kB                                                                                                                                                                   0.1s 
 => [stage-1 1/3] FROM docker.io/diamol/dotnet-aspnet:latest@sha256:d34a231013982f446e54fe15c036bf5e8585ae8e95ff1fd3e0c374a40d3f60f7                                                                  0.6s 
 => => resolve docker.io/diamol/dotnet-aspnet:latest@sha256:d34a231013982f446e54fe15c036bf5e8585ae8e95ff1fd3e0c374a40d3f60f7                                                                          0.1s 
 => [stage-1 2/3] WORKDIR /app                                                                                                                                                                        0.2s 
 => [builder 2/6] WORKDIR /src                                                                                                                                                                        1.8s 
 => [builder 3/6] COPY src/Numbers.Api/Numbers.Api.csproj .                                                                                                                                           0.1s 
 => [builder 4/6] RUN dotnet restore                                                                                                                                                                  1.7s 
 => [builder 5/6] COPY src/Numbers.Api/ .                                                                                                                                                             0.5s 
 => [builder 6/6] RUN dotnet publish -c Release -o /out Numbers.Api.csproj                                                                                                                            3.6s 
 => [stage-1 3/3] COPY --from=builder /out/ .                                                                                                                                                         0.9s 
 => exporting to image                                                                                                                                                                                1.3s 
 => => exporting layers                                                                                                                                                                               0.9s 
 => => exporting manifest sha256:42a817402a7e25ff28a7f8966169d818875930c2d91a57740271acca8d0fbf48                                                                                                     0.0s 
 => => exporting config sha256:df1974bb20f4b78c8f894448cf4e13629f6b761776e9262c695c3001fb08d223                                                                                                       0.0s 
 => => exporting attestation manifest sha256:c1a964fae866566bfd23788b53e6708d6a53116d4678c6d48aee83c93ed8a0ce                                                                                         0.1s 
 => => exporting manifest list sha256:68f749c2ee03190be6fe062b3284b7690735cb4aae52911c3507ad65f38a23e5                                                                                                0.0s 
 => => naming to docker.io/diamol/ch08-numbers-api:v2                                                                                                                                                 0.0s 
 => => unpacking to docker.io/diamol/ch08-numbers-api:v2                                                                                                                                              0.2s 

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/67qexe8mn6w87gf0jmjwgbqim

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview
```

178 버전 v2 이미지로 API 컨테이너를 실행
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container run -d -p 8091:80 diamol/ch08-numbers-api:v2
08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9
```

30초 정도 기다린 다음 컨테이너 목록을 확인
`docker container ls`

```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container ls
CONTAINER ID   IMAGE                        COMMAND                   CREATED             STATUS                   PORTS                  NAMES
08dcbf92c5cd   diamol/ch08-numbers-api:v2   "dotnet /app/Numbers…"   5 minutes ago       Up 5 minutes (healthy)   0.0.0.0:8091->80/tcp   brave_joliot
dad97868e788   diamol/ch08-numbers-api      "dotnet /app/Numbers…"   About an hour ago   Up About an hour         0.0.0.0:8090->80/tcp   kind_galois
```

```
STATUS
(healthy)
```

4번 호출
```
curl http://localhost:8091/rng
curl http://localhost:8091/rng
curl http://localhost:8091/rng
curl http://localhost:8091/rng
```
90초를 기다려 도커가 이상 상태를 감지하는지 확인
`docker container ls`

### Logs
```
2024-10-01 14:21:22 info: Microsoft.Hosting.Lifetime[0]
2024-10-01 14:21:22       Now listening on: http://[::]:80
2024-10-01 14:21:22 info: Microsoft.Hosting.Lifetime[0]
2024-10-01 14:21:22       Application started. Press Ctrl+C to shut down.
2024-10-01 14:21:22 info: Microsoft.Hosting.Lifetime[0]
2024-10-01 14:21:22       Hosting environment: Production
2024-10-01 14:21:22 info: Microsoft.Hosting.Lifetime[0]
2024-10-01 14:21:22       Content root path: /app
2024-10-01 14:27:55 warn: Numbers.Api.Controllers.RngController[0]
2024-10-01 14:27:55       Unhealthy!
```

### Inspect
```
	"State": {
		"Status": "running",
		"Running": true,
		"Paused": false,
		"Restarting": false,
		"OOMKilled": false,
		"Dead": false,
		"Pid": 17020,
		"ExitCode": 0,
		"Error": "",
		"StartedAt": "2024-10-01T05:21:21.454344441Z",
		"FinishedAt": "0001-01-01T00:00:00Z",
		"Health": {
			"Status": "unhealthy",
			"FailingStreak": 7,
			"Log": [
				{
					"Start": "2024-10-01T05:29:22.391099813Z",
...
```

```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container ls
CONTAINER ID   IMAGE                        COMMAND                   CREATED          STATUS                      PORTS                  NAMES
08dcbf92c5cd   diamol/ch08-numbers-api:v2   "dotnet /app/Numbers…"   11 minutes ago   Up 11 minutes (unhealthy)   0.0.0.0:8091->80/tcp   brave_joliot
dad97868e788   diamol/ch08-numbers-api      "dotnet /app/Numbers…"   2 hours ago      Up 2 hours                  0.0.0.0:8090->80/tcp   kind_galois
```

```
STATUS
(unhealthy)
```

```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container inspect $(docker container ls --last 1 --format '{{.ID}}')
[
    {
        "Id": "08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9",
        "Created": "2024-10-01T05:21:21.25013757Z",
        "Path": "dotnet",
        "Args": [
            "/app/Numbers.Api.dll"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 17020,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-10-01T05:21:21.454344441Z",
            "FinishedAt": "0001-01-01T00:00:00Z",
            "Health": {
                "Status": "unhealthy",
                "FailingStreak": 13,
                "Log": [
                    {
                        "Start": "2024-10-01T05:32:22.607210804Z",
                        "End": "2024-10-01T05:32:22.641025322Z",
                        "ExitCode": 22,
                        "Output": "  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current\n                                 Dload  Upload   Total   Spent    Left  Speed\n\r  0   
  0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\r  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\ncurl: (22) The requested URL returned error: 500 
Internal Server Error\n"
                    },
                    {
                        "Start": "2024-10-01T05:32:52.640418184Z",
                        "End": "2024-10-01T05:32:52.674907541Z",
                        "ExitCode": 22,
                        "Output": "  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current\n                                 Dload  Upload   Total   Spent    Left  Speed\n\r  0   
  0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\r  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\ncurl: (22) The requested URL returned error: 500 
Internal Server Error\n"
                    },
                    {
                        "Start": "2024-10-01T05:33:22.674897941Z",
                        "End": "2024-10-01T05:33:22.712471827Z",
                        "ExitCode": 22,
                        "Output": "  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current\n                                 Dload  Upload   Total   Spent    Left  Speed\n\r  0   
  0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\r  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\ncurl: (22) The requested URL returned error: 500 
Internal Server Error\n"
                    },
                    {
                        "Start": "2024-10-01T05:33:52.712857971Z",
                        "End": "2024-10-01T05:33:52.74890084Z",
                        "ExitCode": 22,
                        "Output": "  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current\n                                 Dload  Upload   Total   Spent    Left  Speed\n\r  0   
  0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\r  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\ncurl: (22) The requested URL returned error: 500 
Internal Server Error\n"
                    },
                    {
                        "Start": "2024-10-01T05:34:22.750721287Z",
                        "End": "2024-10-01T05:34:22.791044494Z",
                        "ExitCode": 22,
                        "Output": "  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current\n                                 Dload  Upload   Total   Spent    Left  Speed\n\r  0   
  0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\r  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0\ncurl: (22) The requested URL returned error: 500 
Internal Server Error\n"
                    }
                ]
            }
        },
        "Image": "sha256:68f749c2ee03190be6fe062b3284b7690735cb4aae52911c3507ad65f38a23e5",
        "ResolvConfPath": "/var/lib/docker/containers/08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9/hostname",
        "HostsPath": "/var/lib/docker/containers/08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9/hosts",
        "LogPath": "/var/lib/docker/containers/08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9/08dcbf92c5cd15a8eda8f708b519c6a3d0cb2a5fe84e3c0927ed97309edff0a9-json.log",
        "Name": "/brave_joliot",
        "RestartCount": 0,
        "Driver": "overlayfs",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {
                "80/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "8091"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                17,
                203
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": null,
            "Name": "overlayfs"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "08dcbf92c5cd",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "ASPNETCORE_URLS=http://+:80",
                "DOTNET_RUNNING_IN_CONTAINER=true",
                "DOTNET_VERSION=3.0.3",
                "ASPNETCORE_VERSION=3.0.3",
                "SQLITE_DATA_DIRECTORY=/data",
                "SQLITE_USER=root"
            ],
            "Cmd": null,
            "Healthcheck": {
                "Test": [
                    "CMD-SHELL",
                    "curl --fail http://localhost/health"
                ]
            },
            "Image": "diamol/ch08-numbers-api:v2",
            "Volumes": null,
            "WorkingDir": "/app",
            "Entrypoint": [
                "dotnet",
                "/app/Numbers.Api.dll"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "35e60989bb34b12dc4445ffb3773dac504d2ce4f0939ba9ad69fd1681052e6df",
            "SandboxKey": "/var/run/docker/netns/35e60989bb34",
            "Ports": {
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                    "EndpointID": "da366bcdf563685f0c8c0163151ed18604e898148a00245d5a05885f69c1361b",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.3",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]
```

```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container run -d -p 8092:80 diamol/ch08-numbers-web
Unable to find image 'diamol/ch08-numbers-web:latest' locally
latest: Pulling from diamol/ch08-numbers-web
383c08a2e681: Download complete
699f47ec48c2: Download complete
Digest: sha256:20c6eb1a6d449b2935cee7a72c1758d34013a09033894ca3377f3a7d6ac28b01
Status: Downloaded newer image for diamol/ch08-numbers-web:latest
fb115369e735a4387546b693e38852a440857ee4bd1075f55aaacc0ff86e7d99
```
184
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container run -d -p 8094:80 diamol/ch08-numbers-web:v2
Unable to find image 'diamol/ch08-numbers-web:v2' locally
v2: Pulling from diamol/ch08-numbers-web
8ae9a67499f9: Download complete
45d207aef600: Download complete
Digest: sha256:97818270bc82f5558acad637b7237de98868092cd540c72456bf79bf17029abd
Status: Downloaded newer image for diamol/ch08-numbers-web:v2
04328c6234a1f18af134d4b19203c1c331a0cb5dec209323f75c523c14be885e
```
잘못된 걸? 실행하면 컨테이너가 Exited인채로 만들어짐

187
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container run -d -p 8090:80 --health-interval 5s diamol/ch08-numbers-api:v3 
Unable to find image 'diamol/ch08-numbers-api:v3' locally
v3: Pulling from diamol/ch08-numbers-api
0509960d3a8a: Download complete
5ada40c0e0f8: Download complete
c29f166a9594: Download complete
Digest: sha256:8e01f3f3fa0cc3596a979930437dacb425b3047436513f2615a87063a45b7491
Status: Downloaded newer image for diamol/ch08-numbers-api:v3
2ccbbafcc6bf8e8e1de69e0bcb25078e38d67373222b6eca03c31b5cb0ebb026
```

curl http://localhost:8090/rng * 4
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container ls
CONTAINER ID   IMAGE                        COMMAND                   CREATED              STATUS                          PORTS                  NAMES
2ccbbafcc6bf   diamol/ch08-numbers-api:v3   "dotnet Numbers.Api.…"   About a minute ago   Up About a minute (unhealthy)   0.0.0.0:8090->80/tcp   beautiful_bhaskara
```
189 컨테이너가 바로 종료됨
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container run -d -p 8091:80 diamol/ch08-numbers-web:v3
Unable to find image 'diamol/ch08-numbers-web:v3' locally
v3: Pulling from diamol/ch08-numbers-web
b553df8c29da: Download complete
6bb9ca1efac7: Download complete
3f40d00db61e: Download complete
Digest: sha256:9908c8543297e98afbb3d5b7eaa198d4e0896402a813e3aa99e2e87fab25c42d
Status: Downloaded newer image for diamol/ch08-numbers-web:v3
a30d20cee8a4b35f502a83359d6e8c1ba5827b03ad4381ae3b635175c3d434c8

PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container ls --all
CONTAINER ID   IMAGE                        COMMAND                   CREATED              STATUS                          PORTS                  NAMES
a30d20cee8a4   diamol/ch08-numbers-web:v3   "/bin/sh -c 'dotnet …"   About a minute ago   Exited (1) About a minute ago                          pedantic_golick
2ccbbafcc6bf   diamol/ch08-numbers-api:v3   "dotnet Numbers.Api.…"   5 minutes ago        Up 5 minutes (unhealthy)        0.0.0.0:8090->80/tcp   beautiful_bhaskara
```
## 8-4
192
```
PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker-compose up -d
time="2024-10-01T15:14:32+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch08\\exercises\\numbers\\docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remo
ve it to avoid potential confusion"
time="2024-10-01T15:14:32+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 2/2
 ✔ Container numbers-numbers-web-1  Started                                                                                                                                                           0.7s 
 ✔ Container numbers-numbers-api-1  Started                                                                                                                                                           0.8s 

PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container ls
CONTAINER ID   IMAGE                        COMMAND                   CREATED          STATUS                    PORTS                  NAMES
ee41a91a99bb   diamol/ch08-numbers-api:v3   "dotnet Numbers.Api.…"   31 seconds ago   Up 30 seconds (healthy)   0.0.0.0:8087->80/tcp   numbers-numbers-api-1
ae5c18798348   diamol/ch08-numbers-web:v3   "/bin/sh -c 'dotnet …"   31 seconds ago   Up 29 seconds (healthy)   0.0.0.0:8088->80/tcp   numbers-numbers-web-1

PS D:\cmj\workspaces\docker\080258\ch08\exercises\numbers> docker container logs numbers-numbers-web-1
HTTPCheck: error. Url http://numbers-api/rng, exception Connection refused
HTTPCheck: status OK, url http://numbers-api/rng, took 145ms
warn: Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository[60]
      Storing keys in a directory '/root/.aspnet/DataProtection-Keys' that may not be persisted outside of the container. Protected data will be unavailable when container is destroyed.
warn: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[35]
      No XML encryptor configured. Key {06ec727c-09c4-40b1-98d6-bc242dc22ea2} may be persisted to storage in unencrypted form.
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: http://[::]:80
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /app
```


## 8.6 연습문제
docker image build -t diamol/ch08-lab -f Dockerfile .
docker image build -t diamol/ch08-lab .

docker image build -t diamol/ch08-lab:solution -f Dockerfile:solution .

```
PS D:\cmj\workspaces\docker\080258\ch08\lab> docker image build -t diamol/ch08-lab -f Dockerfile .
[+] Building 2.9s (9/9) FINISHED                                                                                                                                                      docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                                                                  0.0s
 => => transferring dockerfile: 206B                                                                                                                                                                  0.0s 
 => [internal] load metadata for docker.io/diamol/node:latest                                                                                                                                         1.7s 
 => [auth] diamol/node:pull token for registry-1.docker.io                                                                                                                                            0.0s
 => [internal] load .dockerignore                                                                                                                                                                     0.1s
 => => transferring context: 2B                                                                                                                                                                       0.0s 
 => CACHED [1/3] FROM docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879c8                                                                            0.1s 
 => => resolve docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879c8                                                                                   0.1s 
 => [internal] load build context                                                                                                                                                                     0.2s 
 => => transferring context: 1.22kB                                                                                                                                                                   0.1s 
 => [2/3] WORKDIR /app                                                                                                                                                                                0.1s
 => [3/3] COPY src/ .                                                                                                                                                                                 0.1s
 => => exporting layers                                                                                                                                                                               0.3s 
 => => exporting manifest sha256:11c15c3c6cbc435b7641d701052a558ab0889e2db8bce83f6a1e200d3958c440                                                                                                     0.0s 
 => => exporting config sha256:5f36dab03d8afdfaa1306df806c986b2e196a72ac8952f022aa003b3197c754e                                                                                                       0.0s 
 => => exporting attestation manifest sha256:a20356fd9cd97c538f42e4e8694e83c32cb85f81a679aadd439c3257f017194f                                                                                         0.0s 
 => => exporting manifest list sha256:2e5480e2d83b0c223edbf16a1b1b49dd2b257bda14609925c9dcf371c588817c                                                                                                0.0s 
 => => naming to docker.io/diamol/ch08-lab:latest                                                                                                                                                     0.0s 
 => => unpacking to docker.io/diamol/ch08-lab:latest                                                                                                                                                  0.1s 

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/fx9myn0htyel3to5dd1sqfc9n

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview

PS D:\cmj\workspaces\docker\080258\ch08\lab> docker container run diamol/ch08-lab
Allocated: 512MB
Allocated: 1024MB
Allocated: 1536MB
Allocated: 2048MB
Allocated: 2560MB
Allocated: 3072MB
Allocated: 3584MB
Allocated: 4096MB
Allocated: 4608MB
Allocated: 5120MB
Allocated: 5632MB
Allocated: 6144MB
Allocated: 6656MB
Allocated: 7168MB
Allocated: 7680MB
Allocated: 8704MB
Allocated: 9216MB
Allocated: 9728MB
Allocated: 10240MB
Allocated: 10752MB
Allocated: 11264MB
Allocated: 11776MB
Allocated: 12288MB
Allocated: 12800MB
Allocated: 13312MB

got 3 SIGTERM/SIGINTs, forcefully exiting

PS D:\cmj\workspaces\docker\080258\ch08\lab> docker image build -t diamol/ch08-lab:solution -f Dockerfile.solution .
[+] Building 1.6s (8/8) FINISHED                                                                                                                                                      docker:desktop-linux
 => [internal] load build definition from Dockerfile.solution                                                                                                                                         0.0s
 => => transferring dockerfile: 297B                                                                                                                                                                  0.0s 
 => [internal] load metadata for docker.io/diamol/node:latest                                                                                                                                         0.8s 
 => [internal] load .dockerignore                                                                                                                                                                     0.1s
 => => transferring context: 2B                                                                                                                                                                       0.0s 
 => [1/3] FROM docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879c8                                                                                   0.1s 
 => => resolve docker.io/diamol/node:latest@sha256:dfee522acebdfdd9964aa9c88ebebd03a20b6dd573908347be3ebf52ac4879c8                                                                                   0.1s 
 => [internal] load build context                                                                                                                                                                     0.1s 
 => => transferring context: 101B                                                                                                                                                                     0.0s 
 => CACHED [2/3] WORKDIR /app                                                                                                                                                                         0.0s
 => CACHED [3/3] COPY src/ .                                                                                                                                                                          0.0s 
 => exporting to image                                                                                                                                                                                0.3s 
 => => exporting layers                                                                                                                                                                               0.0s
 => => exporting manifest sha256:197c2554316107a84a775facefc86db4880d4682d09ff6b1255901bbd4ef451a                                                                                                     0.1s 
 => => exporting attestation manifest sha256:b26ac96cc783d62fa4b8d98c4fe179dc252084ec31fa06a05d4dafbf012555d3                                                                                         0.1s 
 => => exporting manifest list sha256:bb35f760c1fd0124f2ede035ace2a6e93606d9b96bf709ead1899b0aa3d468b6                                                                                                0.0s 
 => => naming to docker.io/diamol/ch08-lab:solution                                                                                                                                                   0.0s 
 => => unpacking to docker.io/diamol/ch08-lab:solution                                                                                                                                                0.0s 

View build details: docker-desktop://dashboard/build/desktop-linux/desktop-linux/7n1k3wdqhyfmt5fme1ezox1ze

 1 warning found (use docker --debug to expand):
 - JSONArgsRecommended: JSON arguments recommended for CMD to prevent unintended behavior related to OS signals (line 7)

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview

PS D:\cmj\workspaces\docker\080258\ch08\lab> docker container run diamol/ch08-lab:solution
Memory check: OK, none allocated.
Allocated: 512MB
Allocated: 1024MB
Allocated: 1536MB
Allocated: 2048MB
Allocated: 2560MB
Allocated: 3072MB
Allocated: 3584MB
Allocated: 4096MB
Allocated: 4608MB
Allocated: 5120MB
Allocated: 5632MB
Allocated: 6144MB
Allocated: 6656MB
Allocated: 7168MB
Allocated: 7680MB
Allocated: 8192MB
Allocated: 8704MB
Allocated: 9216MB
Allocated: 9728MB
Allocated: 10240MB
Allocated: 10752MB
Allocated: 11264MB
Allocated: 11776MB
Allocated: 12288MB
Allocated: 12800MB
```
https://github.com/gilbutITbook/080258/blob/main/ch08/lab/README.md

