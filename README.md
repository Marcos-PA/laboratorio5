# Comparação de Desempenho entre API REST e GraphQL do GitHub

## 📋 Descrição

Este experimento tem como objetivo comparar o desempenho das APIs **REST** e **GraphQL** do GitHub em termos de:

- ⏱️ Tempo de resposta
- 📦 Tamanho da resposta

## 🔬 Metodologia

- Foram realizadas **30 coletas** de dados para cada API.
- Cada coleta consiste na busca de **1000 repositórios populares** (com mais de 100 estrelas) utilizando os dois tipos de API.
- As métricas coletadas são:
  - **Tempo total de resposta (ms)**
  - **Tamanho total da resposta (bytes)**

## 🔧 Tecnologias e Ferramentas

- Linguagem: Python
- Bibliotecas:
  - `requests`
  - `matplotlib`
  - `numpy`
  - `csv`
  - `os`
  - `time`

## 🧠 Funcionamento

### 1. Coleta dos Dados

- **API REST:**A busca é feita utilizando a rota `/search/repositories`, paginando os resultados até obter 1000 repositórios.
- **API GraphQL:**
  A busca é feita utilizando consultas GraphQL paginadas com `cursor`, até alcançar 1000 repositórios.

> Cada execução gera um arquivo CSV contendo:

- `response_time_ms`: tempo total da coleta
- `response_size_bytes`: tamanho total da resposta

### 2. Processamento dos Dados

- Os arquivos CSV são lidos e processados para extrair as métricas de tempo e tamanho, tanto para REST quanto para GraphQL.

### 3. Análise Visual

- São gerados gráficos de barras comparando:
  - **Tempo médio de resposta**
  - **Tamanho médio da resposta**
  - **Tempo total de resposta**
  - **Tamanho total da resposta**

## 📊 Resultados Esperados

- Observar qual API é mais eficiente em termos de velocidade e economia de dados.
- Avaliar os trade-offs entre as abordagens REST e GraphQL.

## 🚀 Execução

1. Configure seu token do GitHub no campo `GITHUB_TOKEN`.
2. Execute as funções de coleta (comentadas no script principal) para gerar os CSVs:
   ```python
   fetch_repositories_rest()
   fetch_repositories_graphql()
   ```
3. Os arquivos CSV são salvos na pasta `../docs/lab5/metrics/`.
4. Execute a etapa de análise para gerar os gráficos:
   ```python
   generate_simple_bar_graphs(rest_data, graphql_data)
   ```

## 📂 Estrutura dos Arquivos

```
.
├── labs5.ipynb
├── metrics/
│   ├── repositories_rest_primeiro_experimento.csv
│   ├── repositories_graphql_primeiro_experimento.csv
│   └── ...
```

## ⚠️ Observações

- É necessário fornecer um token GitHub válido para autenticação nas APIs.
- O experimento respeita os limites de rate limit do GitHub.
- O uso da API GraphQL pode exigir mais controle sobre paginação via `cursor`.

## 👨‍💻 Autor

- Marcos Paulo
- Renato Paganini
- Curso: Engenharia de Software
- Universidade: PUC Minas
