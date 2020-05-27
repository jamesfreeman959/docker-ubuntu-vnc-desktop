# Default values for variables
REPO  ?= dorowu/ubuntu-desktop-lxde-vnc
TAG   ?= latest

# Test run the container
#  the local dir will be mounted under /src read-only
run: 
	docker run --privileged --rm \
                -p 6080:80 -p 6081:443 \
                -v ${PWD}:/src:ro \
                -e USER=doro -e PASSWORD=mypassword \
                -e ALSADEV=hw:2,0 \
                -e SSL_PORT=443 \
                -e RELATIVE_URL_ROOT=approot \
		-e OPENVPN_USERNAME=vpnuser@example.com \
                -e OPENVPN_PASSWORD=password \
                -e OPENVPN_PROVIDER=zoog \
                -e OPENVPN_CONFIG=se1.udp.zoogvpn \
                -e OPENVPN_OPTS="--inactive 3600 --ping 10 --ping-exit 60" \
                -v ${PWD}/ssl:/etc/nginx/ssl \
                --device /dev/snd \
                --name ubuntu-desktop-lxde-test \
                $(REPO):$(TAG)
