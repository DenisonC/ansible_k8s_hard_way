Kubeadm Ansible Playbook


Crie um cluster Kubernetes usando Ansible com kubeadm. O objetivo é instalar facilmente um cluster Kubernetes em máquinas executando:



- Ubuntu 20.04

- CentOS 7 

- Debian 10



Requisitos de sistema:

- O ambiente de implantação deve conter o Ansible 

- Master e nodes devem ter acesso ao SSH sem senha 



Faça o download dos arquivos atravé do gti:



git clone https://github.com/DenisonC/ansible_k8s_hard_way.git

Adicione as informações do sistema  em um arquivo chamado hosts.ini. Por exemplo:



[master]
192.168.0.76

[node]
192.168.0.77

[kube-cluster:children]
master
node

Se você estiver trabalhando com Ubuntu, adicione as seguintes propriedades a cada host ansible_python_interpreter='python3':


[master]
192.168.0.76 ansible_python_interpreter='python3'
[node] 
192.168.0.77 ansible_python_interpreter='python3'

[kube-cluster:children] 
master
node

Agora edite o arquivo group_vars/all.yml

Para utilizar o flannel ao invés de calico altere a linha:




# Network implementation('flannel', 'calico')
network: flannel
Para utilizar o melallb como Load Balancer para os pods alter a linha abaixo para true:



Para alterar o rutime do docker alterar a linha abaixo:


# Container runtimes ('containerd', 'crio')
container_runtime: crio


Depois de executar a configuração execute o playbook do sitem.yml

ansile-playbook sites.yaml




















