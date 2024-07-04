FROM openshift/php:7.3

# By default, listen on port 8081
EXPOSE 8080/tcp

# Set the working directory in the container
WORKDIR /projects

# Copy the content of the local src directory to the working directory
COPY . .

USER root
RUN yum install git -y
RUN yum install httpd -y
RUN git clone https://github.com/owncloud/core.git
RUN cp -rf owncloud /var/www/html
