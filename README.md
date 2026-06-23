# Case Técnico Data Science - iFood

## 📌 Visão Geral

Este projeto foi desenvolvido como solução para o case técnico de Data Science do iFood. O objetivo é construir um modelo preditivo capaz de estimar a probabilidade de um cliente **completar uma oferta**, utilizando dados históricos de transações, perfis de clientes e características das ofertas.

Durante o desenvolvimento, descobrimos que **variáveis demográficas** (idade, gênero e limite de crédito) têm baixa relevância preditiva. Por isso, o foco da solução foi deslocado para **variáveis comportamentais**, que se mostraram muito mais impactantes.

---

## 🎯 Objetivo

- Analisar os dados de ofertas, clientes e transações
- Desenvolver um modelo de classificação para prever a conclusão de ofertas
- Identificar os principais fatores que influenciam a conversão
- Gerar recomendações acionáveis com projeção de ganhos para o negócio

---

## 📊 Principais Resultados

### Modelo Final
- **Melhor modelo**: Random Forest
- **AUC no teste**: **0.9765** (vs 0.9522 da Regressão Logística)
- **Variáveis mais importantes**: `discount_value`, `offer_frequency`, `total_offers_completed`, `avg_reward`

### Projeção de Ganhos com Foco em Engajamento

Ao segmentar os clientes por **histórico de engajamento** (número de ofertas já completadas), foi possível projetar os seguintes ganhos:

| Segmento                    | Ofertas | Conversão Atual | Conversão Projetada | Ganho Incremental |
|----------------------------|---------|------------------|---------------------|-------------------|
| Alto Engajamento           | 30.686  | 79,8%            | 82%                 | +669              |
| Médio Engajamento          | 27.414  | 42,0%            | 68%                 | **+7.139**        |
| Baixo / Sem Engajamento    | 18.177  | 0%               | 45%                 | **+8.180**        |
| **Total**                  | 76.277  | -                | -                   | **+15.988**       |

> **Uplift total projetado: +44,4%** em conversões

---

## 📁 Estrutura do Repositório
ifood-case/
├── data/
│   ├── raw/                    # Dados originais (JSON)
│   └── processed/              # Dados processados (Parquet)
├── notebooks/
│   ├── 1_data_processing.ipynb # Processamento, limpeza e feature engineering
│   └── 2_modeling.ipynb        # Modelagem, avaliação e análise de impacto
├── presentation/
│   └── iFood_Projecao_Ganhos_Engajamento.pptx
├── src/                        # Código reutilizável (opcional)
├── README.md
├── requirements.txt
└── .gitignore

---

## 🚀 Como Executar

### Recomendação

Recomenda-se utilizar o **Databricks Community Edition** para rodar os notebooks, pois o projeto foi desenvolvido com PySpark + Delta Lake.

### Passos

1. Clone o repositório
2. Coloque os arquivos `offers.json`, `profile.json` e `transactions.json` na pasta `data/raw/`
3. Abra os notebooks na ordem:
   - `1_data_processing.ipynb`
   - `2_modeling.ipynb`

### Tecnologias Utilizadas

- **PySpark** (Databricks)
- **Delta Lake** / Parquet
- **Python** (Pandas, Scikit-learn)
- **Random Forest** (modelo final)
- **Matplotlib / Seaborn** (visualização)

---

## 💡 Principais Insights e Recomendações

1. **Foco em Engajamento Comportamental**
   - Dados demográficos têm baixo poder preditivo.
   - Clientes com histórico de conversão respondem muito melhor a ofertas.

2. **Priorização por Segmento**
   - **Alto Engajamento**: Aumentar frequência e valor das ofertas.
   - **Médio Engajamento**: Maior potencial de ganho (+62%). Focar esforços aqui.
   - **Baixo Engajamento**: Revisar estratégia ou reduzir volume.

3. **Otimização de Ofertas**
   - `discount_value` e `avg_reward` são os principais drivers de conversão.
   - Estruturas de oferta mais agressivas tendem a performar melhor.

4. **Modelo em Produção**
   - O modelo Random Forest está pronto para ser utilizado em scoring de propensão.

---

## 📌 Observações Técnicas

- O projeto seguiu a arquitetura **Medallion** (Bronze → Silver → Gold).
- A análise foi redesenhada para priorizar variáveis comportamentais após análise de importância das features.
- O notebook `2_modeling.ipynb` contém tanto o baseline (Logistic Regression) quanto o modelo otimizado (Random Forest com Cross Validation).

---

## 👤 Autor

Desenvolvido por: **Silvio Rodrigues de Faria Junior**

---

**Obrigado pelo interesse no projeto!**  
Qualquer dúvida ou sugestão, sinta-se à vontade para entrar em contato.

