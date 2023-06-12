

# Set Permision
    chown root:root /data/filebeat/filebeat.yml
    chmod go-w /data/filebeat/filebeat.yml

# Check Modules

    docker exec -it filebeat bash
    ./filebeat modules list
# Enable Modules

    ./filebeat modules enable nginx

# Test Config
    ./filebeat test config -e
    Config OK