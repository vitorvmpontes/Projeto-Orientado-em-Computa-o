#Automação de Cadastro de Atividades com IA Generativa (myMobiConf)

Este repositório contém o código, dataset e resultados do meu Trabalho de Conclusão de Curso (TCC) em Ciência da Computação pela Universidade Federal de Viçosa (UFV).

O projeto propõe e avalia um pipeline de Extração de Informação (EI) focado em automatizar a ingestão de cronogramas de eventos a partir de ficheiros não estruturados (PDF, HTML, Imagens e Planilhas). A solução foi projetada e integrada para resolver um estrangulamento operacional no sistema de gestão de eventos myMobiConf.

##Sobre o Projeto

O cadastro manual de atividades em sistemas de gestão de eventos é uma tarefa repetitiva, de baixa escalabilidade e propensa a erros humanos. No caso de grandes eventos organizados através da plataforma myMobiConf, este processo exigia que os organizadores digitassem os dados de centenas de atividades a partir de programações frequentemente fornecidas em formatos heterogéneos.

Para solucionar este problema, este projeto desenvolveu uma funcionalidade de importação automática baseada num pipeline que utiliza o Grande Modelo de Linguagem (LLM) Google Gemini 2.0-Flash em conjunto com técnicas de Engenharia de Prompt para extrair as atividades e estruturá-las em formato JSON nativo.

##Arquitetura e Tecnologias

###A solução completa (end-to-end) foi desenvolvida com a seguinte stack tecnológica:

- Frontend: Next.js e Tailwind CSS (interface de revisão e validação).

- Backend: NestJS (orquestração do pipeline e endpoints da API).

###Inteligência Artificial:

- Google Gemini 2.0-Flash API para inferência semântica e estruturação de dados (utilizando JSON Mode).

- Google Vision API para Reconhecimento Ótico de Carateres (OCR) em ficheiros de imagem.

- Processamento de Ficheiros (Python): PyMuPDF (PDFs), BeautifulSoup (HTML) e Pandas (Planilhas XLS/CSV).

- Algoritmos de Resolução de Entidades: Implementação de correspondência aproximada (fuzzy matching) com Fuse.js para mapeamento inteligente de locais físicos extraídos para IDs no banco de dados.

##O Pipeline de Extração

O pipeline de processamento funciona em duas fases principais:

- Extração de Texto (Roteamento): Um módulo analisa o formato do ficheiro de entrada (PDF, Imagem, HTML, XLS) e direciona-o para o extrator mais eficiente. Ficheiros codificados utilizam bibliotecas Python nativas, enquanto imagens passam por OCR. O resultado é sempre uma string de texto bruto.

- Extração Semântica e Estruturação: O texto bruto é enviado ao LLM juntamente com um prompt altamente estruturado (utilizando Role Prompting e One-Shot Learning). O modelo interpreta o texto, extrai as entidades (Nome, Local, Datas, Descrição), aplica regras de negócio (ex: fuso horário UTC-3) e retorna um JSON válido pronto para o pré-preenchimento do formulário.

##Resultados e Validação

A solução foi validada utilizando um dataset de 18 programações de eventos reais (totalizando 324 atividades).

- Deteção de Atividades: O sistema obteve um F1-Score global de aproximadamente 89% (Precisão de 88,75% e Revocação de 90,12%).

- Impacto no Negócio: A integração da solução transformou um processo de digitação manual de horas numa tarefa simples de revisão de dados na interface do sistema.

##Desafios Identificados (Limitações)

A avaliação revelou que abordagens puramente baseadas em texto perdem o contexto espacial em Documentos Ricos Visualmente (VRDs) complexos, como tabelas densas em PDF ou Imagem, resultando em menor acurácia na extração de campos temporais nestes cenários.

 ##Dataset

O dataset completo utilizado para a avaliação da metodologia está disponível na pasta /dataset-extracao-eventos deste repositório. Ele inclui:

- As programações originais nos seus diversos formatos (PDF, PNG, JPEG, XLS, HTML).

- O Ground Truth: Ficheiros JSON anotados manualmente com a saída esperada para fins de comparação.

##Artigo Completo

Para uma análise académica detalhada da metodologia, métricas de avaliação e discussão dos resultados por formato de ficheiro, consulte o artigo completo publicado:
Aplicação de Técnicas de Extração de Informação para Automatizar o Cadastro de Atividades no Sistema myMobiConf (Substitua pelo link real ou mantenha o ficheiro no repositório).

##Autores

Vitor Vasconcelos de M. Pontes - Autor Principal - LinkedIn | GitHub

Letícia O. Silva - Co-autora

Fabrício A. Silva - Orientador

Instituto de Ciências Exatas e Tecnológicas - Universidade Federal de Viçosa (UFV-CAF)
