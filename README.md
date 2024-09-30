# docker-textbook
도커교과서 길벗
```
> docker version
> docker-compose version
```
실습 환경 초기화 명령
```
docker container rm -f $(docker container ls -aq)
```
이미지가 차지한 디스크 용량 모두 회수
```
docker image rm -f $(docker image ls -f reference='diamol/*' -q)
```
