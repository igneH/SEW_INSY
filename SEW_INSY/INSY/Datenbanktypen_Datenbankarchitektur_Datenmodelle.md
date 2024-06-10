# 1. Datenbanktypen Datenbankarchitektur und Datenmodelle
## Begriffe und Geschichte/ Datenbanktypen
- <b>Nenne Einsatzgebiete bzw. Vor- und Nachteile von Datenbanken.</b>
    - Einsatzgebiete:
        - Geschäftsanwendungen
            - Kundendatenverwaltung
            - Finanzmanagement
        - E-Commerece:
            - Produktkataloge
            - Bestellverwaltung
        - Gesundheitswesen
            - Patientenakten
            - Medizinische Forschung
        - Bildungswesen
            - Studentenverwalung
            - E-Leraning-Plattformen
    - Vorteile von DB
        - Effiziente Datenverwalung
        - Datenintegrität und -sicherheit
        - Skalierbarkeit
        - Datenkonsistenz
        - Automatisierung und Wiederverwendbarkeit
            - Routineaufgaben
            - Wiederverwenung von gespeicherten Prozeduren und Funktionen
    - Nachteile von DB
        - Komplexität
            - technisches Fachwissen: komplex und zeitaufwendig
        - Kosten
        - Leistungsprobleme
        - Abhängigkeit von DBMS
            - abhängig von dessen Funktionalität und Hersteller -> Schwierigkeiten bei Migration zu anderen Systemen
        - Sicherheitsrisiken
            - schlechter Schutz kann zu Datenverlust oder -diebstahl führen

- <b>Wann würden Sie eine Datenbank einsetzen?</b>
    - Verwaltung großer Datenmengen
        - Wenn System große Datenmengen speichern muss
    - Bedarf an Mehrbenutzerzugriff
        - Wenn mehrere Benutzer gleichzeitig auf die gleichen Daten zugreifen und bearbeiten wollen
    - Sicherstellung von Datenintegrität und -sicherheit
        - Mechanismen zur Gewährleistung der Datenintegrität und Sicherstellung von Zugriffen von nur autorisierten Benutzer
    - Effiziente und flexible Datenabfragen
        - komplexe Abfragen aus Großen Datensätzen
    - Notwendigkeit der Datenkonsoldierung
        - Wenn daten aus verschiednen Quellen konsolidiert und zentral verwaltet werden müssen
    - Automatisierung und Wiederverwendbarkeit
        - DB unterstützen Automatisierung von Routineaufgaben und Wiederwendung gespeicherter Prozeduren und Funktionen
    - Bedarf an Historisierung und Rückverfolgbarkeit
        - Historie von Änderungen und Rückverfolgung von Transaktionen benötigt werden

- <b>Was sind die grundlegenden Funktionen eines Datenbankmanagementsystems(DBMS) unabhängig vom unterstützen Datenmodell?</b>
    - Datenorganisation, -speicherung und -verwaltung
    - Datenmanipulation
    - Datenintegrität und -sicherheit
    - Datenwiederherstellung und -sicherung
    - Mehrbenutzerunterstützung und Synchronisation
- <b>Was bedeuten die Begriffe Konsistenz, Redundanz und Integrität?</b>
    - Konsistenz
        - Daten nach jeder Transatkion in einem gültigen, nicht widersprüchlichen Zustand verbleiben
    - Redundanz
        - überflüssige Datenkopien
            - negative Redundanz
                - Probleme bei erhöhtem Speicherbedarf, erschwerte Datenaktualisierung und Inkonsistenzen
            - positive Redundanz
                - Datenverfügbarkeit und Ausfallsicherheit
            - wird durch Normalisierung reduziert
    - Integrität
        - Genauigkeit und Vollständigkeit der Daten in einer Datenbank
            - Datenintegrität
                - Sicherstellung, dass die Daten korrekt und zuverlässig sind
            - Referenzielle Integrität
                - Sicherstellung, dass Beziehungen zwischen Tabellen korrekt bleiben
            - Domänenintegrität
                - Sicherstellung, dass die Werte in einer Spalte den definierten Datentypen und Einschränkungen entsprechen

