# Docker image with demo data

FROM java:8-jdk-alpine

ENV SCIPIO_VERSION 1.14.4 
ENV SCIPIO_TGZ_URL https://github.com/ilscipio/scipio-erp/archive/v$SCIPIO_VERSION.tar.gz
ENV SCIPIO_HOME /opt/scipio

ENV PATH $SCIPIO_HOME/bin:$PATH
RUN mkdir -p "$SCIPIO_HOME"
WORKDIR $SCIPIO_HOME

RUN set -x \
	&& apk add --no-cache --virtual .fetch-deps \
		ca-certificates \
		tar \
		openssl \	
	&& wget -O scipio.tar.gz "$SCIPIO_TGZ_URL" \
	&& tar -xvf scipio.tar.gz --strip-components=1 \
	&& rm scipio.tar.gz* \
    && sh ant load-demo

EXPOSE 8080 8443 8983
CMD ["sh", "./start.sh"]
