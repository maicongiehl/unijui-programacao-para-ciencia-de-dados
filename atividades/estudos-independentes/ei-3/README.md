# Web Scraper — Books to Scrape

Aplicação desenvolvida em Python para extração automatizada de dados na Web (*Web Scraping*) a partir do portal [Books to Scrape](https://books.toscrape.com). Os dados coletados são tratados e armazenados localmente em arquivos **JSON** estruturados.

## Funcionalidades

O sistema conta com um menu interativo no terminal com as seguintes opções:

* **`[1]` Extrair todos os livros:** Percorre todas as páginas do catálogo geral e salva a listagem completa.
* **`[2]` Extrair livros paginados:** Permite escolher quantas páginas do catálogo deseja extrair.
* **`[3]` Extrair todos os livros por categoria:** Lista as categorias disponíveis (utilizando cache local após a primeira consulta) e extrai os livros da categoria selecionada.
* **`[4]` Extrair informações detalhadas do livro:** Busca um livro pelo título na base extraída e coleta informações complementares na página individual do produto (código UPC, sinopse e quantidade exata em estoque).
* **`[5]` Limpar output:** Limpa a saída do console (útil no ambiente Google Colab).
* **`[0]` Sair:** Encerra a execução do programa.

## Tecnologias Utilizadas

* **Python 3**
* **Requests:** Realização das requisições HTTP.
* **BeautifulSoup4:** Parsing e navegação na estrutura HTML das páginas.

## Como Executar

### No Google Colab
1. Abra o notebook `EI III.ipynb` no Google Colab.
2. Execute as células em ordem para instalar as dependências, criar os diretórios e carregar as funções.
3. Execute a célula do menu interativo e escolha a opção desejada.

## Estrutura dos Arquivos Gerados

Ao iniciar, o script cria automaticamente a pasta `dados/` dividida em subdiretórios conforme o tipo de extração:

```text
dados/
├── categorias/
│   └── categorias.json                  # Cache com ID, nome e URL das categorias
├── livros/
│   └── lista_livros.json                # Catálogo completo de livros
├── livros-paginados/
│   └── lista_livros_pagina_<n>.json     # Extração parcial por página
├── livros-categoria/
│   └── lista_livros_<categoria>.json    # Livros filtrados por categoria
└── livro/
    └── <upc>.json                       # Detalhes individuais de um livro
```

### Exemplo de Dados Estruturados

**Listagem de livros (`lista_livros.json`):**
```json
{
  "titulo": "A Light in the Attic",
  "preco_gbp": 51.77,
  "estoque": "In stock",
  "avaliacao": 3,
  "url": "https://books.toscrape.com/catalogue/a-light-in-the-attic_1000/index.html"
}
```

**Detalhes do livro (`a897fe39b1053632.json`):**
```json
{
  "upc": "a897fe39b1053632",
  "descricao": "It's hard to imagine a world without A Light in the Attic...",
  "disponivel": true,
  "quantidade_em_estoque": 22
}
```
