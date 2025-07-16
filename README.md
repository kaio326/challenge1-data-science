# README - AluraStoreBr Data Science Project

## 📋 Descrição do Projeto

Este projeto é uma análise de dados abrangente de **quatro lojas** de um e-commerce brasileiro (AluraStoreBr). O objetivo é analisar o desempenho de cada loja em diferentes métricas para apoiar decisões de negócio, incluindo faturamento, categorias de produtos, satisfação do cliente e análise de produtos.

## 🏢 Sobre o Projeto

- **Origem**: Challenge de Data Science da Alura
- **Período analisado**: Janeiro de 2020 a Março de 2023
- **Total de transações**: 9.435 vendas
- **Lojas analisadas**: 4 unidades
- **Objetivo**: Determinar qual loja deve ser vendida com base em análises quantitativas

## 📊 Estrutura dos Dados

### Colunas Disponíveis:
- **Produto**: Nome do produto vendido
- **Categoria do Produto**: Categoria (eletrônicos, eletrodomésticos, móveis, etc.)
- **Preço**: Valor do produto (sem frete)
- **Frete**: Valor do frete
- **Data da Compra**: Data da transação (formato: dd/mm/yyyy)
- **Vendedor**: Nome do vendedor
- **Local da compra**: Estado da compra
- **Avaliação da compra**: Nota de 1 a 5
- **Tipo de pagamento**: Forma de pagamento
- **Quantidade de parcelas**: Número de parcelas
- **lat/lon**: Coordenadas geográficas

### Categorias de Produtos:
- Eletrônicos
- Eletrodomésticos
- Móveis
- Instrumentos Musicais
- Esporte e Lazer
- Brinquedos
- Utilidades Domésticas
- Livros

## 🛠️ Instalação e Configuração

### Pré-requisitos
```bash
Python 3.7+
```

### Bibliotecas Necessárias
```bash
pip install pandas numpy matplotlib seaborn
```

### Instalação Alternativa
```bash
# Instalar todas as dependências de uma vez
pip install pandas numpy matplotlib seaborn jupyter
```

## 📁 Estrutura do Repositório

```
challenge1-data-science/
├── AluraStoreBr.ipynb          # Notebook principal com análises
├── base-de-dados-challenge-1/  # Pasta com dados das lojas
│   ├── loja_1.csv             # Dados da Loja 1
│   ├── loja_2.csv             # Dados da Loja 2
│   ├── loja_3.csv             # Dados da Loja 3
│   └── loja_4.csv             # Dados da Loja 4
└── README.md                   # Este arquivo
```

## 🚀 Como Executar o Projeto

### 1. Clonar o Repositório
```bash
git clone https://github.com/kaio326/challenge1-data-science.git
cd challenge1-data-science
```

### 2. Instalar Dependências
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Executar o Notebook
```bash
jupyter notebook AluraStoreBr.ipynb
```

### 4. Executar Células do Notebook
- Execute as células sequencialmente
- Cada seção contém análises específicas
- Os gráficos são gerados automaticamente

## 📈 Análises Realizadas

### 1. **Análise de Faturamento**
- Faturamento total por loja
- Participação percentual de cada loja
- Faturamento médio por transação

### 2. **Análise de Categorias**
- Produtos mais vendidos por categoria
- Faturamento por categoria em cada loja
- Ranking de categorias por popularidade

### 3. **Avaliação dos Clientes**
- Média de avaliações por loja
- Evolução das avaliações ao longo do tempo
- Análise de satisfação

### 4. **Análise de Produtos**
- Produtos mais e menos vendidos
- Faturamento por produto
- Análise de dispersão (quantidade vs. faturamento médio)

### 5. **Análise de Frete**
- Frete médio por loja
- Impacto do frete na competitividade

## 📊 Como Ler os Dados

### Carregamento dos Dados
```python
import pandas as pd

# URLs dos dados das 4 lojas
urls = {
    1: "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_1.csv",
    2: "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_2.csv",
    3: "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_3.csv",
    4: "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science/refs/heads/main/base-de-dados-challenge-1/loja_4.csv"
}

# Carregar e combinar dados
frames = []
for loja, url in urls.items():
    df = pd.read_csv(url)
    df['Loja'] = loja
    frames.append(df)

dados_completos = pd.concat(frames, ignore_index=True)
```

### Preparação dos Dados
```python
# Converter data para datetime
dados_completos['Data da Compra'] = pd.to_datetime(dados_completos['Data da Compra'], format='%d/%m/%Y')

# Criar coluna de faturamento (apenas preço, sem frete)
dados_completos['Faturamento'] = dados_completos['Preço']
```

## 🔍 Exemplos de Análises

### Faturamento por Loja
```python
faturamento_por_loja = dados_completos.groupby('Loja')['Faturamento'].sum().sort_values(ascending=False)
print(faturamento_por_loja)
```

### Produtos Mais Vendidos
```python
produtos_mais_vendidos = dados_completos.groupby('Produto').size().sort_values(ascending=False).head(10)
print(produtos_mais_vendidos)
```

### Avaliação Média por Loja
```python
avaliacao_media = dados_completos.groupby('Loja')['Avaliação da compra'].mean().round(2)
print(avaliacao_media)
```

## 📋 Principais Resultados

### **Ranking de Faturamento:**
1. **Loja 1**: R$ 1.534.509,12 (26,13%)
2. **Loja 2**: R$ 1.488.459,06 (25,35%)
3. **Loja 3**: R$ 1.464.025,03 (24,93%)
4. **Loja 4**: R$ 1.384.497,58 (23,58%)

### **Ranking de Satisfação:**
1. **Loja 3**: 4,05 ⭐
2. **Loja 2**: 4,04 ⭐
3. **Loja 4**: 4,00 ⭐
4. **Loja 1**: 3,98 ⭐

### **Recomendação Final:**
**Vender a Loja 4** por apresentar o menor faturamento e pior performance nas categorias principais.

## 🤝 Contribuição

Este projeto foi desenvolvido como parte do Challenge de Data Science da Alura. Contribuições são bem-vindas!

## 📝 Licença

Este projeto está sob licença aberta.
## 📧 Contato

- **Repositório**: [https://github.com/kaio326/challenge1-data-science](https://github.com/kaio326/challenge1-data-science)
- **Challenge Original**: [Alura Challenge Data Science](https://github.com/alura-es-cursos/challenge1-data-science)

### 📌 Notas Importantes:
- Os dados são fictícios e criados para fins educacionais
- As análises seguem metodologias padrão de Data Science
- O projeto inclui visualizações interativas para melhor compreensão dos dados
- Recomenda-se executar o notebook completo para visualizar todos os gráficos e análises

