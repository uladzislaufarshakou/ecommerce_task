
# Tips
## I suggest such project structure:
```
/
│
├── .env <-- Stores environment variables (DB_USER, DB_PASS, etc.)
├── .gitignore <-- Tells Git to ignore /data, /reports, .env, __pycache__
├── data_generator.py <-- Script to create source data
├── docker-compose.yml
├── main.py <-- The main executable script
├── pyproject.toml <-- Project definition, dependencies (for uv)
├── README.md <-- Project documentation
├── data/ <-- Source data (git-ignored)
├── reports/ <-- Output reports (git-ignored)
├── sql/ <-- SQL scripts
│   └── init.sql <-- Database initialization script(runned in docker container)
├── tests/ <-- Package for all tests
│   ├── __init__.py
│   ├── conftest.py <-- Pytest fixtures (e.g., sample dataframes)
│   └── test_sales_transformer.py <-- Unit tests for the transformation logic
│
└── pipeline/ <-- The main Python source code package
    ├── __init__.py
    ├── config.py <-- Pydantic Settings class (loads .env)
    ├── main_pipeline.py <-- The orchestrator class (Facade pattern)
    │
    ├── extractors/ <-- "Extractor" Component Package
    │   ├── __init__.py <-- Exposes concrete classes
    │   ├── interfaces.py <-- Defines the "Extractor" contracts
    │   ├── db_extractor.py <-- Implements IEnrichmentExtractor
    │   └── file_extractor.py <-- Implements IEventsExtractor
    │
    ├── transformers/ <-- "Transformer" Component Package
    │   ├── __init__.py
    │   ├── interfaces.py <-- Defines the "Transformer" contract
    │   └── sales_transformer.py <-- Implements ITransformer
    │
    ├── loaders/ <-- "Loader" Component Package
    │   ├── __init__.py
    │   ├── interfaces.py <-- Defines the "Loader" contract
    │   └── file_loader.py <-- Implements ILoader
    │
    └── utils/ <-- Shared, non-core utilities
        ├── __init__.py
        ├── db_connection.py <-- Database Connection Context Manager
        └── logging_setup.py <-- Logging configuration
```
## Other Recomendations:
- I recommend to write docstrings in reST(restructured text) format.
- I recommend to create interfaces for all parts, it guarantees widenable code.
- Change .gitignore yourself.
- You can suggest and use your own structure, but try to understand why this one is good.
- Try to do as much as possible without AI help, you will develop your skills better.
- Setup imports correctly, if you don't know how to use __init__.py, watch the YouTube guide before you start working on this project.
- Use OOP code style to write understandable code.
- Use SOLID patterns to guarantee easy support in future.
- You can also use separate packages "interfaces" for each component, it won't be a mistake.
- Use this command if you are planning to make your own repo:
```bash
git clone <repo link> --depth=1
# It ensures you won't clone .git folder, won't face any issues with it.
```