- <b>Grenzen Sie die Begriffe Datenbank, Datenmodell, Datenbankmanagementsystem und Informationssystem voneinander ab.</b>
    - Datenbank
        - organisierte Sammlung von strukturierten Daten, die in einem computerbasierten System gespeichert und verwaltet werden
    - Datenmodell
        - ein konzeptionelles Werkzeug, dass die Struktur und die Beziehungen der Daten in einer Datenbank beschreibt
            - definiert wie Daten organisiert und wie die verschiedenen Datenenlemente miteinander verbunden sind.
        - Arten von Datenmodellen
            - Relationalies Datenmodell: Organisiert Daten in Tabellen (Relationen) mit Zeilen (Tupel) und Spalten (Attribute/Felder)
            - Hierarchisches Datenmodell: Organisiert Daten in einer baumartigen Struktur
            - Netzwerkdatenmodell: Verbindet Daten in einem Netzwerk von Knoten
            - Objektdatenmodell: Verwendet objektorientierte Konzepte zur Datenorganisation
    - Datenbankmanagementsystem (DBMS)
        - eine Software, die die Erstellung, Verwaltung und Nutzung von Datenbanken ermöglicht
            - Funktionen eines DBMS
                - Datenbankdefinition: Definition von Datenstrukturen und Schemata
                - Datenmanipulation: Einfügen, Akturalisieren, Löschen und Abfragen von Daten
                - Datensicherheit: Kontrolle des Zugriffs auf die Daten
                - Datenintegrität: Sicherstellung der Genauigkeit und Konsistenz der Daten
                - Datenwiederherstellung
        - Bsp für DMBS: MySQL, Oracle Database, Microsoft SQL Server
    - Informationssystem
        - ein umfassenderes Konzept, das die Infrastruktur und Werkzeuge zur Sammlung, Speicherung, Verarbeitung und Bereitstellung von Informationen umfasst
        - Bestandteile eines Informationssystems
            - Hardware: Server, Computer, Netzwerke
            - Software: Anwendungen, Betriebssysteme
            - Daten: Rohdaten, die in der Datenbank gespiechert sind
            - Menschen: Benutzer, Administratoren, Entwickler
            - Prozesse: Geschäftsprozesse und Verfahren zur Verarbeitung und Nutzung der Daten

- <b>Welche Typen von DBMS gibt es?</b>
    - Relationale DBMS (RDBMS)
        - Tabellen mit Zeilen und Spalten
        - Beziehungen mit Fremdschlüssel definiert
        - SQL (Structured Query Language)
        - Bsp: MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server
        - Vorteile: Einfache Datenmodellierung, starke Konsistenz und Integrität, weit verbreitet und gut unterstützt
        - Nachteile: Kann bei sehr großen oder unstrukturierten Daten ineffizient sein
    - Hierarchisches DBMS
        - organisiert Daten in einer baumartigen Struktur bei der jede Dateneinheit mehrere untergeordnete Dateneinheiten haben kann
        - Beispiele: IBM information Managment System
        - Vorteile: Schneller Datenzugriff
        - Nachteile: Unflexibel bei Datensturkur Änderungen, schwierig zu verwalten bei komplexen Beziehungen
    - Netzwerk-DBMS
        - graphartige Struktur, bei der Dateneinheiten durch verschiedene Arten von Beziehungen miteinander verbunden sein können
        - Beispiele: Integrated Data Store
        - Vorteile: Unterstützt komplexe viele-zu-viele Beziehungen
        - Nachteile: Komplexe Datenmodellierung und Verwaltung
    - Dokumentenorientiertes DBMS (NoSQL)
        - speichert Daten als Dokumente, die typischerweise in Form von JSON, BSON oder XML vorliegen
        - Beispiele: MongoDB, CouchDB
        - Vorteile: Flexibilität bei der Datenstruktur, skalierbar, gut für unstrukturierte Daten
        - Nachteile: Schwächere Konsistenzgarantien, komplexer Abfrageprozess
    - Schlüssel-Wert-DBMS (NoSQL)
        - speichern Daten als Key-Value-Pairs, ähnlich wie eine Hash-Map
        - Beispiele: Redis, DynamoDB
        - Vorteile: Sehr schnell, einfach zu skalieren
        - Nachteile: Eingeschränkte Abfragemöglichkeiten, nicht geeignet für komplexe Datenstrukturen

