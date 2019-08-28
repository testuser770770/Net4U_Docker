FROM centos:7
RUN yum install httpd  -y
ADD app /var/www/html/
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
