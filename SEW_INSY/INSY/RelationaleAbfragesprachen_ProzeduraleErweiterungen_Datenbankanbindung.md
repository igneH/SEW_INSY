# 3. Relationale Abfragesprachen, Prozedurale Erweiterungen und Datenbankeanbindung
## SQL und Standards
- Was besagt ANSI SQL92 - halten sich die DB-Anbieter daran?
    - es ist die dritte Version der SQL-Standards, die 1992 von der American National Standards Institue und der International Organization for Standardization veröffentlicht wurde. Dieser Standard definiert eine Riehe von Syntax- und Funktionen, die von RDBMS unterstützt werden sollten
    - die meisten großen Datenbankanbieter wie Oracle, Micorosft SQL Server, MySQL... halten sich im Allgemeinen an den SQL-92-Standard, bieten jedoch auch erweiterte und proprietäre Funktionen, die über den Standard hinausgehen
- Wie sind die relationalen und die Mengenoperatioren in SQL umgesetzt?
    - Relationale Operatoren 
        - Selektionsoperator
            ```SQL
            SELECT * FROM Mitarbeiter WHERE Abteilung = 'Vertrieb';
            ```
        - Projektion
            ```SQL
            SELECT Vorname, Nachname FROM Mitarbeiter;
            ```
        - Karthesisches Produkt
            ```SQL
            SELECT * FROM Tabelle1, Tabelle2;
            ```
        - Theta-Join
            ```SQL
            SELECT * FROM Mitarbeiter M JOIN Abteilung A ON M.AbteilungID = A.ID;
            ```
        - Natural Join
            ```SQL
            SELECT * FROM Mitarbeiter NATURAL JOIN Abteilung;
            ```
    - Mengenoperatoren in SQL
        - Vereinigung
            ```SQL
            SELECT Vorname FROM Mitarbeiter
            UNION
            SELECT Vorname FROM Kunden;
            ```
        - Schnittmenge
            ```SQL
            SELECT Vorname FROM Mitarbeiter
            INTERSECT
            SELECT Vorname FROM Kunden;
            ```
        - Differenz
            ```SQL
            SELECT Vorname FROM Mitarbeiter
            EXCEPT
            SELECT Vorname FROM Kunden;
            ```

- Wie erfolgt die Gruppenverarbeitung in SQL?
    - die `GROUP BY`-Klausel wird verwendet, um Datensätze basierend auf einem oder meheren Spaltenwerten in Gruppen zusammenzufassen
    - Schritte zur Gruppenverarbeitung in SQL
        1. Gruppierung der Daten
            ```SQL
            SELECT Spalte1, Spalte2
            FROM Tabelle
            GROUP BY Spalte1, Spalte2;
            ```
        2. Anwendung von Aggregatfunktionen
            ```SQL
            SELECT Abteilung, COUNT(*)
            FROM Mitarbeiter
            GROUP BY Abteilung;
            ```
        3. Verwendung der `HAVING`-Klausel
            ```SQL
            SELECT Abteilung, COUNT(*)
            FROM Mitarbeiter
            GROUP BY Abteilung
            HAVING COUNT(*) > 10;
            ```
    - tbh keine Ahnung yet lol
- Welche Aggregierungsfunktionen gibt es? (Formulieren Sie ein einfache Beispiel für die Anwendung einer SQL-Funktion bei einer Gruppen-Selektion.)
    - COUNT()
        ```SQL
        SELECT Abteilung, COUNT(*)
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```
    - SUM()
        ```SQL
        SELECT Abteilung, SUM(Gehalt)
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```
    - AVG()
        ```SQL
        SELECT Abteilung, AVG(Gehalt)
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```
    - MAX()
        ```SQL
        SELECT Abteilung, MAX(Gehalt)
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```
    - MIN()
        ```SQL
        SELECT Abteilung, MIN(Gehalt)
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```
    - Beispeil: Ermittlung des minimalen Gehalts pro Abteilung
        ```SQL
        SELECT Abteilung, MIN(Gehalt) AS MinGehalt
        FROM Mitarbeiter
        GROUP BY Abteilung;
        ```

