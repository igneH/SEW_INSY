# 2. Relationale Datenbanken und Normalformen
## Relationenalgebra
- Auf welchen mathematischen Grundlagen beruht das relationale Datenmodell?
    - Mengenlehre
    - Relationen
    - Prädikatenlogik
    - Schlüsselkonzept
    - Relationale Algebra

- Wozu brauche ich die Relationenalgebra?
    - fundamentales Konzept in der Datenbanktheorie und wird verwendet, um Operationen auf Relationen auszuführen und dient als formale Grundlage für die Abfrageverarbeitung und Datenmanipulation in relationalen Datenbanksystemen

- Welche mathematischen Funktionen gibt es und wie funktionieren sie?
    - ?
- Was ist der Unterschied zwischen einer Relation und einer (mathematsichen) Funktion?
    - eine Relation ist eine allgemeine Form einer Beziehung zwischen Elementen verschiedener Mengen, währen deine mathematische Funktion eine spezielle Art von Relation ist, bei der jedem Element einer Menge genau ein Element einer anderen Menge zugerordnet ist

- Was bedeutet "Attribut", "Wertebereich", "funktionale Abhängigkeit" und "voll funkionale Abhängigkeit"?
    - Attribut
        - Eigenschaft oder Charakteristik, die ein Teil der Informationen ausmacht, die in einer Datenbank gespeichert sind (Spalte in einer Tabelle)
    - Wertebereich
        - der Wertebereich eines Attributs bezeichnet die Menge aller möglichen Werte, die dieses Attribut annehmen kann
    - funktionale Abhängigkeit
        - wenn der Wert eines Attributs A den Wert eines Attributs B eindeutig bestimmt, gibt es eine funktionale Abhängigkeit von A nach B
    - voll funktionale Abhängigkeit
        - wenn ein Attribut nur von der gesamten Kombination anderer Attribute abhängt und nicht von einem Teil dieser Kombination

- Welche Eigenschaften haben Relationen?
    - Tupel (Zeilen)
    - Attribute (Spalten)
    - Werte
    - Eindeutigkeit
    - Reihenfolge
    - Schlüssel

- Welche sind die im Relationen-Modell verfügbaren relationalen Operatoren und welche sind die Mengenoperatoren.
    - Relationale Operatoren
        - Selektion
        - Projektion
        - Differenz
        - Kreuzprodukt
        - Join
    - Mengenoperatoren
        - Vereinigung (Union)
        - Schnitt (Intersection)
        - Differenz (Difference)

- Wie sind diese definiert?
    - https://de.wikipedia.org/wiki/Relationale_Algebra#Operationen

## Grundlagen des relationalen Datenmodells
- Was ist die Ausgangsbasis für die Umsetzung eines relationealen Modells?
    - die Annahme, dass Daten in Form von Relationen organisiert werden können
    - Konzeptuelles Modell (ER-Modell)?
    - Logisches Modell (relationale Tabellen)?

- Wieso brauche ich beide Modelle?
    - ? Logisches Modell entwickelt sich aus konzeptuellem Modell
- Erklären Sie die wichtigsten Teile des relationalen Modells (Attribut, Tupel, Domäne, Relation, Relationenschema)
    - Attribut
        - Eigenschaft oder Merkmal, das einen bestimmten Aspekt der Daten repräsentiert 
    - Tupel
        - eine einzelne Zeile oder Datensatz in einer Tabelle einer relationalen Datenbank
    - Domäne
        - definiert den zulässigen Wertebereich oder die Art der Daten, die für ein bestimmtes Attribut in einer Tabelle einer relationalen Datenbank zulässig sind
    - Relation
        - eine mathematische Darstellung eienr Tabelle in einer relationalen Datenbank
    - Relationenschema
        - definiert die Struktur einer Relation, einschließlich der Namen der Attribute und der Domänen

- Wie lauten die Regeln zur Umsetzung?
    - Information Rule
        - Alle Informationen in einer relationale Datenbank müssen in Form von Werten in Zellen einer Tabelle dargestellt werden
    - Guaranteed Access Rule
        - Jeder einzelne Datensatz muss durch die Kombination von Wert und Spaltenname eindeutig identifizierbar sein
    - Systematic Treatment of Null
        - eine relationale Datenbank muss die Behandlung von Null-Werten unterstützten, um eine flexible Datenverarbeitung zu ermöglichen
    - View Updating Rule
        - Änderungen an den Daten in der Datenbank sollten sich konsisten in allen Ansichten (Views) widerspielen, die auf diese Datenbank zugreifen
    - High-level Insert, Update und Delete
        - Das DBMS sollte Operationen zum Einfügen, Aktualisieren und Löschen von Datensätzen bereitstellen, ohne dass der Bentuzer direkt mit den physischen Speicherstrukturen arbeiten muss
    - Physical Data independence
        - Änderungen an der physischen Speicherstruktur der Datenbank sollten keine Auswirkungen auf die Anwendungen haben, die auf die Datenbank zugreifen
    - Logical Data Independence
        - Änderungen an der logsichen Struktur der Datenbank sollten keine Auswirkungen auf die Anwendungen haben, die auf die Datenbank zugreifen
    - Integrity Independence
        - Die Integritätsregeln, die die Konsistenz der Datbenbank gewährleisten, sollten unabhähngig von den Anwendungen sein, die auf die Datenbank zugreifen
    
