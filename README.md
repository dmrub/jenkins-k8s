# jenkins-k8s

Jenkins installation and examples based on:
* https://www.jenkins.io/doc/book/installing/kubernetes/
* https://github.com/scriptcamp/kubernetes-jenkins
* https://devopscube.com/setup-jenkins-on-kubernetes-cluster/

## Deploy jenkins

By default, Jenkins is deployed in the `devops-tools` namespace. To change the namespace, change it in the `k8s-config/customization.yaml` and `k8s-config/namespace.yaml` files.

To see which resources are created or updated:

```sh
kubectl kustomize k8s-config;
```

Deploy or update the configuration with the command:

```sh
kubectl apply -k k8s-config;
```

Check the status of the deployed resources by running the following command:

```sh
kubectl get -k k8s-config;
```

Also see https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/ for details.

Connect to the jenkins service:

```sh
kubectl port-forward -n devops-tools svc/jenkins 8080;
```

Then open http://localhost:8080 in your browser

## Configure Kubernetes access

* Install suggested plugins and create admin user
* Install Kubernetes plugin
* Install 'Kubernetes :: Pipeline :: DevOps Steps' plugin
* Create Kubernetes cloud configuration
* Use defaults
* Set Kubernetes Namespace to devops-tools
* Set Jenkins URL to http://jenkins:8080

## License

Copyright 2023 Dmitri Rubinstein

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
