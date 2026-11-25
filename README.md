# Projeto Voz do Cliente · Mineração de Textos

Repositório do projeto **Voz do Cliente** da disciplina **Mineração de Textos** (Pós-graduação em Data Science e IA — Senac-DF).

## Integrante

- **Matheus Resende de Moura**

## Estrutura do repositório

- `01_do_texto_ao_vetor.ipynb` — Notebook completo da **Etapa 1** com todas as células executadas e saídas salvas.

## Resumo da Etapa 1 (`01_do_texto_ao_vetor.ipynb`)

1. **Amostra:** 15.000 avaliações estratificadas de forma balanceada por nota (3.000 avaliações de cada nota de 1 a 5), com semente fixa `SEMENTE = 2026`.
2. **Exploração:** análise de textos vazios e duplicados da base original (132.373 registros), distribuição de notas, recomendação (`recommend_to_a_friend`) e comprimento dos textos.
3. **Catálogo de sujeira:** leitura manual de 30 avaliações sorteadas da amostra, levantamento dos principais ruídos textuais (pontuação repetida, erros de digitação, falta de acentuação, preenchimento artificial de caracteres e incoerências nota/texto) e decisões justificadas.
4. **Pipeline de pré-processamento:** normalização com regex (unificação de `"nao"` → `"não"`, expansão de abreviações, remoção preventiva de URLs e padrões de dados pessoais), ajuste de stopwords (mantendo negações e removendo termos genéricos de domínio) e lematização com spaCy (`pt_core_news_sm`), reduzindo o vocabulário em 66,4% (de 37.537 para 12.594 palavras distintas).
5. **Representações:** vetorização **TF-IDF** com unigramas e bigramas (`15.000 × 7.483`, densidade de 0,2132%) e **embeddings densos** com `paraphrase-multilingual-MiniLM-L12-v2` (`15.000 × 384`, salvos em `embeddings.npy` para uso na Etapa 2).
6. **Busca:** comparação lado a lado entre TF-IDF e embeddings em três consultas (entrega, defeito e atendimento), com avaliação qualitativa de relevância dos 5 primeiros resultados de cada método.
7. **Parte individual:** cálculo manual de TF-IDF para três termos de uma avaliação pré-processada da amostra e justificativa detalhada de uma decisão do pipeline.

## Uso de Inteligência Artificial

Foi utilizado o **Gemini** como ferramenta de apoio nas seguintes frentes:
- Estruturação e ajustes de código em Python (`pandas`, `matplotlib`, expressões regulares e formatação das saídas no Colab).
- Revisão textual e organização em Markdown das análises redigidas a partir dos números, tabelas e exemplos reais obtidos na execução do notebook.

Todas as execuções, leituras das avaliações, conferências dos resultados de busca e validações dos cálculos foram realizadas e verificadas diretamente no Google Colab.

## Créditos do dataset

- **Dataset:** B2W-Reviews01 (Real, Oshiro e Mafra, STIL 2019).
- **Licença:** CC BY-NC-SA 4.0 — uso acadêmico com crédito à **B2W Digital**.
