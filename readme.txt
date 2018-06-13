Login to https://labs.play-with-docker.com/
Templates: 3 Managers and 2 Workers
M1: "docker service create --name=viz --publish=8080:8080/tcp --constraint=node.role==manager --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock bretfisher/visualizer"
M1: Click "8080" link to open Swarm Visualization
M1: "git clone https://github.com/jamesyangwang/docker-compose.git"
M1: "docker pull jamesoy/ducs_admin_server:latest"
M1: "docker pull jamesoy/ducs_consumer_services:latest"
M1: "docker images"
M1: "mkdir -p /app/logs/ducs" on all 5 nodes
M1: "docker stack deploy -c docker-compose/docker-compose-ducs.yml ducs"
M1: "docker stack ls"
M1: "docker stack services ducs"
M1: "docker service ls"
M1: "docker service ps ducs_admin_server"
M1: "docker service ps ducs_consumer_services"
Mn: "docker ps"	on admin_server node
Mn: "docker logs e4f2ee9de9d7"
Mm: "docker ps" on consumer_services node
Mm: "docker logs baca0980818f"
Mx: Wait till...Click "8070", "8090" links, pages loaded
M1: "docker service scale ducs_consumer_services=3"
Mx: Wait till...Click "8070", "8090" links, "3 instances" show up at admin server dashboard
M1: "docker stack rm ducs"
