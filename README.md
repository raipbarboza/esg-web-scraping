# esg-web-scraping
Coleta, armazenamento e análise de dados ESG públicos da Carteira ISE B3 — o principal índice de sustentabilidade empresarial do Brasil.
# 🌿 esg-web-scraping

Coleta, armazenamento e análise de dados ESG públicos da **Carteira ISE B3** — o principal índice de sustentabilidade empresarial do Brasil.

O pipeline completo cobre desde o scraping até a análise final:

```
Web (B3) → requests/BeautifulSoup → PostgreSQL (limpeza em SQL) → Pandas (análise)
```

---

## 📁 Estrutura do Repositório

```
esg-web-scraping/
│
├── notebooks/
│   ├── 01_fundamentos_requests_bs4.ipynb   # HTML, requests e BeautifulSoup
│   ├── 02_coleta_ise_b3.ipynb              # Scraping da carteira ISE B3
│   ├── 03_carga_postgres.ipynb             # Ingestão dos dados brutos no PostgreSQL
│   └── 04_analise_pandas.ipynb             # Leitura das views e análise com Pandas
│
├── sql/
│   ├── 01_create_tables.sql                # Schema: raw + clean + views
│   ├── 02_clean_data.sql                   # Limpeza e transformação
│   └── 03_views_analiticas.sql             # Views prontas para consumo pelo Pandas
│
├── data/
│   └── ise_b3_raw.csv                      # Dados brutos coletados (gerado pelo notebook 02)
│
├── .env.example                            # Variáveis de ambiente (conexão DB)
├── requirements.txt
└── README.md
```

---

## 🛠️ Tecnologias

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat&logo=sqlalchemy&logoColor=white)

---

## 🚀 Como Executar

### 1. Clone e instale as dependências

```bash
git clone https://github.com/raipbarboza/esg-web-scraping.git
cd esg-web-scraping
pip install -r requirements.txt
```

### 2. Configure as variáveis de ambiente

```bash
cp .env.example .env
# Edite o .env com suas credenciais do PostgreSQL
```

### 3. Crie o banco de dados e as tabelas

```bash
psql -U seu_usuario -c "CREATE DATABASE esg_db;"
psql -U seu_usuario -d esg_db -f sql/01_create_tables.sql
```

### 4. Execute os notebooks em ordem

| Notebook | O que faz |
|----------|-----------|
| `01_fundamentos_requests_bs4.ipynb` | Introdução ao scraping |
| `02_coleta_ise_b3.ipynb` | Coleta a carteira ISE B3 e salva CSV bruto |
| `03_carga_postgres.ipynb` | Carrega o CSV na tabela `ise_b3_raw` |
| `04_analise_pandas.ipynb` | Lê as views limpas e gera análises |

### 5. Execute a limpeza SQL

```bash
psql -U seu_usuario -d esg_db -f sql/02_clean_data.sql
psql -U seu_usuario -d esg_db -f sql/03_views_analiticas.sql
```

---

## 🗄️ Modelo de Dados

```
ise_b3_raw          → dados brutos ingeridos pelo Python
ise_b3_clean        → dados padronizados e validados via SQL
vw_empresas_por_setor   → agregação por setor (consumida pelo Pandas)
vw_segmentos_listagem   → distribuição por segmento de listagem
```

---

## 📊 Análises Geradas

- Distribuição de empresas ISE por setor econômico
- Representação por segmento de listagem (Novo Mercado, Nível 2, etc.)
- Evolução da carteira ao longo dos ciclos anuais (roadmap)

---

## 🌍 Sobre o ISE B3

O ISE B3 é uma iniciativa pioneira na América Latina, criado em 2005, e tem como objetivo medir o desempenho das empresas listadas na B3 em relação a critérios ambientais, sociais e de governança.

Frameworks de referência: **GRI**, **TCFD**, **CDP**.

---

## 📂 Projetos Relacionados

🔗 [python-esg-studies](https://github.com/raipbarboza/python-esg-studies) — Fundamentos de Python aplicados a dados ESG

🔗 [carbontrack-br](https://github.com/raipbarboza/carbontrack-br) — Pipeline de risco de carbono de empresas brasileiras

---

## 👩‍💻 Sobre

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rai-pereira-barboza-01a90a262)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/raipbarboza)
