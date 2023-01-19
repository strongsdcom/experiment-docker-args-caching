ARG XXX=100
ARG YYY=200
ARG ZZZ=300

FROM alpine AS step1

RUN echo 'Hello World!'

ARG XXX
ENV XXX=$XXX
RUN echo $XXX

ARG YYY
ENV YYY=$YYY
RUN echo $YYY

ARG ZZZ
ENV ZZZ=$ZZZ
RUN echo $ZZZ

CMD date

FROM step1 As step2

ARG XXX
RUN echo "step2::$XXX"

ARG YYY
RUN echo "step2::$YYY"

ARG ZZZ
RUN echo "step2::$ZZZ"

FROM step2

RUN echo 'bye!!!'
