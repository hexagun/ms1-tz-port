FROM --platform=linux/arm64 ubuntu:20.04@sha256:64162ac111b666daf1305de1888eb67a3033f62000f5ff781fe529aff8f88b09

RUN apt update

RUN apt install -y python3 python3-dev

WORKDIR ~/images/

CMD [ "python3", "-m", "http.server", "7000" ]