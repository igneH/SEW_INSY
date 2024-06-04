# 4. NoSQL-Datenbanken und Anwendungen
## NoSQL Datenbanken
- Was bedeutet No-SQL
    - "Not Only SQL"
- Eigenschaften
    - Flexibles Schema
        - Datenstrukturen ohne feste Schema-Definition gespeichert
    - Horizontale Skalierbarkeit
        - mehrere Server hinweg skalieren können
    - Verteilte Architektur
        - Daten auf mehreren DServern zu speichern und zu replizieren
    - Unterschiedliche Datenmodelle
        - Dokumentendatenbanken
        - Key-Value-Datenbanken
        - Spaltenorientierte Datenbanken
        - Graphdatenbanken
    - Hohe Leistung für spezielle Anwendungsfälle

- Einteilungen mit Beispielen
    - ?

- Vergleich
    - ?

- Einsatzmöglichkeiten
    - ?

- CAP Theorem
    - ist ein fundermentales Konzept in der Informatik, insbesondere im Bereich verteilter Datenbanksysteme
    - es besagt, dass ein verteiltes Datenbanksystem nicht gleichzeitig die drei folgenden Eigenschafte vollständig erfüllen kann
        1. Consistency: Alle Knoten im System sehen dieselben Daten zur gleichen Zeit
        2. Availability: Jeder Request erhält eine Antwort, auch wenn einige Konten im System ausfallen
        3. Partion Tolerance: Das System funktioniert weiter, auch wenn eine Netzwerkpartion auftritt
    - Praktische Anwendung
        - CA: traditionelle Datenbanken
        - CP: NoSQL-Datenbanken wie HBase
        - AP: NoSQL-Datenbanken wie Cassandra oder DynamoDB

- ACID und BASE im Vergleich
    - ACID
        - Atomicity: Transaktion ist eine unteilbare Einheit, entweder vollständig ausgeführt oder gar nicht
        - Consistency: Transaktionen bringt die Datenbank von einem konsistenten Zustand in einen anderen konsistenten Zustand
        - Isoaltion: Transaktionen beeinflussen sich nicht gegenseitig
        - Durability: sobald eine Transaktion abgeschlossen ist, sind ihre Änderungen dauerhaft, selbst im Falle eines Systemausfalls
    - BASE
        - Basically Available: System garantiert Verfügbarkeit der Daten, auch wenn in einem inkonsistenten Zustand
        - Soft state: aufgrund der eventual consistency kann sich der Zustand des Systems im Laufe der Zeit ändern
        - Eventual consistency: System garantiert, dass die Daten schließlich konsistent werden, auch wenn sie für eine gewisse Zeit inkonsistent sein können
    - Vergleich
        - Konsistenz vs. Verfügbarkeit
            - ACID: Priorisiert Konsistenz und Datenintegrität
            - BASE: Priorisiert Verfügbarkeit und Partitionstoleranz
        - Transaktionen
            - ACID: Unterstützt komplexe Transaktionen mit mehreren Operationen, die alle atomar ausgeführt werden müssen
            - BASE: Unterstützt einfache, schnelle Operationen und akzeptiert, dass Änderungen allmählich propagiert werden, bis Konsistenz erreicht ist
        - Anwendungsszenarien
            - ACID: Banken, Buchhaltung, Bestandsverwaltung, wo Genauigkeit und Konsistenz von größter Bedeutung sind
            - BASE: Große verteilte Systemem, wie Content-Delivery-Networks- Web-basierte Applikationen, wo Geschwindigkeit und Verfügbarkeit wichitger sind als sofortige Konsistenz

- Erklären Sie MAP/Reduce und den Einsatz
    - ein Programmiermodell zur Verarbietung und Generierung großer Datenmengen
    - Einsatz
        - Datenverarbeitung und -analyse
        - Indexing und Suche
        - Maschinelles Lernen
        - ETL-Prozesse
- MongoDB als NoSQL Beispiel & Eigenschaften
- CRUD Operationen im Überblick

## MongoDB
- Grundaufbau MongoDB
- Vergleich MongoDB und RDBMS
- Was ändert sich bei der Modellierung?
- Was sind Aggreate im Zusammenhang mit der Modellierung?
- Wie funktioniert die Umsetzung von Beziheungen?
- Was ist Replication?
- Wie läuft sie ab?
- Was ist Sharding?
- Wie erfolgt die Auswahl eines Sharding Keys?

## Servlets: Grundstruktur und DB-Anbindung
- Kommunikationsablauf bei Java Servlets: 
    - Reihenfolge, 
    - beteiligte Klassen mit Funktionen, 
    - beteiligte "Dateitypen" mit Beschreibung, 
    - Lebenszyklus eines Java Servlets, 
    - Was ist ein Deployment Descriptor?
    - Wie wird r verwendet?
    - Kann der Deployment Descriptor ersetzt werden?
    - Wie kann ich die Bearbeitung auf mehrere Servlet aufteilen?
    - Wie verarbeite ich Benutzereingaben in einer HTML-Seite?
    - Welche Konsequenzen hat die Multithreading-Eigenschaft eines Servelet (wer kümmert sich um die Ressourcen, start/stop des Threads)?
    - Was verstht man unter einem "Redirect", wie kann dies via Servelts realisiert werdne und wozu setzt man dies ein?
    - Wie kann ein Servlet parametisiert werden und wie werden Ressourcen (z.B. DB-COnnection) angefordert bzw. wieder frei gegeben?
    - Wie können Annotations eingesetzt werden (Beispiel)?
    - Wozu braucht man bei Servelt einen Kontext?
    - Wodurch unterscheidet sich ein Servelt und ein normales Java-Programm?
    - Können Servelts parametisiert werden - Beispiele.
    - Aufbau einer URL für den Aufruf eines Servelts (Beispiel).
    - Vorteile/Nachteile von Servlets gegenüber anderen Web-Frameworks?

## Servlets: Session Tracking und DB-Anbindung
- Session tracking, Möglichkeiten, Servlet API
- Überblick Session Variablen (implizite Objekte), Request Dispatcher, Mehtoden, Redirect, Synchronisieren oder nicht?
- Cookies:
    - Definition
    - Eigenschaften
    - Lebensdauer
    - Erzeugen
    - Löschen
    - Sicherheit
    - Was sind Filter und wie verwendet man sie?
    - Was sind Listener und wie verwendet man sie?
    - Wie realiseirt man eine Datenbankanbindung mit Servlets?
    - Was kann man dabei optimieren (Anzahl der DB-Connections)?