SINGLE STAGE -> NO TOP ARGS -> ARGS DISTRIBUTED

1) docker build . --build-arg "XXX=xx1" --build-arg "YYY=yy1" --build-arg "ZZZ=zz1"

[+] Building 3.2s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 199B                                                                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        2.3s
 => CACHED [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                  0.0s
 => [2/5] RUN echo 'Hello World!'                                                                                                                                                       0.2s
 => [3/5] RUN echo xx1                                                                                                                                                                  0.2s
 => [4/5] RUN echo yy1                                                                                                                                                                  0.2s
 => [5/5] RUN echo zz1                                                                                                                                                                  0.2s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:8d5750299ec989840a863942624dd8a7c0e8ff3291b5e870f3bc795d7f96a0d1  

2) docker build . --build-arg "XXX=xx1" --build-arg "YYY=yy1" --build-arg "ZZZ=zz1"

[+] Building 0.6s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.5s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo xx1                                                                                                                                                           0.0s
 => CACHED [4/5] RUN echo yy1                                                                                                                                                           0.0s
 => CACHED [5/5] RUN echo zz1                                                                                                                                                           0.0s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:8d5750299ec989840a863942624dd8a7c0e8ff3291b5e870f3bc795d7f96a0d1  

3) docker build . --build-arg "XXX=xx1" --build-arg "YYY=yy1" --build-arg "ZZZ=zz3"

[+] Building 0.9s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.6s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo xx1                                                                                                                                                           0.0s
 => CACHED [4/5] RUN echo yy1                                                                                                                                                           0.0s
 => [5/5] RUN echo zz3                                                                                                                                                                  0.2s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:a127ea8ac55739ddb0273ba02ceba21c6da6a83af9baac2c4a63fa9f3f30f3cd      

Conclusion:

As we can see changing a ARG remove caching only one step after the argument