- Was versteht man unter einem Inner-Join, was unter einem Cross/Right/Left/Full-Join?
    - Inner Join
        - gibt nur die Zeilen zurück, bei denen es eine Übereinstimmung in beiden Tabllen gibt
    - Left Join
        - gibt alle Zeilen aus der linken Tabelle zurück, auch wenn keine Übereinstimmung in der rechten Tabelle vorhanden ist
    - Right Join
        - gibt alle Zeilen aus der rechten Tabelle zurück, auch wenn keine übereinstimmung in der linken Tabelle vorhanden ist
    - Full Join
        - git alle Zeilen zurück, wenn es eine Übereinstimmung in einer der beiden Tabelen gibt
    - Cross Join
        - gibt das kartesische Produkt der beiden Tabellen zurück, d.h., jede Zeile der ersten Tabelle wird mit jeder Zeile der zweiten Tabelle kombiniert
    
- Erklären Sie den Begriff "Unterabfrage" ("Subquery") anhand eines Beispiels.
    - eine Unterabfrage ist eine SQL-Abfrage, die innerhalb einer anderen SQL-Abfrage eingebettet ist
    - Beispiel
        ```SQL
        SELECT name
        FROM Mitarbeiter
        WHERE abteilungs_id = (SELECT id FROM Abteilungen WHERE name = 'Vertrieb');
        ```
- Welche Möglichkeiten zur Formulierung von Integritätsbedingungen gibt es in SQL (auf Tabellen- und auf Spaltenebene)?
    - Integritätsbedingungen auf Spaltenebene
        1. NOT NULL
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            name VARCHAR(100) NOT NULL,
            gehalt DECIMAL(10, 2) NOT NULL
            ); 
            ```
        2. UNIQUE
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            email VARCHAR(100) UNIQUE
            );
            ```
        3. PRIMARY KEY
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            name VARCHAR(100) NOT NULL
            );
            ```
        4. CHECK
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            gehalt DECIMAL(10, 2),
            CHECK (gehalt >= 0)
            );
            ```
        5. DEFAULT
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            status VARCHAR(20) DEFAULT 'aktiv'
            );
            ```
    - Integritätsbedingungen auf Tabellenebene
        1. PRIMARY KEY
            ```SQL
            CREATE TABLE Abteilung (
            abteilungs_id INT,
            mitarbeiter_id INT,
            PRIMARY KEY (abteilungs_id, mitarbeiter_id)
            );
            ```
        2. UNIQUE
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            vorname VARCHAR(100),
            nachname VARCHAR(100),
            UNIQUE (vorname, nachname)
            );
            ```
        3. FOREIGN KEY
            ```SQL
            CREATE TABLE Abteilung (
            id INT PRIMARY KEY,
            name VARCHAR(100)
            );

            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            name VARCHAR(100),
            abteilungs_id INT,
            FOREIGN KEY (abteilungs_id) REFERENCES Abteilung(id)
            );
            ```
        4. CHECK
            ```SQL
            CREATE TABLE Mitarbeiter (
            id INT PRIMARY KEY,
            gehalt DECIMAL(10, 2),
            abteilungs_id INT,
            CHECK (gehalt >= 0 AND abteilungs_id IS NOT NULL)
            );
            ```
- Was versteht man unter "Constraints"?
    - der Begriff "Constraints" bezieht sich auf Regeln oder Einschränkungen, die auf die Datenbankspalten oder Tabellen agewendet werden, um die Integrität und Konsistenz der Daten sicherzustellen
    - Constraints verhinder ungültige Daten und helfen, die Genauigkeit und Zuverlässigkeit der Informationen innerhalb der Datenbank aufrechtzuerhalten
