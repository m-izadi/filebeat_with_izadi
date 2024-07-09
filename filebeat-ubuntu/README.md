# Test

    cd /usr/share/filebeat/bin

        ./filebeat test config -c /etc/filebeat/filebeat.yml --path.home /usr/share/filebeat/ --path.data /var/lib/filebeat/
        ./filebeat test output -c /etc/filebeat/filebeat.yml --path.home /usr/share/filebeat/ --path.data /var/lib/filebeat/

# Setup

    cd /usr/share/filebeat/bin

    ./filebeat setup -c /etc/filebeat/filebeat.yml --path.home /usr/share/filebeat/ --path.data /var/lib/filebeat/