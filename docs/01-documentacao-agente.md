# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas pessoas têm dificuldade para compreender e organizar sua própria vida financeira.

Mesmo possuindo renda, o usuário pode não saber:

- para onde seu dinheiro está indo;
- quanto realmente consegue economizar;
- quais despesas estão comprometendo seu orçamento;
- quais riscos existem ao assumir uma nova dívida;
- como priorizar seus objetivos financeiros;
- quais alternativas podem ser consideradas antes de tomar uma decisão.

As ferramentas financeiras tradicionais geralmente apresentam dados, gráficos e números, mas nem sempre ajudam o usuário a interpretar essas informações de forma simples e personalizada.
O problema é a falta de um assistente capaz de conversar com o usuário, compreender seu contexto financeiro e oferecer dicas e informações relevantes para ajudá-lo a refletir sobre suas próprias decisões.

**<span style="color:#FF0000">O agente não deve decidir pelo usuário. Seu papel é fornecer informações e ampliar a capacidade de análise da pessoa.</span>** 

### Solução
> Como o agente resolve esse problema de forma proativa?

Analisar despesas:
- comparar gastos entre meses.
- Identificar aumento ou redução de despesas.
- Mostrar categorias com maior impacto no orçamento.
-Apresentar a evolução das despesas ao longo do tempo.

################################################################

Analisar receitas:
- Comparar evolução da renda.
- Identificar fontes de receita.
- Demonstrar variações mensais.
- Apontar períodos de maior ou menor entrada de recursos.

################################################################

Analisar patrimônio: 
- Saldo em contas.
- Investimentos cadastrados.
- Bens informados.
- Dívidas registradas.
- Evolução do patrimônio.

################################################################

Acompanhar objetivos financeiros:
- Compra de imóvel.
- Compra de veículo.
- Formação de reserva financeira.
- Planejamento para aposentadoria.
- Viagens.
- Estudos.

################################################################

Identificar tendências: 
- Crescimento contínuo das despesas.
- Redução da capacidade de poupança.
- Alterações no padrão de consumo.
- Aumento do comprometimento da renda.

### Público-Alvo
> Quem vai usar esse agente?

Pessoas que necessitam planejar melhor sua saúde financeira por meio de análises, comparações e informações educativas.

## Persona e Tom de Voz

### Nome do Agente
FinIA () 
### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

[Sua descrição aqui]

### Tom de Comunicação
> Formal, informal, técnico, acessível?

[Sua descrição aqui]

### Exemplos de Linguagem
- Saudação: [ex: "Olá! Como posso ajudar com suas finanças hoje?"]
- Confirmação: [ex: "Entendi! Deixa eu verificar isso para você."]
- Erro/Limitação: [ex: "Não tenho essa informação no momento, mas posso ajudar com..."]

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [ex: Chatbot em Streamlit] |
| LLM | [ex: GPT-4 via API] |
| Base de Conhecimento | [ex: JSON/CSV com dados do cliente] |
| Validação | [ex: Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] [ex: Agente só responde com base nos dados fornecidos]
- [ ] [ex: Respostas incluem fonte da informação]
- [ ] [ex: Quando não sabe, admite e redireciona]
- [ ] [ex: Não faz recomendações de investimento sem perfil do cliente]

### Limitações Declaradas
> O que o agente NÃO faz?

[Liste aqui as limitações explícitas do agente]
