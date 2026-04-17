FROM nginx:alpine
# Remove default nginx page
RUN rm -rf /usr/share/nginx/html/*
# Copy landing site HTML
COPY . /usr/share/nginx/html/
# Remove Dockerfile from served content
RUN rm -f /usr/share/nginx/html/Dockerfile
EXPOSE 80
