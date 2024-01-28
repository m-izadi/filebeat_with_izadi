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
    # filebrat modules enable fortinet
    # vim /usr/share/filebeat/modules.d/fortinet.yml
        enabled: true

# Elastic

    Set Permision
      sudo setfacl -Rm u:ubuntu:rwx /data/elastic/
      sudo setfacl -Rm u:manage:rwx /data/

# Network

    docker network create --scope=swarm --attachable -d overlay elastic

echo -e "deb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-backports main restricted universe multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/focal-security/ ubuntu-security main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security multiverse" > /etc/apt/sources.list


# Test Elastic

    curl -XGET -k -u *:* localhost:9200

# Node Permision

    sudo setfacl -Rm u:manage:rwx /data/elastic/
    sudo setfacl -Rm u:manage:rwx /data/kibana/

# Commands

    docker rm -f filebeat && DOCKER_BUILDKIT=0 docker compose -f docker-compose.yml up -d filebeat

    docker system prune && docker rmi filebeat-filebeat:latest -f && sudo rm -rf /data/* && docker rm -f filebeat kibana es01 && DOCKER_BUILDKIT=0 docker compose -f docker-compose.yml up -d && docker logs -f filebeat