FROM repo-nexus.kavosh.org/elastic/filebeat:8.12.0
###################################################################################### Set Local Repo ######################################################################################
# RUN echo -e "deb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-backports main restricted universe multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/focal-security/ ubuntu-security main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security multiverse" > /etc/apt/sources.list
############################################################################################################################################################################################
# COPY filebeat.yml /usr/share/filebeat/filebeat.yml
COPY --chown=root:filebeat filebeat.yml /usr/share/filebeat/filebeat.yml

USER root
RUN chmod go-w /usr/share/filebeat/filebeat.yml
#RUN filebeat modules enable nginx
RUN ./filebeat modules enable fortinet
COPY fortinet.yml /usr/share/filebeat/modules.d/fortinet.yml
RUN chmod go-w /usr/share/filebeat/modules.d/fortinet.yml
CMD filebeat setup
USER filebeat