SINGLE STAGE -> NO TOP ARGS -> ARGS FIRST

1) docker build . --build-arg "XXX=x1" --build-arg "YYY=y1" --build-arg "ZZZ=z1"

[+] Building 3.3s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        1.8s
 => CACHED [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                  0.0s
 => [2/5] RUN echo 'Hello World!'                                                                                                                                                       0.2s
 => [3/5] RUN echo x1                                                                                                                                                                   0.4s
 => [4/5] RUN echo y1                                                                                                                                                                   0.4s
 => [5/5] RUN echo z1                                                                                                                                                                   0.3s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:22a1f68f15237f8c64d59390b3b6e85e7632a88dca4116c79cb9231f1b9fed5e 

2) docker build . --build-arg "XXX=x1" --build-arg "YYY=y1" --build-arg "ZZZ=z1"

[+] Building 0.8s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 199B                                                                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.7s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo x1                                                                                                                                                            0.0s
 => CACHED [4/5] RUN echo y1                                                                                                                                                            0.0s
 => CACHED [5/5] RUN echo z1                                                                                                                                                            0.0s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:22a1f68f15237f8c64d59390b3b6e85e7632a88dca4116c79cb9231f1b9fed5e 

3) docker build . --build-arg "XXX=x1" --build-arg "YYY=y1" --build-arg "ZZZ=z3"

[+] Building 3.1s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        1.6s
 => CACHED [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                  0.0s
 => [2/5] RUN echo 'Hello World!'                                                                                                                                                       0.2s
 => [3/5] RUN echo x1                                                                                                                                                                   0.4s
 => [4/5] RUN echo y1                                                                                                                                                                   0.3s
 => [5/5] RUN echo z3                                                                                                                                                                   0.4s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:575d3cb6c41228ce4e2ba9f0d790804e279d5018ed10a095cd9d3c9fa86926e8 

Conclusion:

As we can see changing any ARGs remove caching of all steps after the arguments
