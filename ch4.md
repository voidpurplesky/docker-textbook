```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\multi-stage> docker image build -t multi-stage .
[+] Building 3.9s (10/10) FINISHED                                                                                                                                                                            docker:desktop-linux 
 => [internal] load build definition from Dockerfile                                                                                                                                                                          0.1s 
 => => transferring dockerfile: 311B                                                                                                                                                                                          0.0s 
 => [internal] load metadata for docker.io/diamol/base:latest                                                                                                                                                                 0.0s 
 => [internal] load .dockerignore                                                                                                                                                                                             0.1s 
 => => transferring context: 2B                                                                                                                                                                                               0.0s 
 => [build-stage 1/2] FROM docker.io/diamol/base:latest@sha256:787fe221a14f46b55e224ea0436aca77d345c3ded400aaf6cd40125e247f35c7                                                                                               1.7s 
 => => resolve docker.io/diamol/base:latest@sha256:787fe221a14f46b55e224ea0436aca77d345c3ded400aaf6cd40125e247f35c7                                                                                                           1.6s 
 => [auth] diamol/base:pull token for registry-1.docker.io                                                                                                                                                                    0.0s 
 => [build-stage 2/2] RUN echo 'Building...' > /build.txt                                                                                                                                                                     0.5s 
 => [test-stage 2/3] COPY --from=build-stage /build.txt /build.txt                                                                                                                                                            0.1s 
 => [test-stage 3/3] RUN echo 'Testing...' >> /build.txt                                                                                                                                                                      0.4s 
 => [stage-2 2/2] COPY --from=test-stage /build.txt /build.txt                                                                                                                                                                0.1s 
 => exporting to image                                                                                                                                                                                                        0.4s 
 => => exporting layers                                                                                                                                                                                                       0.2s 
 => => exporting manifest sha256:ee51b155b1101ca5a716293af95fe0b54cda3a0ae0c0aec637ba8cc01478c3b9                                                                                                                             0.0s
 => => exporting config sha256:4985df3d9afe5e107e92fb73ec52561b8d0c8b62da1b49841be0fdfe9d0841c5                                                                                                                               0.0s
 => => exporting attestation manifest sha256:c27a09956baa12b406ea38d484f82af6abddad0459fb70d985ae80b603bb0057                                                                                                                 0.0s 
 => => exporting manifest list sha256:9489a5e31e1cb1407409159003ce77c7024b3015f66bb073c3a89f0041d26edc                                                                                                                        0.0s 
 => => naming to docker.io/library/multi-stage:latest                                                                                                                                                                         0.0s 
 => => unpacking to docker.io/library/multi-stage:latest                                                                                                                                                                      0.1s 

 1 warning found (use docker --debug to expand):
 - JSONArgsRecommended: JSON arguments recommended for CMD to prevent unintended behavior related to OS signals (line 10)
```

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-of-the-day> docker image build -t image-of-the-day .
[+] Building 436.3s (17/17) FINISHED                                                                                                                                                                          docker:desktop-linux 
 => [internal] load build definition from Dockerfile                                                                                                                                                                          0.1s 
 => => transferring dockerfile: 357B                                                                                                                                                                                          0.0s 
 => [internal] load metadata for docker.io/diamol/openjdk:latest                                                                                                                                                              3.3s 
 => [internal] load metadata for docker.io/diamol/maven:latest                                                                                                                                                                4.6s 
 => [auth] diamol/maven:pull token for registry-1.docker.io                                                                                                                                                                   0.0s 
 => [auth] diamol/openjdk:pull token for registry-1.docker.io                                                                                                                                                                 0.0s 
 => [internal] load .dockerignore                                                                                                                                                                                             0.1s 
 => => transferring context: 2B                                                                                                                                                                                               0.0s 
 => [builder 1/6] FROM docker.io/diamol/maven:latest@sha256:bc24b7b3beaae18550590fd986b09d7833c4daedb2632c76daddab21351b934f                                                                                                341.9s 
 => => resolve docker.io/diamol/maven:latest@sha256:bc24b7b3beaae18550590fd986b09d7833c4daedb2632c76daddab21351b934f                                                                                                          0.1s 
 => => sha256:85e47f7d664b53174dcc63edad6bc36acc2788ce277d736a04e03085e2f92096 360B / 360B                                                                                                                                    1.7s 
 => => sha256:6a2b01f2ccf756e73274f5d1e242018cf651ee25e90e746da07e9788d2d5d587 857B / 857B                                                                                                                                    0.3s 
 => => sha256:0579b2a6f92cc5a2ca44af6c6807a0294fa45eb144a28ec75852bf37a2240714 9.58MB / 9.58MB                                                                                                                               27.3s 
 => => sha256:84289cf02da5745f71612d8ab7b9759a0db726244997235c102e9600cc6ef175 202.80MB / 202.80MB                                                                                                                          331.6s 
 => => sha256:fdfee37d01c31f60d071f54f2414c0da25597fe2cc5c490ce13920824dc1e23c 212B / 212B                                                                                                                                    0.3s 
 => => sha256:b4735181ba0c236211ac3061b9b64a3c6b6c49be666302913fd5fb9c5a9ef113 5.29MB / 5.29MB                                                                                                                               18.2s 
 => => sha256:f15a0f46f8c38f4ca7daecf160ba9cdb3ddeafda769e2741e179851cfaa14eec 51.83MB / 51.83MB                                                                                                                            122.4s 
 => => sha256:feab2c490a3cea21cc051ff29c33cc9857418edfa1be9966124b18abe1d5ae16 10.00MB / 10.00MB                                                                                                                             35.7s 
 => => sha256:7467d1831b6947c294d92ee957902c3cd448b17c5ac2103ca5e79d15afb317c3 7.83MB / 7.83MB                                                                                                                              302.2s 
 => => sha256:0ecb575e629cd60aa802266a3bc6847dcf4073aa2a6d7d43f717dd61e7b90e0b 50.40MB / 50.40MB                                                                                                                             95.8s 
 => => extracting sha256:0ecb575e629cd60aa802266a3bc6847dcf4073aa2a6d7d43f717dd61e7b90e0b                                                                                                                                     1.7s 
 => => extracting sha256:7467d1831b6947c294d92ee957902c3cd448b17c5ac2103ca5e79d15afb317c3                                                                                                                                     0.3s 
 => => extracting sha256:feab2c490a3cea21cc051ff29c33cc9857418edfa1be9966124b18abe1d5ae16                                                                                                                                     0.2s 
 => => extracting sha256:f15a0f46f8c38f4ca7daecf160ba9cdb3ddeafda769e2741e179851cfaa14eec                                                                                                                                     3.9s 
 => => extracting sha256:b4735181ba0c236211ac3061b9b64a3c6b6c49be666302913fd5fb9c5a9ef113                                                                                                                                     0.4s 
 => => extracting sha256:fdfee37d01c31f60d071f54f2414c0da25597fe2cc5c490ce13920824dc1e23c                                                                                                                                     0.6s 
 => => extracting sha256:84289cf02da5745f71612d8ab7b9759a0db726244997235c102e9600cc6ef175                                                                                                                                     2.9s 
 => => extracting sha256:0579b2a6f92cc5a2ca44af6c6807a0294fa45eb144a28ec75852bf37a2240714                                                                                                                                     0.1s 
 => => extracting sha256:6a2b01f2ccf756e73274f5d1e242018cf651ee25e90e746da07e9788d2d5d587                                                                                                                                     0.1s 
 => => extracting sha256:85e47f7d664b53174dcc63edad6bc36acc2788ce277d736a04e03085e2f92096                                                                                                                                     0.0s 
 => [internal] load build context                                                                                                                                                                                             0.2s 
 => => transferring context: 9.98kB                                                                                                                                                                                           0.1s
 => [stage-1 1/3] FROM docker.io/diamol/openjdk:latest@sha256:bc11278602c48a60f71ea01031c54a73878d19db4803f7dd8705aa77bab89808                                                                                              130.7s
 => => resolve docker.io/diamol/openjdk:latest@sha256:bc11278602c48a60f71ea01031c54a73878d19db4803f7dd8705aa77bab89808                                                                                                        0.1s
 => => sha256:484bb3bd28a7ad59d605f58597d0bf81c9b10fcea21d4b7f705d594cc4c793c5 47.04MB / 47.04MB                                                                                                                            128.8s
 => => sha256:b3555c3885852c38ecf4a297b798053677bc7553f9c7631788ef75e35cb4262c 3.27MB / 3.27MB                                                                                                                                4.4s
 => => sha256:42965fccf40100a915fa0b4b20946987c4e330948b82f687f22d7b6575473af0 212B / 212B                                                                                                                                    2.0s
 => => sha256:6f28985ad1843afd6fd4fe0b42a30bfab63c27d302362e7341e3316e8ba25ced 27.10MB / 27.10MB                                                                                                                            100.6s
 => => sha256:53aadb25d9879ce8868e634b4ca338bfc9b0a10ac3d86b25946f0cdedc61f0c2 1.98MB / 1.98MB                                                                                                                                4.3s 
 => => extracting sha256:6f28985ad1843afd6fd4fe0b42a30bfab63c27d302362e7341e3316e8ba25ced                                                                                                                                     1.2s 
 => => extracting sha256:b3555c3885852c38ecf4a297b798053677bc7553f9c7631788ef75e35cb4262c                                                                                                                                     0.2s 
 => => extracting sha256:42965fccf40100a915fa0b4b20946987c4e330948b82f687f22d7b6575473af0                                                                                                                                     0.0s 
 => => extracting sha256:484bb3bd28a7ad59d605f58597d0bf81c9b10fcea21d4b7f705d594cc4c793c5                                                                                                                                     1.2s 
 => => extracting sha256:53aadb25d9879ce8868e634b4ca338bfc9b0a10ac3d86b25946f0cdedc61f0c2                                                                                                                                     0.1s 
 => [stage-1 2/3] WORKDIR /app                                                                                                                                                                                                2.2s 
 => [builder 2/6] WORKDIR /usr/src/iotd                                                                                                                                                                                       2.0s 
 => [builder 3/6] COPY pom.xml .                                                                                                                                                                                              0.1s 
 => [builder 4/6] RUN mvn -B dependency:go-offline                                                                                                                                                                           80.8s 
 => [builder 5/6] COPY . .                                                                                                                                                                                                    0.2s 
 => [builder 6/6] RUN mvn package                                                                                                                                                                                             4.5s 
 => [stage-1 3/3] COPY --from=builder /usr/src/iotd/target/iotd-service-0.1.0.jar .                                                                                                                                           0.2s 
 => exporting to image                                                                                                                                                                                                        1.5s 
 => => exporting layers                                                                                                                                                                                                       1.1s 
 => => exporting manifest sha256:84fa674764016f7d6d684e4f8125bf15b735999c13f76d3475841281a8455cfc                                                                                                                             0.0s 
 => => exporting config sha256:7d4c0409b8247e5c9b09f8fcca0a670d7778d3946484d4f7dc42f818c09d52a7                                                                                                                               0.0s 
 => => exporting attestation manifest sha256:17cd5044c1dd9733cdf0f503e51446f4cfa4153c95ff3076a36a4ea71d282005                                                                                                                 0.0s 
 => => exporting manifest list sha256:efb93590b09065e47f08c0a3839b2133bafe0e834e7227f51c69d7963b2c7462                                                                                                                        0.0s 
 => => naming to docker.io/library/image-of-the-day:latest                                                                                                                                                                    0.0s 
 => => unpacking to docker.io/library/image-of-the-day:latest                                                                                                                                                                 0.2s
