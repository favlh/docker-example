# Use the latest Ubuntu image as the base
FROM ubuntu:latest

# Set environment variable for non-interactive installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install Nginx, PHP, and MySQL
RUN apt-get update && \
    apt-get install -y nginx php-fpm php-mysql mysql-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Copy Nginx configuration file
COPY ./nginx.conf /etc/nginx/sites-available/default

# Copy HTML directory to the container
COPY ./html /var/www/html

# Expose the port to be used
EXPOSE 80

# Start MySQL and Nginx services
CMD service mysql start && nginx -g 'daemon off;'
