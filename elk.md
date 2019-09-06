# elk

### metricbeat docker command

docker run -d  --name=metricbeat  --user=root  --volume="$\(pwd\)/metricbeat.docker.yml:/usr/share/metricbeat/metricbeat.yml:ro"  --volume="/var/run/docker.sock:/var/run/docker.sock:ro"  --volume="/sys/fs/cgroup:/hostfs/sys/fs/cgroup:ro"  --volume="/proc:/hostfs/proc:ro"  --volume="/:/hostfs:ro"  docker.elastic.co/beats/metricbeat:7.3.1 metricbeat -e  -E output.elasticsearch.hosts=\["192.168.99.1:9200"\]





