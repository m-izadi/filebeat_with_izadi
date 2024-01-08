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

    ## Set Permision
        sudo setfacl -Rm u:ubuntu:rwx /data/elastic/


echo -e "deb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-updates multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu/ focal-backports main restricted universe multiverse\ndeb http://repo-nexus.kavosh.org:8081/repository/focal-security/ ubuntu-security main restricted\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security universe\ndeb http://repo-nexus.kavosh.org:8081/repository/ubuntu-security/ focal-security multiverse" > /etc/apt/sources.list
