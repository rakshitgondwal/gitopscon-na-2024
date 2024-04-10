LFC_NAMESPACE ?= keptn-lifecycle-controller-system
PODTATO_NAMESPACE ?= podtato-kubectl
GRAFANA_PORT_FORWARD ?= 3000

.PHONY: install
install:
	kubectl create namespace monitoring
	kubectl apply --server-side -f config/prometheus/setup
	kubectl apply -f config/prometheus/