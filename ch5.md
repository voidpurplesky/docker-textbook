# 5장 도커 허브 등 레지스트리에 이미지 공유하기
## 5.1 레지스트리, 리포지터리, 이미지 태그 다루기
## 5.2 도커 허브에 직접 빌드한 이미지 푸시하기
$dockerId="voidpurplesky"
```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> $dockerId="voidpurplesky"
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker login -u $dockerId
Password:
Login Succeeded
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker image tag image-gallery $dockerId/image-gallery:v1
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker image ls --filter reference=image-gallery --filter reference=$dockerId/image-gallery:v1 
REPOSITORY                    TAG       IMAGE ID       CREATED          SIZE  
image-gallery                 latest    faa969381f6f   16 minutes ago   27.5MB
voidpurplesky/image-gallery   v1        faa969381f6f   16 minutes ago   27.5MB
```

```
S D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker image push $dockerId/image-gallery:v1
The push refers to repository [docker.io/voidpurplesky/image-gallery]
36718255964b: Waiting
4f4fb700ef54: Waiting
31603596830f: Waiting
792f5419a843: Waiting
eb2d5117851a: Waiting
31ff1d53c793: Waiting
4dbbbcc98a80: Waiting
push access denied, repository does not exist or may require authorization: server message: insufficient_scope: authorization failed
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker login

USING WEB BASED LOGIN
To sign in with credentials on the command line, use 'docker login -u <username>'

Your one-time device confirmation code is: XFPV-RLGD
Press ENTER to open your browser or submit your device code here: https://login.docker.com/activate

Waiting for authentication in the browser…
Login Succeeded
```
데스크탑 로그인이 되있어도 콘솔로그인? 안되있을수 잇다함 로그인완료후
```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker image push $dockerId/image-gallery:v1
The push refers to repository [docker.io/voidpurplesky/image-gallery]
4dbbbcc98a80: Pushed
36718255964b: Pushed
4f4fb700ef54: Pushed
792f5419a843: Mounted from diamol/base
31ff1d53c793: Pushed
31603596830f: Mounted from diamol/ch02-hello-diamol
eb2d5117851a: Pushed
v1: digest: sha256:faa969381f6fce503204e73f68e245a7901add4ffc35cd7201833f0df146e064 size: 856
```
## 5.3 나만의 도커 레지스트리 운영하기
```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker container run -d -p 5000:5000 --restart always diamol/registry
Unable to find image 'diamol/registry:latest' locally
latest: Pulling from diamol/registry
6a2aeb3b52c0: Download complete
aea0fab1b866: Download complete
3fec9ac2e0fe: Download complete
b72408f4bc4f: Download complete
Digest: sha256:49c5a928c870d496013d98d4357c93f35b1896a0385ef275664bc43e69b14950
Status: Downloaded newer image for diamol/registry:latest
ab6cd3583143dce76f6a20735faae794ebbec683848ba160da0d17412d7a4a76
```

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> Add-content -Value "127.0.0.1 registry.local" -Path /windows/system32/drivers/etc/hosts
Add-content : 'D:\windows\system32\drivers\etc\hosts' 경로의 일부를 찾을 수 없습니다.
위치 줄:1 문자:1
+ Add-content -Value "\n127.0.0.1 registry.local" -Path /windows/system ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (D:\windows\system32\drivers\etc\hosts:String) [Add-Content], DirectoryNotFoundException
    + FullyQualifiedErrorId : GetContentWriterDirectoryNotFoundError,Microsoft.PowerShell.Commands.AddContentCommand
 
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> Add-content -Value "127.0.0.1 registry.local" -Path c:/windows/system32/drivers/etc/hosts
Add-content : 'C:\windows\system32\drivers\etc\hosts' 경로에 대한 액세스가 거부되었습니다.
위치 줄:1 문자:1
+ Add-content -Value "\n127.0.0.1 registry.local" -Path c:/windows/syst ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : PermissionDenied: (C:\windows\system32\drivers\etc\hosts:String) [Add-Content], UnauthorizedAccessException
    + FullyQualifiedErrorId : GetContentWriterUnauthorizedAccessError,Microsoft.PowerShell.Commands.AddContentCommand
```
관리자 권한
`
PS C:\Users\EZEN> Add-content -Value "127.0.0.1 registry.local" -Path c:/windows/system32/drivers/etc/hosts
`
안될경우
```
Ping registry.local [218.38.137.28] 32바이트 데이터 사용:
요청 시간이 만료되었습니다.
요청 시간이 만료되었습니다.
요청 시간이 만료되었습니다.
요청 시간이 만료되었습니다.

218.38.137.28에 대한 Ping 통계:
    패킷: 보냄 = 4, 받음 = 0, 손실 = 4 (100% 손실),
```

될경우
```
PS C:\Users\EZEN> ping registry.local

Ping registry.local [127.0.0.1] 32바이트 데이터 사용:
127.0.0.1의 응답: 바이트=32 시간<1ms TTL=128
127.0.0.1의 응답: 바이트=32 시간<1ms TTL=128
127.0.0.1의 응답: 바이트=32 시간<1ms TTL=128
127.0.0.1의 응답: 바이트=32 시간<1ms TTL=128

127.0.0.1에 대한 Ping 통계:
    패킷: 보냄 = 4, 받음 = 4, 손실 = 0 (0% 손실),
왕복 시간(밀리초):
    최소 = 0ms, 최대 = 0ms, 평균 = 0ms
```

설정>Docker Engine
`"insecure-registries" : ["registry.local:5000"]` 추가

```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "insecure-registries" : ["registry.local:5000"]
}
```
Apply & restart

```
> docker info
...
 Insecure Registries:
  hubproxy.docker.internal:5555
  registry.local:5000
  127.0.0.0/8
...
```

```
PS C:\Users\EZEN> docker image push registry.local:5000/gallery/ui:v1
The push refers to repository [registry.local:5000/gallery/ui]
31ff1d53c793: Pushed
36718255964b: Pushed
4f4fb700ef54: Pushed
792f5419a843: Pushed
eb2d5117851a: Pushed
4dbbbcc98a80: Pushed
31603596830f: Pushed
failed commit on ref "manifest-sha256:5e4933f19591b825f7cb4589fc777dd03d98edb6adee9d9ee06529ad642e8a3c": unexpected status from PUT request to http://registry.local:5000/v2/gallery/ui/manifests/v1: 400 B
ad Request
```

