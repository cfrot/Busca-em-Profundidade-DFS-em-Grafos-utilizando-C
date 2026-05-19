# Busca em Profundidade (DFS) em Grafos utilizando C

## Introdução

Este projeto apresenta uma implementação do algoritmo DFS (Depth-First Search), também conhecido como Busca em Profundidade, utilizando grafos representados por lista de adjacência na linguagem C.

O algoritmo DFS é uma das técnicas mais importantes da computação para percorrer grafos e árvores, sendo amplamente utilizado em sistemas de busca, inteligência artificial, análise de redes e diversos problemas computacionais.

---

# O que é um grafo?

Um grafo é uma estrutura utilizada para representar conexões entre elementos.

Ele é composto por:

- **Vértices (nós)** → representam os elementos
- **Arestas** → representam as conexões entre os vértices

---

## Exemplo

```txt
0 → 1 → 3
|
↓
2
```

Nesse exemplo:
- `0`, `1`, `2` e `3` são vértices
- As setas representam as conexões entre eles

---

# Objetivo do projeto

O projeto tem como objetivo:

✅ Implementar o algoritmo DFS  
✅ Percorrer grafos utilizando recursividade  
✅ Representar grafos com lista de adjacência  
✅ Trabalhar com listas encadeadas e ponteiros  
✅ Praticar estruturas de dados na linguagem C  

---

#  O que é DFS?

DFS significa:

# Depth-First Search

ou:

# Busca em Profundidade

---

# Como o algoritmo funciona?

O DFS percorre o grafo explorando o máximo possível de um caminho antes de voltar.

A lógica é:

1. Visitar um vértice
2. Marcar como visitado
3. Ir para um vizinho não visitado
4. Repetir o processo recursivamente
5. Voltar quando não houver mais caminhos disponíveis

---

# Exemplo visual

## Grafo

```txt
0 → 1 → 3
|
↓
2
```

---

## Execução da DFS iniciando em 0

```txt
0 → 1 → 3
↓
2
```

Ordem possível:

```txt
0 1 3 2
```

---

# Estrutura do projeto

O projeto utiliza:

- Lista de adjacência
- Lista encadeada
- Recursividade
- Vetor de controle de visitados

---

# Estrutura do nó

```c
typedef struct No{
	int vertice;
	struct No* prox;
} No;
```

---

## Explicação

| Campo | Função |
|---|---|
| `vertice` | Armazena o vértice conectado |
| `prox` | Ponteiro para o próximo nó |

---

# Estrutura do grafo

```c
typedef struct{
	No* adj[MAX];
	int visitando[MAX];
	int numVertices;
} Grafo;
```

---

## Explicação

| Campo | Função |
|---|---|
| `adj` | Lista de adjacência |
| `visitando` | Controla vértices visitados |
| `numVertices` | Quantidade de vértices |

---

# Funções implementadas

---

# Criar nó

```c
No* criarNo(int v)
```

Responsável por:

- Criar dinamicamente um nó
- Armazenar o vértice
- Inicializar o ponteiro

---

# Inicializar grafo

```c
void inicializarGrafo(Grafo* g, int vertices)
```

Responsável por:

- Inicializar listas vazias
- Inicializar vetor de visitados
- Definir quantidade de vértices

---

## Inicialização

```c
g->adj[i] = NULL;
g->visitando[i] = 0;
```

Inicialmente:
- Nenhum vértice possui conexões
- Nenhum vértice foi visitado

---

# Adicionar aresta

```c
void adicionarAresta(Grafo* g, int origem, int destino)
```

Responsável por conectar vértices no grafo.

---

## Funcionamento

```c
novo->prox = g->adj[origem];
g->adj[origem] = novo;
```

A conexão é adicionada na lista do vértice origem.

---

# Grafo direcionado

Na implementação atual:

```txt
origem → destino
```

A conexão ocorre em apenas uma direção.

---

# Algoritmo DFS

```c
void dfs(Grafo* g, int v)
```

Função principal responsável pela busca em profundidade.

---

# Funcionamento da DFS

O algoritmo:

1. Exibe o vértice atual
2. Marca o vértice como visitado
3. Percorre os vizinhos
4. Chama recursivamente a DFS

---

## Marcação de visitado

```c
g->visitando[v] = 1;
```

Isso impede visitas repetidas e loops infinitos.

---

## Chamada recursiva

```c
dfs(g, adj);
```

A DFS continua explorando profundamente o grafo.

---

# Fluxo visual da recursão

## Grafo

```txt
0 → 1 → 3
|
↓
2
```

---

## Execução

```txt
dfs(0)
 ├── dfs(1)
 │     └── dfs(3)
 └── dfs(2)
```

---

# Exemplo de execução

## Entrada

```txt
Numero de vertices:
4

Numero arestas:
4

Aresta 1:
0 1

Aresta 2:
0 2

Aresta 3:
1 3

Aresta 4:
2 3

Vertice inicial para DFS:
0
```

---

## Saída

```txt
Resultado da DFS:
0 2 3 1
```

---

# Complexidade do algoritmo

## Complexidade de Tempo

```txt
O(V + E)
```

Onde:

- `V` = quantidade de vértices
- `E` = quantidade de arestas

---

# Por que a DFS é eficiente?

Cada:
- vértice é visitado apenas uma vez
- aresta é percorrida apenas uma vez

---

# ✅ Vantagens da DFS

- Implementação simples
- Excelente para exploração de grafos
- Utiliza pouca memória em muitos cenários
- Muito utilizada em problemas computacionais

---

# ❌ Desvantagens

- Pode entrar profundamente em caminhos desnecessários
- Recursão pode consumir muita pilha em grafos grandes

---

# Aplicações reais

A DFS é utilizada em:

- 🌐 Navegação em redes
- 🛰️ Sistemas de mapas
- 🎮 Inteligência artificial em jogos
- 🔍 Resolução de labirintos
- 📂 Sistemas de arquivos
- 🔗 Análise de redes sociais
- 🧠 Problemas de backtracking
- 📊 Detecção de ciclos em grafos

---

# Conceitos utilizados

Durante o desenvolvimento deste projeto foram utilizados conceitos importantes como:

- Grafos
- Lista de adjacência
- Recursividade
- Busca em profundidade
- Listas encadeadas
- Ponteiros
- Estruturas (`struct`)
- Alocação dinâmica de memória
- Manipulação de memória
- Laços de repetição

---

# Tecnologias utilizadas

- Linguagem C
- Estruturas de Dados
- Algoritmos

---

# Como executar o projeto

## Compilar o projeto

```bash
gcc main.c -o dfs
```

---

## Executar

### Linux/macOS

```bash
./dfs
```

### Windows

```bash
dfs.exe
```

---

# Estrutura do projeto

```txt
projeto/
│
├── main.c
```

---

# Objetivo acadêmico

Este projeto foi desenvolvido com fins acadêmicos para estudo de grafos, listas de adjacência, recursividade e algoritmos de busca em profundidade na linguagem C.

---

# Autor

Desenvolvido por Daniel Pacheco.
