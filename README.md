# docker-logspout

## Build

cd ~
git clone https://github.com/sejnub/logspout.git

cd logspout

docker build .

docker tag <hashvalue of new image> sejnub/logspout:rpi-latest
  
docker login

docker push sejnub/logspout:rpi-latest

## Run

cd ~
git clone https://github.com/sejnub/docker-logspout.git

cd docker-logspout


