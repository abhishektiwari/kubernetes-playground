REPO=message-api
TIMESTAMP=tmp-$(shell date +%s )
NSPACE=dev
DFILE=message-api/deployment.yml
SFILE=message-api/svc.yml
IFILE=message-api/ing.yml

.PHONY: local
local:  
	@eval $$(minikube docker-env) ;\
	docker image build -t $(REPO):$(TIMESTAMP) -f Dockerfile .
	kubectl set image -n $(NSPACE) deployment/$(REPO) *=$(REPO):$(TIMESTAMP)

.PHONY: delete
delete:
	kubectl delete -n $(NSPACE) deployment,service $(REPO)

.PHONY: create
create:
	@eval $$(minikube docker-env) ;\
	docker image build -t $(REPO):v1 -f Dockerfile .
	kubectl create -f $(DFILE)
	kubectl create -f $(SFILE)

.PHONY: ingress
ingress:
	kubectl create -f $(IFILE)

