# Part 2

> This part introduces container orchestration with docker-compose and relevant concepts such as *docker network*.

## Exercises

### Exercise 2.1

```bash
$ cd 2.1
$ docker-compose build
[+] Building 5.2s (7/7) FINISHED
 => [internal] load build definition from Dockerfile                                                                                  0.0s
 => => transferring dockerfile: 31B                                                                                                   0.0s
 => [internal] load .dockerignore                                                                                                     0.0s
 => => transferring context: 2B                                                                                                       0.0s
 => [internal] load metadata for docker.io/devopsdockeruh/simple-web-service:latest                                                   5.0s
 => [auth] devopsdockeruh/simple-web-service:pull token for registry-1.docker.io                                                      0.0s
 => [1/2] FROM docker.io/devopsdockeruh/simple-web-service@sha256:20282b20abae04beefa9637bb565943330ed5d085a22fcf8c4878abad80be712    0.0s
 => => resolve docker.io/devopsdockeruh/simple-web-service@sha256:20282b20abae04beefa9637bb565943330ed5d085a22fcf8c4878abad80be712    0.0s
 => CACHED [2/2] WORKDIR /mydir                                                                                                       0.0s
 => exporting to image                                                                                                                0.0s
 => => exporting layers                                                                                                               0.0s
 => => writing image sha256:7d22ea6f03b4cedeefdb65cfca26ac515887a78520d8c723fa3ac767a09b53f3                                          0.0s
 => => naming to docker.io/devopsdockeruh/simple-web-service                                                                          0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker-compose run secret-message
[+] Running 1/0
 - Network 21_default  Created                                                                                                        0.1s
Starting log output
Wrote text to /mydir/text.log
Wrote text to /mydir/text.log
Wrote text to /mydir/text.log
Wrote text to /mydir/text.log
Wrote text to /mydir/text.log
Wrote text to /mydir/text.log
^C

$ docker-compose up
[+] Running 1/0
 - Container web-service  Created                                                                                                    0.0s
Attaching to web-service
web-service  | Starting log output
web-service  | Wrote text to /mydir/text.log
web-service  | Wrote text to /mydir/text.log
web-service  | Wrote text to /mydir/text.log
web-service  | Wrote text to /mydir/text.log
web-service  | Wrote text to /mydir/text.log
web-service  | Wrote text to /mydir/text.log
```

### Exercise 2.2

```bash
$ cd 2.2
$ docker-compose up
[+] Running 1/1
 - Container web-service  Created                                                                                             0.2s
Attaching to web-service
web-service  | [GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.
web-service  | 
web-service  | [GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
web-service  |  - using env:    export GIN_MODE=release
web-service  |  - using code:   gin.SetMode(gin.ReleaseMode)
web-service  |
web-service  | [GIN-debug] GET    /*path                    --> server.Start.func1 (3 handlers)
web-service  | [GIN-debug] Listening and serving HTTP on :8080
web-service  | [GIN] 2022/03/05 - 02:22:39 | 200 |        59.6µs |      172.21.0.1 | GET      "/"
web-service  | [GIN] 2022/03/05 - 02:22:39 | 200 |        31.4µs |      172.21.0.1 | GET      "/favicon.ico"
```

### Exercise 2.3

