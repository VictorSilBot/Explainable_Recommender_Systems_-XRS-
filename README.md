# Vídeo:
[![Assista ao vídeo](https://img.youtube.com/vi/I7LMIFRU7ac/maxresdefault.jpg)](https://www.youtube.com/watch?v=I7LMIFRU7ac)


# Projeto: Sistemas de Recomendação Explicáveis (XRS) com 3 Abordagens

Material didático desenvolvido para a Fase 2 do projeto da disciplina  
**SCC0284 / SCC5966 – Sistemas de Recomendação** (ICMC-USP, 2º Sem/2025)

**Alunos:**  
- Victor Silva Botelho (N° USP: 15645421)  
- João Pedro Barbosa Madeira (N° USP: 13683038)  

**Professor:** Marcelo G. Manzato

---

## 🎯 Motivação: Tornando Recomendadores Mais Transparentes

Grande parte dos sistemas de recomendação funciona como uma **caixa-preta**: o sistema sugere algo, mas não explica *por que* aquela recomendação faz sentido.  
Este projeto demonstra, de forma didática, como implementar **três tipos de Sistemas de Recomendação Explicáveis (XRS)** usando o dataset **MovieLens 100k**.

---

## 💡 Três Abordagens de XRS

O notebook principal deste repositório demonstra três formas diferentes de gerar recomendações acompanhadas de explicações claras e interpretáveis.

---

### 🔹 1. XRS Baseado em Vizinhança (Neighborhood-based XRS)

**Modelo:** `ItemKNN` (CaseRecommender)  
**Ideia central:**  
> “Recomendamos este filme porque ele é **muito parecido com outros filmes que você avaliou bem**.”

**Como a explicação é gerada:**  
- Calculamos similaridade entre itens.  
- Identificamos filmes bem avaliados pelo usuário que são vizinhos próximos do filme recomendado.  
- Esses vizinhos servem como “evidências” da recomendação.

---

### 🔹 2. XRS Baseado em Conteúdo (Content-based XRS)

**Modelo:** `ItemAttributeKNN` (CaseRecommender)  
**Atributos usados:** gêneros dos filmes  

**Ideia central:**  
> “Recomendamos este filme porque ele compartilha os gêneros **X, Y, Z** com filmes que você gostou.”

**Como a explicação é gerada:**  
- Criamos um arquivo de metadados contendo os gêneros de cada filme.  
- O modelo recomenda com base nesses atributos.  
- A explicação lista os gêneros em comum entre o filme recomendado e filmes bem avaliados pelo usuário.

---

### 🔹 3. XRS Pós-Hoc / Agnóstico ao Modelo (Model-Agnostic XRS)

**Modelo:** `BPRMF` (Bayesian Personalized Ranking Matrix Factorization)  
**Observação:** o modelo não é interpretável por natureza.  

**Ideia central:**  
> “O modelo recomenda; a explicação é construída **depois**, usando informações interpretáveis.”

**Como a explicação é gerada:**  
- Selecionamos o filme recomendado pelo BPRMF.  
- Calculamos a **similaridade de Jaccard** entre os gêneros do filme recomendado e dos filmes bem avaliados pelo usuário.  
- O filme com maior sobreposição de gêneros é usado como justificativa.

---

## 🧱 Estrutura do Notebook

O notebook está organizado da seguinte forma:

1. **Introdução e Análise Exploratória**
   - Leitura do MovieLens 100k  
   - Inspeção de filmes, usuários e gêneros  

2. **Pré-processamento**
   - Divisão treino/teste  
   - Construção dos arquivos `train.dat`, `test.dat`  
   - Criação do arquivo `movie_genres.txt` (para o Content-Based XRS)  

3. **Seção 1 – XRS Baseado em Vizinhança**
   - Treinamento do `ItemKNN`  
   - Geração de recomendações  
   - Explicação via itens vizinhos  

4. **Seção 2 – XRS Baseado em Conteúdo**
   - Treinamento do `ItemAttributeKNN`  
   - Explicação via gêneros compartilhados  

5. **Seção 3 – XRS Pós-Hoc / Agnóstico**
   - Treinamento do `BPRMF`  
   - Explicação interpretável via similaridade de gêneros  

Cada seção produz uma explicação em linguagem natural.

---

## 🚀 Como Executar

Este projeto foi preparado para rodar no **Google Colab**, mas funciona em qualquer ambiente Jupyter.

**Passos:**
1. Faça upload do notebook `.ipynb`.  
2. Execute as células em ordem.  

As primeiras células cuidam da instalação de dependências e download do dataset.  
As demais realizam o treinamento dos modelos e a geração das explicações.

---

## 📦 Requisitos

O notebook utiliza as seguintes bibliotecas:

- `CaseRecommender`  
- `numpy`  
- `pandas`  
- `scikit-learn`  

O ambiente do Colab já instala automaticamente tudo o que é necessário.

---

## 📈 Exemplo Geral de Saída

Ao final, você verá:

- **Uma recomendação explicada via vizinhança (ItemKNN)**  
- **Uma recomendação explicada via atributos (ItemAttributeKNN)**  
- **Uma recomendação explicada pós-hoc (BPRMF + Jaccard)**  

Cada recomendação vem acompanhada de uma explicação clara e direta, evidenciando como transformar sistemas de recomendação tradicionais em **sistemas de recomendação explicáveis**.

---

📚 *Este projeto foi criado como material didático para apoiar estudantes e interessados em Sistemas de Recomendação e Inteligência Artificial Explicável.*
