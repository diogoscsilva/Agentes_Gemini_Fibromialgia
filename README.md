# Agentes_Gemini_Fibromialgia

# Projeto de Sugestão de Práticas para Fibromialgia

## Sumário

- [A Importância da Fibromialgia](#a-importância-da-fibromialgia)
- [Estilo de Vida e Práticas Não Medicamentosas](#estilo-de-vida-e-práticas-não-medicamentosas)
- [Objetivo do Projeto](#objetivo-do-projeto)
- [Funcionamento dos Agentes](#funcionamento-dos-agentes)
  - [Agente Buscador de Vídeos](#agente-buscador-de-vídeos)
  - [Agente Selecionador de Vídeos](#agente-selecionador-de-vídeos)
  - [Agente Criador de Cards](#agente-criador-de-cards)
- [Como se Beneficiar das Sugestões](#como-se-beneficiar-das-sugestões)
- [Como Executar o Projeto](#como-executar-o-projeto)

## A Importância da Fibromialgia

A fibromialgia é uma síndrome crônica que causa dor musculoesquelética generalizada, acompanhada por fadiga, problemas de sono, memória e humor. O impacto na qualidade de vida dos pacientes pode ser significativo, afetando suas atividades diárias, capacidade de trabalho e bem-estar emocional. Compreender a complexidade da fibromialgia é crucial para buscar abordagens eficazes de manejo e tratamento.

## Estilo de Vida e Práticas Não Medicamentosas

Embora o tratamento medicamentoso possa ser parte do plano de cuidados, **modificações no estilo de vida e práticas não medicamentosas** desempenham um papel fundamental no bem-estar dos pacientes com fibromialgia. Exercícios de baixo impacto, técnicas de relaxamento, higiene do sono e estratégias de gerenciamento do estresse podem ajudar a aliviar os sintomas e melhorar a qualidade de vida.

## Objetivo do Projeto

O objetivo deste projeto é **facilitar o acesso a informações de qualidade e organizar orientações práticas para portadores de fibromialgia**. Através da curadoria de vídeos de profissionais qualificados, buscamos fornecer um recurso centralizado para auxiliar os pacientes na adoção de hábitos saudáveis e técnicas que possam contribuir para o seu bem-estar.

## Funcionamento dos Agentes

O projeto utiliza um sistema de três agentes inteligentes para coletar, filtrar e organizar as informações:

### Agente Buscador de Vídeos

- **Responsabilidade:** Buscar vídeos no YouTube de profissionais brasileiros.
- **Critérios de Busca:**
    - Duração: entre 5 e 15 minutos.
    - Conteúdo: técnicas práticas para melhorar um domínio específico (ex: dor, sono, saúde mental).
    - Foco: execução da prática para alcançar objetivos.
    - Acessibilidade: práticas que não necessitam de auxílio de terceiros ou equipamentos específicos.
    - Adequação para Fibromialgia: baixa intensidade, movimentos simples e controlados, execução cadenciada.
    - Relevância: vídeos com pelo menos um terço do conteúdo focado no domínio específico.

### Agente Selecionador de Vídeos

- **Responsabilidade:** Analisar os vídeos encontrados pelo Agente Buscador e selecionar o mais adequado.
- **Critérios de Seleção:**
    - Orientação sobre dor: o profissional deve orientar sobre a possibilidade de dor ou piora dos sintomas durante a prática.
    - Clareza: o profissional deve explicar as técnicas e posições com clareza.
- **Resultado:** Retorna apenas 1 vídeo escolhido.

### Agente Criador de Cards

- **Responsabilidade:** Organizar as informações do vídeo selecionado em um formato prático e de fácil consumo.
- **Funcionalidades:**
    - Descreve passo a passo a prática mostrada no vídeo.
    - Divide as práticas em dois grupos por semelhança.
    - Cria "cards" para cada prática contendo:
        - Nome da prática
        - Descrição
        - Número de séries e repetições sugeridos
        - Estimativa de duração
    - Estima a duração total da execução para cada um dos dois grupos de atividades.
- **Formato de Saída:** JSON contendo informações do vídeo (profissional, link) e os grupos de cards com seus respectivos detalhes.

## Como se Beneficiar das Sugestões

Este projeto visa fornecer sugestões personalizadas de práticas com base nas necessidades individuais do usuário, focando em três áreas principais: **dor, sono e saúde mental**.

Ao informar seus níveis de sintomas (como intensidade da dor em diferentes partes do corpo, qualidade do sono, níveis de fadiga e dificuldades de memória), o sistema utilizará essas informações para:

1.  **Identificar as áreas prioritárias** para intervenção.
2.  **Selecionar o tipo de prática e área de conhecimento** mais adequados (ex: fisioterapia para dor intensa, técnicas de relaxamento para insônia, mindfulness para dificuldades de memória).
3.  **Acionar os agentes** para buscar, selecionar e organizar vídeos e cards com exercícios e orientações específicas para o seu caso.

As sugestões apresentadas em formato de "cards" facilitarão o acompanhamento das práticas, com instruções claras e estimativas de tempo, permitindo que você incorpore essas atividades em sua rotina de forma gradual e adaptada às suas condições.

**Importante:** As sugestões fornecidas por este projeto são de caráter informativo e não substituem a orientação de um profissional de saúde qualificado. Sempre consulte seu médico ou fisioterapeuta antes de iniciar qualquer nova prática de exercício ou tratamento.

## Como Executar o Projeto

O código principal do projeto está no arquivo `agentes_sugestao_fibromialgia.py`.

1.  **Configuração:**
    * Certifique-se de ter o Python instalado.
    * Instale as bibliotecas necessárias:
        ```bash
        pip install google-genai google-adk requests
        ```
    * Configure sua chave de API do Google Gemini no ambiente, conforme instruído no início do script (`os.environ["GOOGLE_API_KEY"] = userdata.get('GOOGLE_API_KEY')`). Em um ambiente local, você pode definir a variável de ambiente `GOOGLE_API_KEY` diretamente.

2.  **Entrada de Dados:**
    * O script espera uma entrada de dados do usuário no formato JSON, representando os escores de sintomas. Um exemplo de `input_data` é fornecido no código:
        ```python
        input_data = """
            {
                "superiores": 4,    # Dor em membros superiores (0-5)
                "inferiores": 2,    # Dor em membros inferiores (0-5)
                "lombar": 2,        # Dor lombar (0-5)
                "cervical": 1,      # Dor cervical (0-5)
                "insonia": 4,       # Nível de insônia (0-5)
                "memoria": 3,       # Dificuldade de memória (0-5)
                "fadiga": 4         # Nível de fadiga (0-5)
            }
            """
        ```
    * Você pode modificar esses valores diretamente no script ou adaptar o código para receber a entrada de outra forma (por exemplo, via `input()`).

3.  **Execução:**
    * Rode o script Python:
        ```bash
        python agentes_sugestao_fibromialgia.py
        ```

4.  **Saída:**
    * O sistema imprimirá no console os "cards" gerados para as áreas de dor, sono e saúde mental, com base nos escores de entrada. A saída será em formato JSON, detalhando os vídeos selecionados e as práticas sugeridas.

Lembre-se que a qualidade das sugestões depende da disponibilidade de vídeos relevantes no YouTube que atendam aos critérios dos agentes.
