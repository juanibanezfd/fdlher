# fdlher

A Data Lakehouse beased Framework for Renewable energies (FDLHER)

Folder Structure

```
/fdlher
├── /backend
│   ├── /api
│   │   ├── /controllers           # Lógica de controle (ex.: ingestão, APIs REST)
│   │   ├── /models                # Modelos de dados (ex.: structs Go para Campaign, Equipment)
│   │   ├── /services              # Lógica de negócios e infraestrutura auxiliar
│   │   │   ├── /db                # Serviço de banco de dados
│   │   │   │   ├── /migration     # Migrations do Go (ex.: golang-migrate)
│   │   │   │   ├── /query         # Arquivos gerados pelo sqlc
│   │   │   │   ├── /sql           # Scripts SQL brutos
│   │   │   │   └── init.sql       # Script de inicialização TimescaleDB
│   │   ├── /routes                # Definição de rotas HTTP (ex.: Gin)
│   │   ├── /middleware            # Middlewares (ex.: autenticação, logging básico)
│   │   ├── /config                # Configurações (ex.: conexão DB)
│   │   ├── /docs                  # Documentação Swagger (ex.: swagger.yaml, UI gerada)
│   │   ├── /tests                 # Testes unitários (ex.: testify para Go)
│   │   ├── main.go                # Ponto de entrada da API
│   │   ├── go.mod                 # Dependências Go
│   │   └── go.sum

│   ├── /data-services             # Serviços de dados e pipelines ETL
│   │   ├── /controllers           # Controle de pipelines (ex.: FastAPI ou scripts Python)
│   │   ├── /models                # Modelos de dados (ex.: Pydantic)
│   │   ├── /services              # Lógica de transformação (ex.: Spark, Airflow)
│   │   ├── /scripts               # Scripts de processamento
│   │   │   ├── lidar_parser.py
│   │   │   ├── sodar_parser.py
│   │   │   └── generic_parser.py
│   │   ├── /dags                  # Arquivos DAG do Airflow
│   │   │   └── ingestion_dag.py
│   │   ├── /audit                 # Logs específicos de pipelines
│   │   │   └── pipeline_log.py
│   │   ├── /tests                 # Testes com pytest
│   │   ├── requirements.txt
│   │   └── main.py

│   ├── /audit                     # Módulo central de auditoria
│   │   ├── /models
│   │   ├── /services
│   │   ├── /repository
│   │   ├── /config
│   │   ├── /tests
│   │   └── audit.go

│   └── docker-compose.yml         # Orquestração (API, data-services, DB, etc.)

├── /frontend
│   ├── /pages
│   │   ├── /dashboard
│   │   ├── /data-management
│   │   │   ├── /ingestion
│   │   │   ├── /transformation
│   │   │   └── /export
│   │   ├── /data-visualization
│   │   │   ├── /time-series
│   │   │   ├── /profiles
│   │   │   └── /maps
│   │   ├── /ai-insights
│   │   │   ├── /predictions
│   │   │   ├── /synthetic-data
│   │   │   └── /model-management
│   │   ├── /campaigns
│   │   │   ├── /overview
│   │   │   ├── /analysis
│   │   │   └── /validation
│   │   │       └── equipment_validation.js
│   │   ├── /reports
│   │   │   ├── /summary
│   │   │   ├── /detailed
│   │   │   └── /export-pdf
│   │   ├── /settings
│   │   │   ├── /user-profile
│   │   │   ├── /data-layers
│   │   │   └── /integrations
│   │   ├── /admin
│   │   │   ├── /users
│   │   │   ├── /logs
│   │   │   └── /system-health
│   │   └── /api
│   │       ├── /data
│   │       ├── /ai
│   │       └── /campaigns
│   ├── /components
│   ├── /models
│   ├── /utils
│   ├── /public
│   ├── /tests
│   │   ├── /audit
│   │   └── test_dashboard.js
│   ├── Dockerfile
│   ├── next.config.js
│   ├── package.json
│   └── tsconfig.json

├── /ai
│   ├── /models
│   │   ├── /trained
│   │   └── /prototypes
│   ├── /training
│   │   ├── /datasets
│   │   │   ├── /lidar_a
│   │   │   ├── /lidar_b
│   │   │   └── /sodar
│   │   └── /scripts
│   ├── /inference
│   │   └── predict.py
│   ├── /audit
│   │   └── training_log.py
│   ├── /tests
│   ├── Dockerfile
│   └── requirements.txt

├── /data
│   ├── /bronze
│   │   ├── /campaign_1
│   │   │   ├── /lidar_a
│   │   │   ├── /lidar_b
│   │   └── /campaign_2
│   │       ├── /sodar
│   ├── /silver
│   │   ├── /campaign_1
│   │   ├── /campaign_2
│   ├── /gold
│   │   ├── /campaign_1
│   │   ├── /campaign_2
│   └── /metadata
│       ├── /campaigns
│       │   ├── campaign_1.json
│       │   └── campaign_2.json
│       ├── /equipment
│       │   ├── lidar_a.json
│       │   ├── lidar_b.json
│       │   └── sodar.json
│       └── data_log.txt

├── /infra
│   ├── /docker
│   │   ├── /db
│   │   └── .env
│   ├── /docs
│   │   ├── /architecture
│   │   ├── user_manual.md
│   │   └── dev_guide.md
│   ├── /ci-cd
│   │   └── github-actions.yml
│   │   └── audit_build.yml
│   └── Dockerfile.base

├── /tests
│   ├── /unit
│   ├── /integration
│   └── /e2e
│       └── audit_e2e.js

├── /docs
│   ├── README.md
│   └── CHANGELOG.md

├── .editorconfig
├── .env.development
├── .eslintrc.json
├── .gitignore
├── .nvmrc
├── .prettierrc
├── LICENSE
└── Makefile

```
