# 1. Prozedurale Programmierung in C
## C Grundlagen
- hardwarenahe, prozedurale, höhere Programmiersprache
- called by value, called by reference
    ```C
    // call by value
    #include <stdio.h>

    void modifyValue(int num){
        num = 10;
    }

    int main(){
        int a = 5;
        modifyValue(a);
        printf("%d", a); // prints 5
        return 0;
    }
    ```
    ```C
    // call by reference
    #include <stdio.h>

    void modifyValue(int *num){
        *num = 10;
    }

    int main(){
        int a = 5;
        modifyValue(&a);
        printf("%d", a); // prints 10
        return 0;
    }
    ```
    - & (Ampersand) Variablen beinhalten die Adresse einer andere Variable
    - \* (Derefernzierungsoperator) wird benutzt um auf den Wert einer Adresse zuzugreifen
- H&C files
    - .c-File: Source Code
    - .h-File: enthalten Funktionsdeklarationen, Konstanten usw.
- Variablen-, Konstanten & Funktionen
    - Buchstaben, Ziffern und Unterstrich
    - Mit Buchstaben beginnend
    - Konstanten mit `#define NAME Wert`
- Protoypen
    - informiert den Compiler über Rückgabewerte und Parameter einer Funktion, sodass die Funktion korrekt aufgerufen wird, selbst wenn sie später im Programm erscheint
    ```C
    #include <stdio.h>
    int add(int, int);
    
    int main(){
        printf("%d", add(1,4));
        return 0;
    }

    int add(int a, int b){
        return a + b;
    }
    ```
- Structs
    - benutzerdefinierte Datensturkturen erstellen
    - einem Objekt in OOP sehr ähnlich
        - Datenkapselung
        - Sichtbarkeit ist aber immer öffentlich
    ```C
    struct Person{
        char name[20];
        int id;
    };

    typedef struct {
        char title[20];
        int pages;
    }Book;

    int main(){
        struct Person person;
        Book book;

        strcpy(person1.name, "Jim");
        person1.id = 1;

        strcpy(book.title, "entire history of the world I guess");
        person2.pages = 1000;

        printf("Name: %s\n", person.name);
        printf("ID: %d\n", person.id);

        printf("Title: %s\n", book.title);
        printf("Pages: %d\n", book.pages);

        return 0;
    }
    ```
## Statische und dynamische Datenstrukturen
- statische Datenstrukturen
    - größe einer statsichen Datenstruktur kann zur Laufzeit nicht geändert werden
    - Bsp: Arrays & Structs
- dynamische Datenstrukturen
    - Dynamisch heißt, dass zur Laufzeit des Programms Speicher vom Heap alloziert (zugewiesen) wird.
    - Bsp: verkettete Listen, Ringstruktur, Bäume
    - Methoden
        - `void *malloc(size_t size)`
        - `void free(void ptr*)`

## Verkettete Listen
- Einfach verkette Liste
    - Reihe von Strukturvariablen dynamisch erzeugen
    - in der Struktur Zeiger auf die nächste Struktur
    ```C
    typdef struct data{
        char name[20];
        int id;
        struct data *next;
    }DATA;
    ```
    - neues Element anlegen
    ```C
    DATA *head = (DATA*) malloc(sizeof(DATA));
    if(head != NULL){
        strcpy(head->name, "Jeff");
        head->id = 1;
        head->next = NULL;
    }
    ```
    - zweites Element hinzufügen und anhägen
    ```C
    DATA *second = (DATA*) malloc(sizeof(DATA));
    if(second != NULL){
        strcpy(second->name, "Jim");
        second->id = 2;
        second->next = NULL;
        first->next = second;
    }
    ```
    - löschen eines Elements
    - `head->next = third;`
    - `free(second)`
- doppelt verkettete Liste
    - Zeiger auf die nächste und Vorherige Struktur
    ```C
    typedef struct data {
        char name[MAX_LEN];
        char vorname[MAX_LEN];
        struct data *next;
        struct data *prev;
    }DATA;
    ```