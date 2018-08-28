FROM docker.elastic.co/logstash/logstash:6.3.2
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD pipeline/ /usr/share/logstash/pipeline/
ADD config/synlite_suricata/ /usr/share/logstash/config/
ADD jvm.options /usr/share/logstash/config/