# Análise de Dados Parlamentares 🏛️

Este repositório contém um pipeline de engenharia e análise de dados focado em informações legislativas e parlamentares brasileiras (como deputados, despesas, partidos, proposições e classificações ideológicas). O projeto está estruturado de forma modular para garantir a reprodutibilidade desde a extração até a análise final.

---

## 📁 Estrutura do Repositório

```text
├── data/
│   ├── clean/          # Dados tratados, limpos e estruturados (prontos para análise)
│   │   ├── deputado/
│   │   ├── despesa-para-exercicio-da-atividade-parlamentar/
│   │   ├── partido/
│   │   └── projeto-lei/
│   └── raw/            # Dados brutos extraídos das fontes originais
│       ├── classificacao-ideologica-por-partido-politico-brasileiro/
│       ├── deputados/
│       ├── despesas-pela-cota-para-exercício-da-atividade-parlamentar/
│       ├── partidos/
│       ├── proposicoes/
│       └── proposicoes-autores/
├── docs/               # Documentação detalhada do projeto e decisões metodológicas
│   ├── 01-problema.md
│   ├── 02-origem_dos_dados.md
│   ├── 03-tratamento_e_decisoes.md
│   └── 04-conclusao.md
├── notebooks/          # Jupyter Notebooks organizados por etapas do pipeline
│   ├── 01-extracao.ipynb
│   ├── 02-tratamentos.ipynb
│   └── 03-analise.ipynb
├── .gitignore
├── README.md
└── requirements.txt

📚 Foco na Documentação (docs/)

O diretório docs/ é o coração conceitual do projeto. Ele registra toda a jornada investigativa, desde a motivação inicial até as conclusões analíticas:

    01-problema.md: Define o escopo da investigação, as perguntas de pesquisa norteadoras e os objetivos centrais do projeto.

    02-origem_dos_dados.md: Documenta as fontes primárias de informação, APIs utilizadas (como os dados abertos da Câmara dos Deputados) e a estruturação inicial dos dados brutos em data/raw/.

    03-tratamento_e_decisoes.md: Detalha as etapas de limpeza, tratamento de valores nulos, cruzamento de tabelas e as decisões de engenharia de dados tomadas para transformar a camada raw na camada clean.

    04-conclusao.md: Apresenta os principais insights obtidos, respostas às perguntas iniciais e considerações finais baseadas nas análises executadas.

⚙️ Demais Diretórios

    data/: Armazena os dados do projeto divididos em duas camadas principais:

        raw/: Dados originais sem alterações.

        clean/: Dados transformados e padronizados, prontos para consumo.

    notebooks/: Contém os scripts interativos em Python divididos sequencialmente (01-extracao, 02-tratamentos e 03-analise).