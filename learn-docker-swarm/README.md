# 手順

1. `docker-compose ps`

manager, registry, worker01〜03まで立ち上がっているか確認

1. `docker container exec -it manager docker swarm init`

managerコンテナをswarmのmanagerに設定する

するとJOINトークンが生成される

このJOINトークンは3つのノード(worker01〜03)をSwarmクラスタのworkerとして登録するのに必要

1. `docker container exec -it worker01 docker swarm join --token TOKEN manager:2377`
1. `docker container exec -it worker02 docker swarm join --token TOKEN manager:2377`
1. `docker container exec -it worker03 docker swarm join --token TOKEN manager:2377`

worker01〜03をSwarmクラスタにworkerとして登録

1. `docker container exec -it manager docker node ls`

Swarmクラスタの状態を確認

## Dockerレジストリにimageをpush

翌日以降やる