- <b>Erläutern Sie die geschichtliche und technische Entwicklung.</b>
    - 1950er Daten auf Magnetband und Lochkarten gespeichert
    - 1960er erste Datenbankmodelle: hierarchische Modell und Netzwerkmodell
    - 1970er Edgar F. Codd veröffentlichte relationale Modell
        - SQL
        - erstes RDBMS
    - 1980er - 1990er Objektorientierte Datenbanken
    - 1990er Data Warehousing
        - OLAP
    - 2000er NoSQL und Big Data
    - 2010er - heute Cloud Datenbanken, NewSQL, In-Memory-Datenbanken
- <b>Welche (DBMS) gibt es derzeit noch am Markt?</b>
    - RDBMS
        - Oracle Database
        - Microsoft SQL Server
        - MySQL
        - PostgreSQL
        - IBM Db2
        - MariaDB
    - NoSQL
        - MongoDB
        - Cassandra
        - Redis
        - CouchDB
        - Neo4j
    - NewSQL-Datenbanken
        - Google Spanner
        - CockroachDB

- <b>Welche (DBMS) sind relevant?</b>
    -  populärsten ig?
        - MySQL
        - PostreSQL
        - Microsoft SQL Server
        - MongoDB
        - Cassandra
        - Redis

- <b>Warum für welche Einsatzgebiete entstehen immer mehr Nischenprodukte?</b>
    - Spezialisierte Anforderungen
        - Industire 4.0 und IoT
        - Gesundheitswesen
    - Technologische Fortschritte
        - Big Data und Analytics
        - Maschinelles Lernen
    - Effizienz und Optimierung
        - Echtzeitanalysen
        - Finanzdienstleistungen
    - Regulatorische Anforderungen
        - Finanzsektor
        - Gesundheitswesen
    - Wettbewerbsvorteil
        - E-Commerce
        - Marketing

- <b>Nennen Sie Vor- und Nachteile (der Nischenprodukte).</b>
    - Vorteile:
        - Spezialisierung
            - sind oft speziell für bestimmte Anwenungsfälle oder Branchen etwickelt und bieten maßgeschneiderte Funktionen und Lösungen
        - Effizienz und Leistung
            - könenen in ihrem spezifischen Bereich eine wesentlich höhrere Leistung und Effizienz
        - Flexibilität
            - bieten größere Felexibilität und Anpassungsfähigkeit an die spezifischen Bedürfnisse des Unternehmens
    - Nachteile
        - Engeschränkte Benutzerbasis
            - weniger Community-Support und weniger umfangreiche Dokumentationen
        - Kosten
            - maßgeschneiderte Lösungen und spezialisierte Dienstleistungen erfordern
        - Skalierbarkeit
            - nicht so skalierbar wie allgemeine Produkte, da sie für spezifische Anwendungsfälle optimiert sind
        - Wartung und Updates
            - da die Entwicklerressourcen begrent sind und spezifische Anforderungen bedient werden müssen

## Architektur von Datenbanksystemen
- <b>Was versteht man unter der "Drei Schichten Architektur" nach ANSI-SPARC?</b>
    - ANSI-SPARC = American National Standards Institue - Standards Planning and Requierements Committee
    - ein konzeptionelles Modell für DBMS. Es teilt die Struktur eines DBMS in drei unabhängige Schichten auf: die externe, die konzeptionelle und die interne Schicht
        - Externe Schicht (External Level)
            - repräsentiert die Sichtweise der Endbenutzer oder Anwendungsprogramme auf die Datenbank, wie individuelle Benutzer oder Anwendungen die Daten sehen und mit ihnen interagieren
        - Konzeptionelle Schicht (Conceptual Level)
            - bietet eine einheitliche, logische Sicht auf die gesamte Datenbank, unabhängig von physischen Speicherstrukturen und den spezifischen Anforderungen der Benutzer
        - Interne Schicht (Internal Level)
            - definiert, wie die Daten physisch gespiechert und organisiert sind
        
- <b>Wieso hat man sich überhaupt für mehrere Schichten entschieden?</b>
    - Datenunabhängigkeit
    - Flexibilität und Anpassungsfähigkeit
    - Sicherheit und Zugriffskontrolle
    - Verbesserte Wartbarkeit und Skalierbarkeit
    - Standardisierung und Interoperabilität
    - Optimierte Leistung

- <b>Erläutern Sie die einzelnen Schichten.</b>
    - kinda done
