# node-dojot

Adicionar register local no dockercompose
  
-----
  registry:
    restart: always
    image: registry:2
    ports:
      - 5009:5000
    volumes:
      - /opt/dojot/docker/registry:/var/lib/registry
    networks:
      - default

-----

docker build -t localhost/telegram  .

docker push localhost/telegram 

curl -X POST http://localhost:8000/auth -H 'Content-Type:application/json' -d '{"username": "admin", "passwd" : "admin"}'


curl -H "Authorization: Bearer ${JWT}" http://localhost:8000/flows/v1/node -H "content-type: application/json" -d "{\"image\": \"localhost:5009/telegram:latest\", \"id\":\"telegram\"}"
