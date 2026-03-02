# Pilha Dinamica em C++
Implementação de uma pilha dinâmica utilizando lista encadeada simples em C++.  A estrutura segue o princípio LIFO (Last In, First Out), onde o último elemento inserido é o primeiro a ser removido.


## O projeto é composto por três arquivos:
📂 dynamic-stack
 ├── dynamicstack.h
 ├── dynamicstack.cpp
 └── main_dynamicstack.cpp
 
 ## Conceitos Utilizados

Estruturas (struct);
Classes em C++;
Ponteiros;
Alocação dinâmica (new e delete);
Tratamento de exceções (bad_alloc);
Lista encadeada;
Encapsulamento.

## Estrutura da Pilha

### Cada elemento da pilha é representado por um nó:

```
struct No {
    ItemType valor;
    No* proximo;
};
```
### A classe principal:

```
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
```
---

## Funcionamento


### Inicializa a pilha vazia: (Construtor)
```
NoTopo = NULL;
```

### Libera toda a memória alocada dinamicamente: (Destrutor)
```
while (NoTopo != NULL) {
...
}
```
Evita vazamento de memória.

### push(item)

Verifica se há memória disponível;
Cria um novo nó;
Insere no topo da pilha;
Complexidade: O(1).

### pop()

Verifica se a pilha está vazia;
Remove o elemento do topo;
Libera memória;
Retorna o valor removido;
Complexidade: O(1).

### isempty()

Retorna true se a pilha estiver vazia.

### isfull()

Retorna true se a pilha estiver cheia.

### print()

Percorre a pilha do topo até o último elemento e imprime os valores.
Complexidade: O(n)

---
## Como Executar
### Compilar
```g++ main_dynamicstack.cpp dynamicstack.cpp -o pilha```
### Executar
```./pilha```

## 🖥️ Menu Interativo
O programa possui um menu simples:

Digite 0 para parar o programa;
Digite 1 para inserir um elemento;
Digite 2 para remover um elemento;
Digite 3 para imprimir a pilha.

---
## Códigos:
### 📂 dynamicstack.h
```

typedef int ItemType;

struct No 
{
    ItemType valor;
    No* proximo;
};

class dynamicstack{
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
```
### 📂 dynamicstack.ccp
```
#include <iostream>
#include "dynamicstack.h"
#include <cstddef> //NULL

using namespace std;

    dynamicstack::dynamicstack() //Construtor 
    {
        NoTopo = NULL;
    }

    dynamicstack::~dynamicstack() //Destrutor
    {
        No* NoTemp;
        while (NoTopo != NULL){
            NoTemp = NoTopo;
            NoTopo = NoTopo->proximo;
            delete NoTemp;
        }
    }

    bool dynamicstack::isempty() // Verifica se a pilha esta vazia
    {
        return (NoTopo == NULL);
    }

    bool dynamicstack::isfull() // Verifica se a pilha esta cheia
    {
        No* NoNovo;
        try{
            NoNovo = new No;
            delete NoNovo;
            return false;
        } catch(bad_alloc exception){
            return true;
        }
    }

    void dynamicstack::push(ItemType item) 
    {
        if (isfull()){
            cout << "ERRO.Pilha esta cheia!\n";
            cout << "Nao eh possivel inserir este elemento.\n";
        } else{
            No* NoNovo = new No;
            NoNovo->valor = item;
            NoNovo->proximo = NoTopo;
            NoTopo = NoNovo;
        }
    }

    ItemType dynamicstack::pop()
    {
        if (isempty()){
            cout << "ERRO. Pilha esta vazia!\n";
            cout << "Nao eh possivel remover nenhum elemento.\n";
            return 0;
        } else{
            No* NoTemp;
            NoTemp = NoTopo;
            ItemType item = NoTopo->valor;
            NoTopo = NoTopo->proximo;
            delete NoTemp;
            return item;
        }
    }

    void dynamicstack::print() 
    {
        No* NoTemp = NoTopo;
        cout << "Pilha: [ ";
        while (NoTemp != NULL){
            cout << NoTemp->valor << " ";
            NoTemp = NoTemp->proximo;
        }
        cout << "]\n";
    }
```
### 📂 main_dynamicstack.ccp

```
#include <iostream>
#include "dynamicstack.h"

using namespace std;

int main(){
    dynamicstack pilha1;
    ItemType item;
    int opcao;
    cout << "-----Gerador de Pilha-----\n";

    do {
        cout << "Digite 0 para parar o programa!\n";
        cout << "Digite 1 para inserir um elemento!\n";
        cout << "Digite 2 para remover um elemento!\n";
        cout << "Digite 3 para imprimir a pilha!\n";
        cin >> opcao;
        if (opcao == 1){
            cout << "Digite o elemento a ser inserido:\n";
            cin >> item;
            pilha1.push(item);
        } else if (opcao == 2){
            item = pilha1.pop();
            cout << "Elemento Removido: " << item << endl;
        } else if (opcao == 3){
            pilha1.print();
        }

    } while(opcao != 0);

    return 0;
}
```

## Autora  

**Karoline Alves**  
Entusiasta em tecnologia da informação, robótica e computação em nuvem.