- Geben Sie ein Beispiel für eine Constraint.
    - Angenommen, wir haben eine Tabelle Mitarbeiter, die Informationen über die Mitarbeiter eines Unternehmens speichert. Wir möchten sicherstellen, dass die Tabelle folgende Regeln erfüllt:

        - Jede Zeile hat eine eindeutige Mitarbeiter-ID (PRIMARY KEY).
        - Der Name des Mitarbeiters darf nicht NULL sein (NOT NULL).
        - Die E-Mail-Adresse muss eindeutig sein (UNIQUE).
        - Das Gehalt darf nicht negativ sein (CHECK).
        - Der Einstellungsstatus hat einen Standardwert von 'aktiv' (DEFAULT).
    - Jede Zeile hat eine Abteilungs-ID, die auf eine existierende Abteilung verweist (FOREIGN KEY).
        ```SQL
        CREATE TABLE Abteilungen (
        abteilungs_id INT PRIMARY KEY,
        name VARCHAR(100) NOT NULL
        );

        CREATE TABLE Mitarbeiter (
        mitarbeiter_id INT PRIMARY KEY,                       -- PRIMARY KEY Constraint
        name VARCHAR(100) NOT NULL,                           -- NOT NULL Constraint
        email VARCHAR(100) UNIQUE,                            -- UNIQUE Constraint
        gehalt DECIMAL(10, 2) CHECK (gehalt >= 0),            -- CHECK Constraint
        einstellungsstatus VARCHAR(20) DEFAULT 'aktiv',       -- DEFAULT Constraint
        abteilungs_id INT,
        FOREIGN KEY (abteilungs_id) REFERENCES Abteilungen(abteilungs_id)  -- FOREIGN KEY Constraint
        );
        ```

- Wie wirken sich Constraints aus?
    - großen Einfluss auf die Datenintegrität, Konsistenz und Qualität
- Wo kann man Constraints festlegen bzw. einsehen (DDL/DML/DCL)?
    - ?
- Welche Funktionen bietet SQL an (Beispiele) und wie können diese in Abfragen integriert werden?
    - Aggregatfunktionen
        - SUM
            ```SQL
            SELECT SUM(column) FROM TableName;
            ```
        - AVG
            ```SQL
            SELECT AVG(column) FROM TableName;
            ```
        - COUNT
            ```SQL
            SELECT COUNT(*) FROM TableName;
            ```
        - MAX
            ```SQL
            SELECT MAX(column) FROM TableName;
            ```
        - MIN
            ```SQL
            SELECT MIN(column) FROM TableName;
            ```
    - Stringfunktionen
        - CONCAT
            ```SQL
            SELECT CONCAT(column1, column2) FROM TableName;
            ```
        - UPPER/LOWER
            ```SQL
            SELECT CONCAT(column1, column2) FROM TableName;
            ```
        - SUBSTRING
            ```SQL
            SELECT CONCAT(column1, column2) FROM TableName;
            ```
    - Datum- und Zeitfunktionen
        - NOW
            ```SQL
            SELECT NOW();
            ```
        - DATEADD
            ```SQL
            SELECT DATEADD(day, 7, column) FROM TableName;
            ```
        - DATEDIFF
            ```SQL
            SELECT DATEDIFF(day, column1, column2) FROM TableName;
            ```
    - Logische Funktionen
        - IF/ELSE
            ```SQL
            SELECT IF(condition, value_if_true, value_if_false) FROM TableName;
            ```
        - CASE
            ```SQL
            SELECT CASE WHEN condition1 THEN value1
                        WHEN condition2 THEN value2
                        ELSE defaultValue END
            FROM TableName;
            ```

- Welche Beziehungen (Kardinalitäten!) können unmittelbar mit Hilfe von SQL und den Integritätsbedungen in einem relationalem DBMS umgesetzt werden?
    - ?

