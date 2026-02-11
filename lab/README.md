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

Dia 2 – Criação de grupos e usuários

Neste dia foi iniciada a modelagem de identidades do sistema, separando usuários por função organizacional.

Foram criados os seguintes grupos:
– alunos
– professores
– coordenacao
– adm
– ti

Os usuários foram criados manualmente com useradd, priorizando o entendimento do processo ao invés de automação.

Estratégia adotada:
– alunos com usuários genéricos por turma (aluno_t1em, aluno_t2em, aluno_t3em)
– professores com um usuário por disciplina (prof_<disciplina>)
– coordenação por área
– administração e TI com usuários individuais

Todos os usuários:
– possuem diretório home (-m)
– utilizam /bin/bash como shell
– foram adicionados aos respectivos grupos com usermod -aG
– receberam senhas para testes de login

Objetivo desta etapa:
Estabelecer a base de identidades do sistema antes de aplicar permissões e controle de acesso.

Nenhuma modificação de permissões de diretórios foi realizada nesta fase.

Dia 3: refatoração do controle de acesso e automação de grupos

Neste dia identifiquei que o controle de acesso em sistemas Linux é mais eficiente quando baseado em grupos, e não diretamente em usuários.
Com isso, alterei a política anterior para um modelo mais granular, criando grupos específicos por função/área (ex: prof_matematica) em vez de apenas grupos genéricos como "professores".

Devido à grande quantidade de grupos necessários, automatizei o processo com pequenos scripts bash, documentados em scripts.md.

Também utilizei um script com rsync para replicar e atualizar rapidamente os conteúdos das turmas dentro dos diretórios das disciplinas, evitando recriação manual. Essa abordagem foi possível por se tratarem de arquivos genéricos; em um ambiente real, esses dados seriam individuais.
