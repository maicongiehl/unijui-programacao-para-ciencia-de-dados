# Tratamento de Dados

Este documento descreve o processo de limpeza, transformação e padronização das bases de dados brutas (raw) para o formato limpo e estruturado (clean), salvando-os no formato otimizado .parquet para posterior análise.

1. Configuração Inicial

O ambiente utiliza bibliotecas padrão para manipulação de arquivos, leitura de JSON e processamento de dados tabulares.

    Diretórios de Entrada (raw): ../data/raw

    Diretórios de Saída (clean): ../data/clean

2. Tratamento de Despesas (Cota Parlamentar)

Consolida os arquivos anuais de despesas da Cota para o Exercício da Atividade Parlamentar em uma única base unificada para o período dos mandatos atuais.

    Fontes: Arquivos .csv.zip anuais contidos na pasta de despesas.

    Transformações aplicadas:

        Concatenação de todos os anos (2023 a 2026).

        Filtragem das colunas de interesse analítico (nome parlamentar, partido, descrição da despesa, data de emissão, valor líquido, mês, ano e ID do deputado).

        Renomeação das colunas para o padrão em português (snake_case).

        Salvamento do DataFrame resultante em formato Parquet (despesa-para-exercicio-da-atividade-parlamentar.parquet).

3. Tratamento de Partidos

Padroniza as informações cadastrais dos partidos políticos obtidas via API de Dados Abertos da Câmara.

    Fonte: partidos.json

    Transformações aplicadas:

        Extração dos dados do nó principal e remoção de colunas redundantes (uri).

        Padronização das siglas e nomes dos partidos em letras maiúsculas.

        Renomeação do identificador para partido_id.

4. Classificação Ideológica por Partido

Processa e categoriza os partidos políticos com base na escala ideológica obtida de literatura acadêmica de referência.

    Critério de Classificação (Média):

        0 a 1,5: Extrema-Esquerda

        1,51 a 3,0: Esquerda

        3,01 a 4,49: Centro-Esquerda

        4,5 a 5,5: Centro

        5,51 a 7,0: Centro-Direita

        7,01 a 8,5: Direita

        8,51 a 10: Extrema-Direita

    Transformações aplicadas:

        Limpeza e conversão da coluna de média ideológica (tratamento de vírgulas para pontos decimais).

        Criação da coluna espectro_detalhado (dividida em 7 faixas).

        Criação da coluna espectro_macro (agrupada em 3 blocos: Esquerda, Centro e Direita).

        Espectros de partidos que não existiam/possuíam outra nomenclatura no projeto original foram inferidos pelo autor.

        Cruzamento: Mesclagem dos dados de partidos com a classificação ideológica utilizando a sigla como chave, gerando a base unificada de partidos (partido.parquet).

5. Tratamento de Proposições e Autores

Filtra a produção legislativa focando estritamente nos Projetos de Lei e vinculando-os aos seus respectivos autores principais.

    Fontes: Arquivos CSV de proposições e de autoria de proposições por ano.

    Transformações aplicadas:

        Agregação dos arquivos de proposições e de autores de múltiplos anos.

        Filtragem dos registros onde a ordem de assinatura (ordemAssinatura) corresponde ao autor principal (1).

        Cruzamento entre as tabelas de proposições e autores por meio do ID da proposição.

        Remoção de valores nulos e padronização da descrição do tipo para letras maiúsculas.

        Filtro restrito aos registros do tipo "PROJETO DE LEI".

        Exportação para o arquivo final (projeto_lei.parquet).

6. Tratamento de Deputados

Processa a base cadastral histórica de deputados federais.

    Fonte: br_camara_dados_abertos_deputado.csv

    Transformações aplicadas:

        Remoção de colunas de metadados desnecessárias (como data de falecimento, de nascimento e dados de legislaturas iniciais/finais).

        (Nota: Etapa contida no bloco final do notebook).