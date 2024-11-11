FROM nginx

WORKDIR /home/

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./server.c .
COPY ./whale.sh .

RUN apt-get update \
    && apt-get install -y gcc spawn-fcgi libfcgi-dev \
    && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["sh", "./whale.sh"]

USER nginx

HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost:81/ || exit 1