- Bei welchen ist eine Zusatzprogrammierung erforderlich?
    - ?

- Was versteht man unter einer Transaktion?
    - Eine Transaktion ist eine Abfolge von Datenbankoperationen, die als eine Einheit ausgefürht werden. Sie stellen sicher, dasss entweder alle Operationen einer Transaktion erfolgreich abgeschlossen werden (Commit) oder im Fehlerfall keine Operationen der Transaktion dauerhaft wirksam werden (Rollback)
    - Eigenschaften von Transaktionen werden durch das ACID-Prinzip beschrieben
        1. Atomicity (Atomarität)
            - Eine Transaktion ist eine unteilabre Einheit
            - Entweder werden alle Operationen der Transaktion vollständig ausgeführt, oder keine
        2. Consistency (Konsistenz)
            - Eine Transaktion fürht die Datenbank von einem konsistenten Zustand in einen anderen konsistenten Zustand
        3. Isoaltion
            - Die Operationen innerhalb einer Transaktion sind von den Operationen anderer Transaktionen isoliert
            - Zwischenergebnisse einer laufenden Transaktion sind für anderen Transaktionen nicht sichtbar
        4. Durability (Dauerhaftigkeit)
            - nach Abschluss einer Trasnaktion (Commit) sind die Änderungen dauerhaft in der Datenbank gespeichert, selbst im Falle eines Systemabsturzes
    - Beispiel
    ```SQL
    BEGIN TRANSACTION;

    -- Betrag vom ersten Konto abbuchen
    UPDATE accounts
    SET balance = balance - 100
    WHERE account_id = 1;

    -- Ein Fehler tritt auf, z.B. das Konto hat nicht genügend Guthaben
    IF (error) THEN
        ROLLBACK;
    END IF;

    -- Betrag dem zweiten Konto gutschreiben
    UPDATE accounts
    SET balance = balance + 100
    WHERE account_id = 2;

    COMMIT;
    ```

## Views und Indizes
- Was sind Views?
    - Views sind virtuelle tabellen in einem Datenbanksystem, die aus einer Abfrage definiert werden
    - Sie stellen eine bestimmte Sicht (View) auf die Daten in einer oder mehreren Tabellen dar, ohne dass die Daten tatsächlich dupliziert werden
- Eigenschaften und Vorteile.
    - Eigenschaften
        - vitruelle Tabellen
            - Views enthalten keine eigenen Daten, sondern beziehen ihre Daten dynamisch aus den Tabellen
        - Abhängig von Basisdaten
            - Änderungen in den Tabellen spiegeln sich sofort in der View wieder
        - Keine Datenreplikation
            - kein zusätzlicher Speicherplatz für die Daten View benötigt
        - Flexibilität
            - Views können komplexe Abfragen kapseln, die Daten aus mehreren Tabellen kombinieren, aggregieren oder filtern
    - Vorteile
        - Datenabstraktion
            - Views bieten eine Abstraktionsebene über den tatsächlichen Daten, worduch Benutzer eine vereinfachte und spezifische Sicht auf die Daten erhalten, ohne die zugrunde liegende Struktur kennen zu müssen
        - Datenintegrität
            - Views können verwendet werden, um konsistente und valide Datenansichten zu gewährleisten, insbesondere bei der Präsentation von berechneten Felder oder aggregierten Daten
        - Einfache Wartun
            - Änderungen an der Struktur der zugrunde liegenden Tabellen können durch Anpassung der Views verdeckt werden, ohne dass alle darauf aufbauenden Abfragen angepasst werden müssen
        - Wiederverwendbarkeit
            - Einmal definierte Views können in verschienden Abfragen und Anwendungen wiederverwendet werden, was die Konsistenz und Warbarkeit des Codes erhöht
- Wie erstelle ich eine View?
    ```SQL
    CREATE VIEW view_name AS
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition;
    ```
- Wie bestimme ich die Ausführungsart?
    - ?
