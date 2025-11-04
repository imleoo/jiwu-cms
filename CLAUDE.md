# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Running the Application
- `go run main.go` - Start the CMS application (runs on port from PORT env var)
- `make run` - Start the application using Makefile
- `./spurtcms.sh start` - Start as systemd service (requires sudo)
- `./spurtcms.sh stop` - Stop systemd service (requires sudo)

### Building
- `make build` - Build binary for Linux (CGO_ENABLED=0, GOOS=linux, GOARCH=amd64)
- `make buildwithview` - Build with view templates and assets included
- `go build -o spurtcms-admin` - Basic build

### Testing
- `go test` - Run all tests
- `go test ./...` - Run tests recursively
- Specific test: `go test -run TestSetupRouting`

### Deployment
- `make permission` - Set permissions (777) on spurtcms-admin binary
- `make start` - Start systemd service (requires sudo)

## Architecture Overview

### Multi-Service Architecture
SpurtCMS runs three concurrent services using goroutines:
1. **Admin Panel** - Main CMS administration interface (default port 8082)
2. **Template View** - Website preview service (port 8083)
3. **GraphQL Server** - API service (port 8084)

### Core Components

#### Database Layer
- **GORM ORM** with support for PostgreSQL and MySQL
- **Database configuration** in `config/dbconfig.go`
- **Migration system** with auto-migration and default value insertion
- **Environment-based** database selection via `DATABASE_TYPE` env var

#### Modular Package System
The CMS uses external SpurtCMS packages for core functionality:
- `github.com/spurtcms/auth` - Authentication
- `github.com/spurtcms/categories` - Category management
- `github.com/spurtcms/channels` - Content channels
- `github.com/spurtcms/member` - Member management
- `github.com/spurtcms/team` - Team/role management
- `github.com/spurtcms/forms-builders` - Form builders
- And others for specific CMS features

#### Storage System
Multi-cloud storage support via `storage-controller`:
- **Local filesystem** storage
- **AWS S3** integration
- **Azure Blob** storage
- **Google Drive** integration

#### Route Structure
- **Admin routes** under `/admin/` prefix with full CRUD operations
- **API routes** for GraphQL, file uploads, and external integrations
- **Public routes** for website front-end (template-based)
- **Middleware stack** including JWT auth, CSRF protection, CORS

### Key Directories

- `controllers/` - HTTP handlers for all CMS modules
- `models/` - GORM data models and database structures
- `graphql/` - GraphQL schema, resolvers, and server setup
- `middleware/` - Authentication, CSRF, CORS middleware
- `migration/` - Database migration files (separate MySQL/PostgreSQL)
- `routes/` - HTTP route definitions and setup
- `websites/` - Website front-end controller and routes
- `page-view/` - Template rendering service for website preview
- `storage-controller/` - Multi-cloud storage implementations
- `lang/` - Internationalization and translation support

### Configuration

#### Environment Variables (.env)
- **Database**: `DATABASE_TYPE`, `DB_HOST`, `DB_PORT`, `DB_USERNAME`, `DB_PASSWORD`, `DB_NAME`
- **Security**: `ACCESS_SECRET`, `JWT_SECRET`, `CSRF_SECRET`, various session keys
- **AWS S3**: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_DEFAULT_REGION`, `AWS_BUCKET_NAME`
- **Ports**: `PORT` (admin panel), template view and GraphQL use fixed ports

#### Authentication & Authorization
- **JWT-based authentication** with configurable secrets
- **Session management** using cookie-based sessions
- **Role-based access control** with member groups and permissions
- **Content access control** for restricting content to specific member groups

### Frontend Integration
- **HTML template system** with Go templates
- **Static asset serving** from `/public`, `/storage`, `/locales`
- **Multi-language support** with translation files
- **RESTful APIs** for dynamic content loading
- **GraphQL API** for modern frontend integrations

## Default Credentials
- Username: `Admin`
- Password: `Admin@123`
- Admin panel: `http://localhost:PORT/admin`

## Important Notes
- Application requires PostgreSQL or MySQL database
- AWS S3 configuration needed for file storage features
- SystemD service file (`spurtcms.service`) should be created for production deployment
- All three services (admin, template view, GraphQL) run concurrently