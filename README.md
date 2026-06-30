# Sistema de Gerenciamento de Ocorrências

Sistema de cadastro e atendimento de ocorrências feito em Python, utilizando estruturas de dados como fila, pilha, árvore binária de busca e hash table.

## Como executar

Basta ter o Python 3 instalado e rodar:

```bash
python nome_do_arquivo.py
```

O programa abre um menu interativo no terminal que fica em loop até a opção de sair ser escolhida.

## Estruturas de dados utilizadas

- **Lista** (`lista_ocorrencias`): armazena todas as ocorrências cadastradas, na ordem de cadastro.
- **Fila** (`fila_dados`): controla a ordem de chegada para atendimento (FIFO).
- **Pilha** (`pilha_historico`): registra o histórico de ações realizadas no sistema (LIFO).
- **Árvore Binária de Busca**: permite buscar uma ocorrência pelo ID de forma mais rápida que percorrer a lista inteira.
- **Hash Table** (`hash_por_nome` e `hash_por_tipo`): permite busca rápida por nome do solicitante ou tipo de ocorrência, com colisões resolvidas por encadeamento (listas).
- **Quicksort**: usado para ordenar as ocorrências por ID ou prioridade.

## Funcionalidades do menu

| Opção | Funcionalidade | Estrutura usada |
|---|---|---|
| 1 | Cadastrar ocorrência | Lista, Fila, Hash, Pilha, Árvore |
| 2 | Listar todas as ocorrências | Lista |
| 3 | Atender próxima pela ordem de chegada | Fila |
| 4 | Buscar por nome ou tipo | Hash Table |
| 5 | Ordenar ocorrências (por ID ou prioridade) | Quicksort |
| 6 | Ver histórico de ações | Pilha |
| 7 | Desfazer última ação | Pilha |
| 8 | Buscar ocorrência por ID | Árvore Binária |
| 9 | Atender ocorrência mais urgente (maior prioridade) | Quicksort + Lista |
| 0 | Sair do programa | - |

## Detalhes de cada funcionalidade

### 1 — Cadastrar ocorrência
Solicita nome, tipo, descrição e prioridade (1 a 5). Gera um ID automático sequencial e insere a ocorrência simultaneamente na lista geral, na fila de atendimento, na hash table e na árvore binária. Também registra a ação no histórico (pilha).

### 2 — Listar todas as ocorrências
Exibe todas as ocorrências cadastradas, na ordem em que foram inseridas na lista.

### 3 — Atender pela ordem de chegada
Remove a ocorrência mais antiga da fila (a que chegou primeiro), marca como "Atendido" e registra a ação no histórico.

### 4 — Buscar por nome ou tipo
Permite escolher buscar por nome do solicitante ou por tipo de ocorrência. A busca é feita na hash table, o que torna a consulta rápida mesmo com muitos registros.

### 5 — Ordenar ocorrências
Ordena uma cópia da lista de ocorrências por ID ou por prioridade, usando o algoritmo Quicksort, sem alterar a ordem original da lista.

### 6 — Ver histórico de ações
Mostra todas as ações registradas na pilha, da mais recente para a mais antiga.

### 7 — Desfazer última ação
Remove o registro mais recente do topo da pilha de histórico (não desfaz o efeito da ação nos dados, apenas remove o registro do histórico).

### 8 — Buscar ocorrência por ID
Usa a árvore binária de busca para localizar uma ocorrência específica pelo ID de forma eficiente.

### 9 — Atender mais urgente
Ordena as ocorrências por prioridade e atende a primeira que ainda estiver com status "Aberto", marcando-a como "Atendido" e registrando no histórico.

## Status das ocorrências

Cada ocorrência possui um status que pode ser:
- **Aberto**: ainda não foi atendida.
- **Atendido**: já foi processada (pela fila ou pela urgência).

## Observações

- Os dados são armazenados apenas em memória — ao fechar o programa, todas as ocorrências cadastradas são perdidas.
- A opção "Desfazer última ação" (7) remove o registro do histórico, mas não reverte o status ou os dados da ocorrência em si.