- Erkläre MERGE, Alter View, Updatebale Views mit Beispiel
    - MERGE
        - ein SQL-Befehl, der verwendet wird, um eine Tabelle basierend auf den Daten in einer anderen Tabelle zu aktualisieren oder einzufügen
        - Beispiel
            ```SQL
            -- Tabelle Employees
            CREATE TABLE Employees (
                EmployeeID INT PRIMARY KEY,
                Name VARCHAR(50),
                Department VARCHAR(50),
                Salary DECIMAL(10, 2)
            );

            -- Tabelle EmployeeUpdates
            CREATE TABLE EmployeeUpdates (
                EmployeeID INT,
                Name VARCHAR(50),
                Department VARCHAR(50),
                Salary DECIMAL(10, 2)
            );

            -- MERGE-Befehl
            MERGE INTO Employees AS target
            USING EmployeeUpdates AS source
            ON target.EmployeeID = source.EmployeeID
            WHEN MATCHED THEN
                UPDATE SET target.Name = source.Name,
                        target.Department = source.Department,
                        target.Salary = source.Salary
            WHEN NOT MATCHED BY TARGET THEN
                INSERT (EmployeeID, Name, Department, Salary)
                VALUES (source.EmployeeID, source.Name, source.Department, source.Salary);
            ```
    - Alter View
        - wird verwendet, um eine bestehende View zu ändern
        - Beispiel
            ```SQL
            -- Ursprüngliche View erstellen
            CREATE VIEW EmployeeView AS
            SELECT EmployeeID, Name, Department
            FROM Employees;

            -- View ändern
            ALTER VIEW EmployeeView AS
            SELECT EmployeeID, Name, Department, Salary
            FROM Employees;
            ```
    - Updateable Views
        - eine View, die es erlaubt, Daten über die View zu ändern
        ```SQL
            -- View erstellen
            CREATE VIEW EmployeeView AS
            SELECT EmployeeID, Name, Department, Salary
            FROM Employees;

            -- Daten über die View aktualisieren
            UPDATE EmployeeView
            SET Salary = Salary * 1.1
            WHERE Department = 'Sales';

            -- Daten über die View einfügen
            INSERT INTO EmployeeView (EmployeeID, Name, Department, Salary)
            VALUES (4, 'John Doe', 'Marketing', 60000);

            -- Daten über die View löschen
            DELETE FROM EmployeeView
            WHERE EmployeeID = 4;
        ```
- Erkläre die WITH CHECK OPTION clause mit Beispiel.
    - die `WITH CHECK OPTION` Klausel in SQL wird verwendet, um sicherzustelln, dass alle Daten, die über eine View eingefügt oder aktualisiert werden, die Bedingungen der View erfüllen
    - Beispiel
        - Angenommen, wir haben eine Tabelle namens Employees, die Informationen über Mitarbeiter enthält. Wir erstellen eine View namens SalesEmployeesView, die nur Mitarbeiter aus der Vertriebsabteilung (Sales) anzeigt.
        1. Ertstellen der `Employees` Tabelle
            ```SQL
            CREATE TABLE Employees (
                EmployeeID INT PRIMARY KEY,
                Name VARCHAR(50),
                Department VARCHAR(50),
                Salary DECIMAL(10, 2)
            );

            -- Daten in die Tabelle einfügen
            INSERT INTO Employees (EmployeeID, Name, Department, Salary)
            VALUES
            (1, 'Alice', 'Sales', 50000),
            (2, 'Bob', 'HR', 45000),
            (3, 'Charlie', 'Sales', 55000);
            ```
        2. Erstellen der `SalesEmployeesView` View mit `WITH CHECK OPTION`
            ```SQL
            CREATE VIEW SalesEmployeesView AS
            SELECT EmployeeID, Name, Department, Salary
            FROM Employees
            WHERE Department = 'Sales'
            WITH CHECK OPTION;
            ```
