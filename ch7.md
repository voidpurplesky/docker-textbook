## 7.6 연습문제
```
PS D:\cmj\workspaces\docker\080258\ch07\lab> docker-compose -f docker-compose-dev.yml up -d
time="2024-10-01T12:42:30+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch07\\lab\\docker-compose-dev.yml: the attribute `version` is obsolete, it will be ignored, please remove it to av
oid potential confusion"
time="2024-10-01T12:42:30+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 1/1
 ✔ Container lab-todo-web-1  Started
```
mac - error
```
PS D:\cmj\workspaces\docker\080258\ch07\lab> docker-compose -f docker-compose-test.yml up -d
time="2024-10-01T12:45:08+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch07\\lab\\docker-compose-test.yml: the attribute `version` is obsolete, it will be ignored, please remove it to a
void potential confusion"
time="2024-10-01T12:45:08+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 1/2
 ✔ Network lab_default      Created                                                                                                                                                                   0.0s 
 - Container lab-todo-db-1  Creating                                                                                                                                                                  0.0s 
Error response from daemon: invalid mount config for type "bind": bind source path does not exist: /data/postgres
```
windows
```
PS D:\cmj\workspaces\docker\080258\ch07\lab> docker-compose -f docker-compose-test-windows.yml up -d
time="2024-10-01T12:46:48+09:00" level=warning msg="D:\\cmj\\workspaces\\docker\\080258\\ch07\\lab\\docker-compose-test-windows.yml: the attribute `version` is obsolete, it will be ignored, please remove
 it to avoid potential confusion"
time="2024-10-01T12:46:48+09:00" level=warning msg="networks.app-net: external.name is deprecated. Please set name and external: true"
[+] Running 2/2
 ✔ Container lab-todo-db-1   Started                                                                                                                                                                  1.3s 
 ✔ Container lab-todo-web-1  Started
```
https://github.com/gilbutITbook/080258/tree/main/ch07/lab
c:/data/postgres에 있음 d:/data/postgres 비어있음
http://localhost:8050/
페이지가 작동하지 않습니다.
현재 localhost에서 요청을 처리할 수 없습니다.
HTTP ERROR 500
