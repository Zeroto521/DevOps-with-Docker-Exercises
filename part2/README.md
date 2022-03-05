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
