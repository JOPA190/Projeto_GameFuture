# Comitê de Classificadores (Ensemble) Aplicado ao Mercado de Video Games 🎮

Este projeto é um sistema de Inteligência Artificial baseado em Aprendizado Supervisionado desenvolvido como requisito para a avaliação A3 da disciplina de Inteligência Artificial do curso de Engenharia da Informação da Universidade São Judas Tadeu (USJT), sob orientação do Prof. Rodrigo Bossini Tavares Moreira.

## 👥 Integrantes do Projeto

* **Bryan Lira Junqueira** (RA: 825110147)
* **Felipe Cabral De Aquino** (RA: 82510945)
* **Gabriel Martins Gomes De Oliveira** (RA: 825128943)
* **Guilherme Fernandes Lima** (RA: 82516937)
* **João Carlos Oliveira Passos** (RA: 82510149)

---

## 🎯 Objetivo

O objetivo central deste trabalho é construir um pipeline de Ensemble Learning (Comitê de Classificadores) capaz de prever a percepção crítica (sucesso) de um jogo de videogame com base em variáveis mercadológicas e técnicas. A abordagem combina múltiplos algoritmos para reduzir erros individuais e maximizar a performance preditiva através de uma votação majoritária.

## 📊 Base de Dados

A inferência foi realizada a partir da base de dados real **"Video Game Sales with Ratings"**, extraída do Kaggle. 

**Variáveis Independentes (Features):**
* **Platform:** Dispositivo de publicação (PS4, Xbox, PC, etc.)
* **Genre:** Categoria temática do jogo (Ação, RPG, Esporte, etc.)
* **Year_of_Release:** Ano de lançamento
* **Global_Sales:** Total de vendas globais
* **Rating:** Classificação etária (Faixa de público-alvo)

**Variável Alvo (Target):**
Criada a partir da nota dos críticos (`Critic_Score`), o sucesso do jogo foi categorizado em três classes discretas:
* ✅ **Bom:** Score $\ge 75$
* ⚠️ **Médio:** $50 \le$ Score $< 75$
* ❌ **Ruim:** Score $< 50$

## 🛠️ Tecnologias e Metodologia

O projeto foi desenvolvido em **Python** no ambiente Google Colab, utilizando as bibliotecas `pandas`, `matplotlib` e `scikit-learn`.

**Etapas de Pré-processamento:**
1.  Limpeza e remoção de valores inconsistentes (`NaN`).
2.  Engenharia de features com *One-Hot Encoding* (`pd.get_dummies`) para variáveis categóricas.
3.  Divisão da base de dados: 80% para treino e 20% para teste.

**Modelos Individuais:**
* **K-Nearest Neighbors (KNN):** Classificação por vizinhança espacial com $k=5$.
* **Árvore de Decisão:** Algoritmo de quebras lógicas hierárquicas, oferecendo alta interpretabilidade.
* **Random Forest:** Conjunto com 150 árvores independentes para maior robustez e redução de *overfitting*.

**Comitê (Ensemble):**
* Implementação de um **Voting Classifier** utilizando *Hard Voting*. A predição final é determinada pela classe que receber a maioria simples dos votos dos três modelos base.

## 📈 Resultados Alcançados

O Ensemble superou o desempenho dos classificadores individuais, compensando as fraquezas isoladas de cada modelo. 

| Modelo | Acurácia (%) |
| :--- | :--- |
| KNN | 60.52% |
| Árvore de Decisão | 55.25% |
| Random Forest | 61.39% |
| **Comitê (Ensemble)** | **61.51%** |

*Nota: O modelo demonstrou alta eficácia em identificar jogos da classe "Médio" (maioria da base), porém apresentou desafios na distinção estrita entre "Bom" e "Ruim" devido à natureza subjetiva das notas dos críticos.*

## 🚀 Como Executar

1. Clone o repositório ou faça o download do notebook `A3_prot.ipynb` (`a3_prot (2).py`).
2. Faça o upload do dataset `Video_Games_Sales_as_at_22_Dec_2016.csv` para o seu Google Drive (ou ajuste o caminho do arquivo no código).
3. Execute as células do notebook sequencialmente em um ambiente com suporte a Python (recomendado Google Colab).
4. O código fará a limpeza, o treinamento dos classificadores, exibirá o placar de acurácia e, por fim, plotará a Matriz de Confusão do Comitê.

## 🔮 Melhorias Futuras

* **Balanceamento de Dados:** Aplicação de técnicas como SMOTE para corrigir o desbalanceamento das classes.
* **Soft Voting:** Explorar a votação por probabilidade ao invés de *Hard Voting* para decisões mais calibradas.
* **Novos Modelos (Boosting):** Incorporar algoritmos avançados como XGBoost ou LightGBM no comitê.
