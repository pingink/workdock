ARG ELK_VERSION=7.5.1
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELK_VERSION}
RUN sysctl -w vm.max_map_count=262144
EXPOSE 9200 9300
