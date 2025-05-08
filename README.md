# KI-Automatisierungsplattform für Coolify

Eine umfassende Docker-basierte Automatisierungsplattform, speziell für die Deployment-Plattform Coolify optimiert. Das Projekt integriert n8n, verschiedene Datenbanken und KI-Komponenten in einer Coolify-kompatiblen Umgebung.

![n8n.io - Screenshot](assets/n8n-demo.gif)

## Komponenten

### Hauptkomponenten

- **n8n**: Workflow-Automatisierungsplattform
- **Qdrant**: Vektordatenbank für KI-Anwendungen
- **MongoDB**: Dokumentenorientierte Datenbank
- **PostgreSQL**: Relationale Datenbank für n8n und Basisdaten
- **Supabase Studio**: Web-basierte Datenbankverwaltung
- **Adminer**: Datenbank-Management-Tool

### Coolify-Integration

- Optimierte Traefik-Labels für Coolify-Routing
- Automatische SSL/TLS-Konfiguration durch Coolify
- Integrierte Domain-Verwaltung
- Automatische Container-Orchestrierung

### Netzwerk & Routing

- Traefik als Reverse Proxy (durch Coolify verwaltet)
- Separate Hostnamen für alle Dienste
- TCP-Routing für MongoDB
- HTTP-Routing für Web-Dienste

## Voraussetzungen

- Coolify-Installation
- Docker und Docker Compose
- Domain-Konfiguration in Coolify für die verschiedenen Dienste

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

5. Deployen Sie das Projekt in Coolify

## Dienste und Zugriff

Alle Dienste sind über Coolify verwaltete Domains erreichbar:

- **n8n**: `https://${N8N_HOST}`
- **Adminer**: `https://${ADMINER_HOST}`
- **Supabase Studio**: `https://${BASEDATA_SUPABASE_STUDIO_HOST}`
- **MongoDB**: `mongodb://${MONGO_HOST}:27017`

## Datenpersistenz

Alle Daten werden in Coolify-gemanagten Docker-Volumes gespeichert:

- `n8n_storage`: n8n Workflows und Konfiguration
- `n8n_postgres_storage`: n8n Datenbank
- `basedata_db_data`: Basisdatenbank
- `qdrant_storage`: Vektordatenbank
- `mongo_data`: MongoDB Daten

## Sicherheit

- Basic Authentication für n8n
- Separate Benutzer und Passwörter für alle Dienste
- Umgebungsvariablen für sensible Daten
- Automatische SSL/TLS-Konfiguration durch Coolify
- Traefik für sicheres Routing

## Coolify-spezifische Vorteile

- Automatische Container-Orchestrierung
- Einfaches Deployment und Rollback
- Integrierte Monitoring-Funktionen
- Automatische SSL/TLS-Verwaltung
- Einfache Skalierung der Dienste

## Lizenz

Siehe [LICENSE](LICENSE) Datei für Details.
