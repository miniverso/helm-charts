default: test

RELEASE := helm-es-microk8s
TIMEOUT := 1200s
NAMESPACE := elastic-system

install:
	helm upgrade --wait --timeout=$(TIMEOUT) --install --namespace $(NAMESPACE) --values values.yaml $(RELEASE) ../../

test: install
	helm test --namespace $(NAMESPACE) $(RELEASE)

purge:
	helm del --namespace $(NAMESPACE) $(RELEASE)
