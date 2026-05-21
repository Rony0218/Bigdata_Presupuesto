# 📊 BigData — Gestión Presupuestal 

> Proyecto académico de Big Data que modela la evolución de un sistema de gestión presupuestal institucional: desde Excel/Power Query hasta una arquitectura medallion en Databricks con una aplicación web multiusuario.

---

## 🎯 Objetivo

Demostrar cómo una lógica financiera construida en Power Query y Power Pivot puede migrarse a una plataforma de datos moderna, reproducible y auditable, usando Python, Databricks y una arquitectura medallion (Bronze → Silver → Gold).

---

## 📁 Estructura del repositorio

```
Bigdata_Presupuesto/
└── notebooks/
    ├── presentacion_bigdata_uniban.ipynb               # Presentación ejecutiva del proyecto
    ├── documento_tecnico_presupuesto_databricks.ipynb  # Anexo técnico detallado
    └── assets/
        ├── arquitectura_bigdata.svg                    # Diagrama de arquitectura general
        ├── pipeline_medallion.svg                      # Flujo Bronze → Silver → Gold
        └── app_mvp.svg                                 # Diagrama del MVP web
```

---

## 📓 Notebooks

### 1. `presentacion_bigdata_uniban.ipynb`
Presentación principal del proyecto, orientada a exponer la propuesta de valor académica y operacional:

- Resumen ejecutivo del modelo original vs. solución moderna
- Contexto del problema y fuentes de información integradas
- Arquitectura general de la solución
- Pipeline medallion con descripción de cada capa
- Aplicación web de consulta (MVP)
- Validaciones de datos y resultados

### 2. `documento_tecnico_presupuesto_databricks.ipynb`
Anexo técnico del proyecto con detalle de implementación:

- Stack tecnológico completo (herramientas por capa)
- Configuración de acceso a Databricks (token, warehouse, variables de entorno)
- Scripts principales del pipeline (`config.py`, `databricks_client.py`, `deploy_contract.py`, etc.)
- Consultas SQL de las vistas Gold
- Papel de GitHub Copilot / MCP como apoyo de desarrollo

---

## 🏗️ Arquitectura

```
Fuentes Excel/XLSM
       │
       ▼
   [ Python ]
  openpyxl / zipfile
       │
       ▼
┌─────────────────────────────┐
│         DATABRICKS          │
│                             │
│  Bronze → Silver → Gold     │
│  (Ingesta → Normal → Consumo)│
└─────────────────────────────┘
       │
       ▼
  App Web (Flask)
  Consulta por año,
  unidad de negocio
  y clase financiera
```

---

## 🗂️ Cobertura de datos

| Dimensión | Detalle |
|---|---|
| **Periodo validado** | 2021 – 2025 |
| **Unidades de negocio** | Fundación Unibán, Instituto Unibán, Instituto Técnico, Gestión de Crédito, Administrativo |
| **Tipos de dato** | Presupuesto aprobado y ejecución real |
| **Fuente principal** | Libros Excel institucionales (`.xlsm`) |

---

## ⚙️ Stack tecnológico

| Capa | Herramienta |
|---|---|
| Modelo previo | Excel, Power Query, Power Pivot |
| Desarrollo | VS Code, PowerShell, Python 3 |
| Lectura de fuentes | `openpyxl`, `zipfile`, `xml.etree` |
| Plataforma de datos | Databricks SQL Warehouse |
| Integración | API SQL Statements (HTTP) |
| Seguridad | Personal Access Token (Bearer) |
| Consumo | Flask (`app.py`, `report_service.py`) |

---

## 🔐 Variables de entorno requeridas

```env
DATABRICKS_HOST=https://dbc-xxxx.cloud.databricks.com
DATABRICKS_TOKEN=<tu_token>
DATABRICKS_WAREHOUSE_ID=<id_del_warehouse>
DATABRICKS_CATALOG=presupuesto
DATABRICKS_SCHEMA=gold
DBX_QUERY_CONTRACT=gold
```

> ⚠️ El archivo `.env` **no se publica** en el repositorio. El token de Databricks debe mantenerse fuera de control de versiones.

---

## 👤 Autor

**Rony Guerrero**  
Gestión Financiera 
Proyecto presentado para curso de Big Data · Mayo 2026
