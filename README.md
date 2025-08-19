# Projeto de Machine Learning: Previsão de Churn na Telecom X

## 1. Objetivo

Este projeto teve como objetivo principal desenvolver um pipeline de Machine Learning para prever a evasão (*churn*) de clientes na empresa Telecom X. A meta foi identificar os principais fatores que levam um cliente a cancelar seu serviço e construir um modelo preditivo capaz de sinalizar clientes com alto risco de evasão, permitindo que a empresa atue de forma proativa na retenção.

## 2. Pipeline do Projeto

O projeto foi estruturado nas seguintes etapas:

#### a. Análise e Preparação dos Dados
- **Análise de Desbalanceamento:** Foi verificado que o conjunto de dados era desbalanceado, com **73.5%** de clientes ativos ("Não Churn") e **26.5%** de clientes que evadiram ("Churn").
- **Balanceamento com SMOTE:** Para corrigir o desbalanceamento e evitar que os modelos fossem tendenciosos para a classe majoritária, foi aplicada a técnica SMOTE (*Synthetic Minority Over-sampling Technique*), criando um conjunto de dados de treino perfeitamente balanceado.
- **Encoding de Variáveis:** As variáveis categóricas (como `gender`, `internet_service`, etc.) foram convertidas para um formato numérico através do método *One-Hot Encoding*.
- **Divisão em Treino e Teste:** O conjunto de dados foi dividido em **70% para treinamento** e **30% para teste**, garantindo uma avaliação robusta e imparcial dos modelos.
- **Padronização:** As variáveis numéricas contínuas (`tenure`, `monthly_charges`, `total_charges`) foram padronizadas (*StandardScaler*) para os modelos sensíveis à escala.

#### b. Modelagem Preditiva
Foram treinados e avaliados dois modelos distintos para comparar diferentes abordagens:
1.  **Regressão Logística:** Um modelo linear, rápido e altamente interpretável, utilizado como *baseline*.
2.  **Random Forest:** Um modelo de conjunto (*ensemble*) mais complexo, conhecido por sua alta performance e capacidade de capturar relações não-lineares nos dados.

## 3. Avaliação e Desempenho dos Modelos

Embora a Regressão Logística tenha apresentado maior precisão e ausência de *overfitting*, o **Random Forest foi o modelo com melhor desempenho geral para o objetivo de negócio**, principalmente por seu **Recall superior**. Isso significa que ele é mais eficaz em identificar a grande maioria dos clientes que realmente pretendem cancelar, o que é crucial para as estratégias de retenção.

## 4. Principais Fatores que Influenciam o Churn

A análise de importância das variáveis, consistente em ambos os modelos, revelou os seguintes fatores como os mais determinantes:

- **Fatores de Maior Risco de Churn (Evasão):**
    1.  **Contrato Mês a Mês (`contract_Month-to-month`):** O principal indicador de risco.
    2.  **Serviço de Fibra Ótica (`internet_service_Fiber optic`):** Sugere possíveis problemas de preço, qualidade ou instabilidade com este serviço.
    3.  **Pagamento via Cheque Eletrônico (`payment_method_Electronic check`):** Um método de pagamento associado a maior evasão.
    4.  **Ausência de Serviços de Proteção (`online_security_No`, `tech_support_No`):** Clientes sem estes serviços adicionais são mais propensos a sair.

- **Fatores de Maior Retenção:**
    1.  **Longo Tempo de Contrato (`tenure`):** A variável mais importante para prever a permanência de um cliente.
    2.  **Contratos de Longo Prazo (`contract_Two year`, `contract_One year`):** A melhor ferramenta para garantir a fidelidade do cliente.
    3.  **Cobranças Totais Elevadas (`total_charges`):** Um indicador de um relacionamento duradouro e valioso.

## 5. Recomendações Estratégicas

Com base nos insights dos modelos, as seguintes ações são recomendadas para a Telecom X:

1.  **Foco na Migração de Contratos:** Criar campanhas agressivas para converter clientes de planos mensais para anuais ou bianuais.
2.  **Aprimorar a Experiência da Fibra Ótica:** Investigar e solucionar os motivos de insatisfação (preço, suporte, instabilidade) dos clientes deste serviço.
3.  **Fortalecer o Onboarding:** Oferecer pacotes de `online_security` e `tech_support` como um benefício nos primeiros meses de contrato para aumentar o engajamento e a barreira de saída.
4.  **Incentivar Métodos de Pagamento Automáticos:** Oferecer benefícios para clientes que migrarem do cheque eletrônico para débito automático ou cartão de crédito.
