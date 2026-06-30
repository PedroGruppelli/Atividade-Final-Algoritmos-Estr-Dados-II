# Perguntas obrigatórias — Sistema de Gerenciamento de Ocorrências

## Onde foi usada a fila?

A fila foi usada para controlar a ordem de chegada das ocorrências. Toda vez que uma ocorrência é cadastrada, ela entra no final da fila (`fila_enqueue`), e quando vamos atender pela ordem de chegada (opção 3 do menu), pegamos sempre a que está na frente da fila (`fila_dequeue`). Isso garante que quem chegou primeiro é atendido primeiro (FIFO).

## Onde foi usada a pilha?

A pilha foi usada para guardar o histórico de ações do sistema. Cada vez que algo importante acontece (cadastro, atendimento, etc.), a gente empilha uma mensagem descrevendo a ação (`pilha_push`). Na opção 6 do menu dá pra ver esse histórico, do mais recente pro mais antigo, e na opção 7 dá pra "desfazer" removendo o item do topo da pilha (`pilha_pop`).

## Onde foi usada a árvore?

Foi implementada uma árvore binária de busca para guardar as ocorrências pelo ID. Toda ocorrência cadastrada também é inserida na árvore (`inserir`), e isso permite buscar uma ocorrência específica pelo ID de forma mais rápida do que percorrer a lista inteira (opção 8 do menu, função `buscar_id`).

## Onde foi usada a heap?

Para resolver o atendimento por prioridade (opção 9), a gente usou o Quicksort para ordenar a lista por prioridade e pegar o primeiro item "Aberto".

## Onde foi usada a hash table?

A hash table foi usada para fazer busca rápida por nome do solicitante e por tipo de ocorrência. Criamos dois dicionários, `hash_por_nome` e `hash_por_tipo`, onde a chave é o nome ou tipo em minúsculo e o valor é uma lista de ocorrências (porque pode ter mais de uma ocorrência com o mesmo nome ou tipo). Quando duas ocorrências caem na mesma chave, a gente resolve a colisão por encadeamento, simplesmente adicionando na mesma lista.

## Qual algoritmo de ordenação foi implementado?

Foi implementado o Quicksort (na função `quicksort`/`particionar`), usado para ordenar as ocorrências por ID ou por prioridade na opção 5 do menu, e também internamente na opção 9 para descobrir qual ocorrência é a mais urgente.

## Qual estrutura foi mais adequada para busca rápida?

A hash table. Buscar por nome ou tipo usando o dicionário é praticamente instantâneo, porque a gente acessa direto pela chave, sem precisar percorrer a lista toda comparando ocorrência por ocorrência.

## Qual estrutura foi mais adequada para atendimento por prioridade?

A estrutura mais adequada para atendimento por prioridade, dentro do que implementamos, foi a combinação da lista de ocorrências com o Quicksort.

## Qual foi a maior dificuldade do grupo?

A maior dificuldade foi entender como integrar todas as estruturas funcionando juntas ao mesmo tempo (toda vez que cadastra uma ocorrência, ela precisa entrar na lista, na fila, na hash e na árvore simultaneamente), sem deixar nenhuma desincronizada. Também tivemos dificuldade em decidir qual estrutura usar para cada funcionalidade.
