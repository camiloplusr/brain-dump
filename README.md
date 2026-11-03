# Python Project — Calculator

Proyecto Python básico con pipeline de CI/CD en CircleCI.

## Estructura

```
python-project/
├── .circleci/
│   └── config.yml        # Pipeline de CircleCI
├── src/
│   └── calculator/
│       ├── __init__.py
│       └── calculator.py # Lógica principal
├── tests/
│   ├── __init__.py
│   └── test_calculator.py
├── requirements.txt
├── setup.py
├── pyproject.toml
└── README.md
```

## Instalación local

```bash
pip install -r requirements.txt
```

## Ejecutar tests

```bash
pytest
```

## Lint

```bash
black --check src/ tests/
flake8 src/ tests/
```

## Pipeline (CircleCI)

El workflow `ci-pipeline` ejecuta 4 etapas en orden:

| Etapa     | Qué hace                                        | Se ejecuta en         |
|-----------|------------------------------------------------|----------------------|
| `install` | Instala dependencias y persiste el workspace   | Todas las ramas      |
| `lint`    | `black --check` + `flake8`                     | Todas las ramas      |
| `test`    | `pytest` con reporte de cobertura              | Todas las ramas      |
| `build`   | Genera wheel y sdist con `python -m build`     | `main` y `develop`   |
