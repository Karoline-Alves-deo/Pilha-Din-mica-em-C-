# Pilha-Din-mica-em-C-
Implementação de uma pilha dinâmica utilizando lista encadeada simples em C++.  A estrutura segue o princípio LIFO (Last In, First Out), onde o último elemento inserido é o primeiro a ser removido.


## O projeto é composto por três arquivos:
📂 dynamic-stack
 ├── dynamicstack.h
 ├── dynamicstack.cpp
 └── main_dynamicstack.cpp
 
 ## Conceitos Utilizados

Estruturas (struct)
Classes em C++
Ponteiros
Alocação dinâmica (new e delete)
Tratamento de exceções (bad_alloc)
Lista encadeada
Encapsulamento

## Estrutura da Pilha

### Cada elemento da pilha é representado por um nó:

struct No {
    ItemType valor;
    No* proximo;
};

### A classe principal:

class dynamicstack {
private:
    No* NoTopo;

public:
    dynamicstack();
    ~dynamicstack();
    bool isempty();
    bool isfull();
    void push(ItemType item);
    ItemType pop();
    void print();
};
## Funcionamento


### Inicializa a pilha vazia: (Construtor)

NoTopo = NULL;

### Libera toda a memória alocada dinamicamente: (Destrutor)

while (NoTopo != NULL) {
    ...
}
Evita vazamento de memória.

### push(item)

Verifica se há memória disponível
Cria um novo nó
Insere no topo da pilha
Complexidade: O(1)

### pop()

Verifica se a pilha está vazia
Remove o elemento do topo
Libera memória
Retorna o valor removido
Complexidade: O(1)

### isempty()

Retorna true se a pilha estiver vazia.

### isfull()

Retorna true se a pilha estiver cheia.

### print()

Percorre a pilha do topo até o último elemento e imprime os valores.
Complexidade: O(n)

## Como Executar
### Compilar
g++ main_dynamicstack.cpp dynamicstack.cpp -o pilha
### Executar
./pilha

## 🖥️ Menu Interativo
O programa possui um menu simples:

Digite 0 para parar o programa
Digite 1 para inserir um elemento
Digite 2 para remover um elemento
Digite 3 para imprimir a pilha