- <b>Welche Gründe sprechen für dieses Modell?</b>
    - Datenunabhängigkeit
    - Verbesserte Datenintegration und Konsistenz
    - Erhöhte Datensicherheit
    - Bessere Wartbarkeit und Flexibilität
    - Erleichterte Migration und Skalierbarkeit
    - Effiziente Verwaltung und Optimierung
- <b>Welche Schicht hängt vom Betriebssystem ab?</b>
    - interne Schicht
- <b>Braucht man ein Filesystem - wenn ja: Wer stellt es zur Verfügung und inwieweit kann sich dieses auf das Gesamtsystem auswirken?</b>
    - Windows: NTFS, FAT32, exFAT
    - Linux: ext4, Btrfs, XFS, ZFS
    - macOS: APFS, HFS+
    - Auswirkungen
        - Leistung
        - Datensicherheit
        - Kompatibilität
        - Wartung und Wiederherstellung

- <b>Wo wird die Struktur der abzuspeichernden Informationen hinterlegt?</b>
    - in der Regel in einem DBMS hinterlegt

- <b>Inwieweit reflektiert sich diese Struktur in den Anwendungsprogrammen?</b>
    - Datenmodelle in Anwendungsprogrammen
        - Objekte und Klassen
        - Datenstrukturen
    - Datenzugriffsschichten
        - Data Access Objects (DAO)
        - Object-Relational Mapping (ORM)
    - SQL-Queries und Stored Procedures
        - Direkte SQL-Queries
        - Stored Procedures und Views
    - Validierungen dund Geschäftslogik
        - Datenvalidierung
        - Geschäftslogik
- <b>Wie können komplexe Strukturen vereinfacht dargestellt werden?</b>
    - Abstraktion
        - Klassendiagramme
    - Visualisierung
        - Flussdiagramme
        - ER-Diagramme
    - Hierarchische Darstellung
        - Baumdiagramme
        - Mindmaps

- <b>Was legt ein Datenbankschema fest?</b>
    - legt die Struktur und die organisatorischen Regeln einer Datenbank fest
    - Datenbankschema umfasst folgende Aspekte
        - Tabellen
        - Beziehungen
        - Einschränkungen
        - Indizes
        - Sichten (Views)
        - Prozeduren und Funktionen
        - Trigger

- <b>Was versteht man unter den Begriffen DDL/DML?</b>
    - DDL (Data Definition Language)
        - umfasst Befehle, die zur Definition und Strukturierung der Datenbankobjekte verwendet werden
            - CREATE, ALTER, DROP, TRUNCATE
    - DML (Data Manipulation Language)
        - umfasst Befehle, die zur Manipulation und Verwaltung der Daten innerhalb der Datenbank verwendet werden
            - SELECT, INSERT, UPDATE, DELETE

- <b>Wie reflektiert sich DDL/DML in der Architektur eines Datenbanksystems?</b>
    - DDL
        - Interne Ebene
            - Speicherstruktur
            - Speicherverwaltung
        - Konzeptionelle Ebene
            - Schema-Definition
            - Integrität und Konsistenz
    - DML
        - Konzeptionelle Ebene
            - Datenmanipulation
            - Abfrageoptimierung
        - Externe Ebene
            - Datenzugriff
            - Benutzerschnittstellen
    
- <b>Gehen Sie auf einige Modellierungskonzepte ein, die sich aus der Schichtenarchitektur ergeben.</b>
    - Interne Ebene
        - Speicherstrukturen
            - Dateiorganisation
            - Indexierung
            - Clustering
        - Speicherverwaltung
            - Speicherpools
            - Caching
    - Konzeptionelle Ebene
        - Datenbankmodellierung
            - ER-Modell
            - Relationales Modell
        - Integritätsbedingungen
            - Schlüsselintegrität
            - Domänenintegrität
            - Geschäftsregeln
        - Datenbankentwurf
            - Normalisierung
            - Denormalisierung
    - Externe Ebene
        - Benutzersichten
            - Views
            - Subschemas
        - Sicherheitsmechanismen
            - Zugriffssteuerung
            - Datenmaskierung

