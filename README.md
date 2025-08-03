# Catalog API

[![Go Version](https://img.shields.io/badge/go-1.23.0-blue.svg)](https://golang.org)
[![Architecture](https://img.shields.io/badge/architecture-Clean%20Architecture-green.svg)](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
[![DDD](https://img.shields.io/badge/design-Domain%20Driven-orange.svg)](https://martinfowler.com/tags/domain%20driven%20design.html)
[![Status](https://img.shields.io/badge/status-In%20Development-yellow.svg)]()

A product catalog microservice built with Go, implementing Clean Architecture and Domain-Driven Design principles for the go-labs platform.

## 🏗️ Architecture

**Domain:** Catalog  
**Business Capability:** Product management, Category hierarchy, Price management  
**Microservice Pattern:** DDD with Clean Architecture

## Aggregates
- **Product**: Product information, pricing, and availability
- **Category**: Product categorization with hierarchical structure

## Repository Structure
```
catalog-api/
├── cmd/                    # Service entry points
│   ├── api/               # REST API server
│   ├── worker/            # Background workers (price updates, etc.)
│   └── migrate/           # Database migrations
├── internal/              # Service implementation
│   ├── domain/            # Domain models and business logic
│   ├── application/       # Use cases and orchestration
│   ├── infrastructure/    # External integrations
│   └── interfaces/        # API handlers and adapters
├── api/                   # Service contracts
│   ├── openapi/           # REST API specifications
│   ├── events/            # Domain event schemas
│   └── grpc/              # gRPC definitions (future)
├── database/              # Service data store
│   ├── migrations/        # Database schema migrations
│   ├── seeds/             # Test/demo data
│   └── schema.sql         # Current schema documentation
├── configs/               # Service configuration
│   ├── base.yaml          # Base configuration template
│   ├── development.yaml   # Development overrides
│   └── production.yaml    # Production overrides (template)
├── build/                 # Service build artifacts
│   ├── Dockerfile         # Multi-stage Docker build
│   ├── Makefile           # Build automation
│   └── ci.yaml            # CI/CD pipeline definition
├── tests/                 # Service tests
│   ├── unit/              # Unit tests
│   ├── integration/       # Integration tests
│   └── e2e/               # End-to-end tests
└── docs/                  # Service documentation
    ├── architecture.md    # Architecture decisions
    ├── api.md             # API documentation
    └── runbook.md         # Operations guide
```

## Domain Events (Planned)
- `ProductCreated`
- `ProductUpdated`
- `ProductDeleted`
- `PriceChanged`
- `CategoryCreated`
- `CategoryUpdated`
- `CategoryDeleted`

## API Endpoints (Planned)
- **POST** `/api/v1/categories` - Create category
- **GET** `/api/v1/categories/{id}` - Get category with products
- **PUT** `/api/v1/categories/{id}` - Update category
- **DELETE** `/api/v1/categories/{id}` - Delete category
- **GET** `/api/v1/categories` - List categories (hierarchical)
- **POST** `/api/v1/products` - Create product
- **GET** `/api/v1/products/{id}` - Get product
- **PUT** `/api/v1/products/{id}` - Update product
- **DELETE** `/api/v1/products/{id}` - Delete product
- **GET** `/api/v1/products` - Search products with filtering

## Business Rules
- Products must belong to a category
- Categories can have hierarchical parent-child relationships
- Cannot delete category that contains products
- Product SKU must be unique
- Product price must be positive

## Technology Stack
- **Language:** Go
- **Database:** PostgreSQL (catalog schema)
- **API:** REST with Gin framework
- **Migration:** golang-migrate
- **Testing:** Go standard testing + testify
- **Containerization:** Docker multi-stage builds

## Integration Points
- **Order Service**: Provides product information for orders
- **Inventory Service**: Syncs product availability (future)
- **Search Service**: Provides product search capabilities (future)

## Development Status
- [x] Repository structure created
- [ ] Domain models implementation
- [ ] API handlers implementation
- [ ] Database migrations
- [ ] Unit tests
- [ ] Integration tests
- [ ] Docker build
- [ ] CI/CD pipeline

## Getting Started
*To be implemented*

## Contributing
*To be implemented*

---

**Part of**: [gjaminon-go-labs](https://github.com/gjaminon-go-labs) - A comprehensive Go microservices showcase  
**Status**: In Development - Domain models and API implementation in progress