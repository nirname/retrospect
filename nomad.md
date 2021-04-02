NOMAD_ADDR=http://nomad01.example.com:4646 nomad node status 3a359c64
NOMAD_ADDR=http://nomad01.example.com:4646 nomad node status -self
NOMAD_ADDR=http://nomad01.example.com:4646 nomad run /tmp/job.nomad
curl -v --request PUT 'http://nomad01.example.com:4646/v1/system/gc'
consul services deregister -id rabbit

source /dev/stdin <<< "$(gopass show secret-keys/env)"

docker build -t 172.16.1.103:5000/hello:v1 .
docker push 172.16.1.103:5000/hello:v1
curl -X GET http://172.16.1.103:5000/v2/_catalog
curl -X GET http://172.16.1.103:5000/v2/hello/tags/list

nomad job status -all-allocs service
nomad node drain -enable f6feba36
nomad node drain -disable f6feba36