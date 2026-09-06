# Consulta de Tabela FIPE para Veículos

Projeto desenvolvido em Python para automatizar a consulta de valores da Tabela FIPE de veículos, utilizando um arquivo Excel como fonte de dados.

A aplicação realiza a consulta dos veículos utilizando o **código FIPE**, tornando a busca mais precisa e permitindo relacionar o veículo ao ano do modelo informado na planilha.

## Objetivo

O projeto foi desenvolvido com o objetivo de facilitar e automatizar o processo de consulta de valores FIPE, reduzindo a necessidade de pesquisas manuais e organizando os resultados diretamente em uma planilha Excel.

## Como funciona

O programa utiliza um arquivo Excel contendo informações dos veículos, como:

* Modelo
* Fabricante
* Ano do modelo
* Código FIPE

A partir do código FIPE informado, o sistema:

1. Lê os dados do arquivo Excel.
2. Identifica o código FIPE de cada veículo.
3. Consulta os anos disponíveis para o código informado.
4. Localiza o ano correspondente ao ano do modelo.
5. Consulta os dados do veículo e seu valor FIPE.
6. Preenche os resultados na planilha.
7. Gera um novo arquivo Excel com as informações atualizadas.

## Tecnologias utilizadas

* Python
* Pandas
* Requests
* OpenPyXL
* Google Colab
* Excel
* API da Tabela FIPE

## Estrutura dos dados

O arquivo de entrada deve conter as seguintes colunas:

| Coluna        | Descrição                            |
| ------------- | ------------------------------------ |
| `MODELO`      | Modelo do veículo                    |
| `FABRICANTE`  | Fabricante do veículo                |
| `ANO MODELO`  | Ano do modelo                        |
| `CODIGO FIPE` | Código FIPE utilizado na consulta    |
| `TABELA FIPE` | Coluna destinada ao valor encontrado |

## Arquivo de entrada

O programa utiliza o arquivo:

```text
caminhoes.xlsx
```

Esse arquivo deve estar disponível no ambiente do Google Colab antes da execução.

## Arquivo de saída

Após o processamento, o sistema gera:

```text
resultado_fipe.xlsx
```

Além do valor FIPE, o arquivo de resultado contém informações adicionais sobre a consulta, como:

* Status da consulta
* Nome oficial do veículo retornado pela API
* Mês de referência da Tabela FIPE
* Anos disponíveis para o código FIPE

## Tratamento de erros

O projeto possui um mecanismo de tentativa automática para as requisições à API.

Em caso de falha de conexão ou erro do servidor, o sistema realiza novas tentativas antes de considerar a consulta como falha.

Também são tratados casos como:

* Código FIPE não informado
* Código FIPE inválido
* Ano não disponível para o código informado
* Erro na consulta do preço
* Falha de conexão com a API

## Execução

### 1. Abra o projeto no Google Colab

Abra o notebook:

```text
TABELA_FIPE_VEICULOS.ipynb
```

### 2. Faça o upload do arquivo Excel

O arquivo deve estar disponível no ambiente do Colab com o nome:

```text
caminhoes.xlsx
```

### 3. Execute o notebook

O programa realizará as consultas utilizando os códigos FIPE presentes na planilha.

### 4. Resultado

Ao finalizar o processamento, será gerado automaticamente o arquivo:

```text
resultado_fipe.xlsx
```

## API

As consultas são realizadas utilizando a API da Tabela FIPE:

```text
https://fipe.parallelum.com.br/api/v2
```

O projeto utiliza o endpoint de veículos pesados (`trucks`), com consultas baseadas no código FIPE e no ano do modelo.

## Melhorias realizadas

Uma das principais melhorias desta versão foi a alteração do método de pesquisa.

### Versão anterior

A consulta dependia principalmente das informações de fabricante, modelo e ano para localizar o veículo.

### Versão atual

A aplicação utiliza diretamente o **código FIPE** informado na planilha e, posteriormente, verifica o ano correspondente.

Essa alteração torna o processo de identificação mais preciso e reduz possíveis divergências durante a consulta.

## Possíveis melhorias futuras

Algumas funcionalidades que podem ser adicionadas futuramente:

* Interface gráfica para facilitar a utilização
* Barra de progresso durante o processamento
* Validação automática da estrutura do Excel
* Registro detalhado das consultas realizadas
* Melhor tratamento de limites de requisições da API
* Possibilidade de selecionar diferentes tipos de veículos

## Autor

**Marcelo Junior**

Projeto desenvolvido como prática de programação em Python e automação de processos, aplicando conceitos de manipulação de dados, integração com API e processamento de arquivos Excel.
