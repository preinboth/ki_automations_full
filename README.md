# KI-Automatisierungsplattform für Coolify

Eine umfassende Docker-basierte Automatisierungsplattform, speziell für die Deployment-Plattform Coolify optimiert. Das Projekt integriert n8n, verschiedene Datenbanken und KI-Komponenten in einer Coolify-kompatiblen Umgebung.

![n8n.io - Screenshot](assets/n8n-demo.gif)

## Komponenten

### Hauptkomponenten

- **n8n**: Workflow-Automatisierungsplattform (Latest Version)
  - Basic Authentication aktiviert
  - PostgreSQL als Datenbank
  - Qdrant-Integration für KI-Funktionen
- **Qdrant**: Vektordatenbank für KI-Anwendungen (v1.11.3)
  - Persistente Datenspeicherung
  - API-Key Authentifizierung
  - HTTP/HTTPS-Routing mit SSL/TLS
- **MongoDB**: Dokumentenorientierte Datenbank (Version 7)
  - Root-Benutzer-Authentifizierung
  - TCP-Routing für sichere Verbindungen
- **PostgreSQL**: Relationale Datenbank für n8n und Basisdaten (Version 15)
  - Separate Instanzen für n8n und Basisdaten
  - Persistente Datenspeicherung
- **Supabase Studio**: Web-basierte Datenbankverwaltung
  - Verbunden mit Basisdatenbank
  - SSL/TLS geschützt
- **Adminer**: Datenbank-Management-Tool
  - Universeller Datenbankzugriff
  - SSL/TLS geschützt
- **NocoDB**: Moderne Datenbank-UI (Latest Version)
  - JWT-Authentifizierung
  - PostgreSQL-Backend
  - SSL/TLS geschützt
- **Redis**: In-Memory-Datenbank (Version 7)
  - Passwortschutz
  - Persistente Datenspeicherung
  - Alpine-basiertes Image
- **Redis Commander**: Redis-UI (Latest Version)
  - Passwortgeschützter Zugriff
  - SSL/TLS geschützt
  - Echtzeit-Monitoring

### Coolify-Integration

- Optimierte Traefik-Labels für Coolify-Routing
- Automatische SSL/TLS-Konfiguration durch Coolify
- Integrierte Domain-Verwaltung
- Automatische Container-Orchestrierung

### Netzwerk & Routing

- Traefik als Reverse Proxy (durch Coolify verwaltet)
- Separate Hostnamen für alle Dienste
- TCP-Routing für MongoDB
- HTTP/HTTPS-Routing für Web-Dienste
- Automatische HTTP zu HTTPS Weiterleitung

## Voraussetzungen

- Coolify-Installation
- Docker und Docker Compose
- Domain-Konfiguration in Coolify für die verschiedenen Dienste
- Ausreichend Speicherplatz für Docker Volumes
- Netzwerk-Zugriff für alle konfigurierten Domains

## Installation in Coolify

1. Erstellen Sie ein neues Projekt in Coolify
2. Verbinden Sie dieses Git-Repository
3. Kopieren Sie die Umgebungsvariablen-Vorlage:

   ```bash
   cp env.example .env
   ```

4. Konfigurieren Sie in Coolify:
   - Setzen Sie die Umgebungsvariablen
   - Konfigurieren Sie die Domains für jeden Dienst
   - Aktivieren Sie SSL/TLS für alle Dienste
   - Stellen Sie sicher, dass alle erforderlichen Ports verfügbar sind

5. Deployen Sie das Projekt in Coolify

## Dienste und Zugriff

Alle Dienste sind über Coolify verwaltete Domains erreichbar:

- **n8n**: `https://${N8N_HOST}`
  - Basic Authentication erforderlich
  - Workflow-Editor und Automatisierung
- **Adminer**: `https://${ADMINER_HOST}`
  - Datenbank-Management
  - Unterstützt alle Datenbanken
- **Supabase Studio**: `https://${BASEDATA_SUPABASE_STUDIO_HOST}`
  - Basisdatenbank-Verwaltung
  - SQL-Editor und Tabellenverwaltung
- **MongoDB**: `mongodb://${MONGO_HOST}:27017`
  - Authentifizierung erforderlich
  - TCP-Verbindung
- **NocoDB**: `https://${NOCODB_HOST}`
  - JWT-Authentifizierung
  - Moderne Datenbank-UI
- **Redis Commander**: `https://${REDIS_UI_HOST}`
  - Passwortgeschützter Zugriff
  - Redis-Monitoring

## Datenpersistenz

Alle Daten werden in Coolify-gemanagten Docker-Volumes gespeichert:

- `n8n_storage`: n8n Workflows und Konfiguration
- `n8n_postgres_storage`: n8n Datenbank
- `basedata_db_data`: Basisdatenbank
- `qdrant_storage`: Vektordatenbank
- `mongo_data`: MongoDB Daten
- `nocodb_db_data`: NocoDB Datenbank
- `redis_data`: Redis Daten

## Sicherheit

- Basic Authentication für n8n
- Separate Benutzer und Passwörter für alle Dienste
- Umgebungsvariablen für sensible Daten
- Automatische SSL/TLS-Konfiguration durch Coolify
- Traefik für sicheres Routing
- MongoDB Root-Benutzer-Authentifizierung
- Qdrant API-Key Authentifizierung
- NocoDB JWT-Authentifizierung
- Redis Passwortschutz

## Zusätzliche Funktionen

### n8n Import (Optional)

Das Projekt enthält eine auskommentierte Import-Funktion für n8n, die folgende Möglichkeiten bietet:

- Import von Credentials
- Import von Workflows

Um diese Funktion zu nutzen, müssen Sie:

1. Die entsprechenden Abschnitte in der docker-compose.yaml auskommentieren
2. Die zu importierenden Daten im `./import` Verzeichnis platzieren
3. Sicherstellen, dass die Daten im korrekten Format vorliegen

## Systemkonfiguration

- Zeitzone: Europe/Berlin
- Automatischer Neustart für alle Container
- Optimierte Container-Orchestrierung durch Coolify
- Persistente Datenspeicherung in Docker Volumes
- Automatische SSL/TLS-Konfiguration
- HTTP zu HTTPS Weiterleitung

## Coolify-spezifische Vorteile

- Automatische Container-Orchestrierung
- Einfaches Deployment und Rollback
- Integrierte Monitoring-Funktionen
- Automatische SSL/TLS-Verwaltung
- Einfache Skalierung der Dienste
- Zentralisierte Log-Verwaltung
- Automatische Backup-Möglichkeiten

## Lizenz

Siehe [LICENSE](LICENSE) Datei für Details.
