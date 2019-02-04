# docker-logspout

## Build

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
