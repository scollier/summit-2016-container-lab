FROM registry.access.redhat.com/rhel:7.1-6
MAINTAINER Student <student@foo.io>

ADD ./local.repo /etc/yum.repos.d/local.repo
ADD ./hosts /new-hosts
RUN cat /new-hosts >> /etc/hosts && yum -y update && yum clean all
RUN cat /new-hosts >> /etc/hosts && yum -y install httpd && yum clean all
RUN echo "Apache" >> /var/www/html/index.html
RUN echo 'PS1="[apache]#  "' > /etc/profile.d/ps1.sh

EXPOSE 80

# Simple startup script to avoid some issues observed with container restart 
ADD run-apache.sh /run-apache.sh
RUN chmod -v +x /run-apache.sh

CMD ["/run-apache.sh"]
