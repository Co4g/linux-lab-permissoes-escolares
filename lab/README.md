Esta pasta documenta a execução prática do laboratório em uma máquina virtual Linux.

Nenhuma configuração aqui descrita é aplicada diretamente neste repositório.
O sistema real é montado em ambiente separado, e os procedimentos são registrados manualmente.

A proposta é documentar:
– criação de usuários e grupos
– aplicação de permissões
– testes de acesso
– problemas encontrados e soluções

Futuramente, esta área poderá evoluir para automações com scripts.

Dia 1 – Estrutura inicial

Criação da estrutura base de diretórios do laboratório escolar em /srv/escola, ainda sem arquivos.

Foram utilizadas diferentes abordagens:
– criação manual de diretórios
– uso de caminhos completos com mkdir
– reutilização de estruturas de turmas com cp

A estrutura final foi validada com o comando tree.

