# Processamento de Dados do SIPRI

Este notebook, **`Processing.ipynb`**, tem como objetivo processar e transformar dados de despesas militares do **SIPRI (Stockholm International Peace Research Institute)**. O fluxo de trabalho inclui a leitura de um arquivo Excel, a limpeza dos dados, a manipulação dos DataFrames e a exportação dos dados processados para arquivos CSV.

---

### Visão Geral do Projeto

O script realiza as seguintes etapas:

1.  **Configuração Inicial**: Importa a biblioteca `pandas` e define o caminho do arquivo de entrada (`SIPRI-Milex-data-1949-2024_2.xlsx`) e um dicionário de planilhas (`PLAN`) com o nome e o número da linha do cabeçalho de cada aba.
2.  **Extração de Dados**:
    * Itera sobre as planilhas definidas em `PLAN`.
    * Lê cada planilha usando `pd.read_excel`, especificando o nome da planilha e a linha do cabeçalho.
    * Remove linhas que contêm apenas 'x' ou 'X' e linhas completamente vazias.
    * Armazena cada DataFrame limpo em um dicionário chamado `BUFFER`.
3.  **Análise de Dados**: O script exibe detalhes de cada DataFrame no `BUFFER`, como o número de linhas, colunas e a contagem total de valores nulos, fornecendo uma visão rápida da integridade dos dados após a extração.
4.  **Transformação (Melting)**:
    * Para cada DataFrame no `BUFFER`, o script identifica as colunas que representam anos e as colunas de identificação.
    * Aplica a função `pd.melt` para **transformar as colunas de anos em linhas**, resultando em um formato mais longo e adequado para análise.
    * As colunas `year` e `value` são criadas para armazenar os dados de ano e valor, respectivamente.
5.  **Exportação**: Salva cada DataFrame transformado em um novo arquivo CSV dentro do diretório `./../dataready/`, com o nome da planilha original.

---

### Como Executar o Projeto

1.  Certifique-se de que o arquivo de dados `SIPRI-Milex-data-1949-2024_2.xlsx` está localizado no diretório `./../dataraw/`.
2.  Execute todas as células do notebook `Processing.ipynb` em ordem.

O resultado final será uma série de arquivos `.csv` processados, prontos para serem usados em análises ou visualizações posteriores.
