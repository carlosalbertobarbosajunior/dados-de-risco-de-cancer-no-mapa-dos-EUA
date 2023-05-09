# dados-de-risco-de-cancer-no-mapa-dos-EUA
## Objetivo:
Plotar um gráfico de mapa com as informações de risco de câncer dos condados dos EUA baseado em informações dos centros dos condados e uma base de dados de risco de câncer.

### Problema 1: Unificar as bases de dados:
As informações de centros dos condados e do risco de câncer estão em arquivos CSV distintos. Há uma coluna de código FIPS que pode ser utilizada para unificá-las.

#### read_csv_file(file_name):
    """
    Input:
      file_name - String do nome do arquivo CSV
      
    Output:
      csv_table - Lista aninhada contendo os campos do arquivo CSV
      
    Ação:
      Dado um arquivo CSV, lê as informações para uma lista aninhada
    """ 

#### write_csv_file(csv_table, file_name):
    """
    Input:
      csv_table - Lista aninhada
      file_name - Nome do arquivo CSV
      
    Output:
      Retorna None
      
    Ação:
      Escreve os campos da csv_table em um arquivo CSV 
      separado por vírgulas com o nome file_name.
    """
#### make_dict(table, key_col):
    """
    Inputs:
      table       - Tabela 2D (lista de listas)
      key_col     - Coluna de índice
      
    Output:
      answer_dict - Dicionário onde as chaves são entradas
      de uma coluna específica, e seus valores são listas
      contendo as demais entradas de cada linha.
    """

#### merge_csv_files(cancer_csv_file, center_csv_file, joined_csv_file, cancer_fips_col, center_fips_col):
    """
    Inputs:
      cancer_csv_file - Nome do arquivo CSV das informações de risco de câncer
      center_csv_file - Nome do arquivo CSV com as informações do centro de cada condado dos EUA
      joined_csv_file - Nome do arquivo CSV a ser criado.
      cancer_fips_col - Número da coluna do arquivo cancer_csv_file que possui os dados de código FIPS
      center_fips_col - Número da coluna do arquivo center_csv_file que possui os dados de código FIPS
      
    Output:
      Retorna None
      
    Ação:
      Lê dois arquivos CSV como tabelas.
      Une as informações em uma única tabela através
      do código FIPS compartilhado.
      Escreve um novo arquivo com as informações unificadas.
      Analisa códigos FIPS problemáticos.
    """

### Problema 2: Plotar as informações em um gráfico de mapa
Utilizar as informações tabeladas e unificadas para criar uma representação visual.

#### compute_county_circle(county_population):
    """
    Input:
      county_population                 - População do condado (int)
    
    Output:
      SCATTER_SCALE * county_population - Área do círculo proporcional à
                                          população para uso como opção
                                          para o scatter() no matplotlib
    """

#### create_riskmap(colormap):
    """
    Input:
      colormap                                               - Mapa de cores do matplotlib
      
    Output:
      lambda risk : color_mapper.to_rgba(math.log(risk, 10)) - Função que recebe o risco de
                                                               câncer e retorna o range de
                                                               cores RGB para ser utilizado
                                                               com o scatter() do matplotlib.
    """

#### draw_cancer_risk_map(joined_csv_name, map_name, num_counties = None):
    """
    Inputs:
      joined_csv_file - Nome do arquivo CSV unificado
      map_name        - Nome do mapa PNG dos EUA
      num_counties    - Especifica o número de condados a serem desenhados
      
    Output:
      Retorna None
      
    Ação:
      Dados os nomes do arquivo CSV joined_csv_file e o mapa dos EUA map_name,
      desenha os dados de risco de câncer para cada condado dos EUA. O argumento
      opcional especifica o número de condados a serem desenhados.
    """