SINGLE STAGE -> TOP ARGS -> ARGS DISTRIBUTED

1) docker build . --build-arg "XXX=xx10" --build-arg "YYY=yy10" --build-arg "ZZZ=zz10"

[+] Building 1.5s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 199B                                                                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.5s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => [3/5] RUN echo xx10                                                                                                                                                                 0.3s
 => [4/5] RUN echo yy10                                                                                                                                                                 0.2s
 => [5/5] RUN echo zz10                                                                                                                                                                 0.4s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:0f6c298ec51fa80c93a7bcbe52ceaceaa3593626ef8f3a26f128fb33e9fe9380   

2) docker build . --build-arg "XXX=xx10" --build-arg "YYY=yy10" --build-arg "ZZZ=zz10"

[+] Building 0.7s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.6s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo xx10                                                                                                                                                          0.0s
 => CACHED [4/5] RUN echo yy10                                                                                                                                                          0.0s
 => CACHED [5/5] RUN echo zz10                                                                                                                                                          0.0s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:0f6c298ec51fa80c93a7bcbe52ceaceaa3593626ef8f3a26f128fb33e9fe9380

3) docker build . --build-arg "XXX=xx10" --build-arg "YYY=yy10" --build-arg "ZZZ=zz30"

[+] Building 0.9s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.6s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo xx10                                                                                                                                                          0.0s
 => CACHED [4/5] RUN echo yy10                                                                                                                                                          0.0s
 => [5/5] RUN echo zz30                                                                                                                                                                 0.3s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:4d7c34d713c0e1286ec5c5dce6f2fc788bd21ac076686fb92f6ed93187d6f350

Conclusion:

As we can see changing a ARG remove caching only one step after the argument
