# fdlher
A Data Lakehouse beased Framework

Folder Structure

/fdlher
├── /backend
│   ├── /api
│   │   ├── /controllers           # Lógica de controle (ex.: ingestão, APIs REST)
│   │   ├── /models                # Modelos de dados (ex.: structs Go para Campaign, Equipment)
│   │   ├── /services              # Lógica de negócios (ex.: integração de dados heterogêneos)
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
│   │   │   ├── /lidar_parser.py   # Parser específico para LIDAR
│   │   │   ├── /sodar_parser.py   # Parser específico para SODAR
│   │   │   └── /generic_parser.py # Parser genérico
│   │   ├── /dags                  # Arquivos DAG do Airflow
│   │   │   └── ingestion_dag.py   # Orquestração de pipelines
│   │   ├── /audit                 # Logs específicos de pipelines (ex.: status ETL por campanha/equipamento)
│   │   │   └── pipeline_log.py    # Registro de execuções
│   │   ├── /tests                 # Testes (ex.: pytest para Python)
│   │   ├── requirements.txt       # Dependências Python
│   │   └── main.py                # Ponto de entrada (se aplicável)
│   ├── /db
│   │   ├── /migration             # Migrations do Go (ex.: golang-migrate)
│   │   ├── /query                 # Arquivos gerados pelo sqlc
│   │   └── /sql                   # Scripts SQL brutos
│   │   └── init.sql               # Script de inicialização TimescaleDB
│   ├── /audit                     # Módulo central de auditoria
│   │   ├── /models                # Modelos de eventos de auditoria (ex.: structs Go)
│   │   ├── /services              # Lógica de registro e consulta de logs
│   │   ├── /repository            # Acesso ao banco de dados para logs
│   │   ├── /config                # Configurações de auditoria
│   │   ├── /tests                 # Testes de auditoria
│   │   └── audit.go               # Ponto de entrada ou utilitário principal
│   └── docker-compose.yml         # Orquestração de serviços (API, data-services, DB, etc.)
├── /frontend
│   ├── /pages
│   │   ├── /dashboard              # Painel principal com visão geral
│   │   ├── /data-management        # Gerenciamento de dados
│   │   │   ├── /ingestion          # Upload e monitoramento por campanha/equipamento
│   │   │   ├── /transformation     # Transformação de dados
│   │   │   └── /export             # Exportação de dados
│   │   ├── /data-visualization     # Visualização de dados
│   │   │   ├── /time-series        # Séries temporais (filtradas por equipamento)
│   │   │   ├── /profiles           # Perfis energéticos (comparação entre modelos)
│   │   │   └── /maps               # Mapas geográficos
│   │   ├── /ai-insights            # Análise e predições de IA
│   │   │   ├── /predictions        # Predições energéticas
│   │   │   ├── /synthetic-data     # Dados sintéticos
│   │   │   └── /model-management   # Gerenciamento de modelos
│   │   ├── /campaigns              # Gerenciamento de campanhas
│   │   │   ├── /overview           # Visão geral (lista de campanhas)
│   │   │   ├── /analysis           # Análise detalhada (por equipamento)
│   │   │   └── /validation         # Validação científica
│   │   │       └── equipment_validation.js # Validação por equipamento
│   │   ├── /reports                # Geração de relatórios
│   │   │   ├── /summary            # Resumos
│   │   │   ├── /detailed           # Detalhes técnicos (por campanha/equipamento)
│   │   │   └── /export-pdf         # Exportação para PDF
│   │   ├── /settings               # Configurações
│   │   │   ├── /user-profile       # Perfil do usuário
│   │   │   ├── /data-layers        # Seleção de camadas
│   │   │   └── /integrations       # Integrações externas
│   │   ├── /admin                  # Painel administrativo
│   │   │   ├── /users              # Gerenciamento de usuários
│   │   │   ├── /logs               # Visualização de logs de auditoria
│   │   │   └── /system-health      # Saúde do sistema
│   │   └── /api                    # Rotas internas
│   │       ├── /data               # Endpoints de dados
│   │       ├── /ai                 # Endpoints de IA
│   │       └── /campaigns          # Endpoints de campanhas
│   ├── /components                 # Componentes reutilizáveis (ex.: gráficos, modais)
│   ├── /models                     # Modelos de dados frontend (TypeScript)
│   ├── /utils                      # Funções utilitárias
│   ├── /public                     # Arquivos estáticos
│   ├── /tests                      # Testes
│   │   ├── /audit                  # Testes de visualização de logs
│   │   └── test_dashboard.js       # Outros testes
│   ├── Dockerfile                  # Build da imagem Docker
│   ├── next.config.js              # Configuração Next.js
│   ├── package.json                # Dependências
│   └── tsconfig.json               # Configuração TypeScript
├── /ai
│   ├── /models                     # Modelos de IA
│   │   ├── /trained                # Modelos treinados
│   │   └── /prototypes             # Modelos em desenvolvimento
│   ├── /training                   # Scripts e datasets para treinamento
│   │   ├── /datasets               # Dados de treinamento (organizados por equipamento)
│   │   │   ├── /lidar_a            # Dados de LIDAR modelo A
│   │   │   ├── /lidar_b            # Dados de LIDAR modelo B
│   │   │   └── /sodar              # Dados de SODAR
│   │   └── /scripts                # Scripts de treinamento
│   ├── /inference                  # Lógica de inferência
│   │   └── predict.py              # Script de inferência
│   ├── /audit                      # Logs de treinamento e inferência
│   │   └── training_log.py         # Registro de eventos de IA por equipamento
│   ├── /tests                      # Testes de modelos
│   ├── Dockerfile                  # Build da imagem Docker
│   └── requirements.txt            # Dependências específicas
├── /data
│   ├── /bronze                     # Dados brutos
│   │   ├── /campaign_1             # Dados de campanha 1
│   │   │   ├── /lidar_a            # Dados de LIDAR modelo A
│   │   │   ├── /lidar_b            # Dados de LIDAR modelo B
│   │   └── /campaign_2             # Dados de campanha 2
│   │       ├── /sodar              # Dados de SODAR
│   ├── /silver                     # Dados padronizados
│   │   ├── /campaign_1             # Dados padronizados de campanha 1
│   │   ├── /campaign_2             # Dados padronizados de campanha 2
│   ├── /gold                       # Dados prontos
│   │   ├── /campaign_1             # Dados prontos de campanha 1
│   │   ├── /campaign_2             # Dados prontos de campanha 2
│   └── /metadata                   # Metadados e logs
│       ├── /campaigns              # Metadados por campanha
│       │   ├── /campaign_1.json    # Metadados (ex.: equipamentos usados)
│       │   └── /campaign_2.json    # Metadados
│       ├── /equipment              # Metadados por equipamento
│       │   ├── /lidar_a.json       # Especificações do modelo A
│       │   ├── /lidar_b.json       # Especificações do modelo B
│       │   └── /sodar.json         # Especificações do SODAR
│       └── /data_log.txt           # Registro de mudanças nos dados
├── /infra
│   ├── /docker
│   │   ├── /db                     # Configurações de banco de dados
│   │   └── .env                    # Variáveis de ambiente
│   ├── /docs
│   │   ├── /architecture           # Diagramas (ex.: fluxo de dados)
│   │   ├── /user_manual.md         # Manual do usuário
│   │   └── /dev_guide.md           # Guia de desenvolvimento
│   ├── /ci-cd
│   │   └── github-actions.yml      # Configuração CI/CD
│   │       └── audit_build.yml     # Registro de builds
│   └── Dockerfile.base             # Imagem base
├── /tests
│   ├── /unit                       # Testes unitários globais
│   ├── /integration                # Testes de integração (ex.: upload, transformação)
│   └── /e2e                        # Testes end-to-end
│       └── audit_e2e.js            # Testes de auditoria end-to-end
├── /docs
│   ├── README.md                   # Documentação geral
│   └── CHANGELOG.md                # Registro de mudanças
├── .editorconfig                   # Configuração de estilo
├── .env.development                # Variáveis de ambiente
├── .eslintrc.json                  # Configuração ESLint
├── .gitignore                      # Arquivos ignorados
├── .nvmrc                          # Versão Node.js
├── .prettierrc                     # Configuração Prettier
├── LICENSE                         # Licença
└── Makefile                        # Comandos úteis (ex.: build, test, migrate)
