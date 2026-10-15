### Coleta de Proposições (Requisições HTTP)

Para a obtenção dos dados de proposições legislativas dos anos correspondentes aos mandatos atuais (2023 a 2026), foi desenvolvido um script de automação utilizando a biblioteca **Requests**.

O script realiza o download direto dos arquivos CSV disponibilizados na API de Dados Abertos da Câmara dos Deputados, processando os dados por meio de fluxo contínuo (*stream*) para garantir maior eficiência na transferência.

* **Fonte base dos arquivos:** [Dados Abertos da Câmara - Arquivos Estáticos](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)