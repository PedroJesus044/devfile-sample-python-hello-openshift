#FROM image-registry.openshift-image-registry.svc:5000/openshift/php@sha256:836494d2d6c89b08aee678c0a35bb31b1c7003b190aee4ea30bf04fb4d3a8ff3
FROM rockylinux:8

# By default, listen on port 8081
EXPOSE 80/tcp

# Set the working directory in the container
WORKDIR /projects

# Copy the content of the local src directory to the working directory
COPY . .

USER root
RUN yum update -y
RUN yum install git wget epel-release tar httpd rsync firewalld -y

RUN dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm -y
RUN dnf module switch-to php:remi-7.4 -y
RUN dnf install php php-opcache php-gd php-curl php-mysqlnd php-intl php-json php-ldap php-mbstring php-mysqlnd php-xml php-zip php-process -y

RUN git clone https://github.com/owncloud/core.git
RUN rsync -a core/ /var/www/html
RUN chown -R apache:apache /var/www/html

RUN firewall-cmd --add-service=http --permanent
RUN firewall-cmd --reload

RUN httpd -DFOREGROUND "$@"