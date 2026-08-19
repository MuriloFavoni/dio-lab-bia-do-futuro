# Base de Conhecimento

## Dados Utilizados


| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar as explicações sobre duvidas e necessidades do cliente |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Sim, modifiquei variáveis do perfi_investidor para se encaixar melhor na utilidade do Kali.

---

## Estratégia de Integração

### Como os dados são carregados?
Os dados podem ser ditos diretamente ao Kali pelo prompt ou carregar os arquivos via código

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

```text
Dados do cliente: (data/perfil_cliente.json)
{
  "nome": "João Silva",
  "idade": 32,
  "profissao": "Analista de Sistemas",
  "renda_mensal": 5000.00,
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 15000.00,
  "reserva_emergencia_atual": 10000.00,
  "gastos": 2500,
  "contas": 1100
  "sobra_mes": "renda_mensal" - "gasto_mes"
  "metas": [
    {
      "meta": "Completar reserva de emergência",
      "valor_necessario": 15000.00,
      "prazo": "2026-06"
    },
    {
      "meta": "Entrada do apartamento",
      "valor_necessario": 50000.00,
      "prazo": "2027-12"
    }
  ]
}

Transações do cliente: (data/transacoes.csv)
data	descricao	categoria	valor	tipo
2025-10-01	Salário	receita	5000.00	entrada
2025-10-02	Aluguel	moradia	1200.00	saida
2025-10-03	Supermercado	alimentacao	450.00	saida
2025-10-05	Netflix	lazer	55.90	saida
2025-10-07	Farmácia	saude	89.00	saida
2025-10-10	Restaurante	alimentacao	120.00	saida
2025-10-12	Uber	transporte	45.00	saida
2025-10-15	Conta de Luz	moradia	180.00	saida
2025-10-20	Academia	saude	99.00	saida
2025-10-25	Combustível	transporte	250.00	saida

Histórico de atendimento: (data/historico_atendimento.csv)
data	canal	tema	resumo	resolvido
2025-09-15	chat	compra de uma TV que o cliente não possui	Cliente perguntou se cabia no orçamento	sim
2025-09-22	telefone	Problema no app	Erro ao visualizar extrato foi corrigido	sim
2025-10-01	chat	Comprar mais roupa que não sabe onde usar	Cliente perguntou se vale a pena comprar um vestido de festa sem ter festa para ir	sim
2025-10-12	chat	Metas financeiras	Cliente acompanhou o progresso da reserva de emergência	sim
2025-10-25	e-mail	Atualização cadastral	Cliente atualizou e-mail e telefone	sim
```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Gastos: R$ 2.500
- Contas: R$ 1000
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
