# CodeLift - Tradutor de Código Legado + Testes Automáticos

## 🎯 O que é

O **CodeLift** é uma aplicação que recebe trechos/módulos de código legado (ex.: VB6 ou Delphi) e devolve a versão moderna em Python, já com testes unitários gerados por IA.

## 💡 Valor

Reduz o esforço manual e dá um "ponto de partida" com código transformado e testável - exatamente o que a Ford pede.

## 🏗️ Arquitetura

- **Backend**: Node.js + Express + TypeScript
- **Frontend**: React + TypeScript + Vite + Mantine UI
- **IA**: OpenAI GPT para tradução e geração de testes
- **Testes**: pytest para execução de testes Python

## 🚀 Como usar

### 1. Configuração

Crie um arquivo `.env` na raiz do projeto:

```bash
# Configurações do Backend
PORT=8000

# Configurações da OpenAI
OPENAI_API_KEY=sua_chave_api_aqui
OPENAI_BASE_URL=https://api.openai.com/v1/chat/completions
OPENAI_MODEL=gpt-4o-mini

# Configurações do Frontend (opcional)
REACT_APP_API_URL=http://localhost:8000
```

### 2. Instalação das dependências

```bash
# Backend
npm install

# Frontend (se necessário)
npm install
```

### 3. Executar o projeto

```bash
# Terminal 1 - Backend
npm run dev

# Terminal 2 - Frontend (se necessário)
npm run dev
```

### 4. Acessar a aplicação

- **Frontend**: http://localhost:5173
- **Backend**: http://localhost:8000

## 🔧 Funcionalidades

### Tradução de Código
- Suporte para VB6, Delphi e outras linguagens legadas
- Tradução automática para Python usando OpenAI
- Preservação da lógica e nomes de variáveis
- Adição automática de docstrings

### Geração de Testes
- Criação automática de testes unitários
- Cobertura de casos de teste (happy path, edge cases, erros)
- Uso de fixtures e asserções explícitas
- Formato pytest padrão

### Execução de Testes
- Execução automática dos testes gerados
- Métricas de cobertura e resultados
- Timeout de segurança (60s)
- Exibição de output e erros

## 📁 Estrutura do Projeto

```
src/
├── components/          # Componentes React
│   ├── PagesComponents/ # Componentes das páginas
│   └── Examples/        # Exemplos de código
├── services/            # Serviços de API e lógica
├── stores/              # Gerenciamento de estado (Zustand)
├── routes/              # Rotas do backend e frontend
└── config/              # Configurações
```

## 🧪 Exemplos de Uso

### Função VB6 de Exemplo
```vb6
Function CalcularINSS(salario As Double) As Double
    If salario <= 1320 Then
        CalcularINSS = salario * 0.075
    ElseIf salario <= 2571.29 Then
        CalcularINSS = salario * 0.09
    Else
        CalcularINSS = salario * 0.12
    End If
End Function
```

### Python Gerado
```python
def calcular_inss(salario: float) -> float:
    """
    Calcula o desconto de INSS baseado no salário.
    
    Args:
        salario: Valor do salário em reais
        
    Returns:
        Valor do desconto de INSS
    """
    if salario <= 1320:
        return salario * 0.075
    elif salario <= 2571.29:
        return salario * 0.09
    else:
        return salario * 0.12
```

## 🔒 Segurança

- **Sanitização de código**: Sem execução dinâmica de código legado
- **Timeout de execução**: 60 segundos para execução de testes
- **Limite de tamanho**: Validação de entrada
- **Isolamento**: Workspace separado para execução

## 📊 API Endpoints

### POST /translate
Traduz código legado para Python

**Request:**
```json
{
  "code": "código VB6 aqui"
}
```

**Response:**
```json
{
  "translatedCode": "código Python aqui"
}
```

### POST /tests/generate
Gera testes para código Python

**Request:**
```json
{
  "code": "código Python aqui"
}
```

**Response:**
```json
{
  "tests": "código de testes aqui"
}
```

### POST /tests/run
Executa os testes gerados

**Response:**
```json
{
  "exitCode": 0,
  "stdout": "output dos testes",
  "stderr": "erros (se houver)"
}
```

## 🎥 Demo MVP

Para demonstrar o projeto:

1. **Pegar uma função VB6** (ex.: CalcularINSS)
2. **Clicar em "Traduzir"** → ver Python gerado
3. **"Gerar testes"** → executar → mostrar 100% passando
4. **Fechar com ganho de tempo estimado** (mesmo que qualitativo)

## 🛠️ Tecnologias

- **Backend**: Node.js, Express, TypeScript
- **Frontend**: React, TypeScript, Vite, Mantine
- **Estado**: Zustand
- **IA**: OpenAI GPT
- **Testes**: pytest
- **Build**: Vite, TypeScript

## 📝 Licença

Este projeto foi desenvolvido para a Ford FIAP.