- Was sind Indizes?
    - spezielle Datensturkturen, die in Datenbanken verwendet werden, um den schnellen Zugriff auf Datensätzen in einer Tabelle zu ermöglichen
- Wie erstellt man einen Index?
    ```SQL
    CREATE INDEX index_name ON table_name(column_name);
    ```

- Wie werden sie gespeichert?
    - Balanced Trees
    - Hash-Tabellen
    - Bitmap-Indizes
    - Skiplisten

- Beispiel: Composite Index, Descending Index, Invisible Indices, Use force Index.
    - ?

## Prozedurale Erweiterung von SQL-Datenbanken
- Was versteht man unter "Prozedurale Erweiterung" einer SQL-Datenbank?
    - es bezieht sich auf die Fähigkeit, prozedurale Programmierung innerhalb der Datenbank selbst zu implementieren
        - das ermöglicht es, komplexe Geschäftslogik, Datenmanipulationen und andere Aufgaben direkt innerhalb der Datenbank auszuführen, anstatt sie in seperaten Anwendungscode außerhalb der Datenbank zu implementieren
- Wer hat PL/SQL eingeführt?
    - Oracle Corporation (1991)
- Charakterisieren Sie die Syntax von PL/SQL.
    - Mischung aus SQL und prozdeuralen Programmierkonstrukten
        - Blockstruktur
            - Deklarationsteil
            - Ausführungsteil
            - Ausnahmebehandlungsteil
        - Datentypen
            - Skalare Datentypen
            - Komplexe Datentypen
            - Referenzdatentypen
        - Kontrollstruktur
            - Bedingte Anweisungen
            - Schleifen
        - Cursor
        - ...
- Wo werden diese gespeichert und welche Vor- bzw. Nachteile hat PL/SQL?
    - wdym mit wo werden diese gespeichert?
    - Vorteile
        - Integration mit SQL
        - Leistungsoptimierung
        - Blockstruktur
        - Exception Handling
    - Nachteile
        - Plattformabhängig
        - Lernkurve
        - Komplexität bei großen Anwendungen
        - Performance-Überlegungen
            - schlecht geschriebene PL/SQL-Prozeduren und -Funktionen Performance probleme verursachen

- Inwieweit ist es sinnvoll, die sogenannte "Business Logik" - also Funktionalität von Geschäftsobjekten - in den PL/SQL-Raum zu verlagern?
    - Die Verlagerung der Business-Logik in den PL/SQL-Raum kann erhebliche Vorteile in Bezug auf Performance, Konsistenz, Sicherheit und zentrale Verwaltung bieten
    - Allerdings bringt sie auch Herausforderungen wie Plattformabhängigkeit, komplexe Wartung und mögliche Skalierungsprobleme mit sich.

- Welche Konsequenzen ergeben sich damit auf den Software-Lifecycle?
    - Die Verlagerung erfordert sorgfältige Planung, spezialisierte Ressource, erweiterte Test- und Deplyoment-Strategien sowie kontinuierliche Überwachung und Warteung

- Kann eine JDBC-Anwendung eine PL/pgSQL-Funktion nutzen; wenn ja: wie wird eine Nutzung ausschauen?
    - ?

- Was versteht man unter einer View?
    - eine View ist eine virutelle Tabelle
    - sie repräsentiert eine gespeicherte Abfrage, deren Ergebnis als Tabelle dargestellt wird
    - View speichert keine Daten sondert bietet eine dynamische Ansicht

- Welche Operationen können darauf ausgeführt werden?
    - SELECT
    - INSERT
    - UPDATE
    - DELETE

- Welche Befehle stehen für das Einfügen/Updaten von Daten unter SQL zur Verfügung?
    - INSERT
    - UPDATE
    - DELETE
    - MERGE

