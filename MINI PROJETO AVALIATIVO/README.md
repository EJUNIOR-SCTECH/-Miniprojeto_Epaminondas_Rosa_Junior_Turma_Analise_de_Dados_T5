# Miniprojeto Avaliativo - Análise de Dados de Varejo

## 📌 Descrição do Projeto
Este repositório contém a Análise Exploratória de Dados (EDA) e o processo de Limpeza e Transformação (ETL) aplicados a uma base de dados do setor varejista. O objetivo é diagnosticar inconsistências, realizar o tratamento de textos, nulos e datas, e extrair métricas estatísticas e *insights* sobre o comportamento das vendas.

---

## 🔍 Critério 1: Reflexão Teórica sobre a Importância do ETL

O processo de **ETL (Extract, Transform, Load)** é a espinha dorsal da Análise de Dados. Ele garante que os dados brutos sejam convertidos em informações confiáveis, protegendo os modelos analíticos e os relatórios de negócios contra distorções graves.

### Por que o ETL é fundamental na prática?
1. **Garantia de Qualidade e Integridade:** Sem a etapa de sanitização, erros de digitação e valores ausentes mascarados como texto contaminam os resultados. Por exemplo, nesta base de dados, caso o tratamento da coluna de categoria (`PR_CAT`) não fosse realizado, o ruído `#N/D` seria contabilizado e exibido nos gráficos/tabelas como se fosse uma **categoria real de produto**, distorcendo os relatórios de vendas.
2. **Correção de Tipos e Habilitação de Cálculos:** Dados importados como texto (`string`) impedem operações estatísticas essenciais. A conversão de colunas como `CL_FHL` (número de filhos) para tipo numérico foi indispensável para possibilitar o cálculo de métricas como média, mediana, desvio padrão e quantis.
3. **Tomada de Decisão Segura:** O ETL transforma dados caóticos em uma *fonte única da verdade*, assegurando que os gestores tomem decisões estratégicas baseadas em métricas precisas.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas
- **Linguagem:** Python 3.13
- **Ambiente:** Jupyter Notebook / Visual Studio Code
- **Bibliotecas:**
  - `pandas`: Manipulação e análise de dados
  - `numpy`: Suporte a operações numéricas e tratamento de nulos
  - `IPython.display`: Exibição formatada de tabelas

---

## ⚙️ Processo de Limpeza e Tratamento (ETL Aplicado)
- **Diagnóstico e Remoção de Inconsistências:** Mapeamento e substituição de strings inválidas (`#N/D`, `#N/A`, `?`, `null`, `None`, `nan`) por `np.nan`, preenchendo as categorias ausentes com `"Sem Categoria"`.
- **Conversão de Tipos:**
  - Coluna `DATA`: Convertida para o formato `datetime` (`%d/%m/%Y`).
  - Colunas `CL_FHL` e `CL_EC`: Convertidas para o tipo numérico (`pd.to_numeric`) para permitir agregação estatística.
- **Higienização do Dataset:** Remoção de espaços extras nos nomes das colunas e eliminação de registros duplicados.

---

## 📁 Estrutura do Repositório
- `miniprojeto.ipynb`: Notebook Jupyter contendo todo o código de ETL, estatística descritiva, agrupamentos e conclusões.
- `df_limpo.csv`: Base de dados tratada e exportada após a limpeza e conversão dos tipos.
- `.gitignore`: Arquivo de configuração para ignorar a base bruta pesada (`Base Varejo.csv`).
- `README.md`: Documentação técnica e relatório descritivo do projeto.

---

## 📊 Principais Resultados e Insights
1. **Predomínio por Categoria:** A categoria **ALIMENTOS** lidera o volume total de vendas (mais de 384 mil itens), seguida por **HIGIENE** e **LIMPEZA**.
2. **Distribuição por Gênero e Segmento:** O Segmento B concentrou o maior volume de compras com distribuição idêntica entre homens e mulheres. No Segmento C, o público feminino possui maior representatividade.
3. **Evolução Temporal:** Registrou-se crescimento contínuo de vendas entre 2019 e 2021 (pico de 216 mil itens em 2021).
4. **Perfil Familiar (`CL_FHL`):** A análise descritiva revelou mediana e moda iguais a 0, indicando que a maioria dos clientes cadastrados não possui filhos.

---

## 🚀 Como Executar o Projeto
1. Clone este repositório:
   ```bash
   git clone [https://github.com/EJUNIOR-SCTECH/-Miniprojeto_Epaminondas_Rosa_Junior_Turma_Analise_de_Dados_T5.git](https://github.com/EJUNIOR-SCTECH/-Miniprojeto_Epaminondas_Rosa_Junior_Turma_Analise_de_Dados_T5.git)