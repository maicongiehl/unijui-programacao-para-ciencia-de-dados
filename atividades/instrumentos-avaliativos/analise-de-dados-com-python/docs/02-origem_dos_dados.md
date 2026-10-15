## Origem dos Dados

Conforme os requisitos do trabalho, todas as fontes utilizadas são abertas. As bases de dados e métodos de extração empregados foram:

### 1. Deputados
* **Fonte:** [Base dos Dados](https://basedosdados.org/dataset/3d388daa-2d20-49eb-8f55-6c561bef26b6?table=d37931b4-8b67-47c7-b910-014695dc8f36)
* **Método de Extração:** Coleta automatizada (*web scraping*) utilizando **Selenium** (técnica abordada em aula). A base abrange o histórico de deputados do país, sendo filtrada para o escopo do projeto.

### 2. Classificação Ideológica por Partido
* **Fonte:** [Artigo Científico (Scielo)](https://www.scielo.br/j/dados/a/zzyM3gzHD4P45WWdytXjZWg/?format=html&lang=pt&ilang=en)
* **Método de Extração:** Transcrição manual dos dados do artigo, posteriormente adaptados para o formato CSV.

### 3. Despesas (Cota Parlamentar)
* **Fonte:** [API de Dados Abertos da Câmara dos Deputados](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)
* **Método de Extração:** Requisições automatizadas utilizando o padrão de endereços base (`https://www.camara.leg.br/cotas/Ano-{ano}.csv.zip`), filtrando os dados para o período dos mandatos atuais (2023–2026).

### 4. Partidos
* **Fonte:** [API de Dados Abertos da Câmara dos Deputados](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)
* **Método de Extração:** Chamada HTTP para o endpoint de partidos (`https://www.camara.leg.br/api/v2/partidos`) com o salvamento do retorno em formato JSON.

### 5. Proposições
* **Fonte:** [API de Dados Abertos da Câmara dos Deputados](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)
* **Método de Extração:** Coleta automatizada direcionada aos arquivos de proposições por ano, restrita ao período dos mandatos atuais.

### 6. Autores das Proposições
* **Fonte:** [API de Dados Abertos da Câmara dos Deputados](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)
* **Método de Extração:** Requisições estruturadas com base nos arquivos de temas e autoria por ano (`https://www.camara.leg.br/arquivos/proposicoesTemas/csv/proposicoesTemas-{ano}.csv`), considerando o recorte temporal atual.