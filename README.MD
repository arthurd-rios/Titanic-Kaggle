# Kaggle Titanic: Machine Learning from Disaster

Este repositório contém a minha solução para o desafio Titanic do Kaggle. O objetivo é prever quais passageiros sobreviveram ao naufrágio baseando-se em dados como idade, gênero e classe social.

Este foi o meu primeiro desafio de ciência de dados no Kaggle, onde alcancei um score de 0.78229.

## Variáveis Utilizadas

Para o treinamento dos modelos, utilizei as seguintes colunas processadas:

- Pclass: Classe do passageiro.
- IsFemale: Variável binária indicando o gênero feminino.
- DeckLevel: Representação numérica baseada na classe do passageiro (Primeira Classe = 3, Segunda Classe = 2, Terceira Classe = 1).
- FamilySize: Soma de 1 + Parch + SibSp.
- IsElderly: Variável binária para idosos.
- IsKid: Variável binária para crianças.
- IsTeen: Variável binária para adolescentes.

Observação: Notei posteriormente que o DeckLevel, da forma como foi construído, pode causar redundância com a coluna Pclass, já que ambos derivam diretamente da classe do passageiro.

## Engenharia de Recursos (Feature Engineering)

1. DeckLevel: Atribuí valores fixos baseados na classe. No futuro, pretendo explorar outras formas de extrair o nível do deck (como a partir da letra da cabine), pois pode conter informações valiosas que não foram totalmente aproveitadas nesta abordagem.
2. FamilySize: Calculado pela soma dos membros da família presentes no navio mais o próprio passageiro (1 + Parch + SibSp).
3. Faixas Etárias: Agrupei os passageiros em Kid, Teen, Adult e Elderly.
4. Tratamento de Nulos: Para preencher idades faltantes, utilizei os títulos presentes nos nomes (Mr, Miss, etc). Caso o passageiro não se enquadrasse em Kid, Teen ou Elderly através dessa lógica, ele foi classificado automaticamente como Adult (por este motivo, não foram necessários 4 encodeds, apenas 3).

## Desafios no Processamento de Teste

Durante o processamento do arquivo test.csv, identifiquei o título "Ms", que não estava previsto no script original. Para solucionar, tratei o título "Ms" da mesma forma que o título "Miss", seguindo a lógica aplicada no primeiro notebook.

## Modelagem e Resultados

Para a predição final, utilizei uma abordagem de ensemble (votação) combinando três modelos:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- XGBoost

A decisão final sobre a sobrevivência foi definida pela votação entre esses três algoritmos.

## Performance

- Score Final: 0.78229
- Considero este um bom resultado para um primeiro projeto, demonstrando a eficácia da engenharia de recursos e da combinação de diferentes modelos de classificação.