## ER bzw EER-Modell und Umsetzung
- <b>Wie geht man bei der Erstellung eines ER-Modells vor?</b>
    1. Anforderungsanalyse
        - Verstehen und Sammeln der Anforderugnen an die Datenbank
    2. Identifizierung der Entitäten
        - Bestimmen der Entitäten, über die Daten gespeichert werden sollen
    3. Bestimmung der Attribute
        - Festlegen der Eigenschaften jeder Entität
    4. Identifizierung der Schlüssel
        - Festlegen der eindeutigen Identifikatoren für jede Entität
    5. Bestimmung der Beziehungen
        - Festlegen, wie die Enitäten miteinander in Beziehung stehen
    6. Definition der Kardinalitäten
        - Festlegen der Kardinalitäten der Beziehungen
    7. Erstellung des ER-Diagramms
        - Grafische Darstellung der Entitäten, Attribute und Beziehungen
    8. Überprüfung und Validierung
        - Sicherstellen, dass das ER-Modell korrekt und vollständig ist
    9. Normalisierung
        - Vermeidung von Redundanzenund Inkonsistenzen in der Datenbank
    10. Implementierung
        - Überführung des ER-Modells in ein Datenbankschema
    
- <b>Welche Einsatzgebiete hat ein ER-Modell?</b>
    - Datenbankdesign und -entwicklung
        - Datenbankentwurf
        - Normalisierung
    - Systemanalyse und -entwurf
        - Anforderungsanalyse
        - Systemdesign
    - Datenintegration
        - Datenmigration
        - Datenintegration
    - Business Intelligence und Data Warehousing
        - Datenanalyse
        - Data Warehousing
    - Softwareentwicklung
        - Anwendungsentwicklung
        - Datenvalidierung
    - Dokumentation und Schulung
        - Kommunikation mit Stakeholdern
        - Teamzusammenarbeit
- <b>Was ist eine Entität?</b>
    - ein eindeutig identifizierbares Objekt oder Konzept in einem bestimmten Kontext, das für die Datenmodellierung relevant ist
    - Merkmale
        - Eindeutigkeit
        - Relevanz
        - Eigenschaften
- <b>Was ist ein Entitätstyp?</b>
    - ein abstraktes Konezpt im ER-Modell, das die grundlegende Struktur und die gemeinsamen Eigenschaften einer Gruppe von ähnlichen Entitäten beschreibt
    - Merkmale
        - Abstraktion
        - Eigenschaften
        - Schlüssel

- <b>Was ist eine Beziehung ("Relationship"), was ein Beziehungstype?</b>
    - Beziehung
        - eine Verbindung zwischen zwei oder mehr Entitäten, die eine bestimmte Art von Interaktion, Abhängigkeit oder Assoziation repräsentiert
    - Beziehungstyp
        - definiert die spezifische Art und Weise, wie eine Beziehung zwischen Entitäten modelliert wird, sowie ihre Eigenschaften und Beschränkungen
    
- <b>Erklären Sie anhand des Modells Ausprägung und Modell.</b>
    - Modell
        - abstraktes Schema, Bauplan, Konstrukt der Datenstruktur, unabhängig von festen Werten, Entitätstypen, Beziehungstypen, Klasse in objektorientierter Programmierung
    - Ausprägung
        - Instanz eines Modells mit konkreten Werten, Entitäten, Beziehungen, Objekt in objektorientierter Programmierung
          
- <b>Welche Typen von Beziehungen können Entitäten eingehen?</b>
    - 1:1
    - 1:n
    - m:n
    - reflexive Beziehung
        - Beziehung zu sich selbst
    
- <b>Was versteht man unter einer schwachen Entität?</b>
    - eine Art von Entität in einem Datenmodell, die von einer anderen Entität abhängig ist, um einduetig identifiziert zu werden

- <b>Was versteht man unter Spezialisierung/Generalisierung?</b>
    - sind Konzepte der Hierarchiebildung in der Datenmodellierung, die es ermöglichen, komplexe Datenstrukturen zu organisiern und zu verwalten
    - Spezialisierung
        - bezieht sich auf den Prozess der Identifizierung spezfischer Unterklassen innerhalb einer übergeordneten Klasse
    - Generalisierung
        - ist der umgekehrte Prozess der Spezialisierung

- <b>Wie werden diese umgesetzt?</b>
    - Spezialisierung
        - Identifizierung spezifischer Unterklassen
        - Definition spezifischer Attribute und Beziehungen
        - Vererbung nutzen
    - Generalisierung
        - Identifizierung gemeinsamer Attribute und Beziehungen
        - Zusammenfassung in einer übergeordneten Klasse
        - Vererbung nutzen

