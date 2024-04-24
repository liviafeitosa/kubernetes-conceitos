# kubernetes-conceitos #

**Sites Importantes**

Projeto Kubernetes:

- https://kubernetes.io
- https://github.com/kubernetes/kubernetes/
- https://github.com/kubernetes/kubernetes/issues

Certificações Kubernetes (CKA, CKAD e CKS):

- https://www.cncf.io/certification/cka/
- https://www.cncf.io/certification/ckad/
- https://www.cncf.io/certification/cks/

**Container Engine**

O Container Engine é crucial para gerenciar imagens e volumes, garantindo isolamento e eficiência para os containers. Embora o Docker tenha sido líder, opções como CRI-O e Podman são populares e adequadas para ambientes produtivos.

**Container Runtime**

O Container Runtime é o responsável por executar os containers nos nós. Existem três tipos: 
- Low-level: são os Container Runtime que são executados diretamente pelo Kernel, como o runc, o crun e o runsc.
- High-level: são os Container Runtime que são executados por um Container Engine, como o containerd, o CRI-O e o Podman.
- Sandbox e Virtualized: são os Container Runtime que são executados por um Container Engine e que são responsáveis por executar containers de forma segura. O tipo Sandbox é executado em unikernels ou utilizando algum proxy para fazer a comunicação com o Kernel. O gVisor é um exemplo de Container Runtime do tipo Sandbox. Já o tipo Virtualized é executado em máquinas virtuais. A performance aqui é um pouco menor do que quando executado nativamente. O Kata Containers é um exemplo de Container Runtime do tipo Virtualized.

**Arquitetura do Kubernetes**

O Kubernetes segue um modelo control plane/workers, formando um cluster. Recomenda-se no mínimo três nós: um nó control-plane e workers para executar aplicações. Para estudo, é possível criar um cluster em um único nó, mas não para produção.

Existem diversas soluções para executar Kubernetes localmente, como Kind, Minikube, MicroK8S, k3s e k0s.

**Componentes Principais**
- API Server: Fornece uma API RESTful para comunicação.
- etcd: Datastore para armazenamento de configurações do cluster.
- Scheduler: Aloca pods nos nós com base nos recursos disponíveis.
- Controller Manager: Mantém o cluster no estado desejado.
- Kubelet: Agente nos nós workers para gerenciar pods.
- Kube-proxy: Proxy e load balancer para roteamento de tráfego.

**Portas Relevantes**

Portas importantes para a comunicação dentro do cluster, tanto para o control plane quanto para os workers.

Control Plane
- 6443 (TCP): Kubernetes API server, utilizado para comunicação com o cluster.
- 2379-2380 (TCP): etcd server client API, para comunicação com o banco de dados do cluster.
- 10250 (TCP): Kubelet API, usada para comunicação entre o control plane e os nós.
  
Workers
- 10250 (TCP): Kubelet API, usada para comunicação entre os nós e o control plane.
- 30000-32767 (TCP): Faixa de portas NodePort, utilizada para serviços em todos os nós do cluster.

**Conceitos-Chave do Kubernetes**
- Pod: A menor unidade no Kubernetes, contendo um ou mais containers.
- Deployment: Controla a execução de réplicas de pods e gerencia o ciclo de vida da aplicação.
- ReplicaSets: Garante a quantidade de pods em execução.
- Services: Exponha a comunicação entre os pods, funcionando como um balanceador de carga.