- Grenzen sie Trigger, Stored Procedures und Functions voneinander ab.
    - Trigger: Automatisch durch Datenbankereignisse ausgelöst, verwendet für Datenintegrität und Automatisierung.
    - Stored Procedures: Manuell aufgerufen, kann komplexe Logik und mehrere Parameter enthalten, gibt keine Werte zurück (kann aber OUT-Parameter verwenden).
    - Functions: Manuell aufgerufen oder innerhalb von SQL-Anweisungen verwendet, muss einen Wert zurückgeben, verwendet für Berechnungen und Transformationen.
- Welche unterschiedlichen Parameter gibt es und wie können diese verwendet werden.
    - IN-Parameter: Übergeben Eingabewerte an Prozeduren oder Funktionen.
    - OUT-Parameter: Geben Werte von Prozeduren oder Funktionen zurück.
    - INOUT-Parameter: Dienen sowohl als Eingabe- als auch als Ausgabeparameter.
- Was ist der Unterschied zwischen PreparedStatement, Stored Procedures und Stored Function?
    - PreparedStatement ist eine vorab kompilierte SQL-Anweisung auf Anwendungsebene.
    - Stored Procedures und Stored Functions sind gespeicherte SQL-Anweisungen auf Datenbankebene.
    - Stored Procedures können komplexe Aufgaben ausführen und müssen nicht unbedingt einen Wert zurückgeben.
    - Stored Functions geben einen Wert zurück und können in SQL-Abfragen direkt verwendet werden.
    - PreparedStatement wird häufig zur Verbesserung der Leistung und Sicherheit bei der Ausführung wiederholter Abfragen verwendet, während Stored Procedures und Stored Functions zur Modularisierung von Datenbanklogik und zur Wiederverwendung von Abfragen verwendet werden.
- Wie kann aus einer objektorientierten Sprache wie Java PL/SQL genutzt werden (Beispiel)?
    ```SQL
    import java.sql.*;

    public class Main {
        public static void main(String[] args) {
            try {
                // Verbindung zur Datenbank herstellen
                Connection conn = DriverManager.getConnection("jdbc:oracle:thin:@//localhost:1521/xe", "username", "password");

                // SQL-Anweisung mit PL/SQL-Prozedur aufrufen
                String sql = "{ call update_employee_salary(?, ?) }";

                // PreparedStatement erstellen
                CallableStatement stmt = conn.prepareCall(sql);

                // Werte für die Parameter setzen
                stmt.setInt(1, 123); // Mitarbeiter-ID
                stmt.setDouble(2, 50000.0); // Neues Gehalt

                // Prozedur ausführen
                stmt.execute();

                // Verbindung schließen
                stmt.close();
                conn.close();
                
                System.out.println("PL/SQL-Prozedur erfolgreich aufgerufen.");
            } catch (SQLException e) {
                System.err.println("Fehler beim Aufrufen der PL/SQL-Prozedur: " + e.getMessage());
            }
        }
    }
    ```
- Was ist ein Cursor (wofür wird dieser eingestzt, wie schaut die Struktur aus)?
    - ein Cursor ist ein Konsturkt, das es ermöglicht, eine Menge von Zeilen in einem Ergebnisdatensatz schrittweise zu druchlaufen
    - er wird häufig verwendet, wenn eine Anwendung auf zeilenbasierte Operationen wie Lesen, Aktualisieren oder Löschen von Daten zugreifen muss
    - Struktur eines Cursors:
        1. Öffnen des Cursors
        2. Durchlaufen des Ergenisdatensatzes
        3. Verarbeiten der Datenzeilen
        4. Schließen des Cursors

- Welche einsetzbaren Tool gibt es?
    - ?

- Gibt es Debugger für PL/SQL (Oracle/MySQL/Postgres/MariaDB/..).
    - Oracle: PL/SQL Debugger
    - MySQL: MySQL Debugger
    - PostgreSQL: pqAdmin
    - MariaDB: integriete Debugger-Funktionalität in der MariaDB Workbench

