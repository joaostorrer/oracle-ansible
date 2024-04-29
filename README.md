# oracle
Ansible playbooks para gerenciar e alterar bancos de dados Oracle

## Dependência

É necessário instalar o módulo `opitzconsulting.ansible_oracle` antes de utilizar os playbooks, da seguinte forma:
```console
root@ansible:~$ ansible-galaxy collection install opitzconsulting.ansible_oracle
```

## setup_integracao
Cria usuário, libera as grants SYS para ele, cria os objetos do Sqitch e libera as grants dos objetos do Sqitch para o Tasy

### Variáveis
- host
- novo_usuario
- porta
- senha
- senha_novo_usuario
- service_name
- usuario

### Utilização

Chame o playbook passando as variáveis pelo argumento `--extra-vars` como no exemplo abaixo:

```console
root@ansible:~$ ansible-playbook setup_integracao.yaml --extra-vars "host=10.10.10.10 porta=1521 service_name=teste usuario=sys senha=senha_sys novo_usuario=teste_ansible senha_novo_usuario=senha_teste_ansible"
```

Ou crie um arquivo `vars.yaml` com as variáveis e passe o arquivo no argumento `--extra-vars` como no exemplo abaixo:

```yaml
---
host: 10.10.10.10
porta: 1521
service_name: teste
usuario: sys
senha: senha_sys
novo_usuario: teste_ansible
senha_novo_usuario: senha_teste_ansible
```

```console
root@ansible:~$ ansible-playbook setup_integracao.yaml --extra-vars @vars.yaml
```
