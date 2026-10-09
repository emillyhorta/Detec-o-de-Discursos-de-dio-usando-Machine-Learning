# Classificação de Discurso de Ódio contra Mulheres com Machine Learning

Projeto acadêmico desenvolvido na disciplina **Tópicos de Biotecnologia 2**, utilizando técnicas de Processamento de Linguagem Natural (PLN) e Machine Learning para classificar comentários publicados no Twitter como discurso de ódio ou não ódio direcionado a mulheres.

## Sobre o projeto

A violência de gênero também se manifesta no ambiente digital. Diante desse cenário, este projeto explora o uso de modelos de aprendizado de máquina para identificar padrões linguísticos associados ao discurso de ódio contra mulheres.

Utilizamos o dataset **[MINA-BR — Rotulada](https://redu.unicamp.br/dataset.xhtml?persistentId=doi:10.25824/redu/MQD68Z)**, composto por comentários em português brasileiro classificados em duas categorias:

- `0` — Não ódio
- `1` — Ódio

O objetivo foi comparar diferentes algoritmos de classificação e analisar seus resultados, considerando especialmente os desafios de identificar discursos nocivos em dados textuais.

## Objetivos

- Aplicar técnicas de Processamento de Linguagem Natural em textos em português.
- Preparar e transformar comentários em representações numéricas.
- Treinar e comparar diferentes modelos de classificação supervisionada.
- Avaliar o desempenho dos modelos utilizando métricas de classificação.
- Investigar os desafios relacionados ao desbalanceamento dos dados e à identificação de discurso de ódio.

## Tecnologias e bibliotecas

- **Python 3** — linguagem de programação.
- **Google Colab** — ambiente de desenvolvimento.
- **Pandas e NumPy** — manipulação e processamento de dados.
- **NLTK e spaCy** — processamento de linguagem natural.
- **Scikit-learn** — vetorização, treinamento e avaliação dos modelos.
- **Matplotlib e Seaborn** — visualização dos resultados.
- **WordCloud** — geração de nuvem de palavras.

## Metodologia

### 1. Preparação e limpeza dos dados

Realizamos o tratamento dos textos para reduzir ruídos e padronizar os dados utilizados no treinamento, incluindo:

- Remoção de URLs, menções, pontuações e caracteres especiais.
- Conversão dos textos para letras minúsculas.
- Remoção de stopwords e tokens curtos.
- Aplicação de stemming para reduzir palavras às suas raízes.
- Análise da distribuição das classes e tratamento do desbalanceamento.

O dataset utilizado possuía **2.091 registros**, sendo 1.751 classificados como não ódio e 340 como ódio.

### 2. Vetorização dos textos

Utilizamos a técnica **TF-IDF (Term Frequency–Inverse Document Frequency)** para transformar os textos em representações numéricas, atribuindo pesos aos termos de acordo com sua relevância nos documentos.

Essa representação foi utilizada como entrada para os três modelos avaliados.

### 3. Treinamento dos modelos

O dataset foi dividido em conjuntos de treinamento (80%) e teste (20%), utilizando divisão estratificada para preservar a proporção entre as classes.

Foram avaliados três algoritmos:

| Modelo | Descrição |
|---|---|
| Multinomial Naive Bayes | Classificador probabilístico utilizado como abordagem de referência. |
| Random Forest | Modelo baseado em múltiplas árvores de decisão. |
| Linear SVM | Classificador que busca separar as classes por meio de uma margem de decisão. |

Para lidar com o desbalanceamento, foram utilizadas configurações específicas nos modelos e uma estratégia de divisão estratificada dos dados.

### 4. Avaliação

Os modelos foram avaliados utilizando:

- **Acurácia:** proporção total de classificações corretas.
- **Precisão:** proporção de previsões positivas que estavam corretas.
- **Recall:** proporção dos casos positivos reais identificados pelo modelo.
- **F1-Score:** média harmônica entre precisão e recall.
- **Matriz de confusão:** análise dos acertos e erros de classificação.

## Resultados

Os resultados evidenciaram diferenças entre os modelos, especialmente na identificação da classe de discurso de ódio.

| Modelo | Acurácia | Precisão (ódio) | Recall (ódio) | F1-Score |
|---|---:|---:|---:|---:|
| Random Forest | 87,59% | 70,00% | 41,18% | 51,85% |
| Multinomial Naive Bayes | 80,91% | 43,62% | 60,29% | 50,62% |
| Linear SVM | 80,67% | 42,70% | 55,88% | 48,41% |

*Valores apresentados conforme o estudo comparativo do relatório.*

### Principais observações

- **Random Forest:** apresentou a maior acurácia e precisão, mas identificou uma proporção menor dos casos reais de discurso de ódio.
- **Multinomial Naive Bayes:** apresentou o maior recall, identificando mais casos reais da classe de interesse, embora com mais falsos positivos.
- **Linear SVM:** apresentou recall intermediário, mas obteve o menor F1-Score entre os modelos avaliados.

A comparação demonstra por que a acurácia, isoladamente, não é suficiente para avaliar modelos aplicados a problemas com classes desbalanceadas.

## Limitações e desafios

A classificação automática de discurso de ódio apresenta desafios que vão além do treinamento dos algoritmos.

Entre eles, destacam-se:

- Identificação de ironias, metáforas, memes e gírias.
- Interpretação de contextos e sentidos implícitos.
- Mudanças na linguagem utilizada nas redes sociais.
- Diferenças culturais e linguísticas.
- Desbalanceamento entre as classes e possibilidade de erros de classificação.

Por isso, os resultados devem ser interpretados considerando as características do dataset e as limitações dos modelos. A classificação automática não substitui a análise contextual humana.

## Conclusão

O projeto permitiu explorar diferentes etapas de um pipeline de Machine Learning aplicado a textos, desde a preparação dos dados até a avaliação dos modelos.

Além da comparação técnica, o estudo reforçou a importância de selecionar métricas alinhadas ao problema investigado. Em aplicações relacionadas à violência de gênero, deixar de identificar casos reais e classificar incorretamente comentários são limitações relevantes que precisam ser consideradas.

A experiência também evidenciou como técnicas de ciência de dados podem ser exploradas na investigação de problemas sociais presentes no ambiente digital.

## Aprendizados

- Processamento de Linguagem Natural com Python.
- Pré-processamento e vetorização de textos com TF-IDF.
- Classificação supervisionada com Scikit-learn.
- Comparação de algoritmos de Machine Learning.
- Avaliação de modelos com métricas e matrizes de confusão.
- Análise crítica de resultados e limitações de modelos preditivos.

## Autoria

**Emilly Horta e Nayra Oliveira**

Trabalho acadêmico desenvolvido na disciplina **Tópicos de Biotecnologia 2**, no contexto do Mestrado em Biotecnologia.

---

*Este projeto tem finalidade acadêmica e exploratória. Os modelos avaliados não devem ser considerados sistemas prontos para moderação automática ou tomada de decisão em situações reais sem validação adicional.*
