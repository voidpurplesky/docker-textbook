https://docs.docker.com/guides/java/containerize/
```
docker init
Welcome to the Docker Init CLI!

This utility will walk you through creating the following files with sensible defaults for your project:
  - .dockerignore
  - Dockerfile
  - compose.yaml
  - README.Docker.md

Let's get started!

WARNING: The following Docker files already exist in this directory:
  - docker-compose.yml
? Do you want to overwrite them? Yes
? What application platform does your project use? Java
? What's the relative directory (with a leading .) for your app? ./src
? What version of Java do you want to use? 17
? What port does your server listen on? 8080
```

```
PS D:\cmj\workspaces\spring-petclinic> docker init

Welcome to the Docker Init CLI!

This utility will walk you through creating the following files with sensible defaults for your project:
  - .dockerignore
  - Dockerfile
  - compose.yaml
  - README.Docker.md

Let's get started!

! Warning → The following Docker files already exist in this directory:
  - docker-compose.yml
? Do you want to overwrite them? Yes
? What application platform does your project use? Java --Enter
? What's the relative directory (with a leading .) for your app? (./src) --Enter

? What's the relative directory (with a leading .) for your app? ./src
? What version of Java do you want to use? (17) --Enter

? What version of Java do you want to use? 17
? What port does your server listen on? 8080

? What port does your server listen on? 8080

✔ Created → .dockerignore
✔ Created → Dockerfile
✔ Created → docker-compose.yml
✔ Created → README.Docker.md

→ Your Docker files are ready!
  Review your Docker files and tailor them to your application.
  Consult README.Docker.md for information about using the generated files.

What's next?
  Start your application by running → docker compose up --build
  Your application will be available at http://localhost:8080
```

`docker compose up --build`

[+] Building 479.9s (15/25)  

