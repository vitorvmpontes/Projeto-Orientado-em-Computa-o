# Dataset para Extração de Programação de Eventos com LLMs

Este repositório contém o conjunto de dados, e o *ground truth* utilizados no artigo **Aplicação de Técnicas de Extração de Informação para Automatizar o Cadastro de Atividades no Sistema myMobiConf**.

## 📂 Estrutura do Repositório

* **/Programacoes**: Arquivos originais dos eventos (PDF, PNG, JPG, HTML, XLS).
* **/conjunto de validação/Manual**: Arquivos JSON anotados manualmente contendo a saída esperada (Nome, Data, Local, Descrição).
* **/conjunto de validação/IA**: Saídas brutas geradas pelo modelo (Google Gemini 2.0-Flash).

## 📊 Sobre o Dataset

O conjunto de dados é composto por **17 arquivos** provenientes de **10 eventos acadêmicos reais**, selecionados para representar uma alta heterogeneidade de formatos e layouts (listas simples, tabelas densas, layouts artísticos).
