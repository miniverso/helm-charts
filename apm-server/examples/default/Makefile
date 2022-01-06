default: test

include ../../../helpers/examples.mk

RELEASE := helm-apm-server-default
NAMESPACE := elastic-system

install:
	helm upgrade --wait --timeout=$(TIMEOUT) --install --namespace $(NAMESPACE) $(RELEASE) ../../

test: install goss

purge:
	helm del --namespace $(NAMESPACE) $(RELEASE)
