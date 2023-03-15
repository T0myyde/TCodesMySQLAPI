# TCodesMySQLAPI

Die MySQL-API ermöglicht es Ihnen, eine Verbindung zu einer MySQL-Datenbank herzustellen und Abfragen auszuführen. Die API wurde in Java geschrieben und verwendet die offizielle MySQL JDBC-Treiberbibliothek.

Installation
Die MySQL-API ist eine Java-Bibliothek, die Sie in Ihr Projekt integrieren können. Hier sind die Schritte, um die API in Ihr Projekt einzubinden:

- Laden Sie die MySQL-JDBC-Treiberbibliothek von der offiziellen Website von MySQL herunter.
- Fügen Sie die heruntergeladene Bibliothek zu Ihrem Projekt hinzu.
- Laden Sie die MySQL-API von GitHub herunter.
- Fügen Sie die MySQL-API zu Ihrem Projekt hinzu.

## Verwendung
Um die MySQL-API in Ihrem Projekt zu verwenden, müssen Sie sie instanziieren und eine Verbindung zur Datenbank herstellen. Hier ist ein Beispiel, wie das gemacht wird:

```
String host = "localhost";
String database = "mydatabase";
String username = "myusername";
String password = "mypassword";
String redisHost = "localhost";
int redisPort = 6379;

TCodesMySQLAPI api = new TCodesMySQLAPI(host, database, username, password, redisHost, redisPort);
api.connect();
```

Sie müssen die Variablen host, database, username und password entsprechend Ihrem MySQL-Server konfigurieren. Wenn Sie auch Redis-Caching verwenden möchten, geben Sie die Host- und Port-Informationen für Ihren Redis-Server an.
Nachdem Sie eine Verbindung hergestellt haben, können Sie Abfragen an die Datenbank senden. Hier sind einige Beispiele:

```
// INSERT-Anweisung ausführen
String sql = "INSERT INTO users (name, email) VALUES ('John Doe', 'johndoe@example.com')";
int rowsAffected = api.executeUpdate(sql);

// SELECT-Anweisung ausführen
sql = "SELECT * FROM users";
ResultSet resultSet = api.executeQuery(sql);
String resultSetString = api.createStringFromResultSet(resultSet);
System.out.println(resultSetString);
```
Sie können auch Tabellen in der Datenbank erstellen und löschen:
```
// Tabelle erstellen
String tableName = "users";
String columns = "id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(255), email VARCHAR(255)";
api.createTable(tableName, columns);

// Tabelle löschen
api.dropTable(tableName);
```

Nachdem Sie mit der Datenbank interagiert haben, müssen Sie die Verbindung schließen:
```
api.disconnect();
```
## API-Referenz
```
public TCodesMySQLAPI(String host, String database, String username, String password, String redisHost, int redisPort)
```
Erstellt eine neue Instanz der MySQL-API mit den angegebenen Verbindungsdaten.

- host: Der Hostname des MySQL-Servers.
- database: Der Name der Datenbank.
- username: Der Benutzername für die Verbindung.
- password: Das Passwort für die Verbindung.
- redisHost: Der Hostname des Redis-Servers (optional).
- redisPort: Der Port des Redis-Servers (optional).

## Fehlerbehandlung
Die MySQL-API kann während des Betriebs verschiedene Arten von Fehlern auslösen. Einige der häufigsten Fehler sind:

- SQLException: Wird ausgelöst, wenn es ein Problem mit der SQL-Anweisung gibt, die ausgeführt werden soll.

- ClassNotFoundException: Wird ausgelöst, wenn der JDBC-Treiber nicht gefunden werden kann.

- IOException: Wird ausgelöst, wenn ein Problem beim Lesen oder Schreiben von Daten auftritt.

- Exception: Wird ausgelöst, wenn ein nicht spezifizierter Fehler auftritt.

Sie können diese Fehler abfangen und entsprechend darauf reagieren, indem Sie try-catch-Blöcke verwenden.

## Zusammenfassung
Die MySQL-API ist eine Java-Bibliothek, die es Ihnen ermöglicht, eine Verbindung zu einer MySQL-Datenbank herzustellen und Abfragen auszuführen. Sie wurde mit der offiziellen MySQL JDBC-Treiberbibliothek geschrieben und bietet eine Reihe von Methoden, um Tabellen zu erstellen und zu löschen, Abfragen auszuführen und die Ergebnisse in lesbare Strings umzuwandeln. Die API kann auch mit Redis-Caching erweitert werden, um die Leistung zu verbessern.