- Was ist ein Primärschlüssel (Synonym: Identifikationsschlüssel), was ein Fremdschlüssel?
    - Primärschlüssel
        - eine Spalte oder Kombination von Spalten in einer Tabelle, die eindeutig jedes Tupel in dieser Tabelle identifiziert
    - Fremschlüssel
        - eine Spalte oder Kombination von Spalten in einer Tabelle, die auf den Primärschlüssel einer anderen Tabelle verweist (Anm.: Ziel muss nicht Primärschlüssel sein, sondern kann auch ein/e andere/s, eindeutige/s Attribut/Attributskombination sein. Üblich aber Primärschlüssel)

- Warum brauche ich Fremdschlüssel?
    - Beziehungen zwischen Tabellen herzustellen
    - Referenzielle Integrität gewährleisten
    - Datenkonsistzen sicherstellen
    - Datenintegrität verbessern

- Was sind die wichtigsten Eigenschaften eines Primärschlüssels?
    - Eindeutigkeit
    - Unveränderlichkeit
    - Minimalität
        - aus möglichst wenigen Spalten bestehen
    - Nicht NULL

- Wo stoßen relationale Datenmodelle an ihre Grenzen?
    - Komplexe Datenstrukturen, die nicht gut in tabellarischer Form dargestellt werden können
    - Skalierbarkeit (keine horizontale Skalierung)
    - Flexibilität
    - Komplexe Abfragen (?)
    - Semistrukturierte Daten

- Warum ist das relationale Datenmodell so erfolgreich?
    - Einfachheit
        - basiert auf Konzpeten wie Tabellen, Zeilen und Spalten
    - leistungsstarke Abfragesprachen wie SQL
    - Integrität
    - Sicherheit

## Erstellung und Umwandlung von UML/ER Modellen
- Was ist ein Datenmodell?
    - abstrakte Darstellung der Sturktur und Organisation von Daten in einem Informationssystem
    - es definiert die Art und Weise, wie Daten gespiechert, organisiert, verwaltet und abgerufen werden können
    - beschreibt Beziehungen zwischen den verschiedenen Datenobjekten und legt frest, wie sie miteinander verknüpft sind und wie sie in der Datenbank gespeichert werden
- Welche Datenmodelle kennen Sie?
    - Relationales Datenmodell
    - Hierarchisches Datenmodell
    - Netzwerkdatenmodell
    - Objektorientiertes Datenmodell
    - Dokumentenorientiertes Datenmodell
    - Grpahdatenmodell
- Zählen Sie mindestens drei auf und gehen Sie kurz auf die Strukturmerkmale ein.
    - Relationales Datenmodell
        - Sturktur: Organisiert Daten in Tabellen, wobei jede Tabelle Attribute und Tupel enthält
        - Beziehungen: Beziehungen zwischen den Tabellen werden durch Schlüssel definiert, wie z.B. Primärschlüssel und Fremdschlüssel
    - Objektorientiertes Datenmodell
        - Struktur: Daten werden als Objekte dargestellt, die sowohl Attribute als auch Verhalten (Mehtoden) enthalten können
        - Beziehungen: Objekte können Beziehungen zueinander haben, die durch Methoden oder Attribute dargestellt werden
    - Dokumentenorientiertes Datenmodell
        - Sturktur: Daten werden als Dokumente gespeichert, die in einem bestimmten Format wie JSON oder XML sturkturiert sind
        - Beziehungen: Die Beziehungen zwischen den Dokumenten können durch Einbettung oder Referenzierung dargestellt werden

- Wie werden Sie bei der Auswahl des Datenmodells vorgehen?
    - Anforderungsanalyse
    - Datenmodellierung
    - Vergleich der Datenmodelle
    - Prototyping und Test
    - Entscheidungsfindung

- Erläutern Sie an einem Beispiel die Auswahl.
    - YEP

- Wie werden Modelle im Schichtenmodell eingeteilt?
    - ?

- Wie unterscheiden sich die Modelle?
    - ?
- Erläutern Sie die einzelnen Konzepte des Diagramms.
    - ah hell naw

- Wie wird ein ER-Modell in ein Relationenmodell umgesetzt?
    1. Idetifizierung von Entitätstypen und Attributen
    2. Identifizierung von Beziehungstypen
    3. Identifizierung von Beziehungstypen mit Attributen
    4. Bestimmung von Schlüsseln
    5. Normalisierung
    6. Erstellung von Tabellen und Festlegung von Beziehungen
    7. Optimierung und Indexierung

- Welche Elemente/Teile des Diagramms werden nicht umgesetzt bzw. gebraucht.
    - YEP

- Vergleichen Sie ER- und UML Diagramm.
    - YEP

