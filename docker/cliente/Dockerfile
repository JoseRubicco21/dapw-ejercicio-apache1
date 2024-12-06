FROM debian:12

RUN apt update &&  apt install -y net-tools procps most iproute2  iputils-ping dnsutils firefox-esr curl wget

RUN apt clean && rm -rf /var/lib/apt/lists/*

# Modificamos el entrypoint para que al lanzarlo se nos habra FireFox en vez de que quede al pendiente.
ENTRYPOINT ["firefox"]