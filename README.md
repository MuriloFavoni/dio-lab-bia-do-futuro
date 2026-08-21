# Kali - Agente Financeiro Inteligente

Agente de IA que roda 100% localmente e ajuda a organizar a vida financeira com base nos dados reais do usuário: perfil, transações e histórico de atendimento.

Projeto desenvolvido como desafio do bootcamp da DIO ("Agente Financeiro Inteligente com IA Generativa"), a partir do fork de [`digitalinnovationone/dio-lab-bia-do-futuro`](https://github.com/digitalinnovationone/dio-lab-bia-do-futuro), com código, dados e prompt reescritos como solução própria.

## Como funciona

1. O app carrega o perfil do cliente (`perfil_cliente.json`), o histórico de transações (`transacoes.csv`) e o histórico de atendimentos (`historico_atendimento.csv`).
2. Calcula dinamicamente quanto já foi gasto no mês e quanto ainda pode ser gasto, direto a partir das transações — nada fica fixo no perfil.
3. Monta um contexto com esses dados e envia junto da pergunta do usuário para um modelo de IA rodando localmente via [Ollama](https://ollama.com).
4. A resposta aparece em uma interface de chat feita com [Streamlit](https://streamlit.io).

## Estrutura do projeto

```
dio-lab-bia-do-futuro/
├── data/
│   ├── perfil_cliente.json          # dados do cliente e metas
│   ├── transacoes.csv               # histórico de transações
│   └── historico_atendimento.csv    # histórico de atendimentos
├── src/
│   └── app.py                       # aplicação principal (Streamlit)
├── docs/                            # documentação do desafio (caso de uso, prompts, métricas)
├── assets/                          # imagens e diagramas
└── examples/                        # referências de implementação da DIO
```

## Tecnologias

- **Python**
- **Streamlit** — interface de chat
- **Ollama** — inferência de LLM local (modelo configurável, ex: `llama3.2:1b`)
- **Pandas** — leitura e processamento dos dados financeiros

## Como rodar

1. Instale as dependências:
   ```
   pip install streamlit pandas requests
   ```
2. Instale o [Ollama](https://ollama.com/download) e baixe um modelo:
   ```
   ollama pull llama3.2:1b
   ```
3. Rode a aplicação a partir da raiz do projeto:
   ```
   streamlit run .\src\app.py
   ```

## Status

Projeto em desenvolvimento contínuo como parte dos estudos de transição de carreira para dados/tech.
