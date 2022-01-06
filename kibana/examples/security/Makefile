default: test

include ../../../helpers/examples.mk

RELEASE := helm-kibana-security
NAMESPACE := elastic-system

install:
	helm upgrade --install --values values.yaml --namespace $(NAMESPACE) $(RELEASE) ../../

test: secrets install goss

purge:
	kubectl delete secret kibana --namespace $(NAMESPACE) || true
	helm del --namespace $(NAMESPACE) $(RELEASE)

secrets:
	encryptionkey=$$(docker run --rm busybox:1.31.1 /bin/sh -c "< /dev/urandom tr -dc _A-Za-z0-9 | head -c50") && \
	kubectl create secret generic kibana --from-literal=encryptionkey=$$encryptionkey --namespace $(NAMESPACE)
