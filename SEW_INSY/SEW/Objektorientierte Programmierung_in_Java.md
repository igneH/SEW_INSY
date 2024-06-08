## 2. Objektorientierte Programmierung in Java ##
1. Datenkapselung:
	- grundlegendses Prinzip der objektorientierten Programmierung, Daten und die darauf operierenden Mehtoden innerhalb einer Klasse versteckt, verhindern von dirketen Zugriff und Modifikation eines Objektes, nur vorgesehene Schnittstellen verwenden
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