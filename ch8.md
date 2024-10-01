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

