# Atualização Automática do Cluster Kubernetes

Este repositório contém um projeto Ansible para automatizar a atualização de sistemas em um cluster Kubernetes, realizando previamente um procedimento de cordon e drain antes de executar a atualização do sistema, garantindo a alta disponiblidade do cluster.

## Descrição dos Arquivos

### `playbook.yml`

Executa as tarefas de atualização nos nodes do cluster Kubernetes.

### `inventory.ini`

Arquivo de inventário do Ansible que lista os endereços de acesso aos nodes do cluster Kubernetes.

### `roles/atualizar-k8s/tasks/main.yml`

Inclui as tarefas de cordon e drain, atualização do sistema operacional e desativação do cordon e drain, chamando as tasks presentes na role "atualizar-k8s" para realizar esses procedimentos.

### `roles/atualizar-k8s/tasks/drain.yml`

Realiza o cordon, drain e verifica se os processos foram bem sucedidos antes de prosseguir.

### `roles/atualizar-k8s/tasks/centos.yml`

Atualiza todos os pacotes no sistema CentOS e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/suse.yml`

Atualiza todos os pacotes no sistema SUSE e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/ubuntu.yml`

Atualiza todos os pacotes no sistema Ubuntu e reinicia o servidor se necessário.

### `roles/atualizar-k8s/tasks/undrain.yml`

Desabilita o cordon e drain em um node do Kubernetes, aguardando até que o node esteja pronto para agendamento novamente.

## Como Usar

1. Clone este repositório.
2. Atualize o arquivo `inventory.ini` com os detalhes dos nodes do seu cluster Kubernetes, alterando os endereços de acesso e o caminho para a chave SSH.
3. Execute o playbook Ansible usando o comando `ansible-playbook playbook.yml -i inventory.ini -e bin_dir=/bin`.

Certifique-se de ter as permissões adequadas e as chaves SSH configuradas corretamente para acessar os nodes.

**Observação:** Este projeto assume que o `kubectl` está disponível no caminho especificado pela variável `bin_dir` (Por padrão seria o diretório /bin). Não esqueça de ajustar conforme necessário.