- <b>Erklären Sie rekursive Datenstrukturen im ER-Modell.</b>
    - rekusive Datenstrukturen beziehen sich auf Situationen, in denen eine Entität eine Beziehung zu sich selbst hat.

- <b>Welche Beziehungen (Kardinalitäten!) können unmittelbar als Relationenschema (im Relationenmodell) dargestellt werden?</b>
    - 1:1-Beziehung
    - 1:n-Beziehung
    - n:m-Beziehung

- <b>Was muss ich bei der Umsetzung der Beziehungen beachten?</b>
    - Korrekte Identifikation der Beziehungen
    - Festlegung der Kardinalitäten
    - Verwendung von Fremschlüsseln
    - Integritätsbedingungen
        - Datenbankkonsistenz erhalten bleibt

- <b>Wie können "schwwache Entiäten" als ER-Diagramm bzw. als Tabellenschema modelliert werden?</b>
    - ER-Diagramm
        - Verwendung des Doppelrechteck-Symbols
        - Abhängige Beziehung zu starker Entität
        - Identifizierender Beziehungstyp
    - Tabellenschema
        - Verwendung von Fremschlüsseln
        - Kein eigener eindeutiger Identifikator
            - Kombination aus Fremdschlüsseln

- <b>Warum dürfen/sollen Beziehungen nicht in Beziehung zu anderen Beziehungen stehen?</b>
    - Semantische Klarheit
    - Datenintegrität
    - Komplexität reduzieren
    - Flexibilität und Skalierbarkeit

- <b>Was versteht man in diesem Zusammenhang unter "Uminterpretation"?</b>
    - Es bezieht sich auf die Möglichkeit, dass die Bedeutung oder Semantik von Daten falsch interpretiert oder fehlinterpretiert werden kann, insbesondere wenn die Datenmodelle nicht klar definiert oder dokumentiert sind

- <b>Wie werden Rekursionen in ein relationales Modell umgesetzt?</b>
    - durch die Verwendung von Fremdschlüsseln und Selbstverweisen in Tabellen

- <b>Welche Notationen bietet das ER-Modell?</b>
    - Entitäten
    - Attribute
    - Primärschlüssel
    - Beziehungen
    - Kardinalitäten
    - Schwache Entitäten
    - Beziehungstypen

- <b>Was sind die Unterschiede?</b>
    - ?

## UML Modell und Umsetzung
- <b>Welches Diagramm eignet sich zur Datendarstellung im Datenbankbereich?</b>
    - ER-Diagramm
        - Modellierung von Datenstrukturen
        - Visualisierung von Beziehungen
        - Kommunikation mit Stakeholdern
        - Identifizierung von Anforderungen

- <b>In welche Gruppen werden die Diagramme von UML unterteilt?</b>
    - Strukturdiagramme
        - Klassendiagramme
    - Verhaltensdiagramme
        - Aktivitätsdiagramme
    - Interaktionsdiagramme
        - Sequenzdiagramme

- <b>Nenne Beispiele und Einsatzgebiete für jede Gruppe.</b>
    - Strukturdiagramme
        - Klassendiagramme
            - Modellierung von Datenstrukturen in Softwareanwendugnen, Identifizierung von Klassen und deren Attribute sowie Beziehungen zwischen Klassen
    - Verhaltensdiagramme
        - Aktivitätsdiagramme
            - Verwendung zur Modellierung von Prozessen, Workflows und Geschäftsabläufen, einschließlich der Darstellung von Entscheidungsstrukturen und parallelen Aktivitäten
    - Interaktionsdiagramme
        - Sequenzdiagramme
            - Verwendung zur Modellierung von Interaktionen und Nachrichtenaustausch zwischen Objekten in einer bestimmten Sequenz, häufig für die Analyse von Systemverhalten verwendet

- <b>Was versteht man unter dem Begriff "ORM"?</b>
    - "Object-Relational Mapping" ist ein Konzept, das die Abbildung von objekten in einer objektorientierten Programmiersparche auf relationale Datenbankstrukturen ermöglicht

