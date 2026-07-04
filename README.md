CloudOps Goal Tracker - Three-Tier Architecture
This project demonstrates a modern three-tier architecture:

Presentation Layer (Frontend): Node.js/Express server serving a JavaScript frontend
Business Logic Layer (Backend): Go API service
Data Layer: PostgreSQL database
Architecture Overview
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│     Frontend    │     │     Backend     │     │    Database     │
│    (Node.js)    │────▶│      (Go)       │────▶│   (PostgreSQL)  │
│   Port: 3000    │     │   Port: 8080    │     │    Port: 5432   │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                 
Local Deployment using Docker Compose:
Prerequisites:
Docker (version 20.10+)
Docker Compose (version 2.0+)

Step 1: Go to the docker-local-deployment directory
cd docker-local-deployment

Step 2: Copy paste the below command to run the application
docker-compose up -d

Step 3: Access the application
Frontend: http://localhost:3000
Backend API: http://localhost:8080
Database: http://localhost:5432 (use pgAdmin or any other client to connect )

Terraform File Structure:

infra/
├── main.tf                 # Root configuration file
├── variables.tf            # Input variables for the root module
├── outputs.tf              # Output values after deployment
├── providers.tf            # Provider configurations
├── backend.tf              # Remote state configuration
├── modules/                # All modular components
│   ├── networking/         # VNet, subnets, NSGs, Bastion
│   ├── compute/            # VM Scale Sets and load balancers
│   ├── database/           # PostgreSQL Flexible Server
│   ├── dns/                # Private DNS Zones
│   └── keyvault/           # Azure Key Vault
└── environments/           # Environment-specific configurations
    └── prod/               # Production environment
