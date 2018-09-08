#include<stdio.h>
#include<stdlib.h>
#include <conio.h>
#include<string.h>

struct Libro {
  char *titulo;
  int anioDePublicacion;
  int pos=0;
  struct Libro *next;
  struct Libro *Previous;
};

void imprimir_lista(Libro *);
void aniadir(Libro &*, Libro *);
void obtener(Libro *, int);
void borrar(Libro *, int);
int menu();
void modificar(Libro *, int);

using namespace std;
int main (int args, char *argv[]){
  struct Libro *raiz, *cola;
  int s;
  do{
    op=menu();
    switch (op) {
      case 1: {
        aniadir();
        break;
      }
      case 2: {
        int i;
        cout << "Que posicion quiere obtener:" << '\n';
        cin << i;
        if(i<(posi/2)){
          obtener(raiz, i);
        }
        else {
          obtener(cola, i);
        }
        break;
      }
      case 3: {
        cout << "Que posicion quiere Modificar:" << '\n';
        cin << i;
        if(i<(posi/2)){
          modificar(raiz, i);
        }
        else {
          modificar(cola, i);
        }
        break;
      }
      case 4: {
        imprimir_lista(raiz);
        break;
      }
      case 5: {
        cout << "Que posicion quiere borrar:" << '\n';
        cin << i;
        if(i<(posi/2)){
          borrar(raiz, i);
        }
        else {
          borrar(cola, i);
        }
        break;
      }
      case 6: {
        cou << '\n' << "Hata la Proxima" << '\n';
        s=6;
        break;
      }
      default: {
        cout << "Opcion no valida" << '\n';
      }
    }
    system("cls");
  }while(s!=6);
  return 0;
}

int posi;

void imprimir_lista(Libro *raiz, Libro *cola){
  Libro *aux= new Nodo();
  aux = raiz;
  cou << "Lista enlazada completa" << '\n';
  while(aux != NULL){
    cout << "LIbro " << aux->pos << '\n'; 
    cout << aux->titulo << '\n';
    cout << aux->anioDePublicacion << '\n';
  }
  if(pos=0);
    cout << "La lista esta vacia" << '\n';
}

void aniadir(Libro &*raiz){
  Libro *nuevo = new Libro();
  if (nuevo==NULL){
    printf("Te acabaste la memoria");
    posi++;
  }
  nuevo->titulo=NULL;
  cout << '\n'<<'\n'<< "NUEVO LIBRO" << '\n';
  cout << "Ingrese el autor:" << '\n';
  cin >> nuevo->titulo;
  cout << "Ingrese el anio de publicacion:" << '\n';
  cin >> nuevo->anioDePublicacion;
  nuevo->pos=posi;
  Libro *aux1 = nuevo;
  Libro *aux2;
  while(aux != NULL){
      aux2=aux1;
      aux1=aux1->siguiente;
    }
  if(aux==raiz){
    raiz = nuevo;
  }
  else{
    aux2->next = nuevo;
  }
  nuevo->next = aux1; 
  nuevo->previous=cola;
  cola = nuevo;
}

void borrar(Libro *raiz, int i){
  Libro *actual = raiz;
  Libro *ant=NULL;
  Libro *post=NULL;
  if(i<=pos&&i>0){
    if(i<(pos/2)){
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->next;
      }
    }
    else{
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->previous;
      }
    }
    ant=actual->previous;
    post=actual->next;
    ant->next = post;
    post->previous = ant;
    delete actual;
  }
  else{
    cout << "Posicion no Encontrada" << '\n';
  }
}

void obtener(Libro *raiz, int i){
  Libro *actual = raiz;
  if(i<=pos&&i>0){
    if(i<(pos/2)){
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->next;
      }
    }
    else{
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->previous;
      }
    }
    cout << "LIbro " << actual->pos << '\n'; 
    cout << actual->titulo << '\n';
    cout << actual->anioDePublicacion << '\n';
  }
  else{
    cout << "Posicion no Encontrada" << '\n';
  }
}

void modificar(Libro *raiz, int i){
  Libro *actual = raiz;
  if(i<=pos&&i>0){
    if(i<(pos/2)){
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->next;
      }
    }
    else{
      while(actual != NULL){
        if(actual->pos==i){
          break;
        }
        actual=actual->previous;
      }
    }
    nuevo->titulo=NULL;
    cout << '\n'<<'\n'<< "NUEVO LIBRO" << '\n';
    cout << "Ingrese el autor:" << '\n';
    cin >> nuevo->titulo;
    cout << "Ingrese el anio de publicacion:" << '\n';
    cin >> nuevo->anioDePublicacion;
    cout << "LIbro " << actual->pos << '\n'; 
    cout << actual->titulo << '\n';
    cout << actual->anioDePublicacion << '\n';
  }
  else{
    cout << "Posicion no Encontrada" << '\n';
  }
}

int menu(){
  int op;
  cout << '\n'<< '\n' << "Menu" << '\n'<< '\n';
  cout << "1. Insertar Nuevo" << '\n';
  cout << "2. Obtener" << '\n';
  cout << "3. Modificar" << '\n';
  cout << "4. Mostrar toda la lista" << '\n';
  cout << "5. Borrar" << '\n';
  cout << "6. Salir" << '\n';
  cout << '\n' << "Elija la opcion:" << '\n';
  cin << op;
  return op;
}
