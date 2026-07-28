🚀 Como Usar
1. Preparação da Planilha de Entrada
O script espera um arquivo Excel chamado caminhoes.xlsx (com uma aba chamada Planilha1) no mesmo diretório de execução.

A planilha deve conter obrigatoriamente as seguintes colunas:

fabricante: Nome do fabricante/marca (ex: VOLKSWAGEN, MERCEDES-BENZ).

modelo: Nome/descrição do modelo (ex: DELIVERY, ATEGO).

ano modelo: Ano do veículo (ex: 2018, 2021).

Nota: Se o seu arquivo tiver outro nome ou se a aba do Excel for diferente, edite a seguinte linha no script:

Python
df = pd.read_excel('SEU_ARQUIVO.xlsx', sheet_name='SuaAba')
2. Execução
Execute o script diretamente pelo terminal ou em um ambiente Jupyter / Google Colab:

Bash
python consulta_fipe.py
3. Resultado
Após a conclusão do processo, o script criará o arquivo caminhoes_com_fipe.xlsx contendo todas as colunas originais acrescidas da coluna Preço FIPE.

⚙️ Estrutura do Fluxo da API
Obter Marcas: Busca a lista de marcas cadastradas no segmento de caminhões na FIPE.

Obter Modelos: Mapeia o ID da marca e pesquisa os modelos disponíveis.

Obter Ano: Identifica o código do ano correspondente do modelo.

Obter Preço: Retorna o valor atualizado e adiciona ao DataFrame final.
```bash
pip install pandas requests openpyxl
# Consulta Automática de Preços na Tabela FIPE para Frotas

Este script em Python automatiza a busca e atualização dos preços da Tabela FIPE para listas de veículos contidas em planilhas Excel. Ele elimina a necessidade de pesquisar e preencher manualmente os valores de cada veículo, otimizando o tempo de gestão e análise de frotas.

---

## 📌 Funcionalidades

- **Leitura de Dados**: Importa dados de uma planilha Excel (`caminhoes.xlsx`).
- **Consulta via API**: Integra com a API pública da Tabela FIPE (`parallelum.com.br`) para consultar marcas, modelos e anos.
- **Mapeamento Flexível**: Realiza busca por correspondência de texto para identificar fabricantes e modelos mesmo com pequenas variações de nome.
- **Controle de Requisições**: Inclui intervalos de pausa (`time.sleep`) entre as chamadas à API para evitar bloqueios por excesso de requisições.
- **Exportação de Resultados**: Gera uma nova planilha (`caminhoes_com_fipe.xlsx`) contendo a coluna adicional **Preço FIPE**.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

- **Python 3.x**
- **Pandas**: Para leitura, manipulação e exportação de dados em planilhas Excel.
- **Requests**: Para envio de requisições HTTP REST à API da Tabela FIPE.
- **openpyxl**: Biblioteca de suporte ao Pandas para manipulação de arquivos `.xlsx`.
- **Time**: Módulo nativo do Python usado para controlar os intervalos entre requisições.

---

## 📋 Pré-requisitos

Antes de executar o código, certifique-se de instalar as dependências necessárias:

```bash
pip install pandas requests openpyxl
