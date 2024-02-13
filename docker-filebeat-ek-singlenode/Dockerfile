FROM repo-nexus.kavosh.org/elastic/filebeat:8.12.0
# Switch to root for setup
USER root
SHELL ["/bin/bash", "-c"]

# Set Local Repo
# RUN echo "deb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-backports main restricted universe multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/focal-security/ ubuntu-security main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security multiverse" > /etc/apt/sources.list
# RUN \
#     apt update 2>/dev/null && \
#     apt install -y cron vim 2>/dev/null && \
#     apt-get clean && \
#     rm -rf /var/lib/apt/lists/*


# Copy Filebeat configuration
COPY filebeat.yml /usr/share/filebeat/filebeat.yml
# Set permissions on Filebeat configuration
RUN chmod go-w /usr/share/filebeat/filebeat.yml

# Enable Fortinet module
RUN ./filebeat modules enable fortinet
# RUN ./filebeat modules enable gcp

# Copy Fortinet module configuration
COPY --chown=root:root fortinet.yml /usr/share/filebeat/modules.d/fortinet.yml

# Set permissions on Fortinet module configuration
RUN chmod go-w /usr/share/filebeat/modules.d/fortinet.yml

# CMD ["filebeat", "-e", "setup", "&&", "service", "filebeat", "start"]

# Switch back to filebeat user for runtime
USER filebeat
