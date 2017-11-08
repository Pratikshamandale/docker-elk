FROM java

RUN apt-get update && \
    wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add - && \
    apt-get install apt-transport-https && \
    echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-5.x.list && \
    apt-get update && apt-get install logstash

WORKDIR /usr/share/logstash

RUN bin/logstash-plugin install x-pack

CMD bin/logstash -f pipeline/logstash.conf --config.reload.automatic

