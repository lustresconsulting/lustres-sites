FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
# Copy cloud site HTML including previews/ assets
COPY . /usr/share/nginx/html/
RUN rm -f /usr/share/nginx/html/Dockerfile
EXPOSE 80
