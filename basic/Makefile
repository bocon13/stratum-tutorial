ONOS_URL := http://localhost:8181/onos
ONOS_POST := curl -sSL --user onos:rocks --noproxy localhost -X POST -H 'Content-Type:application/json'
dir := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))

start:
	docker-compose up -d
stop:
	docker-compose down --remove-orphans

netcfg:
	${ONOS_POST} ${ONOS_URL}/v1/network/configuration/ -d@${dir}netcfg.json

gnmi:
	docker run -it --rm --network=basic_stratum bocon/gnmi-cli --grpc-addr mininet:50001 ${ARGS}
