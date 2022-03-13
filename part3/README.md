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
