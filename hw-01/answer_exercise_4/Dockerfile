FROM nginx:1.19.3

COPY index.html /usr/share/nginx/html

HEALTHCHECK --interval=45s --timeout=5s --start-period=15s --retries=2 \
    CMD curl -f http://localhost/index.html || exit 1
