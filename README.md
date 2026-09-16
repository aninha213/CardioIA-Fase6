# CardioIA — Sistema Preditivo Multiagente

> Projeto desenvolvido para a **Fase 6** da disciplina de Inteligência Artificial.

O **CardioIA** é um sistema preditivo multiagente desenvolvido para realizar uma simulação de classificação de risco cardiovascular utilizando **Machine Learning**, agentes especializados e uma base simulada de protocolos

---

## Objetivo

O projeto tem como objetivo desenvolver um sistema capaz de:

- Treinar um modelo de Machine Learning para prever a variável `pico_risco`;
-  Classificar novos pacientes de acordo com o modelo preditivo;
-  Integrar o modelo de Machine Learning a uma arquitetura multiagente;
-  Utilizar *handoffs* para organizar a comunicação entre os agentes;
-  Consultar protocolos simulados de acordo com a classificação de risco;
-  Apresentar uma resposta estruturada com probabilidade, classificação e protocolos sugeridos.

---

##  Arquitetura do sistema

O CardioIA é composto por três agentes principais:

###  Agente Analista de Risco

Responsável por consultar o modelo preditivo e obter:

- Probabilidade de pico de risco;
- Classificação do risco.

###  Agente Especialista em Protocolos

Responsável por relacionar a classificação de risco aos protocolos disponíveis na base simulada.

###  Agente Orquestrador

Responsável por coordenar o fluxo entre os agentes e organizar a execução utilizando *handoffs*.

### Fluxo

```text
                     Novo paciente
                           │
                           ▼
                 ┌────────────────────┐
                 │    Orquestrador    │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Analista de Risco  │
                 │  Modelo preditivo  │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Classificação de   │
                 │       risco        │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Especialista em    │
                 │     Protocolos     │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Resultado final    │
                 │ + protocolos       │
                 └────────────────────┘
```

---

##  Modelo de Machine Learning
Para a classificação de risco foi utilizado o algoritmo:

**Random Forest Classifier**

O modelo utiliza as seguintes variáveis:

| Variável | Descrição |
|---|---|
| `idade` | Idade do paciente |
| `frequencia_cardiaca` | Frequência cardíaca |
| `spo2` | Saturação de oxigênio |
| `carga_sistema` | Carga do sistema |
| `disponibilidade_recursos` | Disponibilidade de recursos |

A variável alvo utilizada foi:

```text
pico_risco
```

Os dados utilizados no treinamento são **sintéticos**, criados especificamente para a simulação proposta no projeto.

---

##  Resultados do modelo

O modelo apresentou:

**Acurácia: 100%**

Matriz de confusão:

```text
[[176   0]
 [  0  24]]
```

O modelo também foi utilizado para realizar a simulação de um novo paciente.

### Exemplo

```text
Idade: 72
Frequência cardíaca: 125
SpO2: 90
Carga do sistema: 85
Disponibilidade de recursos: 0
```

Resultado:

```text
Probabilidade de risco: 100.00%
Classificação: Alto risco
```

Protocolos simulados:

```text
- Monitoramento cardíaco contínuo
- Avaliação médica prioritária
- Verificação frequente dos sinais vitais
```

---

## 🛠️ Tecnologias utilizadas

-  Python
-  Pandas
-  NumPy
-  Scikit-learn
-  Joblib
-  OpenAI Agents SDK
-  Ollama
-  Qwen 2.5 0.5B
-  Google Colab

---

##  Estrutura do projeto

```text
CardioIA-Fase6/
│
├── README.md
│
├── requirements.txt
│
├── notebook/
│   └── CardioIA_Fase6_Modelo_Preditivo.ipynb
│
└── modelo/
    └── modelo_cardioia.pkl
```

###  Notebook

O notebook contém:

- Geração da base sintética;
- Definição da variável alvo;
- Preparação dos dados;
- Divisão entre treino e teste;
- Treinamento do modelo;
- Avaliação do modelo;
- Matriz de confusão;
- Simulação de novo paciente;
- Salvamento do modelo;
- Configuração dos agentes;
- Handoffs;
- Integração do fluxo multiagente.

###  Modelo

O arquivo `modelo_cardioia.pkl` contém o modelo Random Forest treinado e salvo utilizando `joblib`.

---

##  Como executar

### 1. Instalar as dependências

No ambiente Python:

```bash
pip install -r requirements.txt
```

### 2. Executar o notebook

Abra:

```text
notebook/CardioIA_Fase6_Modelo_Preditivo.ipynb
```

Execute as células do notebook na ordem apresentada.

### 3. Executar a arquitetura multiagente

A integração dos agentes utiliza o **Ollama** com o modelo:

```text
qwen2.5:0.5b
```

O Ollama deve estar instalado e o modelo disponível localmente para executar a parte multiagente.

---

##  Reprodutibilidade

Para reproduzir o projeto:

1. Instale as dependências presentes em `requirements.txt`;
2. Abra o notebook;
3. Execute as células na ordem;
4. Certifique-se de que o arquivo `modelo_cardioia.pkl` esteja disponível na pasta `modelo`;
5. Para a parte multiagente, mantenha o Ollama em execução;
6. Utilize o modelo `qwen2.5:0.5b`.

---

##  Limitações

Este projeto possui caráter **acadêmico e experimental**.

Os principais pontos de limitação são:

- Os dados utilizados são sintéticos;
- A variável alvo foi definida a partir de uma regra determinística;
- Os protocolos utilizados são simulados;
- O resultado de 100% de acurácia não representa desempenho clínico real;
- O sistema não deve ser utilizado para diagnóstico ou decisão médica real.

Para uma aplicação real, seriam necessários dados clínicos reais e anonimizados, validação adequada do modelo, monitoramento contínuo e avaliação por profissionais especializados.

---
##  Conclusão

O CardioIA demonstra a integração entre **Machine Learning e arquitetura multiagente** em um sistema preditivo.

O modelo Random Forest realiza a classificação de risco, enquanto os agentes especializados participam da análise e organização das informações.

A arquitetura proposta permite separar responsabilidades entre os componentes do sistema e demonstrar o uso de ferramentas, agentes e *handoffs* em um fluxo integrado.

---

##

**CardioIA — Fase 6**

Sistema Preditivo Multiagente  
Inteligência Artificial • Machine Learning • Agentes de IA
