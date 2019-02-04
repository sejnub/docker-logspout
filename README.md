# docker-logspout





## Build

```bash


clear

cd ~
rm -rf docker-logspout
git clone https://github.com/sejnub/docker-logspout.git


cd ~/docker-logspout
rm -rf logspout
git clone https://github.com/gliderlabs/logspout.git


#cd ~/docker-logspout
#rm -rf logspout-logstash
#git clone https://github.com/looplab/logspout-logstash.git


cp ~/docker-logspout/modules.go ~/logspout/modules.go

cd ~/logspout

cat ./modules.go

#docker build -t sejnub/logspout:rpi-latest .
docker build -t sejnub/logspout:rpi-1 .



# Clean up

cd ~

rm -rf docker-logspout
rm -rf logspout
rm -rf docker-logspout

```


## Build / old

```bash
cd ~
git clone https://github.com/sejnub/logspout.git

cd logspout

docker build -t sejnub/logspout:rpi-latest .

docker login

docker push sejnub/logspout:rpi-latest
```

## Run

```bash

cd ~
rm -rf docker-logspout

cd ~
git clone https://github.com/sejnub/docker-logspout.git

cd docker-logspout

docker-compose -f rpi-03-compose.yml up -d
```