```bash
$ cd 2.3
$ docker-compose up
[+] Building 644.8s (27/27) FINISHED
 => [23_backend internal] load build definition from Dockerfile                                                                                           0.0s
 => => transferring dockerfile: 261B                                                                                                                      0.0s
 => [23_backend internal] load .dockerignore                                                                                                              0.0s
 => => transferring context: 118B                                                                                                                         0.0s
 => [23_frontend internal] load build definition from Dockerfile                                                                                          0.1s
 => => transferring dockerfile: 396B                                                                                                                      0.0s
 => [23_frontend internal] load .dockerignore                                                                                                             0.1s
 => => transferring context: 90B                                                                                                                          0.0s
 => [23_backend internal] load metadata for docker.io/library/golang:1.16                                                                                 5.3s
 => [23_frontend internal] load metadata for docker.io/library/ubuntu:latest                                                                              5.2s
 => [auth] library/golang:pull token for registry-1.docker.io                                                                                             0.0s
 => [auth] library/ubuntu:pull token for registry-1.docker.io                                                                                             0.0s
 => [23_backend internal] load build context                                                                                                              0.2s
 => => transferring context: 29.50kB                                                                                                                      0.0s 
 => [23_backend 1/6] FROM docker.io/library/golang:1.16@sha256:d06eed568f39329de3a3b760f2c815e64c86c1d4fc74ad5fbd5f0b5866fe1a73                         371.2s 
 => => resolve docker.io/library/golang:1.16@sha256:d06eed568f39329de3a3b760f2c815e64c86c1d4fc74ad5fbd5f0b5866fe1a73                                      0.1s 
 => => sha256:d06eed568f39329de3a3b760f2c815e64c86c1d4fc74ad5fbd5f0b5866fe1a73 2.35kB / 2.35kB                                                            0.0s 
 => => sha256:35fa3cfd4ec01a520f6986535d8f70a5eeef2d40fb8019ff626da24989bdd4f1 1.80kB / 1.80kB                                                            0.0s 
 => => sha256:972d8c0bc0fc7d67045f744b6949c2884e6c64bc6b262d511a853b4b5aeb0d23 7.05kB / 7.05kB                                                            0.0s 
 => => sha256:4ff1945c672b08a1791df62afaaf8aff14d3047155365f9c3646902937f7ffe6 5.15MB / 5.15MB                                                           23.8s
 => => sha256:e4d61adff2077d048c6372d73c41b0bd68f525ad41f5530af05098a876683055 54.92MB / 54.92MB                                                        210.2s 
 => => sha256:ff5b10aec998344606441aec43a335ab6326f32aae331aab27da16a6bb4ec2be 10.87MB / 10.87MB                                                         55.9s
 => => sha256:12de8c754e45686ace9e25d11bee372b070eed5b5ab20aa3b4fab8c936496d02 54.58MB / 54.58MB                                                        243.6s 
 => => sha256:8c86ff77a3175ed4d7958578d141a96b5da005855d60ea24067de33cd62e4c36 85.81MB / 85.81MB                                                        279.0s 
 => => sha256:0395a1c478ba68635e5d1bc9349b8fddba5584adc454cec751cd3f29af9080aa 129.16MB / 129.16MB                                                      360.8s 
 => => extracting sha256:e4d61adff2077d048c6372d73c41b0bd68f525ad41f5530af05098a876683055                                                                 4.3s 
 => => extracting sha256:4ff1945c672b08a1791df62afaaf8aff14d3047155365f9c3646902937f7ffe6                                                                 0.5s 
 => => extracting sha256:ff5b10aec998344606441aec43a335ab6326f32aae331aab27da16a6bb4ec2be                                                                 0.8s 
 => => sha256:245345d44ed8225f5d3f80fb591b72fddeb8e40e1020926849fcaf0aac1ed060 156B / 156B                                                              245.7s 
 => => extracting sha256:12de8c754e45686ace9e25d11bee372b070eed5b5ab20aa3b4fab8c936496d02                                                                 4.8s 
 => => extracting sha256:8c86ff77a3175ed4d7958578d141a96b5da005855d60ea24067de33cd62e4c36                                                                 6.2s 
 => => extracting sha256:0395a1c478ba68635e5d1bc9349b8fddba5584adc454cec751cd3f29af9080aa                                                                 9.3s 
 => => extracting sha256:245345d44ed8225f5d3f80fb591b72fddeb8e40e1020926849fcaf0aac1ed060                                                                 0.0s 
 => [23_frontend  1/10] FROM docker.io/library/ubuntu:latest@sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9                     88.1s 
 => => resolve docker.io/library/ubuntu:latest@sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9                                    0.0s 
 => => sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9 1.42kB / 1.42kB                                                            0.0s 
 => => sha256:9c152418e380c6e6dd7e19567bb6762b67e22b1d0612e4f5074bda6e6040c64a 529B / 529B                                                                0.0s 
 => => sha256:2b4cba85892afc2ad8ce258a8e3d9daa4a1626ba380677cee93ef2338da442ab 1.46kB / 1.46kB                                                            0.0s 
 => => sha256:7c3b88808835aa80f1ef7f03083c5ae781d0f44e644537cd72de4ce6c5e62e00 28.57MB / 28.57MB                                                         84.4s 
 => => extracting sha256:7c3b88808835aa80f1ef7f03083c5ae781d0f44e644537cd72de4ce6c5e62e00                                                                 3.1s 
 => [23_frontend internal] load build context                                                                                                             0.2s 
 => => transferring context: 725.30kB                                                                                                                     0.1s 
 => [23_frontend  2/10] WORKDIR /usr/src/app                                                                                                              0.5s 
 => [23_frontend  3/10] COPY . .                                                                                                                          0.3s 
 => [23_frontend  4/10] RUN apt-get update                                                                                                              198.6s 
 => [23_frontend  5/10] RUN apt-get install -y curl                                                                                                      53.2s 
 => [23_frontend  6/10] RUN curl -sL https://deb.nodesource.com/setup_16.x | bash                                                                        69.8s 
 => [23_backend 2/6] WORKDIR /usr/src/app                                                                                                                 2.6s 
 => [23_backend 3/6] COPY . .                                                                                                                             0.1s 
 => [23_backend 4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                                             0.5s 
 => [23_backend 5/6] RUN go build                                                                                                                        23.5s 
 => [23_backend 6/6] RUN go test                                                                                                                          7.9s 
 => [23_frontend] exporting to image                                                                                                                     11.2s 
 => => exporting layers                                                                                                                                  11.1s 
 => => writing image sha256:c0d163eb86c2e3a0e6f2a8bb0b0aaded2978918cf403cb1e5786b9215c5e471c                                                              0.0s 
 => => naming to docker.io/library/23_backend                                                                                                             0.0s 
 => => writing image sha256:2f3a87720f238433dbacf5f66b714bf1d5541a2e69f1db2d5459916e4105fe34                                                              0.0s 
 => => naming to docker.io/library/23_frontend                                                                                                            0.0s 
 => [23_frontend  7/10] RUN apt install -y nodejs                                                                                                        17.9s 
 => [23_frontend  8/10] RUN npm install                                                                                                                 165.2s 
 => [23_frontend  9/10] RUN npm run build                                                                                                                26.9s 
 => [23_frontend 10/10] RUN npm install -g serve                                                                                                          7.7s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 3/3
 - Network 23_default  Created                                                                                                                            0.1s 
 - Container backend   Created                                                                                                                            1.3s
 - Container frontend  Created                                                                                                                            1.4s 
Attaching to backend, frontend
backend   | [Ex 2.4+] REDIS_HOST env was not passed so redis connection is not initialized
backend   | [Ex 2.6+] POSTGRES_HOST env was not passed so postgres connection is not initialized
backend   | [GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.
backend   |
backend   | [GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
backend   |  - using env:       export GIN_MODE=release
backend   |  - using code:      gin.SetMode(gin.ReleaseMode)
backend   |
backend   | [GIN-debug] GET    /ping                     --> server/router.pingpong (4 handlers)
backend   | [GIN-debug] GET    /messages                 --> server/controller.GetMessages (4 handlers)
backend   | [GIN-debug] POST   /messages                 --> server/controller.CreateMessage (4 handlers)
backend   | [GIN-debug] Listening and serving HTTP on :8080
frontend  | INFO: Accepting connections at http://localhost:5000
backend   | [GIN] 2022/03/05 - 05:55:36 | 200 |        82.8µs |      172.22.0.1 | GET      "/ping"
```

