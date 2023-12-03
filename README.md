# Atualização Automática do Cluster Kubernetes

Este repositório contém um projeto Ansible para automatizar a atualização de sistemas em um cluster Kubernetes. A estrutura do projeto é organizada da seguinte forma:

|-- roles
| |-- atualizar-k8s
| |-- tasks
| |-- centos.yml
| |-- drain.yml
| |-- main.yml
| |-- suse.yml
| |-- ubuntu.yml
| |-- undrain.yml
|-- inventory.ini
|-- playbook.yml


## Descrição dos Arquivos

### `roles/atualizar-k8s/tasks/centos.yml`

Atualiza todos os pacotes no sistema CentOS e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/drain.yml`

Realiza o cordon, dreno (drain) e verificações associadas em um nó do Kubernetes.

### `roles/atualizar-k8s/tasks/main.yml`

Inclui as tarefas de cordon e drain, atualização do sistema operacional e desativação do cordon e drain.

### `roles/atualizar-k8s/tasks/suse.yml`

Atualiza todos os pacotes no sistema SUSE e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/ubuntu.yml`

Atualiza todos os pacotes no sistema Ubuntu e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/undrain.yml`

Desabilita o cordon e drain em um nó do Kubernetes, aguardando até que o nó esteja pronto para agendamento novamente.

### `inventory.ini`

Arquivo de inventário do Ansible que lista os nós do cluster Kubernetes.

### `playbook.yml`

Executa as tarefas de atualização nos nós do cluster Kubernetes.
