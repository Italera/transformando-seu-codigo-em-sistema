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

# Carregar o arquivo CSV
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

# Salvar os dados filtrados em um novo arquivo CSV
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