### Exercise 2.4

```bash
$ cd 2.4
$ docker-compose up
[+] Running 7/7
 - redis Pulled                                                                                                                                         101.1s
   - f7a1c6dad281 Pull complete                                                                                                                          90.9s
   - c5f81eaec564 Pull complete                                                                                                                          91.0s
   - 2be237d3defa Pull complete                                                                                                                          91.2s 
   - 1640a11de2e5 Pull complete                                                                                                                          91.9s 
   - 9138edee9512 Pull complete                                                                                                                          92.0s 
   - c62664237d8c Pull complete                                                                                                                          92.1s 
[+] Building 4.7s (27/27) FINISHED
 => [24_backend internal] load build definition from Dockerfile                                                                                           0.1s
 => => transferring dockerfile: 239B                                                                                                                      0.0s 
 => [24_frontend internal] load build definition from Dockerfile                                                                                          0.1s 
 => => transferring dockerfile: 396B                                                                                                                      0.0s 
 => [24_backend internal] load .dockerignore                                                                                                              0.1s
 => => transferring context: 118B                                                                                                                         0.0s 
 => [24_frontend internal] load .dockerignore                                                                                                             0.0s
 => => transferring context: 90B                                                                                                                          0.0s 
 => [24_backend internal] load metadata for docker.io/library/golang:1.16                                                                                 4.1s 
 => [24_frontend internal] load metadata for docker.io/library/ubuntu:latest                                                                              4.0s
 => [auth] library/golang:pull token for registry-1.docker.io                                                                                             0.0s
 => [auth] library/ubuntu:pull token for registry-1.docker.io                                                                                             0.0s 
 => [24_frontend  1/10] FROM docker.io/library/ubuntu:latest@sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9                      0.0s
 => [24_frontend internal] load build context                                                                                                             0.1s 
 => => transferring context: 1.21kB                                                                                                                       0.0s 
 => [24_backend internal] load build context                                                                                                              0.1s 
 => => transferring context: 499B                                                                                                                         0.0s 
 => [24_backend 1/6] FROM docker.io/library/golang:1.16@sha256:d06eed568f39329de3a3b760f2c815e64c86c1d4fc74ad5fbd5f0b5866fe1a73                           0.0s 
 => CACHED [24_backend 2/6] WORKDIR /usr/src/app                                                                                                          0.0s
 => CACHED [24_backend 3/6] COPY . .                                                                                                                      0.0s 
 => CACHED [24_backend 4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                                      0.0s 
 => CACHED [24_backend 5/6] RUN go build                                                                                                                  0.0s
 => CACHED [24_backend 6/6] RUN go test                                                                                                                   0.0s 
 => CACHED [24_frontend  2/10] WORKDIR /usr/src/app                                                                                                       0.0s 
 => CACHED [24_frontend  3/10] COPY . .                                                                                                                   0.0s 
 => CACHED [24_frontend  4/10] RUN apt-get update                                                                                                         0.0s 
 => CACHED [24_frontend  5/10] RUN apt-get install -y curl                                                                                                0.0s 
 => CACHED [24_frontend  6/10] RUN curl -sL https://deb.nodesource.com/setup_16.x | bash                                                                  0.0s 
 => CACHED [24_frontend  7/10] RUN apt install -y nodejs                                                                                                  0.0s 
 => CACHED [24_frontend  8/10] RUN npm install                                                                                                            0.0s 
 => CACHED [24_frontend  9/10] RUN npm run build                                                                                                          0.0s 
 => CACHED [24_frontend 10/10] RUN npm install -g serve                                                                                                   0.0s 
 => [24_backend] exporting to image                                                                                                                       0.2s 
 => => exporting layers                                                                                                                                   0.0s 
 => => writing image sha256:2f3a87720f238433dbacf5f66b714bf1d5541a2e69f1db2d5459916e4105fe34                                                              0.0s 
 => => writing image sha256:c0d163eb86c2e3a0e6f2a8bb0b0aaded2978918cf403cb1e5786b9215c5e471c                                                              0.1s 
 => => naming to docker.io/library/24_frontend                                                                                                            0.0s 
 => => naming to docker.io/library/24_backend                                                                                                             0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 4/4
 - Network 24_default     Created                                                                                                                         0.1s 
 - Container redis-cache  Created                                                                                                                         1.0s
 - Container backend      Created                                                                                                                         0.2s
 - Container frontend     Created                                                                                                                         0.2s
Attaching to backend, frontend, redis-cache
redis-cache  | 1:C 05 Mar 2022 07:24:24.295 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis-cache  | 1:C 05 Mar 2022 07:24:24.295 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis-cache  | 1:C 05 Mar 2022 07:24:24.295 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis-cache  | 1:M 05 Mar 2022 07:24:24.296 * monotonic clock: POSIX clock_gettime
redis-cache  | 1:M 05 Mar 2022 07:24:24.298 * Running mode=standalone, port=6379.
redis-cache  | 1:M 05 Mar 2022 07:24:24.298 # Server initialized
redis-cache  | 1:M 05 Mar 2022 07:24:24.298 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis-cache  | 1:M 05 Mar 2022 07:24:24.299 * Ready to accept connections
backend      | [Ex 2.4+] Initializing redis client
backend      | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend      | [Ex 2.6+] POSTGRES_HOST env was not passed so postgres connection is not initialized
backend      | [GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.
backend      |
backend      | [GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
backend      |  - using env:    export GIN_MODE=release
backend      |  - using code:   gin.SetMode(gin.ReleaseMode)
backend      |
backend      | [GIN-debug] GET    /ping                     --> server/router.pingpong (4 handlers)
backend      | [GIN-debug] GET    /messages                 --> server/controller.GetMessages (4 handlers)
backend      | [GIN-debug] POST   /messages                 --> server/controller.CreateMessage (4 handlers)
backend      | [GIN-debug] Listening and serving HTTP on :8080
frontend     | INFO: Accepting connections at http://localhost:5000
backend      | ping pong
backend      | [GIN] 2022/03/05 - 07:24:32 | 200 |      1.8851ms |      172.23.0.1 | GET      "/ping?redis=true"
```
