FROM centos:7

RUN yum -y update && yum clean all

# Apacheのインストール
RUN yum -y install httpd

# Apacheの自動起動設定
RUN systemctl enable httpd

CMD ["/sbin/init"]