- Was versteht man unter SQL-Injection und wie kann man sich davor schützen?
    - SQL-Injection ist eine Angriffstechnik, bei der ein Angreifer bösartigen SQL-Code in eine Anwendungsanfrage einschleust, der dann von der zugrunde liegenden Datenbank asugefürht wird
    - Sicherheitspraktiken
        - Verwendung von parametrisierten Abfragen
        - Validieren und bereinigen der Benutzereingaben
        - Begrenzung der Datenbankberechtigungen
        - Verwendung von Sicherheitsmechanismen auf Anwendungsebene

## Anbindungsmöglichkeiten einer Datenbank (JDBC, JPA)
- Was ist JDBC?
    - "Java Database Connectivity" ist eine Java-API für den Zugriff auf Datenbanken

- Vorteile von der Verwendung von JDBC.
    - Plattformunabhängig
    - Standardisierte API
    - einfache Integration

- Welche JDBC-Architekturen gibt es?
    - Zwei-Schichten-Architektur
    - Drei-Schichten-Architektur
    - Vier-Schichten-Architektur

- Welche wird hauptsächlich verwendet?
    - Drei-Schichten-Architektur

- Grundaufbau der Anbindung an eine Datenbank in Java mit JDBC.
    1. Importieren der JDBC-Pakete
        ```Java
        import java.sql.Connection;
        import java.sql.DriverManager;
        import java.sql.SQLException;
        import java.sql.Statement;
        import java.sql.ResultSet;
        ```
    2. Laden des JDBC-Treibers
        ```Java
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");  // Beispiel für MySQL
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
        ```
    3. Herstellen der Verbindung zur Datenbank
        ```Java
        String url = "jdbc:mysql://localhost:3306/meineDatenbank";  // URL für die Datenbank
        String user = "root";  // Benutzername für die Datenbank
        String password = "passwort";  // Passwort für die Datenbank

        Connection connection = null;

        try {
            connection = DriverManager.getConnection(url, user, password);
            System.out.println("Verbindung erfolgreich!");
        } catch (SQLException e) {
            e.printStackTrace();
        }
        ```
    4. Erstellen eines Statements
        ```Java
        Statement statement = null;
        try {
            statement = connection.createStatement();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        ```
    5. Ausführen einer SQL-Abfrage
        ```Java
        String query = "SELECT * FROM meineTabelle";
        ResultSet resultSet = null;

        try {
            resultSet = statement.executeQuery(query);
        } catch (SQLException e) {
            e.printStackTrace();
        }
        ```
    6. Verarbeiten des Ergebnisses
        ```Java
        try {
            while (resultSet.next()) {
                int id = resultSet.getInt("id");
                String name = resultSet.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        ```
    7. Schließen der Ressourcen
        ```Java
        try {
            if (resultSet != null) resultSet.close();
            if (statement != null) statement.close();
            if (connection != null) connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        ```

- Web-Anwendung und JDBC.
    - ?

- Wo werden die Connectiondaten abgelegt?
    - in einer properties file

- Wie wird diese aufgebaut?
    - eine properties file ist eine einfache Textdatei, die Schlüssel-Wert-Paare zur Konfiguration einer Anwendung enthält
    ```properties
    db.url=jdbc:mysql://localhost:3306/meineDatenbank
    db.user=root
    db.password=passwort
    db.driver=com.mysql.cj.jdbc.Driver
    ```

- Was sind Alternativen zu JDBC?
    - JPA
    - Hibernate
    - Spring Data JPA

- Erläutern Sie den Aufbau einer JPA Anwendung, Was brauche ich dafür?
    - Maven oder Gradle
    - Entity-Klassen
    - persistence.xml
    - Repository-Klassen für Datenzugriff

- Was ist automatisiert, was muss ich modellieren?
    - ?
    
- Wo liegen die Herausforderungen?
    - ?