Telecom X: Modelagem Preditiva de Churn de Clientes
📖 Visão Geral do Projeto
Este repositório representa a segunda fase do projeto de análise da Telecom X, focada na construção e avaliação de modelos de Machine Learning para prever a evasão de clientes (churn). Partindo de um conjunto de dados já limpo e explorado na primeira fase, este projeto aborda todo o ciclo de vida da modelagem preditiva, desde a preparação final dos dados até a interpretação dos resultados e a recomendação de estratégias de negócio.

O objetivo final é criar um modelo preditivo que não só identifique com precisão os clientes em risco de cancelamento, mas que também forneça insights sobre quais fatores mais influenciam essa decisão, permitindo que a empresa atue de forma proativa para aumentar a retenção.

🎯 O Problema de Negócio
Com uma taxa de churn de 26,5%, a Telecom X enfrenta um desafio significativo que afeta diretamente a sua receita. A capacidade de prever quais clientes estão prestes a sair, antes que o façam, é uma vantagem competitiva crucial. Este projeto visa transformar dados brutos em uma ferramenta estratégica para a equipa de retenção, respondendo à pergunta: "Podemos prever com precisão quais clientes irão cancelar e porquê?"

🛠️ Metodologia e Pipeline do Projeto
O projeto seguiu um pipeline estruturado de modelagem de dados:

Preparação e Codificação dos Dados:

As variáveis categóricas restantes foram transformadas em formato numérico utilizando a técnica de One-Hot Encoding.

Variáveis com baixo poder preditivo, como customerID e PhoneService, foram removidas para simplificar e focar os modelos.

Análise de Desequilíbrio de Classes:

Foi confirmado um desequilíbrio significativo nos dados (73,5% "Não Churn" vs. 26,5% "Churn"). Esta constatação foi fundamental para a avaliação dos modelos, dando maior importância a métricas como Recall e F1-Score em detrimento da acurácia.

Seleção e Treinamento dos Modelos:

Foram escolhidos dois modelos distintos para uma análise comparativa:

Regressão Logística: Um modelo linear, rápido e altamente interpretável, ideal para criar uma linha de base e entender a influência de cada variável. Exigiu a padronização (StandardScaler) dos dados.

Random Forest: Um modelo de ensemble baseado em árvores, robusto e de alto desempenho, capaz de capturar relações complexas e não lineares nos dados sem a necessidade de normalização.

Divisão e Avaliação:

Os dados foram divididos em 70% para treino e 30% para teste, utilizando a estratificação para garantir que a proporção de churn fosse a mesma em ambos os conjuntos.

📊 Análise de Desempenho dos Modelos
A avaliação crítica mostrou que, embora ambos os modelos tivessem uma acurácia semelhante (~80%), o seu comportamento e utilidade para o negócio eram distintos.

Métrica	Regressão Logística (Esperado)	Random Forest (Esperado)
Acurácia	~80%	~80%
Recall (para Churn)	~53%	~49%
Precisão (para Churn)	~65%	~67%

Exportar para as Planilhas
Conclusão da Avaliação: A Regressão Logística demonstrou um Recall ligeiramente superior, tornando-se marginalmente mais eficaz em "apanhar" os clientes que de facto cancelam. No entanto, ambos os modelos de base mostraram-se insuficientes para uma estratégia de retenção robusta, reforçando a necessidade de aplicar técnicas de balanceamento (como SMOTE) para melhorar significativamente o Recall.

🔑 Fatores Mais Relevantes para a Evasão
A análise de importância das variáveis, tanto através dos coeficientes da Regressão Logística como do feature_importance_ do Random Forest, convergiu para os mesmos fatores críticos:

Fatores Contratuais: tenure (tempo de permanência) e o Contract_Type (especialmente o mensal vs. o de dois anos) são, de longe, os preditores mais fortes.

Fatores Financeiros: MonthlyCharges (mensalidade) e TotalCharges (total gasto) têm um alto impacto.

Tipo de Serviço: Ter InternetService_Fiber optic é um forte indicador de risco.

Método de Pagamento: PaymentMethod_Electronic check também se destacou como um fator de risco relevante.

🚀 Recomendações Estratégicas
Com base nos modelos, as seguintes ações são propostas:

Implementar um Sistema de Pontuação de Risco: Utilizar o modelo preditivo para atribuir uma "pontuação de risco de churn" a cada cliente. A equipa de retenção deve focar os seus esforços naqueles com as pontuações mais altas.

Personalizar Campanhas de Retenção:

Para clientes com contrato mensal e baixo tenure: Oferecer descontos agressivos para a migração para contratos anuais.

Para clientes de Fibra Ótica com altas mensalidades: Agregar valor ao serviço, incluindo Suporte Técnico ou Segurança Online como parte do pacote.



pip install pandas scikit-learn matplotlib seaborn jupyterlab imbalanced-learn
(Nota: imbalanced-learn é incluído para permitir a implementação futura do SMOTE)

Execute o Notebook de Análise:
Abra o Jupyter Lab e navegue até ao notebook principal para ver todo o processo de modelagem.

Bash

jupyter-lab
🛠️ Tecnologias Utilizadas
Python

Pandas para manipulação de dados

Scikit-learn para pré-processamento, modelagem e avaliação

Matplotlib e Seaborn para visualização

Imbalanced-learn para técnicas de balanceamento de dados
