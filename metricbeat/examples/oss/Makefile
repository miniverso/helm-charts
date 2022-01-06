default: test

include ../../../helpers/examples.mk

RELEASE := helm-metricbeat-oss
GOSS_SELECTOR = release=$(RELEASE),app=helm-metricbeat-oss-metricbeat
NAMESPACE := elastic-system

install:
	helm repo add stable https://charts.helm.sh/stable
        helm dependency update ../../
	helm upgrade --wait --timeout=$(TIMEOUT) --install --namespace $(NAMESPACE) --values values.yaml $(RELEASE) ../../

test-metrics:
	 GOSS_FILE=goss-metrics.yaml make goss GOSS_SELECTOR=release=$(RELEASE),app=helm-metricbeat-oss-metricbeat-metrics

test: install goss test-metrics

purge:
	helm del --namespace $(NAMESPACE) $(RELEASE)
