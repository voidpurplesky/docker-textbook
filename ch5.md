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