```
[+] Building 867.8s (27/27) FINISHED                                                        docker:desktop-linux 
 => [server internal] load build definition from Dockerfile                                                 0.1s 
 => => transferring dockerfile: 4.09kB                                                                      0.0s 
 => [server] resolve image config for docker-image://docker.io/docker/dockerfile:1                          2.5s 
 => [server auth] docker/dockerfile:pull token for registry-1.docker.io                                     0.0s 
 => [server] docker-image://docker.io/docker/dockerfile:1@sha256:865e5dd094beca432e8c0a1d5e1c465db5f998dca  2.1s 
 => => resolve docker.io/docker/dockerfile:1@sha256:865e5dd094beca432e8c0a1d5e1c465db5f998dca4e439981029b3  0.0s 
 => => sha256:1e45ed8b8be3fcf5baec105c530196be8d0b853893e209e4adf6c0e925079ff0 12.49MB / 12.49MB            1.7s 
 => => extracting sha256:1e45ed8b8be3fcf5baec105c530196be8d0b853893e209e4adf6c0e925079ff0                   0.3s 
 => [server internal] load metadata for docker.io/library/eclipse-temurin:17-jre-jammy                      2.9s 
 => [server internal] load metadata for docker.io/library/eclipse-temurin:17-jdk-jammy                      2.6s 
 => [server auth] library/eclipse-temurin:pull token for registry-1.docker.io                               0.0s 
 => [server internal] load .dockerignore                                                                    0.1s 
 => => transferring context: 1.07kB                                                                         0.0s 
 => [server deps 1/5] FROM docker.io/library/eclipse-temurin:17-jdk-jammy@sha256:d41eff8f20494968aaa1f5bb  32.2s 
 => => resolve docker.io/library/eclipse-temurin:17-jdk-jammy@sha256:d41eff8f20494968aaa1f5bbea4547303076b  0.1s 
 => => sha256:21beeebd32c0abccb0b45e99a7fd283212bb21ac4fad10c36216455082df95d0 2.11kB / 2.11kB              0.3s 
 => => sha256:589e94d8e4bef4afb4cff24dcb435416fa3f42401c7ab9b0401e913516968373 176B / 176B                  0.3s 
 => => sha256:7ad3b5e04f2c57070106a37d5d44429d29123ae69ff54b93f63c101129c298d9 145.18MB / 145.18MB         29.2s 
 => => sha256:fcbf49cabfbfcba18d6177c1ac6c7e9330c15d3d20cbc4f88c58bd335ee450a2 17.42MB / 17.42MB           12.5s 
 => => sha256:7478e0ac0f23f94b2f27848fbcdf804a670fbf8d4bab26df842d40a10cd33059 30.44MB / 30.44MB            7.8s 
 => => extracting sha256:7478e0ac0f23f94b2f27848fbcdf804a670fbf8d4bab26df842d40a10cd33059                   2.6s 
 => => extracting sha256:fcbf49cabfbfcba18d6177c1ac6c7e9330c15d3d20cbc4f88c58bd335ee450a2                   3.0s 
 => => extracting sha256:7ad3b5e04f2c57070106a37d5d44429d29123ae69ff54b93f63c101129c298d9                   2.0s 
 => => extracting sha256:589e94d8e4bef4afb4cff24dcb435416fa3f42401c7ab9b0401e913516968373                   0.0s 
 => => extracting sha256:21beeebd32c0abccb0b45e99a7fd283212bb21ac4fad10c36216455082df95d0                   0.0s 
 => [server internal] load build context                                                                    0.4s 
 => => transferring context: 1.28MB                                                                         0.2s 
 => [server final 1/6] FROM docker.io/library/eclipse-temurin:17-jre-jammy@sha256:e373e97c3c398deb15ccdc8  17.5s 
 => => resolve docker.io/library/eclipse-temurin:17-jre-jammy@sha256:e373e97c3c398deb15ccdc84e3063e0dbd353  0.1s 
 => => sha256:1a5fd5c7e18487a3562654981bd4650210fbcffd763f2e4ef507da0ac514c4bb 2.11kB / 2.11kB              0.5s
 => => sha256:80338217a4aba4f8c6f0db147f66124a7d20f3bcd346bf35e5a8f2771864e538 160B / 160B                  0.3s
 => => sha256:7d9a34308537d0e24a7f0071494a76905295ed7c0b75d214d6ea286d8baa07f0 47.28MB / 47.28MB           11.3s
 => => sha256:90a925ab929ad30c9575f0f5adfd3cb8cae7ae5e9d76aa62360634e5a5a1217c 12.87MB / 12.87MB            3.7s
 => => extracting sha256:90a925ab929ad30c9575f0f5adfd3cb8cae7ae5e9d76aa62360634e5a5a1217c                   1.8s
 => => extracting sha256:7d9a34308537d0e24a7f0071494a76905295ed7c0b75d214d6ea286d8baa07f0                   2.7s
 => => extracting sha256:80338217a4aba4f8c6f0db147f66124a7d20f3bcd346bf35e5a8f2771864e538                   0.1s
 => => extracting sha256:1a5fd5c7e18487a3562654981bd4650210fbcffd763f2e4ef507da0ac514c4bb                   0.2s 
 => [server final 2/6] RUN adduser     --disabled-password     --gecos ""     --home "/nonexistent"     --  2.3s 
 => [server deps 2/5] WORKDIR /build                                                                        0.9s 
 => [server deps 3/5] COPY --chmod=0755 mvnw mvnw                                                           0.1s 
 => [server deps 4/5] COPY .mvn/ .mvn/                                                                      0.1s 
 => [server deps 5/5] RUN --mount=type=bind,source=pom.xml,target=pom.xml     --mount=type=cache,target=  730.6s 
 => [server package 1/3] WORKDIR /build                                                                     0.4s 
 => [server package 2/3] COPY ./src src/                                                                    0.6s 
 => [server package 3/3] RUN --mount=type=bind,source=pom.xml,target=pom.xml     --mount=type=cache,targe  82.9s 
 => [server extract 1/2] WORKDIR /build                                                                     0.1s 
 => [server extract 2/2] RUN java -Djarmode=layertools -jar target/app.jar extract --destination target/ex  2.4s 
 => [server final 3/6] COPY --from=extract build/target/extracted/dependencies/ ./                          1.5s 
 => [server final 4/6] COPY --from=extract build/target/extracted/spring-boot-loader/ ./                    0.3s 
 => [server final 5/6] COPY --from=extract build/target/extracted/snapshot-dependencies/ ./                 0.2s 
 => [server final 6/6] COPY --from=extract build/target/extracted/application/ ./                           0.5s 
 => [server] exporting to image                                                                             5.5s 
 => => exporting layers                                                                                     4.4s 
 => => exporting manifest sha256:67e721319e934385b851e80f5204293b41d95ceeb436d05149a7380813fbc601           0.1s 
 => => exporting config sha256:9a9f3c8f136ff367330654ae303ed9984716434bb0baeb6d745fd4976002fabc             0.0s 
 => => exporting attestation manifest sha256:8860d9c7d8af56c2fe544e87944c325c349f5639ddb91c0cdec4bb5e98d38  0.1s 
 => => exporting manifest list sha256:ffa433c6b0518209a11a7c3bb5d6051f43628d163034d0f7087911f7a894d6c1      0.1s 
 => => naming to docker.io/library/spring-petclinic-server:latest                                           0.0s 
 => => unpacking to docker.io/library/spring-petclinic-server:latest                                        0.8s 
 => [server] resolving provenance for metadata file                                                         0.1s 
[+] Running 2/2
 ✔ Network spring-petclinic_default     Created                                                             0.1s 
 ✔ Container spring-petclinic-server-1  Created                                                             0.8s 
Attaching to server-1
server-1  | 
server-1  | 
server-1  |               |\      _,,,--,,_
server-1  |              /,`.-'`'   ._  \-;;,_
server-1  |   _______ __|,4-  ) )_   .;.(__`'-'__     ___ __    _ ___ _______
server-1  |  |       | '---''(_/._)-'(_\_)   |   |   |   |  |  | |   |       |
server-1  |  |    _  |    ___|_     _|       |   |   |   |   |_| |   |       | __ _ _
server-1  |  |   |_| |   |___  |   | |       |   |   |   |       |   |       | \ \ \ \
server-1  |  |    ___|    ___| |   | |      _|   |___|   |  _    |   |      _|  \ \ \ \
server-1  |  |   |   |   |___  |   | |     |_|       |   | | |   |   |     |_    ) ) ) )
server-1  |  |___|   |_______| |___| |_______|_______|___|_|  |__|___|_______|  / / / /
server-1  |  ==================================================================/_/_/_/
server-1  | 
server-1  | :: Built with Spring Boot :: 3.3.4
server-1  | 
server-1  | 
server-1  | 2024-10-04T07:48:42.099Z  INFO 1 --- [           main] o.s.s.petclinic.PetClinicApplication     : Sta
rting PetClinicApplication v3.3.0-SNAPSHOT using Java 17.0.12 with PID 1 (/BOOT-INF/classes started by appuser in
 /)
server-1  | 2024-10-04T07:48:42.105Z  INFO 1 --- [           main] o.s.s.petclinic.PetClinicApplication     : No 
active profile set, falling back to 1 default profile: "default"
server-1  | 2024-10-04T07:48:43.553Z  INFO 1 --- [           main] .s.d.r.c.RepositoryConfigurationDelegate : Boo
tstrapping Spring Data JPA repositories in DEFAULT mode.
server-1  | 2024-10-04T07:48:45.847Z  INFO 1 --- [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: default]
server-1  | 2024-10-04T07:48:45.939Z  INFO 1 --- [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.5.3.Final
server-1  | 2024-10-04T07:48:45.989Z  INFO 1 --- [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
server-1  | 2024-10-04T07:48:46.452Z  INFO 1 --- [           main] o.s.o.j.p.SpringPersistenceUnitInfo      : No LoadTimeWeaver setup: ignoring JPA class transformer
server-1  | 2024-10-04T07:48:47.834Z  INFO 1 --- [           main] o.h.e.t.j.p.i.JtaPlatformInitiator       : HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA 
platform integration)
server-1  | 2024-10-04T07:48:47.838Z  INFO 1 --- [           main] j.LocalContainerEntityManagerFactoryBean : Initialized JPA EntityManagerFactory for persistence unit 'default'
server-1  | 2024-10-04T07:48:48.566Z  INFO 1 --- [           main] o.s.d.j.r.query.QueryEnhancerFactory     : Hibernate is in classpath; If applicable, HQL parser will be used.
server-1  | 2024-10-04T07:48:50.541Z  INFO 1 --- [           main] o.s.b.a.e.web.EndpointLinksResolver      : Exposing 14 endpoints beneath base path '/actuator'
server-1  | 2024-10-04T07:48:50.896Z  INFO 1 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port 8080 (http) with context path '/'
server-1  | 2024-10-04T07:48:50.920Z  INFO 1 --- [           main] o.s.s.petclinic.PetClinicApplication     : Started PetClinicApplication in 9.463 seconds (process running for 10.325)


v View in Docker Desktop   o View Config   w Enable Watch
```




