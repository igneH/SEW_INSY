## 2. Objektorientierte Programmierung in Java ##
1. Datenkapselung:
	- grundlegendses Prinzip der objektorientierten Programmierung, Daten und die darauf operierenden Methoden innerhalb einer Klasse versteckt, verhindern von dirketen Zugriff und Modifikation eines Objektes, nur vorgesehene Schnittstellen verwenden
2. Sichtbarkeit:
	- `private`: nur innerhalb der Klasse
	- `protected`: derselben Klasse, desselben Paketes und Unterklasse sichtbar
	- `public`: für alle Klassen sichtbar
3. Zugriffsmethoden:
	- Getter-Methode: gibt den Wert eines privaten Attributs zurück
    ```Java
    public String getSurname() {
        return surname;
    }
    ```
	- Setter-Methode: setzt den Wert eines privaten Attributs, Validierung oder andere Logik
    ```Java
    public void setSurname(String surname) {
        this.surname = surname;
    }
    ```
4. Klassen
    - definieren die Struktur und das Verhalten von Objekten
    ```Java
    public class Car {
        // Felder (Eigenschaften)
        private String color;
        private String model;
        private int year;

        // Konstruktor
        public Car(String color, String model, int year) {
            this.color = color;
            this.model = model;
            this.year = year;
        }

        // Methoden (Verhalten)
        public void displayInfo() {
            System.out.println("Color: " + color);
            System.out.println("Model: " + model);
            System.out.println("Year: " + year);
        }

        // Getter und Setter Methoden
    }
    ```
    ```Java
    public class Main {
        public static void main(String[] args) {
            // Erstellen einer Instanz der Klasse Car
            Car myCar = new Car("Red", "Toyota", 2020);

            // Verwenden von Methoden der Klasse
            myCar.displayInfo();

            // Verwendung von Getter und Setter Methoden
            myCar.setColor("Blue");
            System.out.println("Updated Color: " + myCar.getColor());
        }
    }
    ```
5. Interfaces und Abstrakte Klassen
    - Abstrakte Klassen
        - können nicht instanziiert werden und können abstrakte Methoden enthalten, die in den Unterklassen implementiert werden müssen
        ```Java
        abstract class Animal {
            public abstract void makeSound(); // Abstrakte Methode

            public void eat() {
                System.out.println("This animal eats food");
            }
        }

        class Dog extends Animal {
            @Override
            public void makeSound() {
                System.out.println("Bark");
            }
        }
        ```
    - Interfaces
        - definieren Methoden, die von einer Klasse implementiert werden müssen
        - eine Klasse kann mehere Interfaces implementieren
        ```Java
        interface Animal {
            void makeSound(); // Methode ohne Implementierung
        }

        class Dog implements Animal {
            @Override
            public void makeSound() {
                System.out.println("Bark");
            }
        }   
        ```
6. Vererbung/Ableitung
    - ein Mechanismus, bei dem eine neue Klasse (Unterklasse) Eigenschaften und Methoden von einer bestehenden Klasse (Oberklasse) erbt
    ```Java
    class Animal {
        public void eat() {
            System.out.println("This animal eats food.");
        }
    }

    class Dog extends Animal {
        public void bark() {
            System.out.println("The dog barks.");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.eat(); // Methode der Oberklasse
            dog.bark(); // Methode der Unterklasse
        }
    }
    ```
7. dynamische Bindung
8. Polymorphie
    - ist die Fähigkeit einer Methode, verschiedene Implementierungen basierend auf dem Objekt, auf dem sie aufgerufen wird, zu haben
        - überladen
            - mehrere selbe Klassennamen, aber unterschiedliche Parameterlisten
            ```Java
            class MathUtils {
                public int add(int a, int b) {
                    return a + b;
                }

                public double add(double a, double b) {
                    return a + b;
                }
            }

            public class Main {
                public static void main(String[] args) {
                    MathUtils math = new MathUtils();
                    System.out.println(math.add(5, 10)); // Ausgabe: 15
                    System.out.println(math.add(5.5, 10.5)); // Ausgabe: 16.0
                }
            }
            ```
        - überschreiben
            - eine Methode der Unterklasse die Implementierung einer Methode der Oberklasse ändert
            ```Java
            class Animal {
                public void makeSound() {
                    System.out.println("Some generic animal sound");
                }
            }

            class Dog extends Animal {
                @Override
                public void makeSound() {
                    System.out.println("Bark");
                }
            }

            class Cat extends Animal {
                @Override
                public void makeSound() {
                    System.out.println("Meow");
                }
            }

            public class Main {
                public static void main(String[] args) {
                    Animal myDog = new Dog();
                    Animal myCat = new Cat();
                    
                    myDog.makeSound(); // Ausgabe: Bark
                    myCat.makeSound(); // Ausgabe: Meow
                }
            }
            ```