# FileBeat

    ## Set Permision
        chown root:root /data/filebeat/filebeat.yml
        chmod go-w /data/filebeat/filebeat.yml

    ## Check Modules

        docker exec -it filebeat filebeat modules list
    ## Enable Modules

        docker exec -it filebeat ./filebeat modules enable nginx

    ## Test Config
        ./filebeat test config -e
        Config OK
filebeat modules list

    Hint: https://mpolinowski.github.io/docs/DevOps/Elasticsearch/2022-02-03--elasticsearch-v8-data-ingestion/2022-02-03/

## Enable moudles

    # filebeat modules list
    # filebeat modules enable fortinet
    # vim /usr/share/filebeat/modules.d/fortinet.yml
        
        - module: fortinet
          firewall:
            enabled: true

            # Set which input to use between tcp, udp (default) or file.
            var.input: udp

            # The interface to listen to syslog traffic. Defaults to
            # localhost. Set to 0.0.0.0 to bind to all available interfaces.
            var.syslog_host: 0.0.0.0

            # The port to listen for syslog traffic. Defaults to 9004.
            var.syslog_port: 9004
# Elastic

    Set Permision
      sudo setfacl -Rm u:ubuntu:rwx /data/elastic/
      sudo setfacl -Rm u:manage:rwx /data/

# Network

    docker network create --scope=swarm --attachable -d overlay elastic

# Test Elastic

    curl -XGET -k -u *:* localhost:9200

# Node Permision

    sudo setfacl -Rm u:manage:rwx /data/elastic/
    sudo setfacl -Rm u:manage:rwx /data/kibana/

# Commands

    docker rm -f filebeat && DOCKER_BUILDKIT=0 docker compose -f docker-compose.yml up -d filebeat

    docker system prune && docker rmi filebeat-filebeat:latest -f && sudo rm -rf /data/* && docker rm -f filebeat kibana es01 && DOCKER_BUILDKIT=0 docker compose -f docker-compose.yml up -d && docker logs -f filebeat

    docker rm -f filebeat && docker system prune && docker rmi filebeat-filebeat:latest -f && DOCKER_BUILDKIT=0 docker compose -f docker-compose.yml up -d filebeat && docker logs -f filebeat
# Fortigate Commands

    config log syslogd setting
    show