Script para a criação de grupos de alunos:

#!/bin/bash

# Lista de turmas
turmas=(t1em t2em t3em)

for t in "${turmas[@]}"
do
    grupo="alunos_$t"

    echo "Criando grupo $grupo..."
    sudo groupadd "$grupo" 2>/dev/null
done

echo "Grupos de alunos finalizados."

Script para a criação de grupos de professores:

#!/bin/bash

disciplinas=(
arte filosofia geografia matematica portugues redacao
biologia fisica historia mat_financeira quimica sociologia
)

for d in "${disciplinas[@]}"
do
    grupo="prof_$d"

    echo "Criando grupo $grupo..."
    sudo groupadd "$grupo" 2>/dev/null
done

echo "Grupos de professores finalizados."

Script para a criação de grupos de Coordenação:

#!/bin/bash

areas=(exatas humanas linguagens)

for a in "${areas[@]}"
do
    grupo="coord_$a"

    echo "Criando grupo $grupo..."
    sudo groupadd "$grupo" 2>/dev/null
done

echo "Grupos de coordenação finalizados."

Script para a sincronização dos arquivos das pastas das turmas(este executado diretamente em linha):

for d in biologia filosofia fisica geografia historia matematica mat_financeira portugues quimica redacao sociologia; do sudo rsync -a /srv/escola/disciplinas/artes/T1EM/ "/srv/escola/disciplinas/$d/T1EM"; done