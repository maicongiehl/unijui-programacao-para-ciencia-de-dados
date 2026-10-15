### Coleta de Autores das Proposições (Requisições HTTP)

Para mapear a autoria da produção legislativa no recorte temporal de 2023 a 2026, foi implementado um script em Python utilizando a biblioteca **Requests**.

O script realiza o download automatizado dos arquivos CSV de autoria diretamente da API de Dados Abertos da Câmara, utilizando transferência por fluxo (*stream*) para otimizar o salvamento na pasta de dados brutos.

* **Fonte base dos arquivos:** [Dados Abertos da Câmara - Arquivos Estáticos](https://dadosabertos.camara.leg.br/swagger/api.html?tab=staticfile)