FROM docker.elastic.co/elasticsearch/elasticsearch:5.5.3

RUN ./bin/elasticsearch-plugin install analysis-icu && \
    ./bin/elasticsearch-plugin install analysis-kuromoji && \
    ./bin/elasticsearch-plugin install analysis-phonetic && \
    ./bin/elasticsearch-plugin install analysis-smartcn && \
    ./bin/elasticsearch-plugin install analysis-stempel && \
    ./bin/elasticsearch-plugin install analysis-ukrainian && \
    ./bin/elasticsearch-plugin install ingest-attachment && \
    # ./bin/elasticsearch-plugin install ingest-user-agent && \
    ./bin/elasticsearch-plugin install mapper-size && \
    ./bin/elasticsearch-plugin install mapper-murmur3
