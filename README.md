
# Case Técnico Data Science - iFood

## 📌 Visão Geral

Este projeto foi desenvolvido como solução para o case técnico de Data Science do iFood. O objetivo principal foi construir um modelo preditivo para estimar a probabilidade de um cliente **completar uma oferta**.

Durante a análise, identificamos que **variáveis demográficas** (idade, gênero e limite de crédito) possuem baixa relevância preditiva. Por isso, o foco foi deslocado para **variáveis comportamentais**, que se mostraram muito mais impactantes para o problema de negócio.

---

## 🎯 Objetivo

- Analisar os dados de ofertas, perfis e transações
- Identificar os principais drivers de conversão de ofertas
- Segmentar clientes por nível de engajamento comportamental
- Projetar ganhos potenciais com ações direcionadas

---

## 📊 Principais Resultados

### Modelo Preditivo
- **Melhor modelo**: Random Forest
- **AUC no teste**: **0.9765**
- **Variáveis mais importantes**: `discount_value`, `offer_frequency`, `total_offers_completed`

### Segmentação Comportamental por Engajamento

Os clientes foram segmentados com base no histórico de ofertas completadas:

| Segmento                    | Clientes | Ofertas | Taxa de Conversão | Ticket Médio | Desconto Médio |
|----------------------------|----------|---------|-------------------|--------------|----------------|
| **Alto Engajamento**       | 6.307    | 30.686  | **79,8%**         | R$ 19,97     | R$ 4,43        |
| **Médio Engajamento**      | 6.467    | 27.414  | **42,0%**         | R$ 12,29     | R$ 3,95        |
| **Baixo / Sem Engajamento**| 4.220    | 18.177  | **0%**            | R$ 3,75      | R$ 4,19        |

### Projeção de Ganhos (Foco no Médio Engajamento)

| Cenário                    | Taxa de Conversão | Ganho Adicional em Faturamento |
|---------------------------|-------------------|--------------------------------|
| Cenário Atual             | 42,0%             | —                              |
| **Cenário Meio-Termo**    | **60%**           | **+ R$ 60.792**                |
| **Melhor dos Mundos**     | **79,8%**         | **+ R$ 195.590**               |

> O grupo de **Médio Engajamento** representa a maior oportunidade de ganho incremental.

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

## 💡 Principais Insights

- Variáveis **demográficas** têm baixa importância no modelo.
- Variáveis **comportamentais** são os principais drivers de conversão (`discount_value`, `offer_frequency` e `total_offers_completed`).
- O grupo de **Médio Engajamento** é o que apresenta maior potencial de melhoria com ajuste na estratégia de descontos.
- O grupo de **Alto Engajamento** já performa bem e recebe os maiores descontos.
- O grupo de **Baixo Engajamento** tem conversão nula e ticket médio muito baixo.

---

## 🚀 Como Executar

Recomenda-se rodar os notebooks na seguinte ordem:

1. `1_data_processing.ipynb`
2. `2_modeling.ipynb`

O projeto foi desenvolvido utilizando **PySpark** no Databricks, mas também pode ser adaptado para execução local com Spark.

---

## 📌 Observações Técnicas

- Arquitetura utilizada: **Medallion** (Bronze → Silver → Gold)
- O modelo final priorizou variáveis comportamentais após análise de importância das features
- A análise de cenários foi feita com base em segmentação comportamental, e não demográfica

---

## 👤 Autor

**Silvio Rodrigues de Faria Junior**

---

**Obrigado pelo interesse no projeto!**

