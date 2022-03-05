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
