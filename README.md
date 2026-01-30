# A IA realmente entende a Contabilidade Brasileira? 🤖📚

> Framework para avaliação da capacidade de modelos de Inteligência Artificial em interpretar normas contábeis complexas (CPC 00).

Este repositório contém o código fonte e a fundamentação teórica para o estudo de caso sobre a aplicação de **Vetorização (Embedding)** e **RAG (Retrieval-Augmented Generation)** na interpretação de documentos contábeis brasileiros.

## 📄 Sobre o Projeto

A Inteligência Artificial Generativa é excelente em criar textos fluídos, mas como garantir que ela entende a diferença técnica entre conceitos contábeis específicos?

Este projeto propõe um método objetivo para medir se a IA organizou as ideias corretamente, focando em um conjunto de métricas quantitativas para validar a "busca semântica" em normas técnicas.

### 📂 Conteúdo do Repositório

* `Artigo_vetorizacao_IA_CPC.ipynb`: Jupyter Notebook com o pipeline completo de ingestão, vetorização e cálculo das métricas.
* `573_CPC00(R2)`: Norma CPC00, usada na análise. Também disponível aqui: https://www.cpc.org.br/CPC/Documentos-Emitidos/Pronunciamentos/Pronunciamento?Id=80 

## 📊 Metodologia e Métricas

Para medir o desempenho da IA sem subjetivismo, utilizamos quatro indicadores principais:

### 1. Silhouette Score (Organização)
Mede a qualidade dos agrupamentos (clusters).
* **O que diz:** Quão bem a IA separa conceitos distintos no espaço vetorial.
* **Interpretação:** Quanto mais próximo de 1, mais definidos e coesos são os conceitos na "cabeça" da IA.

### 2. Precision@5 (Busca)
Mede a eficácia da recuperação de informação (RAG).
* **O que diz:** Ao buscar por um conceito, a resposta correta aparece nas 5 primeiras sugestões da IA?
* **Interpretação:** Essencial para sistemas de tira-dúvidas. Se a IA não acha a informação, ela inventa.

### 3. ARI - Adjusted Rand Index (Fidelidade)
Mede a similaridade entre os agrupamentos da IA e a estrutura original do documento.
* **O que diz:** A IA agrupou os parágrafos do CPC 00 da mesma forma que os contadores que escreveram a norma?
* **Interpretação:** Um ARI alto indica que a IA "pensa" a estrutura do documento de forma similar à humana/técnica original.

### 4. Score Médio (O "Ranking Final")
Uma métrica composta criada para facilitar a tomada de decisão.
* **Cálculo:** Média harmonizada/ponderada entre a capacidade de Organização (*Silhouette/ARI*) e a capacidade de Busca (*Precision*).
* **Objetivo:** Oferecer um número único para rankear qual modelo (ex: OpenAI vs Gemini vs Llama) é o mais equilibrado para tarefas contábeis.

## 🚀 Tecnologias Utilizadas

* **Python 3.x**
* **Sentence Transformers**: Geração de embeddings.
* **Scikit-Learn**: Cálculo de métricas (Silhouette, ARI).
* **Pandas/NumPy**: Manipulação de dados e cálculo do Score Médio.
* **Transformers (Hugging Face)**: Tokenização e modelos de linguagem.

## 🛠️ Como Executar

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/LucasMielke/vetorizacao_ia.git]
    ```
2.  Instale as dependências
3.  Execute o notebook para reproduzir os testes:
    ```bash
    jupyter notebook Artigo_vetorizacao_IA_CPC.ipynb
    ```

## 📈 Principais Conclusões

O estudo demonstrou que não existe uma "Bala de Prata". O Gemini teve o melhor desempenho para o caso específico da CPC00, mas os resultados podem variar bastante conforme o documento usado. Modelos com **Score Médio** mais alto geralmente combinam um bom treino em português (contexto local) com janelas de contexto amplas.

O **ARI** revelou que alguns modelos famosos "bagunçam" a estrutura lógica das normas, agrupando parágrafos de temas diferentes, o que aumenta o risco de alucinação em perguntas complexas.

---

**Autor:** Lucas Mielke
