#FROM image-registry.openshift-image-registry.svc:5000/openshift/php@sha256:836494d2d6c89b08aee678c0a35bb31b1c7003b190aee4ea30bf04fb4d3a8ff3
FROM rockylinux:9

# By default, listen on port 8081
EXPOSE 8080/tcp

# Set the working directory in the container
WORKDIR /projects

# Copy the content of the local src directory to the working directory
COPY . .

USER root
RUN yum update -y
RUN yum install git -y
RUN git clone https://github.com/owncloud/core.git
RUN cp -rf owncloud /var/www/html
