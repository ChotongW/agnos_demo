# Agnos Demo Service

A secure, hospital-isolated patient management service built with Go, Gin, PostgreSQL, and Nginx.

## 🚀 Quick Start

The easiest way to run the application is using Docker Compose.

### Prerequisites
*   [Docker](https://www.docker.com/) & Docker Compose
*   Make (optional, for convenience commands)

### Running the Application

1.  **Clone the repository**
    ```bash
    git clone https://github.com/ChotongW/agnos_demon.git
    cd agnos_demo
    ```

2.  **Start the services**
    ```bash
    docker-compose up -d --build
    ```
    This will start:
    *   **PostgreSQL** (Database)
    *   **Migrate** (Applies database schema changes)
    *   **App** (Go API Service, internal port 8080)
    *   **Nginx** (Reverse Proxy, exposed on port 80)

3.  **Verify it's running**
    Visit `http://localhost/health` in your browser or use curl:
    ```bash
    curl http://localhost/health
    ```
    You should see `{"status":"OK"}`.

## 📚 Documentation

*   **[API Specification](docs/API_SPEC.md)**: Detailed endpoint definitions.
*   **[API Examples](API_EXAMPLES.md)**: Curl commands for testing common scenarios.
*   **[Architecture](docs/ARCHITECTURE.md)**: System design and project structure.
*   **[Database Schema](docs/ER_DIAGRAM.mmd)**: Entity-Relationship diagram.

## 🧪 Testing

To run the unit tests (requires Go installed locally):

```bash
go test ./... -cover
```

For more details on testing, see **[TESTING.md](TESTING.md)**.

## 🛠 Development

### Project Structure
See **[docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)** for a detailed breakdown of the project layout.

### Database Migrations
Migrations are handled automatically on startup. To manage them manually:
```bash
# Create a new migration
make migrate-create name=my_migration

# Run migrations manually (if running locally without Docker)
go run cmd/migrate.go up
```
See **[MIGRATIONS.md](MIGRATIONS.md)** for more details.

## 🔒 Security Features

*   **JWT Authentication**: Secure access to all patient endpoints.
*   **Hospital Isolation**: Strict data access control based on staff's hospital assignment.
*   **Nginx Reverse Proxy**: The application server is not directly exposed to the internet.
