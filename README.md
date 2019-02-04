# docker-logspout

## Build

```bash

# Get sources
clear

cd ~
rm -rf docker-logspout
git clone https://github.com/sejnub/docker-logspout.git


cd ~
rm -rf logspout
git clone https://github.com/gliderlabs/logspout.git


cd ~
rm -rf logspout-logstash
git clone https://github.com/looplab/logspout-logstash.git


# Copy stuff to ~/logspout/
cp ~/docker-logspout/modules.go ~/logspout/modules.go

cp -r ~/logspout-logstash/  ~/logspout/adapters
rm -rf ~/logspout/adapters/logspout-logstash/.git
rm     ~/logspout/adapters/logspout-logstash/.gitignore
rm     ~/logspout/adapters/logspout-logstash/LICENSE
rm     ~/logspout/adapters/logspout-logstash/README.md


# Debug
cd ~/logspout
cat ./modules.go

cd ~/logspout/adapters
ls -asl


# Build
cd ~/logspout
#docker build -t sejnub/logspout:rpi-latest .
docker build -t sejnub/logspout:rpi-1 .

# Leads to
#
# [INFO]  --> Exporting github.com/Sirupsen/logrus
# [INFO]  --> Exporting github.com/hashicorp/go-cleanhttp
# [INFO]  --> Exporting golang.org/x/sys
# [INFO]  --> Exporting golang.org/x/net
# [INFO]  Replacing existing vendor dependencies
# modules.go:13:2: cannot find package "github.com/looplab/logspout-logstash" in any of:
#         /go/src/github.com/gliderlabs/logspout/vendor/github.com/looplab/logspout-logstash (vendor tree)
#         /usr/lib/go/src/github.com/looplab/logspout-logstash (from $GOROOT)
#         /go/src/github.com/looplab/logspout-logstash (from $GOPATH)
# The command '/bin/sh -c cd /src && ./build.sh "$(cat VERSION)"' returned a non-zero code: 1


# Push
docker tag sejnub/logspout:rpi-1 sejnub/logspout:rpi-latest
docker login
docker push sejnub/logspout:rpi-latest


# Clean up
cd ~
rm -rf docker-logspout
rm -rf logspout
rm -rf logspout-logstash


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
