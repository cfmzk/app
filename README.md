Este notebook implementa técnicas avançadas de descoberta causal em populações heterogêneas, identificando relações causais que variam entre diferentes subgrupos (definidos pela variável 'grupo'). O objetivo é proporcionar uma compreensão mais precisa e nuançada da eficácia de intervenções para ansiedade, utilizando a biblioteca DoWhy para modelagem causal.

## Fluxo de Trabalho

1. **Carregamento e Validação de Dados**: Carrega dados de intervenção em ansiedade, valida sua estrutura, conteúdo e tipos de dados. Trata possíveis erros de forma elegante.

2. **Pré-processamento de Dados**: Realiza codificação one-hot de características categóricas (mantendo a coluna original de grupo) e escala características numéricas.

3. **Descoberta Causal Heterogênea**: Utiliza DoWhy para criar e analisar modelos causais *para cada grupo separadamente*.

4. **Análise de Valores SHAP**: Quantifica a importância das características *dentro de cada modelo causal descoberto*.

5. **Visualização de Dados**: Gera gráficos KDE, Violin, Coordenadas Paralelas e Hipergrafos.

6. **Resumo Estatístico**: Realiza análise bootstrap e gera estatísticas resumidas.

7. **Relatório de Insights com LLM**: Sintetiza descobertas utilizando Grok, Claude e Grok-Enhanced, enfatizando a *heterogeneidade* dos efeitos causais.

## Componentes Principais

### Funções de Carregamento e Validação
- `create_output_directory`: Cria diretório para resultados
- `load_data_from_synthetic_string`: Carrega dados do CSV para DataFrame
- `validate_dataframe`: Valida colunas, tipos de dados e valores

### Análise Causal
- `discover_causal_structure_dowhy`: Realiza descoberta causal por subgrupos
- `calculate_shap_values_causal`: Calcula valores SHAP baseados no modelo causal

### Visualização
- `create_kde_plot`: Gera gráficos de densidade kernel
- `create_violin_plot`: Cria gráficos de violino para comparar grupos
- `create_parallel_coordinates_plot`: Visualiza trajetórias pré/pós intervenção
- `visualize_hypergraph`: Cria representação em hipergrafo das relações entre participantes

### Análise Estatística
- `perform_bootstrap`: Executa análise bootstrap com intervalos de confiança
- `save_summary`: Salva estatísticas resumidas e informações causais

### Integração com LLMs
- `analyze_text_with_llm`: Função para análise via LLM (placeholder para API real)
- `generate_insights_report`: Gera relatório combinando diferentes análises de LLMs

## Requisitos Técnicos

### Bibliotecas
- pandas, matplotlib, seaborn, networkx
- shap, plotly, scipy
- DoWhy para modelagem causal
- sklearn para pré-processamento e modelagem

### Variáveis de Ambiente
- Configurado para Google Colab ou ambiente local
- Requer chaves de API para Grok e Claude (atualmente com placeholders)

## Estrutura de Dados

### Colunas Principais
- `participant_id`: Identificador único do participante
- `group`: Grupo de intervenção (Group A, Group B, Control)
- `anxiety_pre`: Nível de ansiedade pré-intervenção
- `anxiety_post`: Nível de ansiedade pós-intervenção
- Variáveis adicionais: idade, gênero, histórico de doença mental

## Implementação e Uso

O notebook está estruturado para execução sequencial com tratamento de erros em cada etapa. A função `main()` coordena todo o fluxo de trabalho:

1. Cria diretório de saída
2. Carrega e valida o conjunto de dados sintético
3. Pré-processa os dados com codificação one-hot e escalonamento
4. Constrói modelos causais específicos para cada grupo
5. Realiza análise SHAP por grupo
6. Gera visualizações
7. Executa análise bootstrap
8. Salva estatísticas resumidas
9. Gera relatório de insights integrado

## Saídas

### Gráficos
- Gráficos causais específicos por grupo
- Gráficos de valores SHAP por grupo
- Gráficos KDE, Violin, Coordenadas Paralelas e Hipergrafos

### Arquivos de Texto
- Estatísticas resumidas
- Relatório de insights integrado combinando análises de múltiplos LLMs

## Características Especiais

- **Modelagem Causal Heterogênea**: Captura como as relações causais variam entre subgrupos
- **Visualizações Especializadas**: Representa graficamente as diferenças entre grupos
- **Integração de LLMs**: Combina análises de múltiplos modelos de linguagem
- **Tratamento Robusto de Erros**: Validação e tratamento de erros em cada etapa

## Referências

- Biblioteca DoWhy para inferência causal
- Biblioteca SHAP para explicabilidade
- Modelos de Linguagem: Grok, Claude 3.7 Sonnet, Grok-Enhanced

## Autor
Hélio Craveiro Pessoa Júnior
