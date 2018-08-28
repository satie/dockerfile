FROM nginx:latest

ENV CACHE_KEY_ZONE 'faas_cache'
ENV CACHE_TTL '24h'
ENV MAX_CACHE_SIZE '1g'

COPY gateway.conf /etc/nginx/conf.d/default.conf.template

CMD /bin/bash -c "envsubst '\$CACHE_KEY_ZONE \$CACHE_TTL \$MAX_CACHE_SIZE' < /etc/nginx/conf.d/default.conf.template > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
