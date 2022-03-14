# Part 3

> This part introduces production-ready practices such as container optimization and deployment pipelines. We'll also familiarize ourselves with other container orchestration solutions.

## Exercises

### Exercise 3.1: A deployment pipeline to Heroku

Please see [fork project](https://github.com/Zeroto521/docker-hy.github.io) and check the [Heroku Website](https://github.com/Zeroto521/docker-hy.github.io).

### Exercise 3.2: Building images inside of a container

```bash
$ docker build ./3.2 -t mypypy
[+] Building 22.0s (6/6) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                      0.5s
 => => transferring dockerfile: 48B                                                                                                                       0.2s 
 => [internal] load .dockerignore                                                                                                                         0.4s 
 => => transferring context: 2B                                                                                                                           0.1s
 => [internal] load metadata for docker.io/library/pypy:latest                                                                                            4.9s
 => [auth] library/pypy:pull token for registry-1.docker.io                                                                                               0.0s
 => [1/1] FROM docker.io/library/pypy@sha256:d26b0d1b4d40a8d8d7b74b9a8e361f3f6584b371d3dda73843fa0fb84ed61ef8                                            16.4s
 => => resolve docker.io/library/pypy@sha256:d26b0d1b4d40a8d8d7b74b9a8e361f3f6584b371d3dda73843fa0fb84ed61ef8                                             0.0s 
 => => sha256:3074528535a98b6c7fcf1327c6ca2543805b386fe5bec893d2c205ae272ec047 2.01kB / 2.01kB                                                            0.0s
 => => sha256:d26b0d1b4d40a8d8d7b74b9a8e361f3f6584b371d3dda73843fa0fb84ed61ef8 1.25kB / 1.25kB                                                            0.0s 
 => => sha256:ccc9ce0d1c30871920fa1ab3454962ad5f9900dfd2da0500da7f5694eead2426 8.65kB / 8.65kB                                                            0.0s 
 => => sha256:89d6942e647077fc9e6a8e4aa52b1f56ae1056c0b7ae5abb42d84ccc9848677b 3.21MB / 3.21MB                                                            4.2s 
 => => sha256:2e5cab4837b13dad83e85b7f57fb3b452b959e16b3f854bea27e1b337a71a1f0 30.00MB / 30.00MB                                                         13.1s 
 => => sha256:939c1cc46fc4058a43eea3731a11716fb93cdbf902a02167931f0cb84d728a06 2.35MB / 2.35MB                                                            2.4s 
 => => extracting sha256:89d6942e647077fc9e6a8e4aa52b1f56ae1056c0b7ae5abb42d84ccc9848677b                                                                 0.4s
 => => extracting sha256:2e5cab4837b13dad83e85b7f57fb3b452b959e16b3f854bea27e1b337a71a1f0                                                                 2.4s
 => => extracting sha256:939c1cc46fc4058a43eea3731a11716fb93cdbf902a02167931f0cb84d728a06                                                                 0.3s 
 => exporting to image                                                                                                                                    0.1s 
 => => exporting layers                                                                                                                                   0.0s 
 => => writing image sha256:00fd71ae5817163163505e3886b1d3074786e9c752f0ca9233ff2c8d7945bd1b                                                              0.0s 
 => => naming to docker.io/library/mypypy                                                                                                                 0.0s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

$ docker run -it -v /var/run/docker.sock:/var/run/docker.sock mypypy
Python 3.8.12 (d00b0afd2a5dd3c13fcda75d738262c864c62fa7, Feb 18 2022, 09:52:33)
[PyPy 7.3.8 with GCC 10.2.1 20210130 (Red Hat 10.2.1-11)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>> 
```

### Exercise 3.3

The source codes under [3.3](3.3) folder are copied from [example-frontend](https://github.com/docker-hy/material-applications/tree/main/example-frontend) and [example-backend](https://github.com/docker-hy/material-applications/tree/main/example-backend) except for docker-compose.yml, nginx.conf and Dockerfile.

```bash
$ cd 3.3
$ docker-compose up
[+] Building 504.2s (22/22) FINISHED
 => [33_frontend internal] load build definition from Dockerfile                                                                    0.1s 
 => => transferring dockerfile: 227B                                                                                                0.0s 
 => [33_backend internal] load build definition from Dockerfile                                                                     0.1s 
 => => transferring dockerfile: 207B                                                                                                0.0s 
 => [33_frontend internal] load .dockerignore                                                                                       0.1s 
 => => transferring context: 90B                                                                                                    0.0s 
 => [33_backend internal] load .dockerignore                                                                                        0.1s 
 => => transferring context: 118B                                                                                                   0.0s 
 => [33_frontend internal] load metadata for docker.io/library/node:16                                                              5.0s 
 => [33_backend internal] load metadata for docker.io/library/golang:1.16                                                           4.9s 
 => [33_backend internal] load build context                                                                                        0.1s 
 => => transferring context: 29.50kB                                                                                                0.0s 
 => [33_backend 1/6] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e   185.9s 
 => => resolve docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e                0.1s 
 => => sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e 2.35kB / 2.35kB                                      0.0s 
 => => sha256:972d8c0bc0fc7d67045f744b6949c2884e6c64bc6b262d511a853b4b5aeb0d23 7.05kB / 7.05kB                                      0.0s 
 => => sha256:35fa3cfd4ec01a520f6986535d8f70a5eeef2d40fb8019ff626da24989bdd4f1 1.80kB / 1.80kB                                      0.0s 
 => => sha256:e4d61adff2077d048c6372d73c41b0bd68f525ad41f5530af05098a876683055 54.92MB / 54.92MB                                   18.5s 
 => => sha256:4ff1945c672b08a1791df62afaaf8aff14d3047155365f9c3646902937f7ffe6 5.15MB / 5.15MB                                      6.1s 
 => => sha256:ff5b10aec998344606441aec43a335ab6326f32aae331aab27da16a6bb4ec2be 10.87MB / 10.87MB                                   10.7s 
 => => sha256:12de8c754e45686ace9e25d11bee372b070eed5b5ab20aa3b4fab8c936496d02 54.58MB / 54.58MB                                   27.4s 
 => => sha256:8c86ff77a3175ed4d7958578d141a96b5da005855d60ea24067de33cd62e4c36 85.81MB / 85.81MB                                   48.8s 
 => => sha256:0395a1c478ba68635e5d1bc9349b8fddba5584adc454cec751cd3f29af9080aa 129.16MB / 129.16MB                                 54.4s 
 => => extracting sha256:e4d61adff2077d048c6372d73c41b0bd68f525ad41f5530af05098a876683055                                           6.4s 
 => => extracting sha256:4ff1945c672b08a1791df62afaaf8aff14d3047155365f9c3646902937f7ffe6                                           0.5s 
 => => extracting sha256:ff5b10aec998344606441aec43a335ab6326f32aae331aab27da16a6bb4ec2be                                           0.5s 
 => => sha256:245345d44ed8225f5d3f80fb591b72fddeb8e40e1020926849fcaf0aac1ed060 156B / 156B                                         28.8s 
 => => extracting sha256:12de8c754e45686ace9e25d11bee372b070eed5b5ab20aa3b4fab8c936496d02                                           6.6s 
 => => extracting sha256:8c86ff77a3175ed4d7958578d141a96b5da005855d60ea24067de33cd62e4c36                                          10.0s 
 => => extracting sha256:0395a1c478ba68635e5d1bc9349b8fddba5584adc454cec751cd3f29af9080aa                                          27.0s 
 => => extracting sha256:245345d44ed8225f5d3f80fb591b72fddeb8e40e1020926849fcaf0aac1ed060                                           0.0s 
 => [33_frontend 1/7] FROM docker.io/library/node:16@sha256:61b6cc81ecc3f94f614dca6bfdc5262d15a6618f7aabfbfc6f9f05c935ee753c      299.0s 
 => => resolve docker.io/library/node:16@sha256:61b6cc81ecc3f94f614dca6bfdc5262d15a6618f7aabfbfc6f9f05c935ee753c                    0.1s 
 => => sha256:61b6cc81ecc3f94f614dca6bfdc5262d15a6618f7aabfbfc6f9f05c935ee753c 1.21kB / 1.21kB                                      0.0s 
 => => sha256:7816d2b80c111e0973657b292f604649ef55addbd48ef2cc7f6565a7ec87fe8c 2.21kB / 2.21kB                                      0.0s 
 => => sha256:b426ce8b7669391d2b17144e06723bca91cd71420a11a0102e62dc9db43775b6 7.61kB / 7.61kB                                      0.0s 
 => => sha256:1c9a8b42b5780ac49c71f392c9512c0167ecc23de9b30b1b5f38747b73097d1a 50.44MB / 50.44MB                                   59.0s 
 => => sha256:163066942b43a00ba7f4674c4c1ca90eccc8d99366a3dc47cb64e06ad79c36e5 7.83MB / 7.83MB                                     54.4s 
 => => sha256:cf70e03a8272d87e65c7b1592f97f6e739cf1f5d13cc536670f41c28b086b4cb 10.00MB / 10.00MB                                   61.6s 
 => => sha256:86c5ff33549498a7154441116b5843e184c1f4441df2eab519ad2c498cb8a716 51.84MB / 51.84MB                                   72.5s 
 => => sha256:8c03e72651e6b47f74f08da02f8570740d842273289cac86572b8eca1712e9ee 192.42MB / 192.42MB                                228.0s 
 => => extracting sha256:1c9a8b42b5780ac49c71f392c9512c0167ecc23de9b30b1b5f38747b73097d1a                                          11.6s 
 => => sha256:0ba5b187bf1b90964cdf3971ddceddde53393b6df3e9de6142972443d9613039 4.20kB / 4.20kB                                     63.2s 
 => => sha256:4efdf6f1b568ef131d36654ce007e230846bf0a16908ac6992c21d776d5cfe53 33.81MB / 33.81MB                                  143.0s 
 => => extracting sha256:163066942b43a00ba7f4674c4c1ca90eccc8d99366a3dc47cb64e06ad79c36e5                                           1.3s 
 => => sha256:38284072a01edf4985907d7f8b96309d56ad47081d2485fd0e7eaf746bedf165 2.27MB / 2.27MB                                     92.4s 
 => => extracting sha256:cf70e03a8272d87e65c7b1592f97f6e739cf1f5d13cc536670f41c28b086b4cb                                           1.0s 
 => => extracting sha256:86c5ff33549498a7154441116b5843e184c1f4441df2eab519ad2c498cb8a716                                           8.8s 
 => => sha256:825c069944691f2f59c392bc3baf87f3dbe4219617b5d147be08ca09f85902d3 451B / 451B                                        153.3s 
 => => extracting sha256:8c03e72651e6b47f74f08da02f8570740d842273289cac86572b8eca1712e9ee                                          30.0s 
 => => extracting sha256:0ba5b187bf1b90964cdf3971ddceddde53393b6df3e9de6142972443d9613039                                           0.2s 
 => => extracting sha256:4efdf6f1b568ef131d36654ce007e230846bf0a16908ac6992c21d776d5cfe53                                           4.7s 
 => => extracting sha256:38284072a01edf4985907d7f8b96309d56ad47081d2485fd0e7eaf746bedf165                                           0.3s 
 => => extracting sha256:825c069944691f2f59c392bc3baf87f3dbe4219617b5d147be08ca09f85902d3                                           0.0s 
 => [33_frontend internal] load build context                                                                                       0.2s 
 => => transferring context: 725.30kB                                                                                               0.0s 
 => [33_backend 2/6] WORKDIR /usr/src/app                                                                                           0.4s 
 => [33_backend 3/6] COPY . .                                                                                                       0.2s 
 => [33_backend 4/6] RUN go env -w GOPROXY=https://goproxy.cn                                                                       2.0s 
 => [33_backend 5/6] RUN go build                                                                                                  79.7s 
 => [33_backend 6/6] RUN useradd -m appuser                                                                                        28.4s 
 => [33_frontend] exporting to image                                                                                               10.7s 
 => => exporting layers                                                                                                            10.7s 
 => => writing image sha256:94e8e064a919533d465f3af485543244d35bbda84a120c07a61f52db45afada7                                        0.0s 
 => => naming to docker.io/library/33_backend                                                                                       0.1s 
 => => writing image sha256:e746d2ba6099a468657404c84690b5d6d909b5919151815c80ad2441071b420f                                        0.0s 
 => => naming to docker.io/library/33_frontend                                                                                      0.0s 
 => [33_frontend 2/7] WORKDIR /usr/src/app                                                                                          0.2s 
 => [33_frontend 3/7] COPY . .                                                                                                      0.3s 
 => [33_frontend 4/7] RUN npm install                                                                                             146.3s 
 => [33_frontend 5/7] RUN npm run build                                                                                            34.2s 
 => [33_frontend 6/7] RUN npm install -g serve                                                                                      7.1s 
 => [33_frontend 7/7] RUN useradd -m appuser                                                                                        0.8s 

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
[+] Running 6/6
 - Network 33_default  Created                                                                                                      0.1s 
 - Container redis     Created                                                                                                      1.4s
 - Container postgres  Created                                                                                                      1.4s 
 - Container backend   Created                                                                                                      0.3s
 - Container frontend  Created                                                                                                      0.2s
 - Container nginx     Created                                                                                                      0.2s
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
redis     | 1:C 14 Mar 2022 03:17:16.950 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis     | 1:C 14 Mar 2022 03:17:16.951 # Redis version=6.2.6, bits=64, commit=00000000, modified=0, pid=1, just started
redis     | 1:C 14 Mar 2022 03:17:16.951 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis     | 1:M 14 Mar 2022 03:17:16.952 * monotonic clock: POSIX clock_gettime
redis     | 1:M 14 Mar 2022 03:17:16.953 * Running mode=standalone, port=6379.
redis     | 1:M 14 Mar 2022 03:17:16.953 # Server initialized
redis     | 1:M 14 Mar 2022 03:17:16.953 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis     | 1:M 14 Mar 2022 03:17:16.954 * Ready to accept connections
postgres  | running bootstrap script ... ok
postgres  | performing post-bootstrap initialization ... ok
backend   | [Ex 2.4+] Initializing redis client
backend   | [Ex 2.4+] Connection to redis initialized, ready to ping pong.
backend   | [Ex 2.6+] Initializing postgres connection with envs
backend   |             POSTGRES_HOST      postgres,
backend   |             POSTGRES_USER:     postgres,
backend   |             POSTGRES_PASSWORD: postgres,
backend   |             POSTGRES_DATABASE: postgres
backend   |             to postgres:5432
backend   | [Ex 2.6+] Connection to postgres failed! Retrying...
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
postgres  | waiting for server to start....2022-03-14 03:17:18.792 UTC [48] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-14 03:17:18.804 UTC [48] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-14 03:17:18.821 UTC [49] LOG:  database system was shut down at 2022-03-14 03:17:17 UTC
postgres  | 2022-03-14 03:17:18.840 UTC [48] LOG:  database system is ready to accept connections
postgres  |  done
postgres  | server started
postgres  | 
postgres  | /usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*
postgres  |
postgres  | 2022-03-14 03:17:18.926 UTC [48] LOG:  received fast shutdown request
postgres  | waiting for server to shut down....2022-03-14 03:17:18.932 UTC [48] LOG:  aborting any active transactions
postgres  | 2022-03-14 03:17:18.934 UTC [48] LOG:  background worker "logical replication launcher" (PID 55) exited with exit code 1     
postgres  | 2022-03-14 03:17:18.934 UTC [50] LOG:  shutting down
postgres  | 2022-03-14 03:17:18.971 UTC [48] LOG:  database system is shut down
postgres  |  done
postgres  | server stopped
postgres  |
postgres  | PostgreSQL init process complete; ready for start up.
postgres  |
postgres  | 2022-03-14 03:17:19.080 UTC [1] LOG:  starting PostgreSQL 14.2 (Debian 14.2-1.pgdg110+1) on x86_64-pc-linux-gnu, compiled by 
gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit
postgres  | 2022-03-14 03:17:19.081 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
postgres  | 2022-03-14 03:17:19.081 UTC [1] LOG:  listening on IPv6 address "::", port 5432
postgres  | 2022-03-14 03:17:19.094 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
postgres  | 2022-03-14 03:17:19.108 UTC [60] LOG:  database system was shut down at 2022-03-14 03:17:18 UTC
postgres  | 2022-03-14 03:17:19.121 UTC [1] LOG:  database system is ready to accept connections
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
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:31 +0000] "GET / HTTP/1.1" 200 1067 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:31 +0000] "GET /static/css/main.9ee2e4df.chunk.css HTTP/1.1" 200 285 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:31 +0000] "GET /static/js/main.dbc0b0a4.chunk.js HTTP/1.1" 200 1963 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:31 +0000] "GET /static/js/2.43ca3586.chunk.js HTTP/1.1" 200 79364 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:31 +0000] "GET /static/media/toskalogo.c0f35cf0.svg HTTP/1.1" 200 1524 "http://localhost/" 
"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:32 +0000] "GET /manifest.json HTTP/1.1" 200 214 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:32 +0000] "GET /favicon.ico HTTP/1.1" 200 1067 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:36 +0000] "GET /api/ping HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
backend   | [GIN] 2022/03/14 - 03:17:36 | 200 |          65µs |      172.18.0.6 | GET      "/ping"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:37 +0000] "GET /api/ping?redis=true HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
backend   | ping pong
backend   | [GIN] 2022/03/14 - 03:17:37 | 200 |         606µs |      172.18.0.6 | GET      "/ping?redis=true"
backend   | &{1 pong}
backend   | [GIN] 2022/03/14 - 03:17:37 | 200 |      1.5292ms |      172.18.0.6 | GET      "/ping?postgres=true"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:37 +0000] "GET /api/ping?postgres=true HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
backend   | [GIN] 2022/03/14 - 03:17:38 | 200 |        40.3µs |      172.18.0.6 | GET      "/ping"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:38 +0000] "GET /api/ping HTTP/1.1" 200 4 "http://localhost/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
backend   | [GIN] 2022/03/14 - 03:17:39 | 200 |      1.7085ms |      172.18.0.6 | GET      "/messages"
nginx     | 172.18.0.1 - - [14/Mar/2022:03:17:39 +0000] "GET /api/messages HTTP/1.1" 200 37 "http://localhost/" "Mozilla/5.0 (Windows NT 
10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.51 Safari/537.36"
```
