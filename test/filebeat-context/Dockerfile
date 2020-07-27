ARG 7.7.0
FROM docker.elastic.co/beats/filebeat-oss:${ELK_VERSION}
COPY config/filebeat.docker.yml /usr/share/filebeat/filebeat.yml
COPY certs /etc/filebeat/certs
USER root
RUN chmod go-w /usr/share/filebeat/filebeat.yml
RUN chown root:filebeat /usr/share/filebeat/filebeat.yml
