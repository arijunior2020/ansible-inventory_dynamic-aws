# Automatizando na Nuvem com Ansible e AWS!

Inventário dinâmico simples através do ansible e ec2 utilizando o plugin aws_ec2

## Passos para Automatização:

1. **Configurar o Arquivo ansible.cfg:**
   Antes de começar, certifique-se de incluir o plugin `aws_ec2` no arquivo `ansible.cfg`. 
   No item `[inventory]`, adicione a seguinte linha:
   
   ```enable_plugins = aws_ec2, host_list, script, auto, yaml, ini, toml1```

2. **Estabelecer Comunicação SSH:**
   É necessário estabelecer a comunicação SSH com suas instâncias EC2 na AWS. Isso é feito através de chaves SSH, que devem ser configuradas na criação da instância.

3. **Acesso Externo Liberado:**
   Certifique-se de que sua instância EC2 tem acesso externo liberado. Isso é fundamental para que o Ansible possa se comunicar com a instância e executar comandos remotamente.

4. **Criar Inventário Dinâmico:**
   Defina um arquivo YAML para o inventário dinâmico, indicando o plugin `aws_ec2`. Isso permite que o Ansible descubra automaticamente suas instâncias EC2 na AWS. O Arquivo se encontra na pasta src do projeto.

5. **Executar Comandos Adicionais:**
   Além de listar os recursos disponíveis com o comando `ansible-inventory -i aws_ec2.yml --list`, você pode extrair informações detalhadas dos hosts. Por exemplo, utilizando o comando:
   
   ```ansible -i aws_ec2.yml all -m shell -a 'ps aux'```
