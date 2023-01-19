MULTI STAGE -> TOP ARGS -> ARGS DISTRIBUTED

1) docker build . --build-arg "XXX=xxx11" --build-arg "YYY=yyy11" --build-arg "ZZZ=zzz11"

[+] Building 2.2s (13/13) FINISHED                                                                                                                                                           
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.5s
 => [step1 1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                   0.0s
 => CACHED [step1 2/5] RUN echo 'Hello World!'                                                                                                                                          0.0s
 => [step1 3/5] RUN echo xxx11                                                                                                                                                          0.2s
 => [step1 4/5] RUN echo yyy11                                                                                                                                                          0.2s
 => [step1 5/5] RUN echo zzz11                                                                                                                                                          0.3s
 => [step2 1/3] RUN echo "step2::xxx11"                                                                                                                                                 0.2s
 => [step2 2/3] RUN echo "step2::yyy11"                                                                                                                                                 0.2s
 => [step2 3/3] RUN echo "step2::zzz11"                                                                                                                                                 0.2s
 => [stage-2 1/1] RUN echo 'bye!!!'                                                                                                                                                     0.2s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:a5880ddd5ffd1730b2c849bfa7d380f5f3fe16b97600457978551ab05cb2528b  

2) docker build . --build-arg "XXX=xxx11" --build-arg "YYY=yyy11" --build-arg "ZZZ=zzz11"

[+] Building 0.6s (13/13) FINISHED                                                                                                                                                           
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.5s
 => [step1 1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                   0.0s
 => CACHED [step1 2/5] RUN echo 'Hello World!'                                                                                                                                          0.0s
 => CACHED [step1 3/5] RUN echo xxx11                                                                                                                                                   0.0s
 => CACHED [step1 4/5] RUN echo yyy11                                                                                                                                                   0.0s
 => CACHED [step1 5/5] RUN echo zzz11                                                                                                                                                   0.0s
 => CACHED [step2 1/3] RUN echo "step2::xxx11"                                                                                                                                          0.0s
 => CACHED [step2 2/3] RUN echo "step2::yyy11"                                                                                                                                          0.0s
 => CACHED [step2 3/3] RUN echo "step2::zzz11"                                                                                                                                          0.0s
 => CACHED [stage-2 1/1] RUN echo 'bye!!!'                                                                                                                                              0.0s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:a5880ddd5ffd1730b2c849bfa7d380f5f3fe16b97600457978551ab05cb2528b  

3) docker build . --build-arg "XXX=xxx11" --build-arg "YYY=yyy11" --build-arg "ZZZ=zzz31"

[+] Building 1.8s (13/13) FINISHED                                                                                                                                                           
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.6s
 => [step1 1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                   0.0s
 => CACHED [step1 2/5] RUN echo 'Hello World!'                                                                                                                                          0.0s
 => CACHED [step1 3/5] RUN echo xxx11                                                                                                                                                   0.0s
 => CACHED [step1 4/5] RUN echo yyy11                                                                                                                                                   0.0s
 => [step1 5/5] RUN echo zzz31                                                                                                                                                          0.2s
 => [step2 1/3] RUN echo "step2::xxx11"                                                                                                                                                 0.2s
 => [step2 2/3] RUN echo "step2::yyy11"                                                                                                                                                 0.2s
 => [step2 3/3] RUN echo "step2::zzz31"                                                                                                                                                 0.2s
 => [stage-2 1/1] RUN echo 'bye!!!'                                                                                                                                                     0.2s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:f9186d79a87e471c259a52f52d3ffa10eb0cf0aea2fe14915d449baae1a00f4b

Conclusion:

As we can see changing a ARG remove caching only one step after the argument
