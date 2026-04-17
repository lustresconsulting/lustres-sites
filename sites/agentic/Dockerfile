FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/* /etc/nginx/conf.d/default.conf
# Copy custom nginx config with security headers + gzip
COPY nginx.conf /etc/nginx/conf.d/default.conf
# Copy agentic site HTML
COPY . /usr/share/nginx/html/
# Remove build files from served content
RUN rm -f /usr/share/nginx/html/Dockerfile /usr/share/nginx/html/nginx.conf
EXPOSE 80
