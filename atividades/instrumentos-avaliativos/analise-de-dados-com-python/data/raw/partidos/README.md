### Obtenção de Dados via API

Os dados dos partidos políticos foram obtidos diretamente via REST API da Câmara dos Deputados. 

* **Endpoint utilizado:**
  ```bash
  curl -X 'GET' \
      '[https://dadosabertos.camara.leg.br/api/v2/partidos?ordem=ASC&ordenarPor=sigla](https://dadosabertos.camara.leg.br/api/v2/partidos?ordem=ASC&ordenarPor=sigla)' \
      -H 'accept: application/json'