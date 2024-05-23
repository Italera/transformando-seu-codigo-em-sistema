# transformando-seu-codigo-em-sistema

# Filtragem de Exportações para França
## Descrição do Projeto
Este projeto tem como objetivo automatizar o processo de filtragem de dados de exportações para a França, utilizando a linguagem Python e a biblioteca Pandas. O processo envolve a leitura de um arquivo CSV contendo dados de exportações, a aplicação de filtros para selecionar apenas os dados relevantes e a exportação dos dados filtrados para um novo arquivo CSV.

# Estrutura do Projeto
- importar_arquivos_e_bibliotecas.py: Script responsável por importar as bibliotecas necessárias e carregar o arquivo CSV.
- filtrar_dados.py: Script que aplica os filtros necessários para selecionar os dados de exportações para a França a partir de 2016.
- exportar_dados_filtrados.py: Script que salva os dados filtrados em um novo arquivo CSV.

# Arquivos
- exportacoes_franca.csv: Arquivo CSV original contendo dados de exportações.
- exportacoes_filtradas_franca.csv: Arquivo CSV gerado contendo os dados filtrados.

# Como Executar
1. Importação de Arquivos e Bibliotecas
Este passo importa a biblioteca Pandas e carrega o arquivo CSV original.

import pandas as pd

Carregar o arquivo CSV
tabela = pd.read_csv("exportacoes_franca.csv")
display(tabela)

2. Filtragem de Dados
Neste passo, aplicamos filtros para selecionar apenas os dados de exportações para a França a partir de 2016.

# Filtrar dados a partir de 2016 e para o país França
tabela = tabela.loc[tabela['Year'] >= 2016, :]

tabela = tabela.loc[tabela['Country'] == "France", :]

display(tabela)

3. Exportação de Dados Filtrados
Após a filtragem, os dados são exportados para um novo arquivo CSV.

Salvar os dados filtrados em um novo arquivo CSV
tabela.to_csv("exportacoes_filtradas_franca.csv", index=False)
display(tabela)

# Estrutura do CSV
O arquivo CSV original e o filtrado possuem a seguinte estrutura:

- Year: Ano da exportação
- Month: Mês da exportação
- Country: País de destino
- City: Cidade de origem
- SH4 Code: Código SH4 do produto
- SH4 Description: Descrição do produto no código SH4
- SH2 Code: Código SH2 do produto
- SH2 Description: Descrição do produto no código SH2
- Economic Block: Bloco econômico de destino
- US$ FOB: Valor da exportação em dólares
- Net Weight: Peso líquido da exportação
  
# Observações

- Certifique-se de que o arquivo exportacoes_franca.csv esteja no mesmo diretório dos scripts antes de executá-los.
- A filtragem pode ser ajustada conforme necessário, alterando os critérios nos scripts de filtragem.

# Conclusão
- Este projeto fornece um sistema automatizado para a filtragem de dados de exportações, facilitando a análise e o tratamento dos dados de maneira eficiente.

# Análise de Exportações para a França (2016-2020)

Este README fornece uma visão geral do processo de análise das exportações brasileiras para a França entre 2016 e 2020. O objetivo é analisar e apresentar informações sobre a evolução das exportações, os produtos mais exportados e as cidades com maior volume de exportação. Este documento descreve as etapas necessárias para realizar essa análise usando Python e a biblioteca pandas.

Requisitos

Python 3.x
pandas
Passos para a Análise

1. Importar Bibliotecas Necessárias

import pandas as pd

3. Carregar e Filtrar a Base de Dados
Carregue a base de dados de exportações e filtre os registros para incluir apenas exportações para a Europa.

tabela = pd.read_csv("exportacoes_franca.csv")
tabela = tabela.loc[tabela['Economic Block']=='Europe', :]

3. Exibir a Tabela Filtrada
Visualize os dados filtrados para assegurar que a filtragem foi realizada corretamente.

display(tabela)

4. Informações Gerais sobre os Dados
Obtenha informações gerais e estatísticas descritivas sobre a tabela.

print(tabela.info())
display(tabela.describe())

5. Evolução das Exportações (US$) ao Longo dos Anos
Agrupe os dados por ano e calcule a soma das exportações (US$ FOB) para cada ano.

exportacao_ano = tabela.groupby('Year').sum()[['US$ FOB']]

def formatar(valor):
    return f'${valor:,.2f}'

exportacao_ano['US$ FOB'] = exportacao_ano['US$ FOB'].map(formatar)
display(exportacao_ano)

6. Produtos Mais Exportados (US$) ao Longo de Todo o Período
Agrupe os dados pela descrição dos produtos (SH4 Description) e calcule a soma das exportações (US$ FOB) para cada produto.

exportacao_produto = tabela.groupby('SH4 Description').sum()[['US$ FOB']]
exportacao_produto = exportacao_produto.sort_values('US$ FOB', ascending=False)
exportacao_produto['US$ FOB'] = exportacao_produto['US$ FOB'].map(formatar)
display(exportacao_produto)

7. Cidade com Maior Volume de Exportações para a França em 2020
Filtre os dados para o ano de 2020, agrupe por cidade e calcule a soma das exportações (US$ FOB).

tabela_2020 = tabela.loc[tabela['Year']==2020, :]
exportacao_cidades_2020 = tabela_2020.groupby('City').sum()[['US$ FOB']]
exportacao_cidades_2020 = exportacao_cidades_2020.sort_values('US$ FOB', ascending=False)
exportacao_cidades_2020['US$ FOB'] = exportacao_cidades_2020['US$ FOB'].map(formatar)
display(exportacao_cidades_2020)

8. Análise dos Produtos Exportados pela Maior Cidade em 2020
Selecione a cidade com maior volume de exportações e analise os produtos exportados por essa cidade.

cidade = exportacao_cidades_2020.index[0]
tabela_cidade = tabela_2020.loc[tabela_2020['City']==cidade, :]
tabela_cidade = tabela_cidade.groupby('SH4 Description').sum()[['US$ FOB']]
tabela_cidade = tabela_cidade.sort_values('US$ FOB', ascending=False)
tabela_cidade['US$ FOB'] = tabela_cidade['US$ FOB'].map(formatar)
display(tabela_cidade)

# Conclusão
Este processo permite uma análise detalhada das exportações brasileiras para a França, incluindo a identificação das tendências ao longo dos anos, os principais produtos exportados e as cidades com maior volume de exportações. A formatação dos valores facilita a interpretação dos dados financeiros, tornando a análise mais intuitiva e compreensível.

# Autor
Este script foi desenvolvido para fins de análise de dados e pode ser ajustado conforme necessário para outras análises ou períodos. Para quaisquer dúvidas ou melhorias, sinta-se à vontade para contribuir.
