SINGLE STAGE -> TOP ARGS -> ARGS FIRST

1) docker build . --build-arg "XXX=x10" --build-arg "YYY=y10" --build-arg "ZZZ=z10"

[+] Building 2.5s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 236B                                                                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        1.5s
 => CACHED [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                  0.0s
 => [2/5] RUN echo 'Hello World!'                                                                                                                                                       0.2s
 => [3/5] RUN echo x10                                                                                                                                                                  0.2s
 => [4/5] RUN echo y10                                                                                                                                                                  0.2s
 => [5/5] RUN echo z10                                                                                                                                                                  0.2s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:542014221aacf060ccaef43114e9586ec727607b94b3681368df2d46dea34914    

2) docker build . --build-arg "XXX=x10" --build-arg "YYY=y10" --build-arg "ZZZ=z10"

=> [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.6s
 => [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                         0.0s
 => CACHED [2/5] RUN echo 'Hello World!'                                                                                                                                                0.0s
 => CACHED [3/5] RUN echo x10                                                                                                                                                           0.0s
 => CACHED [4/5] RUN echo y10                                                                                                                                                           0.0s
 => CACHED [5/5] RUN echo z10                                                                                                                                                           0.0s
 => exporting to image                                                                                                                                                                  0.0s
 => => exporting layers                                                                                                                                                                 0.0s
 => => writing image sha256:542014221aacf060ccaef43114e9586ec727607b94b3681368df2d46dea34914

3) docker build . --build-arg "XXX=x10" --build-arg "YYY=y10" --build-arg "ZZZ=z30"

[+] Building 2.0s (9/9) FINISHED                                                                                                                                                             
 => [internal] load build definition from Dockerfile                                                                                                                                    0.0s
 => => transferring dockerfile: 37B                                                                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                                       0.0s
 => => transferring context: 2B                                                                                                                                                         0.0s
 => [internal] load metadata for docker.io/library/alpine:latest                                                                                                                        0.7s
 => CACHED [1/5] FROM docker.io/library/alpine@sha256:f271e74b17ced29b915d351685fd4644785c6d1559dd1f2d4189a5e851ef753a                                                                  0.0s
 => [2/5] RUN echo 'Hello World!'                                                                                                                                                       0.2s
 => [3/5] RUN echo x10                                                                                                                                                                  0.3s
 => [4/5] RUN echo y10                                                                                                                                                                  0.4s
 => [5/5] RUN echo z30                                                                                                                                                                  0.3s
 => exporting to image                                                                                                                                                                  0.1s
 => => exporting layers                                                                                                                                                                 0.1s
 => => writing image sha256:4ac181eb692181688fb0c1c294b3613dfc88f119fc331c57cc3412d1b5b1361c   

Conclusion:

As we can see changing any ARGs remove caching of all steps after the arguments