- Welche Vorteile bietet das ER-Modell gegenüber dem UML-Modell?
    - ich glaube YEP

- Gehen Sie auf die Umsetzung speziell der mc-Notation in ein relationales System ein.
    - ah hell naw

## Normalformen
- Erläutern Sie die Bedingung für die ersten drei Normalformen (1NF, 2NF, 3NF) und die erforderlichen Schritte zur Transformation in diese Normalformen!
    - 1NF
        - Bedingung: Alle Attribute in einer Tabelle müssen atomar sein
        - Transformationsschritte
            - Identifziere wiederholte Gruppen von Attributen und trenne sie in seperate Tabellen auf
            - Jede der neuen Tabellen sollte einen eindeutinge Schlüssel haben, der die Beziehung zur ursprünglichen Tabelle herstellt
            - Entferne redundante Attribute aus der ursprünglichen Tabelle und verweise stattdessen auf die neuen Tabellen über Fremdschlüsselbeziehungen.
    - 2NF
        - Bedingung: Tabelle muss in der 1NF sein
        - Transformationsschritte
            - Überprüfe, ob alle Nicht-Schlüsselattribute von einem Teil des Primärschlüssels abhängen
            - Falls nicht, teile die Tabelle in mehrere Tabellen auf, wobei jede Tabelle eine Teilemenge der ursprünglichen Attribte enthält, die von einem bestimmten Teil des Primärschlüssels abhängen
            - Füge Fremdschlüsselbeziehungen hinzu, um die Beziehung zwischen den neuen Tabellen und der ursprünglichen Tabelle herzustellen
    - 3NF
        - Bedingung: Tabelle mus in der 2NF sein
        - Transformationsschritte
            - Identifiziere transitive Abhängigkeiten zwischen Nicht-Schlüsselattributen, die nicht direkt vom Primärschlüssel abhängen
            - Teile die Tabell erneut auf, um diese transitive Abhängigkeiten zu eliminieren, indem du die betroffenen Attribute in seperate Tabellen verschiebst
            - Verwende Fremdschlüsselbeziehungen, um die Beziehung zwischen den neuen Tabellen und der ursprünglichen Tabelle zu definieren
- Welche Vor- bzw. Nachteile ergeben sich, wenn sich ein ER-Modell in der 3. NF berfindet?
    - Vorteile
        - Reduzierung von Redundanz
        - Verbesserte Datenintegrität
        - Bessere Performance bei Abfragen
    - Nachteile
        - Komplexität bei Abfragen
        - Höherer Speicherbedarf für Joins
        - Schwierigkeiten bei der Datenmodellierung

- Gibt es nocht weitere Stufen von Normalformen?
    - Boyce-Codd-Normalform
        - eine Erweiterung der 3NF und legt zusätzlich Eingschränkungen für funktionale Abhängigkeiten fest
    - 4NF
        - behandelt Multivalued-Abhängigkeiten und verbietet, dass ein Nicht-Schlüsselattribut mehrwertig von einem Teil des Primärschlüssels abhängt
    - 5NF
        - addressiert Abhängigkeiten zwischen Nicht-Schlüsselattributen und betrachtet die mölichen Verluste von sematischen Beziehungen, die durch die Zerlegung von Tabellen in kleinere Tabellen entstehen können
        
- Was versteht man in diesem Zusammenhang unter "Anomalie"?
    - unerwünschte und unerwarete Effekte, die auftreten können, wenn Daten in einer Datenbank nicht korrekt organisiert sind oder wenn die Struktur der Datenbank nicht den Anforderungen entspricht
        
- Welche Anomalien kennen Sie - Führen Sie dazu Beispiele an!
    - Einfügeanomalie
            - unmöglich einen Datensatz einzufügen, ohne zusätzliche Informationen hinzuzufügen, die nichts mit dem eigentlichen Datensatz zu tun haben
            - kann auftrete wenn Tabelle zu viele Attribute enthält
        - Löschanomalie
            - wenn das Löschen eines Datensatzes dazu führt, dass auch andere, möglicherweise relevante Daten verloren gehen
            - kann passieren wenn Informationen in einer Tabelle redundant gespiechert werden und das Löschen eines Datensatzes auch die Löschung anderer, nicht redundanter Informationen erfordert
        - Änderungsanomalie
            - tritt auf, wenn eine Änderung an einem Datensatz durchgeführt werden muss, die an meheren Stellen vorgenommen weerden muss, um die Konsistenz der Datenbank zu gewährleisten

- Wo stößt die Normalisierung an ihre Grenzen im praktischen Einsatz.
    - Performance
        - komplexe Abfragen zu längeren Abfragzeiten
    - Komplexität
        - zu starke Normalisierung kann Datenbankstrukturen komplex machen
    - Felxibilität
        - hochgradige Datenbanken können weniger flexibel sein, wenn Änderungen an der Datenstruktur erforderlich sind
    - Speicherplatz
        - zusätzliche Tabellen und Indizes führen zu erhöhtem Speicherbedarf