- <b>Was versteht man unter dem Begriff "impedance mismatch" in Hinblich auf Programmiersprachen und Datenbanken?</b>
    - Problem, das bei der Integration von verschiednen Datebenmodellen oder Programmierparadigmen auftreten kann, insbesondere ziwschen objektorientierten Programmiersprachen und realtionalen Datenbanken

- <b>Wie können Objekte am besten persistent gespeichert werden - geben Sie dazu ein Beispiel.</b>
    - Objekte können am besten persisten gespeichert werden, indem sie in einer relationalen Datenbank gespeichert werden, was mithilfe von ORM Frameworks erfolgen kann
    - Beispiel:
    ```Java
    public class UserDAO {
        private static final String DB_URL = "jdbc:mysql://localhost:3306/example";
        private static final String DB_USER = "username";
        private static final String DB_PASSWORD = "password";

        public void saveUser(User user) {
            try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD)) {
                String sql = "INSERT INTO users (name, age) VALUES (?, ?)";
                try (PreparedStatement stmt = conn.prepareStatement(sql)) {
                    stmt.setString(1, user.getName());
                    stmt.setInt(2, user.getAge());
                    stmt.executeUpdate();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
    ```
- <b>Erläutere die einzelnen Konzepte des Diagramms.</b>
    - ?
- <b>Wie gehe ich bei der Erstellung eines UML-Modells vor.</b>
    1. Anforderugnsanalyse
    2. Identifizierung von Akteuren und Use Cases
    3. Erstellung von Use Case-Diagrammen
    4. Identifizeirung von Klassen und Attributen
    5. Erstellung von Klassendiagrammen
    6. Identifizierung von Interaktionsabläufen
    7. Erstellung von Interaktionsdiagrammen
    8. Überprüfung und Validierung

- <b>Wie werden diese in ein Relationsmodell umgesetzt?</b>
    - Identifizierung von Klassen und Attributen: Die Klassen im UML-Modell werden zu Tabellen in der Datenbank, und die Attribute der Klassen werden zu Spalten in diesen Tabellen. Jede Instanz einer Klasse wird zu einer Zeile in der entsprechenden Tabelle.

    - Festlegung von Primärschlüsseln: Ein Attribut oder eine Kombination von Attributen wird als Primärschlüssel für jede Tabelle festgelegt, um jede Zeile eindeutig zu identifizieren.

    - Festlegung von Fremdschlüsseln: Beziehungen zwischen Klassen im UML-Modell werden zu Beziehungen zwischen Tabellen in der Datenbank. Fremdschlüssel werden verwendet, um die Beziehungen zwischen den Tabellen zu modellieren. Der Fremdschlüssel in einer Tabelle verweist auf den Primärschlüssel einer anderen       Tabelle und stellt so die Beziehung zwischen den beiden Tabellen her.

    - Umsetzung von Assoziationen und Aggregationen: Assoziationen und Aggregationen im UML-Modell werden ebenfalls durch Beziehungen zwischen Tabellen im Relationsmodell dargestellt. Je nach Art der Beziehung werden entsprechende Fremdschlüssel verwendet, um die Beziehung zwischen den beteiligten Tabellen zu        modellieren.

    - Normalisierung: Das Relationsmodell wird normalisiert, um Redundanzen zu reduzieren und die Integrität der Datenbank zu verbessern. Dies kann durch Aufteilen von Tabellen, Kombinieren von Tabellen oder andere Techniken erreicht werden, um die Datenbank in eine effiziente und gut strukturierte Form zu bringen.

    - Erstellung von SQL-Skripten: Basierend auf dem Relationsmodell werden SQL-Skripte erstellt, um die Tabellen, Beziehungen, Indizes und andere Objekte in der Datenbank zu erstellen.

    - Datenbankimplementierung: Die SQL-Skripte werden auf einem Datenbanksystem ausgeführt, um das Datenbankdesign zu implementieren und die Datenbank zu erstellen.
      
- <b>Welche Elemente/Teile des Diagramms werden nicht umgesetzt bzw. gebraucht.</b>
    - Interaktionen und Squenzdiagramme
    - Aktivitätsdiagramme
    - Zustandsdiagramme
- <b>Vergleichen Sie ER- und UML Diagramm.</b>
    - ?
- <b>Welche Vorteile bietet das UML-Modell gegenüber dem ER-Modell?</b>
    - ?
