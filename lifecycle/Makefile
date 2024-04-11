LFC_NAMESPACE ?= keptn-lifecycle-controller-system
PODTATO_NAMESPACE ?= podtato-kubectl
GRAFANA_PORT_FORWARD ?= 3000

.PHONY: install
install:
	kubectl create namespace monitoring
	kubectl apply --server-side -f config/prometheus/setup
	kubectl apply -f config/prometheus/

.PHONY: apply
apply:
	kubectl apply -f deployment.yaml
	kubectl apply -f metric.yaml
	kubectl apply -f metric-provider.yaml
	kubectl apply -f slack-secret.yaml
	kubectl apply -f pre-deploy-eval.yaml
	kubectl apply -f post-deploy-task.yaml
	kubectl apply -f appcontext.yaml

.PHONY: delete
delete:
	kubectl delete ns podtato-kubectl