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

### Exercise 2.5

The source codes under [2.5](2.5) folder are copied from [scaling-exercise](https://github.com/docker-hy/material-applications/tree/main/scaling-exercise).

```bash
$ cd 2.5
$ docker-compose up --scale compute=2
[+] Running 7/8
 - load-balancer Error                                                                                                                                    5.1s
 - calculator Pulled                                                                                                                                     10.1s
   - 59bf1c3509f3 Already exists                                                                                                                          0.0s
   - b616ac4a64bf Already exists                                                                                                                          0.0s
   - 3b9e1e8ab9ce Already exists                                                                                                                          0.0s
   - 3507ddbf3909 Already exists                                                                                                                          0.0s
   - 8215d3b1f05c Pull complete                                                                                                                           4.6s
   - 3bdef4317ef4 Pull complete                                                                                                                           4.7s
[+] Building 3.1s (6/6) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                      0.0s
 => => transferring dockerfile: 31B                                                                                                                       0.0s
 => [internal] load .dockerignore                                                                                                                         0.0s
 => => transferring context: 2B                                                                                                                           0.0s
 => [internal] load metadata for docker.io/jwilder/nginx-proxy:latest                                                                                     2.8s
 => [auth] jwilder/nginx-proxy:pull token for registry-1.docker.io                                                                                        0.0s
 => CACHED [1/1] FROM docker.io/jwilder/nginx-proxy@sha256:9b0d210a7d16800404f5dac64e9039711f2a39f60e6f7f9ad068392f4708e29b                               0.0s
 => exporting to image                                                                                                                                    0.1s 
 => => exporting layers                                                                                                                                   0.0s 
 => => writing image sha256:9d2a8880945d5ab3237b264a9b631f90abd92a111c30727e4c38b131e361a6b4                                                              0.0s 
 => => naming to docker.io/library/load-balancer                                                                                                          0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 5/5
 - Network 25_default       Created                                                                                                                       0.1s 
 - Container load-balancer  Created                                                                                                                       0.4s 
 - Container calculator     Created                                                                                                                       0.4s 
 - Container 25-compute-2   Created                                                                                                                       0.4s 
 - Container 25-compute-1   Created                                                                                                                       0.4s 
Attaching to 25-compute-1, 25-compute-2, calculator, load-balancer
load-balancer  | Info: running nginx-proxy version 0.10.1-31-g993e5f8
load-balancer  | Setting up DH Parameters..
load-balancer  | forego      | starting dockergen.1 on port 5000
load-balancer  | forego      | starting nginx.1 on port 5100
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: using the "epoll" event method
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: nginx/1.21.6
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: OS: Linux 5.10.60.1-microsoft-standard-WSL2
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: getrlimit(RLIMIT_NOFILE): 1048576:1048576
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker processes
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 26
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 27
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 28
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 29
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 30
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 31
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 32
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 33
25-compute-2   | I am alive in port 3000!
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Template error: open /etc/nginx/certs: no such file or directory
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Generated '/etc/nginx/conf.d/default.conf' from 4 containers
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Running 'nginx -s reload'
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 1 (SIGHUP) received from 36, reconfiguring
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: reconfiguring
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: using the "epoll" event method
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker processes
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 41
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 42
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 43
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Watching docker events
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 44
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 45
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 46
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 47
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: start worker process 48
25-compute-1   | I am alive in port 3000!
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 26#26: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 28#28: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 27#27: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 29#29: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 29#29: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 29#29: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 26#26: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 28#28: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 26#26: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 28#28: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 27#27: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 30#30: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 27#27: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 31#31: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 30#30: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 30#30: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 32#32: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 33#33: gracefully shutting down
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 31#31: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 31#31: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 32#32: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 32#32: exit
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Template error: open /etc/nginx/certs: no such file or directory
load-balancer  | dockergen.1 | 2022/03/05 08:40:22 Contents of /etc/nginx/conf.d/default.conf did not change. Skipping notification 'nginx -s reload'
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 33#33: exiting
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 33#33: exit
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 17 (SIGCHLD) received from 29
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 29 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 29 (SIGIO) received
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 17 (SIGCHLD) received from 31
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 31 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 29 (SIGIO) received
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 17 (SIGCHLD) received from 28
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 28 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 32 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 29 (SIGIO) received
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 17 (SIGCHLD) received from 32
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 26 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 27 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 29 (SIGIO) received
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 17 (SIGCHLD) received from 30
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 30 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: worker process 33 exited with code 0
load-balancer  | nginx.1     | 2022/03/05 08:40:22 [notice] 22#22: signal 29 (SIGIO) received
calculator     | INFO: Accepting connections at http://localhost:3000
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:50 +0000] "OPTIONS / HTTP/1.1" 204 0 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
25-compute-2   | Added to queue
25-compute-2   | Started resolving loop
25-compute-2   | Started calculations for 5 + 5
25-compute-2   | Added to queue
25-compute-1   | Added to queue
25-compute-1   | Started resolving loop
25-compute-1   | Started calculations for 1 + 1
25-compute-1   | Added to queue
25-compute-1   | Added to queue
25-compute-1   | Added to queue
25-compute-2   | Calculated 5 + 5: 10
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:53 +0000] "POST / HTTP/1.1" 200 40 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
25-compute-2   | Started calculations for 7 + 7
25-compute-1   | Added to queue
25-compute-1   | Calculated 1 + 1: 2
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:53 +0000] "POST / HTTP/1.1" 200 39 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
25-compute-1   | Started calculations for 2 + 2
25-compute-2   | Added to queue
25-compute-2   | Calculated 7 + 7: 14
25-compute-2   | Started calculations for 6 + 6
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:57 +0000] "POST / HTTP/1.1" 200 40 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
25-compute-2   | Added to queue
25-compute-1   | Calculated 2 + 2: 4
25-compute-1   | Started calculations for 3 + 3
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:40:57 +0000] "POST / HTTP/1.1" 200 39 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
25-compute-2   | Added to queue
25-compute-2   | Calculated 6 + 6: 12
25-compute-2   | Started calculations for 10 + 10
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:00 +0000] "POST / HTTP/1.1" 200 40 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
25-compute-1   | Calculated 3 + 3: 6
25-compute-1   | Started calculations for 4 + 4
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:00 +0000] "POST / HTTP/1.1" 200 39 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
25-compute-2   | Calculated 10 + 10: 20
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:03 +0000] "POST / HTTP/1.1" 200 42 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
25-compute-2   | Started calculations for 8 + 8
25-compute-1   | Calculated 4 + 4: 8
25-compute-1   | Started calculations for 9 + 9
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:04 +0000] "POST / HTTP/1.1" 200 39 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
25-compute-2   | Calculated 8 + 8: 16
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:07 +0000] "POST / HTTP/1.1" 200 40 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.2:3000"
25-compute-1   | Calculated 9 + 9: 18
load-balancer  | nginx.1     | compute.localtest.me 172.22.0.1 - - [05/Mar/2022:08:41:08 +0000] "POST / HTTP/1.1" 200 40 "http://localhost:3000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36" "172.22.0.3:3000"
```

### Exercise 2.6

```bash
$ cd 2.6
$ docker-compose up
[+] Running 14/14
 - postgres-db Pulled                                                                                                                                   107.2s 
   - f7a1c6dad281 Already exists                                                                                                                          0.0s 
   - 77c22623b5a6 Pull complete                                                                                                                           7.3s 
   - 0f6a6a85d014 Pull complete                                                                                                                           7.5s 
   - 6012728e8256 Pull complete                                                                                                                           8.2s 
   - 1eca9143e721 Pull complete                                                                                                                          29.6s 
   - 598625d1c828 Pull complete                                                                                                                          29.8s 
   - ec548f0dc89b Pull complete                                                                                                                          30.0s 
   - 10c57d7e0b40 Pull complete                                                                                                                          30.1s 
   - 6b54020a98bb Pull complete                                                                                                                         100.1s 
   - 5fb4de1f64de Pull complete                                                                                                                         100.3s 
   - 19248ca3a367 Pull complete                                                                                                                         100.4s 
   - 1fbbf10b9826 Pull complete                                                                                                                         100.6s 
   - 745f153e9d8d Pull complete                                                                                                                         100.7s 
[+] Building 47.0s (27/27) FINISHED
 => [26_frontend internal] load build definition from Dockerfile                                                                                          0.1s
 => => transferring dockerfile: 396B                                                                                                                      0.0s 
 => [26_backend internal] load build definition from Dockerfile                                                                                           0.1s 
 => => transferring dockerfile: 239B                                                                                                                      0.0s 
 => [26_frontend internal] load .dockerignore                                                                                                             0.1s
 => => transferring context: 90B                                                                                                                          0.0s 
 => [26_backend internal] load .dockerignore                                                                                                              0.1s 
 => => transferring context: 118B                                                                                                                         0.0s 
 => [26_frontend internal] load metadata for docker.io/library/ubuntu:latest                                                                              4.4s
 => [26_backend internal] load metadata for docker.io/library/golang:1.16                                                                                 5.4s 
 => [auth] library/ubuntu:pull token for registry-1.docker.io                                                                                             0.0s
 => [auth] library/golang:pull token for registry-1.docker.io                                                                                             0.0s
 => [26_frontend internal] load build context                                                                                                             0.7s
 => => transferring context: 1.21kB                                                                                                                       0.0s 
 => [26_frontend  1/10] FROM docker.io/library/ubuntu:latest@sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9                      0.0s
 => CACHED [26_frontend  2/10] WORKDIR /usr/src/app                                                                                                       0.0s
 => CACHED [26_frontend  3/10] COPY . .                                                                                                                   0.0s 
 => CACHED [26_frontend  4/10] RUN apt-get update                                                                                                         0.0s 
 => CACHED [26_frontend  5/10] RUN apt-get install -y curl                                                                                                0.0s 
 => CACHED [26_frontend  6/10] RUN curl -sL https://deb.nodesource.com/setup_16.x | bash                                                                  0.0s 
 => CACHED [26_frontend  7/10] RUN apt install -y nodejs                                                                                                  0.0s 
 => CACHED [26_frontend  8/10] RUN npm install                                                                                                            0.0s
 => CACHED [26_frontend  9/10] RUN npm run build                                                                                                          0.0s 
 => CACHED [26_frontend 10/10] RUN npm install -g serve                                                                                                   0.0s 
 => [26_backend] exporting to image                                                                                                                       2.1s 
 => => exporting layers                                                                                                                                   2.0s 
 => => writing image sha256:2f3a87720f238433dbacf5f66b714bf1d5541a2e69f1db2d5459916e4105fe34                                                              0.0s 
 => => naming to docker.io/library/26_frontend                                                                                                            0.0s 
 => => writing image sha256:eb248cb2d636d946a2b9d930cb3bf53e280b31145b3947cce52e88366caf04f2                                                              0.0s 
 => => naming to docker.io/library/26_backend                                                                                                             0.0s 
 => [26_backend internal] load build context                                                                                                              0.1s 
 => => transferring context: 29.50kB                                                                                                                      0.0s 
 => [26_backend 1/6] FROM docker.io/library/golang:1.16@sha256:995b095588ef5e635aec9bdc97cd2a40f29ddec0525461eeba062a9487e82bcd                           0.1s 
 => => resolve docker.io/library/golang:1.16@sha256:995b095588ef5e635aec9bdc97cd2a40f29ddec0525461eeba062a9487e82bcd                                      0.1s 
 => CACHED [26_backend 2/6] WORKDIR /usr/src/app                                                                                                          0.0s 
 => [26_backend 3/6] COPY . .                                                                                                                             0.3s 
 => [26_backend 4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                                             0.8s 
 => [26_backend 5/6] RUN go build                                                                                                                        28.3s 
 => [26_backend 6/6] RUN go test                                                                                                                          9.6s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

[+] Running 4/4
 - Container redis     Created                                                                                                                                                  0.0s
 - Container postgres  Recreated                                                                                                                                                0.6s
 - Container backend   Recreated                                                                                                                                                0.6s
 - Container frontend  Recreated                                                                                                                                                0.5s
Attaching to backend, frontend, postgres, redis
redis     | 1:C 05 Mar 2022 11:00:49.746 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis     | 1:C 05 Mar 2022 11:00:49.746 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis     | 1:C 05 Mar 2022 11:00:49.746 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis     | 1:M 05 Mar 2022 11:00:49.747 * monotonic clock: POSIX clock_gettime
redis     | 1:M 05 Mar 2022 11:00:49.749 * Running mode=standalone, port=6379.
redis     | 1:M 05 Mar 2022 11:00:49.749 # Server initialized
redis     | 1:M 05 Mar 2022 11:00:49.749 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis     | 1:M 05 Mar 2022 11:00:49.755 * Loading RDB produced by version 6.2.6
redis     | 1:M 05 Mar 2022 11:00:49.755 * RDB age 18 seconds
redis     | 1:M 05 Mar 2022 11:00:49.755 * RDB memory usage when created 0.79 Mb
redis     | 1:M 05 Mar 2022 11:00:49.756 # Done loading RDB, keys loaded: 1, keys expired: 0.
redis     | 1:M 05 Mar 2022 11:00:49.756 * DB loaded from disk: 0.001 seconds
redis     | 1:M 05 Mar 2022 11:00:49.756 * Ready to accept connections
postgres  | 
postgres  | PostgreSQL Database directory appears to contain a database; Skipping initialization
postgres  |
postgres  | 2022-03-05 11:00:49.829 UTC [1] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-05 11:00:49.829 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres  | 2022-03-05 11:00:49.829 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres  | 2022-03-05 11:00:49.842 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-05 11:00:49.857 UTC [27] LOG:  database system was shut down at 2022-03-05 11:00:31 UTC
postgres  | 2022-03-05 11:00:49.869 UTC [1] LOG:  database system is ready to accept connections
backend   | [Ex 2.4+] Initializing redis client
backend   | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend   | [Ex 2.6+] Initializing postgres connection with envs
backend   |             POSTGRES_HOST      postgres,
backend   |             POSTGRES_USER:     postgres,
backend   |             POSTGRES_PASSWORD: postgres,
backend   |             POSTGRES_DATABASE: postgres
backend   |             to postgres:5432
backend   | [Ex 2.6+] Connection to postgres initialized, ready to ping pong.
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
backend   | &{1 pong}
backend   | [GIN] 2022/03/05 - 11:01:08 | 200 |      1.8936ms |      172.23.0.1 | GET      "/ping?postgres=true"
backend   | [GIN] 2022/03/05 - 11:01:24 | 200 |     32.3052ms |      172.23.0.1 | POST     "/messages"
backend   | [GIN] 2022/03/05 - 11:01:24 | 200 |       748.6µs |      172.23.0.1 | GET      "/messages"
backend   | [GIN] 2022/03/05 - 11:01:26 | 200 |      1.9737ms |      172.23.0.1 | GET      "/messages"
```

### Exercise 2.7

The source codes under [2.7](2.7) folder are copied from [ml-kurkkumopo-frontend](https://github.com/docker-hy/ml-kurkkumopo-frontend), [ml-kurkkumopo-backend](https://github.com/docker-hy/ml-kurkkumopo-backend) and [ml-kurkkumopo-training](https://github.com/docker-hy/ml-kurkkumopo-training) except docker-compose.yml.

```bash
$ cd 2.7
$ docker-compose up
[+] Building 1815.1s (23/23) FINISHED
 => [27_backend internal] load build definition from Dockerfile                                                                          0.1s
 => => transferring dockerfile: 381B                                                                                                     0.0s 
 => [27_training internal] load build definition from Dockerfile                                                                         0.1s 
 => => transferring dockerfile: 391B                                                                                                     0.0s 
 => [27_backend internal] load .dockerignore                                                                                             0.0s
 => => transferring context: 2B                                                                                                          0.0s 
 => [27_training internal] load .dockerignore                                                                                            0.1s
 => => transferring context: 134B                                                                                                        0.0s 
 => [27_training internal] load metadata for docker.io/library/python:3.6.7-slim                                                         3.3s 
 => [auth] library/python:pull token for registry-1.docker.io                                                                            0.0s
 => [27_backend 1/9] FROM docker.io/library/python:3.6.7-slim@sha256:abedac233d506b945b377f3846900b7cebb2f23e724226ee6a59032cb3039057    0.0s
 => [27_training internal] load build context                                                                                            0.1s 
 => => transferring context: 126.82kB                                                                                                    0.0s 
 => [27_backend internal] load build context                                                                                             0.1s 
 => => transferring context: 2.44kB                                                                                                      0.0s
 => CACHED [27_training 2/9] WORKDIR /src                                                                                                0.0s 
 => CACHED [27_training 3/9] RUN apt-get update                                                                                          0.0s 
 => CACHED [27_training 4/9] RUN apt-get install ffmpeg libsm6 libxext6 -y                                                               0.0s 
 => CACHED [27_backend 5/9] COPY ./requirements.txt ./requirements.txt                                                                   0.0s 
 => CACHED [27_backend 6/9] RUN pip install --upgrade pip                                                                                0.0s 
 => CACHED [27_backend 7/9] RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple                                 0.0s 
 => [27_backend 8/9] RUN pip install -r requirements.txt                                                                              1787.9s
 => CACHED [27_training 5/9] COPY ./requirements.txt ./requirements.txt                                                                  0.0s 
 => CACHED [27_training 6/9] RUN pip install --upgrade pip                                                                               0.0s 
 => CACHED [27_training 7/9] RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple                                0.0s 
 => [27_training 8/9] RUN pip install -r requirements.txt                                                                             1779.7s 
 => [27_training 9/9] COPY . .                                                                                                           0.2s 
 => [27_backend] exporting to image                                                                                                     23.2s 
 => => exporting layers                                                                                                                 23.1s 
 => => writing image sha256:3640fa68b47613a227cb7cc697075a1227a3046d8fb78dd068cb73f3e1b27a70                                             0.0s 
 => => naming to docker.io/library/27_training                                                                                           0.0s 
 => => writing image sha256:a43656794ff5241b5a8fba60b76ebf7e39cd4d57e2c8687ffc9a23d60612e5ec                                             0.0s 
 => => naming to docker.io/library/27_backend                                                                                            0.0s 
 => [27_backend 9/9] COPY . .                                                                                                            0.1s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

[+] Running 6/6
 - Network 27_default  Created                                                                                                           0.1s
 - Volume "27_model"   Created                                                                                                           0.0s
 - Volume "27_imgs"    Created                                                                                                           0.0s
 - Container training  Created                                                                                                           0.3s
 - Container backend   Created                                                                                                           0.4s
 - Container frontend  Created                                                                                                           0.3s
Attaching to backend, frontend, training
training  | 2022-03-06 00:39:22.201109: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcudart.so.11.0'; dlerror: libcudart.so.11.0: cannot open shared object file: No such file or directory
training  | 2022-03-06 00:39:22.201218: I tensorflow/stream_executor/cuda/cudart_stub.cc:29] Ignore above cudart dlerror if you do not have a GPU set up on your machine.
backend   | 2022-03-06 00:39:23.526459: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcudart.so.11.0'; dlerror: libcudart.so.11.0: cannot open shared object file: No such file or directory
backend   | 2022-03-06 00:39:23.526554: I tensorflow/stream_executor/cuda/cudart_stub.cc:29] Ignore above cudart dlerror if you do not have a GPU set up on your machine.
frontend  | INFO: Accepting connections at http://localhost:3000
backend   | Backend starting
backend   | No model in the model volume. Waiting for training service to provide one.
training  | Gathering cucumbers...
Gathering cucumbers...:  99%|█████████▊| 210/213 [01:07<00:00,  5.24cucumbers/s]Gathering mopeds...
Gathering cucumbers...: 100%|██████████| 213/213 [01:07<00:00,  3.18cucumbers/s]
Gathering mopeds...: 100%|██████████| 213/213 [01:23<00:00,  2.56mopeds/s]
training  | 2022-03-06 00:41:58.563274: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcuda.so.1'; dlerror: libcuda.so.1: cannot open shared object file: No such file or directory
training  | 2022-03-06 00:41:58.563416: W tensorflow/stream_executor/cuda/cuda_driver.cc:326] failed call to cuInit: UNKNOWN ERROR (303)
training  | 2022-03-06 00:41:58.563484: I tensorflow/stream_executor/cuda/cuda_diagnostics.cc:156] kernel driver does not appear to be running on this host (b7a083e3089c): /proc/driver/nvidia/version does not exist
training  | 2022-03-06 00:41:58.564241: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX2 FMA
training  | To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
training  | 2022-03-06 00:41:58.986870: I tensorflow/compiler/mlir/mlir_graph_optimization_pass.cc:176] None of the MLIR Optimization Passes are enabled (registered 2)
training  | 2022-03-06 00:41:58.988109: I tensorflow/core/platform/profile_utils/cpu_utils.cc:114] CPU Frequency: 1799995000 Hz
training  | Epoch 1/10
training  | 2022-03-06 00:42:01.026217: W tensorflow/core/framework/cpu_allocator_impl.cc:80] Allocation of 128000000 exceeds 10% of free system memory.
 1/12 [=>............................] - ETA: 31s - loss: 0.8242 - accuracy: 0.37502022-03-06 00:42:01.963280: W tensorflow/core/framework/cpu_allocator_impl.cc:80] Allocation of 128000000 exceeds 10% of free system memory.
 2/12 [====>.........................] - ETA: 7s - loss: 0.6056 - accuracy: 0.5938 2022-03-06 00:42:02.738028: W tensorflow/core/framework/cpu_allocator_impl.cc:80] Allocation of 128000000 exceeds 10% of free system memory.
 3/12 [======>.......................] - ETA: 6s - loss: 0.6785 - accuracy: 0.60422022-03-06 00:42:03.481021: W tensorflow/core/framework/cpu_allocator_impl.cc:80] Allocation of 128000000 exceeds 10% of free system memory.
 4/12 [=========>....................] - ETA: 6s - loss: 0.6207 - accuracy: 0.64842022-03-06 00:42:04.235179: W tensorflow/core/framework/cpu_allocator_impl.cc:80] Allocation of 128000000 exceeds 10% of free system memory.
12/12 [==============================] - 9s 530ms/step - loss: 0.5097 - accuracy: 0.7549
training  | Epoch 2/10
12/12 [==============================] - 5s 421ms/step - loss: 0.2636 - accuracy: 0.9099
training  | Epoch 3/10
12/12 [==============================] - 5s 395ms/step - loss: 0.1431 - accuracy: 0.9577
training  | Epoch 4/10
12/12 [==============================] - 5s 388ms/step - loss: 0.0859 - accuracy: 0.9775
training  | Epoch 5/10
12/12 [==============================] - 5s 441ms/step - loss: 0.0902 - accuracy: 0.9831
training  | Epoch 6/10
12/12 [==============================] - 5s 391ms/step - loss: 0.0876 - accuracy: 0.9803
training  | Epoch 7/10
12/12 [==============================] - 4s 360ms/step - loss: 0.0918 - accuracy: 0.9690
training  | Epoch 8/10
12/12 [==============================] - 4s 344ms/step - loss: 0.0783 - accuracy: 0.9831
training  | Epoch 9/10
12/12 [==============================] - 4s 353ms/step - loss: 0.0671 - accuracy: 0.9887
training  | Epoch 10/10
12/12 [==============================] - 4s 370ms/step - loss: 0.1476 - accuracy: 0.9465
2/2 [==============================] - 0s 73ms/step - loss: 1.4286 - accuracy: 0.6984
training  | 2022-03-06 00:42:51.102761: W tensorflow/python/util/util.cc:348] Sets are not currently considered sequences, but this may change in the future, so consider avoiding using them.
backend   | 2022-03-06 00:42:53.007021: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcuda.so.1'; dlerror: libcuda.so.1: cannot open shared object file: No such file or directory
backend   | 2022-03-06 00:42:53.007117: W tensorflow/stream_executor/cuda/cuda_driver.cc:326] failed call to cuInit: UNKNOWN ERROR (303)
backend   | 2022-03-06 00:42:53.007157: I tensorflow/stream_executor/cuda/cuda_diagnostics.cc:156] kernel driver does not appear to be running on this host (d1ec7c79a2ae): /proc/driver/nvidia/version does not exist
backend   | 2022-03-06 00:42:53.008105: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX2 FMA
backend   | To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
training exited with code 0
backend   |  * Serving Flask app 'app' (lazy loading)
backend   |  * Environment: production
backend   |    WARNING: This is a development server. Do not use it in a production deployment.
backend   |    Use a production WSGI server instead.
backend   |  * Debug mode: on
backend   |  * Running on all addresses.
backend   |    WARNING: This is a development server. Do not use it in a production deployment.
backend   |  * Running on http://172.27.0.3:5000/ (Press CTRL+C to quit)
backend   |  * Restarting with stat
backend   | 2022-03-06 00:42:55.279949: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcudart.so.11.0'; dlerror: libcudart.so.11.0: cannot open shared object file: No such file or directory
backend   | 2022-03-06 00:42:55.280032: I tensorflow/stream_executor/cuda/cudart_stub.cc:29] Ignore above cudart dlerror if you do not have a GPU set up on your machine.
backend   | 2022-03-06 00:42:58.212462: W tensorflow/stream_executor/platform/default/dso_loader.cc:64] Could not load dynamic library 'libcuda.so.1'; dlerror: libcuda.so.1: cannot open shared object file: No such file or directory
backend   | 2022-03-06 00:42:58.212558: W tensorflow/stream_executor/cuda/cuda_driver.cc:326] failed call to cuInit: UNKNOWN ERROR (303)
backend   | 2022-03-06 00:42:58.212597: I tensorflow/stream_executor/cuda/cuda_diagnostics.cc:156] kernel driver does not appear to be running on this host (d1ec7c79a2ae): /proc/driver/nvidia/version does not exist
backend   | 2022-03-06 00:42:58.213027: I tensorflow/core/platform/cpu_feature_guard.cc:142] This TensorFlow binary is optimized with oneAPI Deep Neural Network Library (oneDNN) to use the following CPU instructions in performance-critical operations:  AVX2 FMA
backend   | To enable them in other operations, rebuild TensorFlow with the appropriate compiler flags.
backend   |  * Debugger is active!
backend   |  * Debugger PIN: 112-276-044
backend   | 172.27.0.1 - - [06/Mar/2022 00:43:39] "POST /kurkkuvaimopo HTTP/1.1" 200 -
```

### Exercise 2.8

```bash
$ cd 2.8
$ docker-compose up
[+] Building 241.8s (15/15) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                      0.0s
 => => transferring dockerfile: 32B                                                                                                                       0.0s
 => [internal] load .dockerignore                                                                                                                         0.0s
 => => transferring context: 34B                                                                                                                          0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                          1.7s
 => [internal] load build context                                                                                                                         0.0s
 => => transferring context: 1.21kB                                                                                                                       0.0s
 => [ 1/10] FROM docker.io/library/ubuntu:latest@sha256:8ae9bafbb64f63a50caab98fd3a5e37b3eb837a3e0780b78e5218e63193961f9                                  0.0s
 => CACHED [ 2/10] WORKDIR /usr/src/app                                                                                                                   0.0s
 => CACHED [ 3/10] COPY . .                                                                                                                               0.0s
 => CACHED [ 4/10] RUN apt-get update                                                                                                                     0.0s
 => CACHED [ 5/10] RUN apt-get install -y curl                                                                                                            0.0s
 => CACHED [ 6/10] RUN curl -sL https://deb.nodesource.com/setup_16.x | bash                                                                              0.0s
 => CACHED [ 7/10] RUN apt install -y nodejs                                                                                                              0.0s
 => [ 8/10] RUN npm install                                                                                                                             182.0s
 => [ 9/10] RUN npm run build                                                                                                                            34.8s
 => [10/10] RUN npm install -g serve                                                                                                                      7.6s
 => exporting to image                                                                                                                                   15.4s
 => => exporting layers                                                                                                                                  15.4s
 => => writing image sha256:35f31e803f953a75036c68b65e187c7b4e01ac9b0b5963861d47d0756e03fb1e                                                              0.0s
 => => naming to docker.io/library/28_frontend                                                                                                            0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

[+] Running 5/5
 - Container nginx     Created                                                                                                                            0.3s 
 - Container backend   Created                                                                                                                            0.3s 
 - Container redis     Created                                                                                                                            0.3s 
 - Container postgres  Created                                                                                                                            0.3s 
 - Container frontend  Created                                                                                                                            0.3s
Attaching to backend, frontend, nginx, postgres, redis
redis     | 1:C 06 Mar 2022 06:15:50.012 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis     | 1:C 06 Mar 2022 06:15:50.012 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis     | 1:C 06 Mar 2022 06:15:50.012 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis     | 1:M 06 Mar 2022 06:15:50.013 * monotonic clock: POSIX clock_gettime
redis     | 1:M 06 Mar 2022 06:15:50.014 * Running mode=standalone, port=6379.
redis     | 1:M 06 Mar 2022 06:15:50.015 # Server initialized
redis     | 1:M 06 Mar 2022 06:15:50.015 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis     | 1:M 06 Mar 2022 06:15:50.015 * Ready to accept connections
nginx     | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx     | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
nginx     | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
nginx     | 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
nginx     | /docker-entrypoint.sh: Configuration complete; ready for start up
postgres  | The files belonging to this database system will be owned by user "postgres".
postgres  | This user must also own the server process.
postgres  |
postgres  | The database cluster will be initialized with locale "en_US.utf8".
postgres  | The default database encoding has accordingly been set to "UTF8".
postgres  | The default text search configuration will be set to "english".
postgres  |
postgres  | Data page checksums are disabled.
postgres  |
postgres  | fixing permissions on existing directory /var/lib/postgresql/data ... ok
postgres  | creating subdirectories ... ok
postgres  | selecting dynamic shared memory implementation ... posix
backend   | [Ex 2.4+] Initializing redis client
backend   | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend   | [Ex 2.6+] Initializing postgres connection with envs
backend   |             POSTGRES_HOST      postgres,
backend   |             POSTGRES_USER:     postgres,
postgres  | selecting default max_connections ... 100
backend   |             POSTGRES_PASSWORD: postgres,
backend   |             POSTGRES_DATABASE: postgres
backend   |             to postgres:5432
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
postgres  | selecting default shared_buffers ... 128MB
postgres  | selecting default time zone ... Etc/UTC
postgres  | creating configuration files ... ok
postgres  | running bootstrap script ... ok
postgres  | performing post-bootstrap initialization ... ok
postgres  | syncing data to disk ... ok
postgres  | 
postgres  |
postgres  | Success. You can now start the database server using:
postgres  |
postgres  |     pg_ctl -D /var/lib/postgresql/data -l logfile start
postgres  |
postgres  | initdb: warning: enabling "trust" authentication for local connections
postgres  | You can change this by editing pg_hba.conf or using the option -A, or
postgres  | --auth-local and --auth-host, the next time you run initdb.
postgres  | waiting for server to start....2022-03-06 06:15:52.360 UTC [48] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-06 06:15:52.366 UTC [48] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-06 06:15:52.391 UTC [49] LOG:  database system was shut down at 2022-03-06 06:15:51 UTC
postgres  | 2022-03-06 06:15:52.404 UTC [48] LOG:  database system is ready to accept connections
postgres  |  done
postgres  | server started
postgres  | 
postgres  | /usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*
postgres  |
postgres  | 2022-03-06 06:15:52.552 UTC [48] LOG:  received fast shutdown request
postgres  | waiting for server to shut down....2022-03-06 06:15:52.568 UTC [48] LOG:  aborting any active transactions
postgres  | 2022-03-06 06:15:52.571 UTC [48] LOG:  background worker "logical replication launcher" (PID 55) exited with exit code 1
postgres  | 2022-03-06 06:15:52.576 UTC [50] LOG:  shutting down
postgres  | 2022-03-06 06:15:52.644 UTC [48] LOG:  database system is shut down
postgres  |  done
postgres  | server stopped
postgres  |
postgres  | PostgreSQL init process complete; ready for start up.
postgres  |
postgres  | 2022-03-06 06:15:52.707 UTC [1] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-06 06:15:52.708 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres  | 2022-03-06 06:15:52.708 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres  | 2022-03-06 06:15:52.724 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-06 06:15:52.745 UTC [60] LOG:  database system was shut down at 2022-03-06 06:15:52 UTC
postgres  | 2022-03-06 06:15:52.761 UTC [1] LOG:  database system is ready to accept connections
frontend  | INFO: Accepting connections at http://localhost:5000
backend   | [Ex 2.6+] Connection to postgres initialized, ready to ping pong.
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
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /static/css/main.9ee2e4df.chunk.css HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /static/js/main.fa448335.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /static/js/2.43ca3586.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /static/media/toskalogo.c0f35cf0.svg HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /favicon.ico HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:03 +0000] "GET /manifest.json HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:08 +0000] "GET /api/ping HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
backend   | [GIN] 2022/03/06 - 06:16:08 | 200 |         111µs |      172.18.0.4 | GET      "/ping"
backend   | [GIN] 2022/03/06 - 06:16:11 | 200 |        27.4µs |      172.18.0.4 | GET      "/ping"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:11 +0000] "GET /api/ping HTTP/1.1" 200 4 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.18.0.1 - - [06/Mar/2022:06:16:12 +0000] "GET /favicon.ico HTTP/1.1" 304 0 "http://localhost/api/ping" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
```

### Exercise 2.9

```bash
$ cd 2.9
$ docker-compose up
[+] Running 6/6
 - Network 29_default  Created                                                                                                                            0.1s 
 - Container postgres  Created                                                                                                                            0.4s
 - Container backend   Created                                                                                                                            0.4s 
 - Container redis     Created                                                                                                                            0.4s 
 - Container nginx     Created                                                                                                                            0.4s 
 - Container frontend  Created                                                                                                                            0.3s
Attaching to backend, frontend, nginx, postgres, redis
redis     | 1:C 06 Mar 2022 06:45:59.065 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis     | 1:C 06 Mar 2022 06:45:59.065 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis     | 1:C 06 Mar 2022 06:45:59.065 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis     | 1:M 06 Mar 2022 06:45:59.066 * monotonic clock: POSIX clock_gettime
redis     | 1:M 06 Mar 2022 06:45:59.070 * Running mode=standalone, port=6379.
redis     | 1:M 06 Mar 2022 06:45:59.070 # Server initialized
redis     | 1:M 06 Mar 2022 06:45:59.070 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis     | 1:M 06 Mar 2022 06:45:59.071 * Ready to accept connections
postgres  | The files belonging to this database system will be owned by user "postgres".
postgres  | This user must also own the server process.
postgres  |
postgres  | The database cluster will be initialized with locale "en_US.utf8".
postgres  | The default database encoding has accordingly been set to "UTF8".
postgres  | The default text search configuration will be set to "english".
postgres  |
postgres  | Data page checksums are disabled.
postgres  |
postgres  | fixing permissions on existing directory /var/lib/postgresql/data ... ok
postgres  | creating subdirectories ... ok
postgres  | selecting dynamic shared memory implementation ... posix
nginx     | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx     | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
nginx     | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
backend   | [Ex 2.4+] Initializing redis client
backend   | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend   | [Ex 2.6+] Initializing postgres connection with envs
backend   |             POSTGRES_HOST      postgres,
backend   |             POSTGRES_USER:     postgres,
backend   |             POSTGRES_PASSWORD: postgres,
backend   |             POSTGRES_DATABASE: postgres
backend   |             to postgres:5432
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
nginx     | 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
nginx     | /docker-entrypoint.sh: Configuration complete; ready for start up
postgres  | selecting default max_connections ... 100
postgres  | selecting default shared_buffers ... 128MB
postgres  | selecting default time zone ... Etc/UTC
postgres  | creating configuration files ... ok
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
frontend  | INFO: Accepting connections at http://localhost:5000
postgres  | running bootstrap script ... ok
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
postgres  | performing post-bootstrap initialization ... ok
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
postgres  | syncing data to disk ... ok
postgres  | 
postgres  |
postgres  | Success. You can now start the database server using:
postgres  |
postgres  |     pg_ctl -D /var/lib/postgresql/data -l logfile start
postgres  |
postgres  | initdb: warning: enabling "trust" authentication for local connections
postgres  | You can change this by editing pg_hba.conf or using the option -A, or
postgres  | --auth-local and --auth-host, the next time you run initdb.
postgres  | waiting for server to start....2022-03-06 06:46:21.524 UTC [50] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-06 06:46:21.532 UTC [50] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-06 06:46:21.624 UTC [51] LOG:  database system was shut down at 2022-03-06 06:46:15 UTC
postgres  | 2022-03-06 06:46:21.710 UTC [50] LOG:  database system is ready to accept connections
postgres  |  done
postgres  | server started
postgres  | 
postgres  | /usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*
postgres  |
postgres  | 2022-03-06 06:46:22.028 UTC [50] LOG:  received fast shutdown request
postgres  | waiting for server to shut down....2022-03-06 06:46:22.039 UTC [50] LOG:  aborting any active transactions
postgres  | 2022-03-06 06:46:22.044 UTC [50] LOG:  background worker "logical replication launcher" (PID 57) exited with exit code 1
postgres  | 2022-03-06 06:46:22.054 UTC [52] LOG:  shutting down
postgres  | 2022-03-06 06:46:22.286 UTC [50] LOG:  database system is shut down
postgres  |  done
postgres  | server stopped
postgres  |
postgres  | PostgreSQL init process complete; ready for start up.
postgres  |
postgres  | 2022-03-06 06:46:22.468 UTC [1] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-06 06:46:22.469 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres  | 2022-03-06 06:46:22.469 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres  | 2022-03-06 06:46:22.487 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-06 06:46:22.556 UTC [62] LOG:  database system was shut down at 2022-03-06 06:46:22 UTC
postgres  | 2022-03-06 06:46:22.632 UTC [1] LOG:  database system is ready to accept connections
backend   | [Ex 2.6+] Connection to postgres initialized, ready to ping pong.
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
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /static/css/main.9ee2e4df.chunk.css HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /static/js/2.43ca3586.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /static/js/main.fa448335.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /static/media/toskalogo.c0f35cf0.svg HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /manifest.json HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:40 +0000] "GET /favicon.ico HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET /static/css/main.9ee2e4df.chunk.css HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET /static/js/2.43ca3586.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET /static/js/main.fa448335.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET /static/media/toskalogo.c0f35cf0.svg HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:45 +0000] "GET /manifest.json HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 172.26.0.1 - - [06/Mar/2022:06:51:46 +0000] "GET /favicon.ico HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx exited with code 0
nginx exited with code 0
frontend exited with code 137
frontend exited with code 0
backend exited with code 137
backend exited with code 0
postgres  | 2022-03-06 06:53:17.657 UTC [1] LOG:  received fast shutdown request
postgres  | 2022-03-06 06:53:17.689 UTC [1] LOG:  aborting any active transactions
redis     | 1:signal-handler (1646549597) Received SIGTERM scheduling shutdown...
postgres  | 2022-03-06 06:53:17.710 UTC [1] LOG:  background worker "logical replication launcher" (PID 34) exited with exit code 1
postgres  | 2022-03-06 06:53:17.711 UTC [29] LOG:  shutting down
redis     | 1:M 06 Mar 2022 06:53:17.750 # User requested shutdown...
redis     | 1:M 06 Mar 2022 06:53:17.750 * Saving the final RDB snapshot before exiting.
redis     | 1:M 06 Mar 2022 06:53:17.777 * DB saved on disk
redis     | 1:M 06 Mar 2022 06:53:17.778 # Redis is now ready to exit, bye bye...
postgres  | 2022-03-06 06:53:18.132 UTC [1] LOG:  database system is shut down
redis exited with code 0
postgres exited with code 0

$ docker-compose down
[+] Running 6/6
 - Container frontend  Removed                                                                                                                            10.8s
 - Container nginx     Removed                                                                                                                             1.6s
 - Container backend   Removed                                                                                                                            12.8s
 - Container redis     Removed                                                                                                                             1.0s
 - Container postgres  Removed                                                                                                                             1.4s
 - Network 29_default  Removed                                                                                                                             0.3s
```

### Exercise 2.10

The source codes under [2.10](2.10) folder are copied from [example-frontend](https://github.com/docker-hy/material-applications/tree/main/example-frontend) except docker-compose.yml and Dockerfile.

```bash
$ cd 2.10
$ dokcer-compose up
[+] Running 7/7
 - nginx Pulled                                                                                                                    8.1s 
   - f7a1c6dad281 Already exists                                                                                                   0.0s
   - 4d3e1d15534c Already exists                                                                                                   0.0s 
   - 9ebb164bd1d8 Already exists                                                                                                   0.0s 
   - 59baa8b00c3c Already exists                                                                                                   0.0s 
   - a41ae70ab6b4 Already exists                                                                                                   0.0s
   - e3908122b958 Already exists                                                                                                   0.0s 
[+] Building 1.9s (21/21) FINISHED
 => [210_frontend internal] load build definition from Dockerfile                                                                  0.0s
 => => transferring dockerfile: 187B                                                                                               0.0s 
 => [210_backend internal] load build definition from Dockerfile                                                                   0.0s
 => => transferring dockerfile: 239B                                                                                               0.0s 
 => [210_frontend internal] load .dockerignore                                                                                     0.0s 
 => => transferring context: 34B                                                                                                   0.0s 
 => [210_backend internal] load .dockerignore                                                                                      0.1s 
 => => transferring context: 34B                                                                                                   0.0s
 => [210_frontend internal] load metadata for docker.io/library/node:16                                                            1.4s 
 => [210_backend internal] load metadata for docker.io/library/golang:1.16                                                         1.4s 
 => [210_frontend internal] load build context                                                                                     0.0s
 => => transferring context: 1.21kB                                                                                                0.0s 
 => [210_frontend 1/6] FROM docker.io/library/node:16@sha256:61b6cc81ecc3f94f614dca6bfdc5262d15a6618f7aabfbfc6f9f05c935ee753c      0.0s 
 => [210_backend 1/6] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e   0.0s
 => => resolve docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e               0.0s 
 => [210_backend internal] load build context                                                                                      0.1s 
 => => transferring context: 499B                                                                                                  0.0s 
 => CACHED [210_frontend 2/6] WORKDIR /usr/src/app                                                                                 0.0s 
 => CACHED [210_frontend 3/6] COPY . .                                                                                             0.0s 
 => CACHED [210_frontend 4/6] RUN npm install                                                                                      0.0s
 => CACHED [210_frontend 5/6] RUN npm run build                                                                                    0.0s 
 => CACHED [210_frontend 6/6] RUN npm install -g serve                                                                             0.0s 
 => [210_backend] exporting to image                                                                                               0.1s 
 => => exporting layers                                                                                                            0.0s 
 => => writing image sha256:fcd5c60dcbcdd6390c9025e613e5e8104fa94fc98289a9077e67d74215b419e6                                       0.0s 
 => => naming to docker.io/library/210_frontend                                                                                    0.0s 
 => => writing image sha256:c0d163eb86c2e3a0e6f2a8bb0b0aaded2978918cf403cb1e5786b9215c5e471c                                       0.0s 
 => => naming to docker.io/library/210_backend                                                                                     0.0s 
 => CACHED [210_backend 2/6] WORKDIR /usr/src/app                                                                                  0.0s 
 => CACHED [210_backend 3/6] COPY . .                                                                                              0.0s 
 => CACHED [210_backend 4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                              0.0s 
 => CACHED [210_backend 5/6] RUN go build                                                                                          0.0s 
 => CACHED [210_backend 6/6] RUN go test                                                                                           0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 6/6
 - Network 210_default  Created                                                                                                    0.1s 
 - Container redis      Created                                                                                                    0.2s
 - Container postgres   Created                                                                                                    0.2s 
 - Container backend    Created                                                                                                    0.2s
 - Container frontend   Created                                                                                                    0.2s
 - Container nginx      Created                                                                                                    0.2s
Attaching to backend, frontend, nginx, postgres, redis
postgres  | The files belonging to this database system will be owned by user "postgres".
postgres  | This user must also own the server process.
postgres  |
postgres  | The database cluster will be initialized with locale "en_US.utf8".
postgres  | The default database encoding has accordingly been set to "UTF8".
postgres  | The default text search configuration will be set to "english".
postgres  | 
postgres  | Data page checksums are disabled.
postgres  |
postgres  | fixing permissions on existing directory /var/lib/postgresql/data ... ok
postgres  | creating subdirectories ... ok
postgres  | selecting dynamic shared memory implementation ... posix
postgres  | selecting default max_connections ... 100
postgres  | selecting default shared_buffers ... 128MB
postgres  | selecting default time zone ... Etc/UTC
postgres  | creating configuration files ... ok
redis     | 1:C 12 Mar 2022 06:41:33.805 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis     | 1:C 12 Mar 2022 06:41:33.806 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis     | 1:C 12 Mar 2022 06:41:33.806 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis     | 1:M 12 Mar 2022 06:41:33.806 * monotonic clock: POSIX clock_gettime
redis     | 1:M 12 Mar 2022 06:41:33.809 * Running mode=standalone, port=6379.
redis     | 1:M 12 Mar 2022 06:41:33.810 # Server initialized
redis     | 1:M 12 Mar 2022 06:41:33.810 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis     | 1:M 12 Mar 2022 06:41:33.812 * Ready to accept connections
postgres  | running bootstrap script ... ok
postgres  | performing post-bootstrap initialization ... ok
postgres  | syncing data to disk ... initdb: warning: enabling "trust" authentication for local connections
postgres  | You can change this by editing pg_hba.conf or using the option -A, or
postgres  | --auth-local and --auth-host, the next time you run initdb.
postgres  | ok
postgres  |
postgres  |
postgres  | Success. You can now start the database server using:
postgres  |
postgres  |     pg_ctl -D /var/lib/postgresql/data -l logfile start
postgres  |
postgres  | waiting for server to start....2022-03-12 06:41:35.334 UTC [49] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-12 06:41:35.340 UTC [49] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-12 06:41:35.471 UTC [50] LOG:  database system was shut down at 2022-03-12 06:41:34 UTC
postgres  | 2022-03-12 06:41:35.482 UTC [49] LOG:  database system is ready to accept connections
postgres  |  done
postgres  | server started
backend   | [Ex 2.4+] Initializing redis client
backend   | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend   | [Ex 2.6+] Initializing postgres connection with envs
backend   |             POSTGRES_HOST      postgres,
backend   |             POSTGRES_USER:     postgres,
backend   |             POSTGRES_PASSWORD: postgres,
backend   |             POSTGRES_DATABASE: postgres
backend   |             to postgres:5432
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
postgres  | 
postgres  | /usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*
postgres  |
postgres  | waiting for server to shut down...2022-03-12 06:41:35.625 UTC [49] LOG:  received fast shutdown request
postgres  | .2022-03-12 06:41:35.637 UTC [49] LOG:  aborting any active transactions
postgres  | 2022-03-12 06:41:35.639 UTC [49] LOG:  background worker "logical replication launcher" (PID 56) exited with exit code 1    
postgres  | 2022-03-12 06:41:35.639 UTC [51] LOG:  shutting down
postgres  | 2022-03-12 06:41:35.711 UTC [49] LOG:  database system is shut down
postgres  |  done
postgres  | server stopped
postgres  |
postgres  | PostgreSQL init process complete; ready for start up.
postgres  |
postgres  | 2022-03-12 06:41:35.766 UTC [1] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-12 06:41:35.766 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres  | 2022-03-12 06:41:35.766 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres  | 2022-03-12 06:41:35.779 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-12 06:41:35.796 UTC [61] LOG:  database system was shut down at 2022-03-12 06:41:35 UTC
postgres  | 2022-03-12 06:41:35.805 UTC [1] LOG:  database system is ready to accept connections
nginx     | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx     | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
nginx     | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
nginx     | 10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx     | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
nginx     | /docker-entrypoint.sh: Configuration complete; ready for start up
frontend  | INFO: Accepting connections at http://localhost:5000
backend   | [Ex 2.6+] Connection to postgres initialized, ready to ping pong.
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
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET / HTTP/1.1" 200 1067 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/css/main.9ee2e4df.chunk.css HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/js/main.dbc0b0a4.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/js/2.43ca3586.chunk.js HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/css/main.9ee2e4df.chunk.css.map HTTP/1.1" 200 550 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/media/toskalogo.c0f35cf0.svg HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/js/main.dbc0b0a4.chunk.js.map HTTP/1.1" 200 3843 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /static/js/2.43ca3586.chunk.js.map HTTP/1.1" 200 257446 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /favicon.ico HTTP/1.1" 200 1067 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:44 +0000] "GET /manifest.json HTTP/1.1" 304 0 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
backend   | [GIN] 2022/03/12 - 06:41:45 | 200 |         235µs |    192.168.32.6 | GET      "/ping"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:45 +0000] "GET /api/ping HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:46 +0000] "GET /api/ping?redis=true HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
backend   | ping pong
backend   | [GIN] 2022/03/12 - 06:41:46 | 200 |       769.4µs |    192.168.32.6 | GET      "/ping?redis=true"
backend   | &{1 pong}
backend   | [GIN] 2022/03/12 - 06:41:46 | 200 |      1.8041ms |    192.168.32.6 | GET      "/ping?postgres=true"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:46 +0000] "GET /api/ping?postgres=true HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
backend   | [GIN] 2022/03/12 - 06:41:47 | 200 |        36.1µs |    192.168.32.6 | GET      "/ping"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:47 +0000] "GET /api/ping HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
backend   | [GIN] 2022/03/12 - 06:41:48 | 200 |       868.2µs |    192.168.32.6 | GET      "/messages"
nginx     | 192.168.32.1 - - [12/Mar/2022:06:41:48 +0000] "GET /api/messages HTTP/1.1" 200 37 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.20 Safari/537.36"
```