```

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-of-the-day> docker network create nat
a89c71828797f9f849ca75ab80b091550d5f3c1d1bdaba45f343ac51046e7676
```
```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-of-the-day> docker container run --name iotd -d -p 800:80 --network nat image-of-the-day
c71cff7b5765a6b911f8cbf96f7170e1a0af912ba7a6c5c1bdd34ec8d722179f
```
http://localhost:800/image

## 4.3
D:\cmj\workspaces\docker\080258\ch04\exercises\access-log\Dockfile
```
FROM node:18 AS builder

WORKDIR /src
COPY src/package.json .
RUN npm install restify@latest

# app
FROM node:18

EXPOSE 80
CMD ["node", "server.js"]

WORKDIR /app
COPY --from=builder /src/node_modules/ /app/node_modules/
COPY src/ .
```

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\access-log> docker image build -t access-log .
[+] Building 314.8s (13/13) FINISHED                                                                                                                                                                          docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                                                                                          0.1s
 => => transferring dockerfile: 286B                                                                                                                                                                                          0.0s 
 => [builder 2/4] WORKDIR /src                                                                                                                                                                                                1.5s 
 => [builder 3/4] COPY src/package.json .                                                                                                                                                                                     0.1s 
 => [builder 4/4] RUN npm install restify@latest                                                                                                                                                                             19.8s 
 => [stage-1 3/4] COPY --from=builder /src/node_modules/ /app/node_modules/                                                                                                                                                   1.4s 
 => [stage-1 4/4] COPY src/ .                                                                                                                                                                                                 0.4s 
 => exporting to image                                                                                                                                                                                                        3.7s 
 => => exporting layers                                                                                                                                                                                                       2.0s 
 => => exporting manifest sha256:4fd16136f5716187a6a71cadbfd40335830ab183595ee6e47452d6ce8bed2d3c                                                                                                                             0.1s 
 => => exporting config sha256:9cc821fd7cb9b6df564a23d61275dc4a31232ddbc5fc325f8bf3c10c14879f98                                                                                                                               0.1s 
 => => exporting attestation manifest sha256:69a0c7364e033194f6f111879fd044e691558c7bcc01785ad3d506f0f7133841                                                                                                                 0.1s 
 => => exporting manifest list sha256:99f5e69e9e8bf68c8bf8a5e8b905e65d667eaba9b3f91d30b9f1cbd2a5d91147                                                                                                                        0.1s 
 => => naming to docker.io/library/access-log:latest                                                                                                                                                                          0.0s 
 => => unpacking to docker.io/library/access-log:latest
