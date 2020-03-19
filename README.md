# micro-mesh
 Examples for service mesh

## Start minikube cluster
`minikube start`

## Build docker image
`./docker-build.sh`

## Pull curl and httpbin images
`docker pull tutum/curl`
`docker pull citizenstig/httpbin`

## Run httpbin
`docker run -d --name httpbin citizenstig/httpbin`

## Check httpbin endpoint using curl
`docker run -it --rm --link httpbin tutum/curl curl -X GET http://httpbin:8000/headers`

## Run envoy proxy for the httpbin service
`docker run -d --name proxy --link httpbin envoy:v1 envoy -c /etc/envoy/simple.yaml`

## Verify envoy proxy running
`docker logs proxy`

## Verify httpbin service through the envoy proxy
`docker run -it --rm --link proxy tutum/curl curl -X GET http://proxy:15001/headers`

## Remove envoy proxy
docker rm -f proxy

