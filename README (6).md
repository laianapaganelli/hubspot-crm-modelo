# Dashboard de Andamento do CRM: Leads, Negócios, Instalações, Reparos e Saúde da Carteira

Simulação, em Excel, do **painel de acompanhamento** de um CRM para um negócio de serviços com instalação em campo. Em uma única tela, mostra o **andamento de toda a jornada do cliente**: do lead ao negócio fechado, da instalação ao reparo e à saúde do cliente depois da venda.

Complementa os modelos de CRM de Salesforce e de HubSpot: eles desenham os objetos, as fases e as automações, e este painel mostra **como seria o acompanhamento** com esses dados.

> **Aviso:** todos os dados são **fictícios**, gerados para demonstração. Esta é uma simulação feita em planilha, **não é uma captura de tela do Salesforce ou do HubSpot**. Nenhuma informação de empresa ou cliente real foi usada.

![Dashboard de andamento do CRM](docs/painel-andamentos.png)

## Para que serve

Responder, de forma visual e rápida:

- Quantos negócios estão **em andamento** e quanto valem?
- Em qual **fase do funil** os negócios estão parados?
- De qual **origem** vêm os leads que mais convertem?
- Quais **instalações** estão atrasadas ou sem checklist?
- Quais **reparos** estão abertos há muito tempo e por qual causa?
- Quantos clientes estão em **risco**?
- O que precisa de **atenção hoje**?

## O que o painel mostra

| Bloco | Conteúdo |
|---|---|
| **Cartões de resumo** | Negócios criados, em andamento, ganhos, perdidos, taxa de conversão, valor em andamento, valor ponderado, ticket médio, instalações concluídas e pontos de atenção |
| **Funil por fase** | Quantidade, valor e percentual por fase do negócio |
| **Origem dos leads** | Negócios, ganhos e taxa de conversão por origem |
| **Instalações por status** | Agendada, material conferido, em execução e concluída, com as atrasadas |
| **Reparos por causa** | Causas mais frequentes e quantos continuam em aberto |
| **Saúde da carteira** | Clientes em Saudável, Atenção e Risco |
| **Evolução mensal** | Negócios criados por mês e quantos foram ganhos |

## Como os dados se ligam

```
Negócio  ──(ganho)──▶  Instalação  ──(problema)──▶  Reparo
   │                       │
   └──────▶ Cliente ◀──────┘
               │
               ▼
        Saúde do cliente (health score)
```

| Aba | Conteúdo | Liga com |
|---|---|---|
| **Negocios** | Do lead ao fechamento, com fase, valor, origem, último contato e motivo da perda | |
| **Instalacoes** | Uma por negócio ganho, com instalador, data, status e checklist | Negócio |
| **Reparos** | Causa, status e dias em aberto | Instalação |
| **Contas** | Health score e status de saúde por cliente | Cliente |
| **Listas** | Fases com probabilidade, status, causas e origens | Todas |
| **Painel** | Indicadores, tabelas e gráficos | Todas |
| **Como usar** | Legenda, passo a passo e premissas | |

## Indicadores e regras

| Indicador | Como é calculado |
|---|---|
| Taxa de conversão | Ganhos ÷ (ganhos + perdidos) |
| Valor ponderado | Valor de cada negócio em aberto × probabilidade da fase |
| Ticket médio | Valor médio dos negócios ganhos |
| Instalações concluídas | Concluídas e validadas ÷ total de instalações |
| Status de saúde | 80 ou mais: Saudável · 50 a 79: Atenção · abaixo de 50: Risco |

**Pontos de atenção** contados no painel:

- negócio aberto **sem contato há mais de 7 dias**;
- negócio perdido **sem motivo** registrado;
- instalação **atrasada**;
- instalação concluída **sem checklist**;
- reparo **aberto há mais de 7 dias**.

As probabilidades, o prazo de 7 dias e as faixas de saúde são **premissas de exemplo**, editáveis.

## Leitura do exemplo (dados fictícios)

- Dos 80 negócios, **36 estão em andamento**, somando um valor ponderado de cerca de R$ 220 mil.
- A **taxa de conversão é de 64%**. A origem **Indicação converte 90%** e o **WhatsApp, 38%**, o que apontaria onde reforçar o atendimento.
- **16 pontos de atenção** pedem ação: leads esfriando, instalações atrasadas, um checklist pendente e reparos abertos.
- Entre os clientes, **5 estão em Risco** e pediriam contato imediato.

> Esses números existem só para mostrar como o painel conta uma história. Com dados reais, a leitura será outra.

## Como usar com seus dados

1. Baixe `planilha/Dashboard_CRM_Andamentos.xlsx`.
2. Substitua os dados fictícios das abas **Negocios**, **Instalacoes**, **Reparos** e **Contas** pelos seus.
3. Ajuste a **Data de referência** no Painel para recalcular atrasos e dias sem contato.
4. Se tiver mais linhas do que o exemplo, estenda as fórmulas das abas e os intervalos do Painel até o novo fim dos dados.

Células amarelas com texto azul são para preencher. Células cinza têm fórmula.

## Ferramentas e técnicas

- Excel / Google Sheets
- `COUNTIFS`, `SUMIFS`, `AVERAGEIFS`, `INDEX` e `MATCH`, `VLOOKUP`, `IFERROR`
- Formatação condicional para alertas
- Gráficos de barras e colunas
- Modelagem de dados ligando negócio, instalação, reparo e cliente

## Estrutura do repositório

```
dashboard-crm-andamentos/
├── README.md
├── planilha/
│   └── Dashboard_CRM_Andamentos.xlsx
└── docs/
    └── painel-andamentos.png
```

## Autora

**Laiana Paganelli** · Processos, Operações e Customer Success
[LinkedIn](https://www.linkedin.com/in/laianapaganelli/)