```

`docker container run --name accesslog -d -p 801:80 --network nat access-log`

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\access-log> docker container run --name accesslog -d -p 801:80 --network nat access-log
d41e570242d98dba3396f4ab268b012ecc3686e8bcbd28eacb0f217a9aa85162
```
http://localhost:801/stats

## 4.4 애플리케이션 빌드 실전 예제:Go 소스 코드
`docker image build -t image-gallery .`

```
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker image build -t image-gallery .
[+] Building 290.1s (16/16) FINISHED                                                                                                                                                                          docker:desktop-linux 
 => [internal] load build definition from Dockerfile                                                                                                                                                                          0.1s 
 => => transferring dockerfile: 339B                                                                                                                                                                                          0.0s 
 => [internal] load metadata for docker.io/diamol/golang:latest                                                                                                                                                               7.1s 
 => [internal] load metadata for docker.io/diamol/base:latest                                                                                                                                                                 0.0s 
 => [auth] diamol/golang:pull token for registry-1.docker.io                                                                                                                                                                  0.0s 
 => [internal] load .dockerignore                                                                                                                                                                                             0.1s 
 => => transferring context: 2B                                                                                                                                                                                               0.0s 
 => exporting to image                                                                                                                                                                                                        1.5s 
 => => exporting layers                                                                                                                                                                                                       1.0s 
 => => exporting manifest sha256:0837ced648a7881cbfb297455f95dd09647a28af83a4f821fb108d9b150bb7ea                                                                                                                             0.0s 
 => => exporting config sha256:bf4439050357e4f49da08ec1a5d4fb3f37e18807fe5fc09823ac9b47ee78613c                                                                                                                               0.0s 
 => => exporting attestation manifest sha256:5e4933f19591b825f7cb4589fc777dd03d98edb6adee9d9ee06529ad642e8a3c                                                                                                                 0.0s 
 => => exporting manifest list sha256:faa969381f6fce503204e73f68e245a7901add4ffc35cd7201833f0df146e064                                                                                                                        0.0s 
 => => naming to docker.io/library/image-gallery:latest                                                                                                                                                                       0.0s 
 => => unpacking to docker.io/library/image-gallery:latest
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker container ls
CONTAINER ID   IMAGE              COMMAND                   CREATED          STATUS          PORTS                 NAMES
d41e570242d9   access-log         "docker-entrypoint.s…"   9 minutes ago    Up 9 minutes    0.0.0.0:801->80/tcp   accesslog
c71cff7b5765   image-of-the-day   "java -jar /app/iotd…"   45 minutes ago   Up 45 minutes   0.0.0.0:800->80/tcp   iotd
PS D:\cmj\workspaces\docker\080258\ch04\exercises\image-gallery> docker container run -d -p 802:80 --network nat image-gallery
61bc3672a116a2ff1cd1d9d0826efa876ed75ba474fbdd25e70785d4bb6c6a81
```
http://localhost:802/
http://localhost:801/stats
{"logs":2}
