# ESG Web Scraping

Projeto de estudo para coleta, organização e análise de dados públicos da carteira ISE B3 com Python e PostgreSQL.

**Estado atual:** estrutura inicial. Os quatro notebooks, os três scripts SQL, `requirements.txt` e `.env.example` estão vazios. Ainda não há pipeline executável ou análises produzidas por esses arquivos.

## Estrutura publicada

```text
esg-web-scraping/
├── notebooks/
│   ├── 01_fundamentos_requests_bs4.ipynb
│   ├── 02_coleta_ise_b3.ipynb
│   ├── 03_carga_postgres.ipynb
│   └── 04_analise_pandas.ipynb
├── sql/
│   ├── 01_create_tables.sql
│   ├── 02_clean_data.sql
│   └── 03_views_analiticas.sql
├── data/
│   └── .gitkeep
├── .env.example
├── requirements.txt
└── README.md
```

Esses arquivos reservam a organização pretendida; os notebooks vazios ainda não são documentos Jupyter válidos.

## Fluxo planejado

1. Implementar a coleta, registrando fonte e data de referência.
2. Salvar os dados brutos e definir seu esquema.
3. Criar as tabelas e carregar os registros no PostgreSQL.
4. Executar a limpeza e criar as views analíticas.
5. Executar o notebook de análise sobre os dados preparados.

As análises pretendidas incluem distribuição por setor e segmento de listagem. Comparações entre ciclos anuais dependerão da obtenção de dados históricos compatíveis.

## Como acompanhar

```bash
git clone https://github.com/raipbarboza/esg-web-scraping.git
cd esg-web-scraping
```

Não há comandos de execução do pipeline nesta etapa. Dependências, credenciais de exemplo e instruções do banco serão documentadas junto com a implementação. Instalar o `requirements.txt` vazio ou executar os SQLs vazios não prepara o ambiente descrito no planejamento.

## Projetos relacionados

- [Python ESG Studies](https://github.com/raipbarboza/python-esg-studies): estudos de Python e exploração de dados.
- [CarbonTrack BR](https://github.com/raipbarboza/carbontrack-br): CSVs e recortes exploratórios de companhias brasileiras.

## Autor

[Rai Barboza](https://www.linkedin.com/in/rai-barboza-01a90a262/)
