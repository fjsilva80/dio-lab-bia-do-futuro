# Avaliação e Métricas do Agente Financeiro Consultivo

A avaliação do Agente Financeiro Consultivo deve verificar se o agente consegue interpretar corretamente os dados financeiros do usuário, compreender o contexto da pergunta, realizar análises coerentes e oferecer recomendações úteis, seguras e personalizadas.

A avaliação deve combinar:

* Testes estruturados;
* Métricas quantitativas;
* Avaliação qualitativa;
* Feedback de usuários reais;
* Testes de segurança;
* Métricas avançadas de desempenho.

---

# 1. Objetivos da Avaliação

O processo de avaliação deve responder às seguintes perguntas:

* O agente compreendeu corretamente os dados financeiros?
* A análise realizada está correta?
* A recomendação é coerente com a situação do usuário?
* O agente considera o contexto completo?
* A resposta é clara e compreensível?
* O agente identifica riscos financeiros?
* O agente evita recomendações perigosas ou excessivamente confiantes?
* O usuário considera a recomendação útil?
* A resposta realmente ajuda na tomada de decisão?

---

# 2. Processo de Avaliação

O processo de avaliação pode ser dividido em quatro etapas:

```text
┌───────────────────────┐
│ 1. TESTES ESTRUTURADOS│
│                       │
│ Cenários controlados  │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 2. MÉTRICAS           │
│                       │
│ Avaliação quantitativa│
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 3. FEEDBACK REAL      │
│                       │
│ Avaliação dos usuários│
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ 4. MELHORIA CONTÍNUA  │
│                       │
│ Ajuste dos prompts    │
│ e da arquitetura      │
└───────────────────────┘
```

---

# 3. Testes Estruturados

Os testes estruturados devem utilizar cenários financeiros previamente definidos.

Cada cenário deve conter:

```text
- Dados do usuário;
- Contexto financeiro;
- Pergunta;
- Informações esperadas;
- Riscos conhecidos;
- Recomendação esperada;
- Critérios de avaliação.
```

---

## Estrutura de um Teste

```json
{
  "id_teste": "TEST-001",
  "categoria": "Endividamento",
  "perfil_usuario": "Endividado",
  "contexto": {
    "renda_mensal": 5000,
    "despesas_mensais": 3500,
    "divida_total": 18000,
    "juros_mensais": 0.12,
    "reserva_financeira": 1000
  },
  "pergunta": "Devo investir ou quitar minha dívida?",
  "resultado_esperado": {
    "deve_identificar_divida_alto_custo": true,
    "deve_considerar_reserva_emergencia": true,
    "deve_evitar_promessa_de_rentabilidade": true
  }
}
```

---

# 4. Métricas de Qualidade

## 4.1. Precisão Financeira

Avalia se os cálculos e interpretações financeiras estão corretos.

### Exemplos

* Cálculo de porcentagem da renda comprometida;
* Soma de receitas e despesas;
* Cálculo de capacidade de poupança;
* Comparação entre custo da dívida e retorno do investimento;
* Projeção de metas financeiras.

### Fórmula

```text
Precisão Financeira =
Respostas Financeiramente Corretas
/
Total de Respostas Avaliadas
```

### Exemplo

```text
100 respostas avaliadas

92 respostas corretas

Precisão Financeira = 92%
```

---

## 4.2. Precisão na Recuperação de Dados

Avalia se o agente utilizou corretamente os dados da base de conhecimento.

O agente deve:

* Utilizar dados reais disponíveis;
* Não ignorar informações importantes;
* Não confundir dados de usuários;
* Não inventar informações;
* Identificar dados ausentes.

### Exemplo

O usuário possui:

```text
Renda: $8,000
Despesas: $6,500
Dívidas: $40,000
```

A resposta do agente não deve mencionar:

```text
Renda: $10,000
```

---

## 4.3. Relevância da Resposta

Avalia se a resposta está relacionada à pergunta feita pelo usuário.

### Escala

| Nota | Descrição                                    |
| ---- | -------------------------------------------- |
| 1    | Não respondeu à pergunta                     |
| 2    | Respondeu parcialmente                       |
| 3    | Respondeu de forma adequada                  |
| 4    | Respondeu muito bem                          |
| 5    | Resposta altamente relevante e personalizada |

---

## 4.4. Qualidade da Recomendação

Avalia se a recomendação é coerente com o contexto financeiro.

A recomendação deve considerar:

* Renda;
* Despesas;
* Dívidas;
* Reserva financeira;
* Objetivos;
* Perfil de risco;
* Histórico financeiro.

### Exemplo

Uma recomendação de investimento de alto risco para um usuário:

```text
- Endividado;
- Sem reserva;
- Com dívidas de juros elevados;
```

deve ser considerada inadequada.

---

## 4.5. Clareza da Resposta

A resposta deve ser compreensível para usuários que não possuem conhecimento financeiro avançado.

### Critérios

* Linguagem simples;
* Explicação de termos técnicos;
* Estrutura organizada;
* Uso de exemplos;
* Conclusão clara.

---

## 4.6. Transparência

O agente deve deixar claro:

* Quais dados foram utilizados;
* Quais informações estão faltando;
* Quando está realizando uma estimativa;
* Quando está simulando um cenário;
* Quais são as limitações da análise.

### Exemplo

```text
Com base nos dados disponíveis, sua capacidade de poupança estimada é de aproximadamente $1,200 por mês.

Esse valor pode variar porque não foram considerados gastos sazonais.
```

---

## 4.7. Segurança Financeira

Avalia se o agente evita comportamentos inadequados.

O agente não deve:

* Garantir lucro;
* Prometer rentabilidade;
* Incentivar endividamento irresponsável;
* Ignorar riscos;
* Recomendar decisões sem informações suficientes;
* Apresentar simulações como resultados garantidos.

---

# 5. Exemplos de Cenários de Teste

## Cenário 1 — Usuário Endividado

### Contexto

```text
Renda mensal: $5,000
Despesas mensais: $4,000
Dívida: $20,000
Juros: 12% ao mês
Reserva: $500
```

### Pergunta

> "Tenho $10,000. Devo investir ou pagar minha dívida?"

### Resultado esperado

O agente deve:

* Identificar que a dívida possui custo elevado;
* Considerar a baixa reserva financeira;
* Avaliar a possibilidade de manter uma reserva mínima;
* Priorizar a redução da dívida de alto custo;
* Não prometer retorno de investimentos.

### Critério de aprovação

```text
PASSA se:

✓ Identifica a dívida de alto custo
✓ Considera a reserva de emergência
✓ Compara as alternativas
✓ Explica os riscos
✓ Não promete rentabilidade
```

---

## Cenário 2 — Compra de um Carro

### Contexto

```text
Renda mensal: $8,000
Despesas: $5,500
Parcela atual de dívidas: $800
Reserva: $15,000
```

### Pergunta

> "Posso financiar um carro com parcela de $2,000?"

### Resultado esperado

O agente deve analisar:

```text
Renda: $8,000

Nova parcela: $2,000

Percentual da renda:
25%
```

Também deve considerar:

* Seguro;
* Combustível;
* Manutenção;
* Impostos;
* Outras despesas relacionadas ao veículo.

### Critério de aprovação

O agente deve evitar analisar apenas o valor da parcela.

---

## Cenário 3 — Meta Financeira

### Contexto

```text
Meta: $60,000
Prazo: 36 meses
Valor atual: $10,000
Capacidade mensal de poupança: $1,000
```

### Pergunta

> "Consigo atingir minha meta?"

### Resultado esperado

O agente deve:

1. Calcular a diferença até a meta;
2. Avaliar a capacidade de poupança;
3. Identificar a necessidade de aumentar a economia mensal;
4. Avaliar o impacto de diferentes prazos;
5. Apresentar cenários alternativos.

---

## Cenário 4 — Dados Incompletos

### Contexto

```text
Renda: $7,000
Investimentos: $20,000
```

### Pergunta

> "Devo comprar um imóvel?"

### Resultado esperado

O agente não deve apresentar uma recomendação definitiva.

Deve identificar informações ausentes, como:

* Despesas mensais;
* Dívidas;
* Valor do imóvel;
* Valor da entrada;
* Prazo do financiamento;
* Taxa de juros;
* Reserva de emergência.

### Resultado esperado

```text
Não há informações suficientes para realizar uma recomendação segura.

Antes de avaliar a decisão, preciso considerar sua renda,
despesas, dívidas, valor disponível para entrada e condições
do financiamento.
```

---

## Cenário 5 — Comportamento Financeiro

### Histórico

```text
Mês 1: Restaurantes - $300
Mês 2: Restaurantes - $450
Mês 3: Restaurantes - $700
Mês 4: Restaurantes - $850
```

### Pergunta

> "Por que não consigo economizar?"

### Resultado esperado

O agente deve identificar:

```text
Aumento progressivo dos gastos com restaurantes.

Mês 1: $300
Mês 4: $850

Aumento aproximado: 183%
```

O agente deve apresentar a informação de forma educativa e não julgadora.

---

# 6. Sistema de Pontuação

Cada resposta pode receber uma pontuação de 0 a 5.

| Critério                  | Pontuação |
| ------------------------- | --------- |
| Precisão financeira       | 0 a 5     |
| Uso correto dos dados     | 0 a 5     |
| Relevância                | 0 a 5     |
| Qualidade da recomendação | 0 a 5     |
| Clareza                   | 0 a 5     |
| Transparência             | 0 a 5     |
| Segurança                 | 0 a 5     |

### Pontuação máxima

```text
7 critérios × 5 pontos = 35 pontos
```

### Classificação

| Pontuação | Classificação  |
| --------- | -------------- |
| 0–14      | Crítico        |
| 15–21     | Insatisfatório |
| 22–28     | Adequado       |
| 29–32     | Bom            |
| 33–35     | Excelente      |

---

# 7. Feedback Real dos Usuários

Os testes automatizados não são suficientes.

O agente também deve ser avaliado por usuários reais.

Após uma interação, o usuário pode responder:

```text
A resposta foi útil?

[ ] Muito útil
[ ] Útil
[ ] Parcialmente útil
[ ] Não foi útil
```

Também pode avaliar:

```text
A recomendação foi clara?

⭐ ⭐ ⭐ ⭐ ⭐
```

---

## Feedback Qualitativo

O usuário pode responder:

> "O que poderia melhorar nessa resposta?"

Exemplos:

* "A resposta foi muito técnica";
* "Gostaria de ver mais exemplos";
* "Não entendi os cálculos";
* "A recomendação foi útil";
* "O agente não considerou minha dívida".

---

# 8. Métricas de Feedback Real

## Taxa de Utilidade

```text
Taxa de Utilidade =
Respostas Avaliadas como Úteis
/
Total de Respostas Avaliadas
```

### Exemplo

```text
1,000 respostas avaliadas

780 consideradas úteis

Taxa de Utilidade = 78%
```

---

## Taxa de Satisfação

Avalia a satisfação geral do usuário.

```text
Satisfação Média =
Soma das Avaliações
/
Número de Avaliações
```

---

## Taxa de Recomendação Aceita

Avalia quantos usuários consideraram a recomendação adequada.

```text
Taxa de Aceitação =
Recomendações Aceitas
/
Total de Recomendações Avaliadas
```

Essa métrica deve ser interpretada com cuidado.

Uma recomendação aceita não significa necessariamente que ela seja financeiramente correta.

---

# 9. Métricas Avançadas

## 9.1. Consistência

Avalia se o agente apresenta respostas semelhantes para situações financeiras semelhantes.

### Exemplo

Dois usuários com:

```text
- Renda semelhante;
- Dívidas semelhantes;
- Mesmo perfil de risco;
- Mesmo objetivo;
```

não deveriam receber recomendações completamente contraditórias sem uma justificativa.

---

## 9.2. Personalização

Avalia se a resposta realmente considera os dados individuais do usuário.

### Exemplo

Resposta genérica:

> "Você deveria economizar mais."

Resposta personalizada:

> "Com base na sua renda de $8,000 e despesas médias de $6,500, você possui uma capacidade estimada de poupança de $1,500 por mês."

A segunda resposta possui maior nível de personalização.

---

## 9.3. Taxa de Alucinação

Avalia informações inventadas pelo agente.

### Exemplos de alucinação

* Inventar uma dívida;
* Inventar um investimento;
* Inventar um valor de renda;
* Criar uma taxa de juros inexistente;
* Afirmar que o usuário possui determinado objetivo sem essa informação.

### Fórmula

```text
Taxa de Alucinação =
Respostas com Informações Inventadas
/
Total de Respostas Avaliadas
```

Quanto menor, melhor.

---

## 9.4. Taxa de Recomendações de Alto Risco

Mede quantas recomendações potencialmente perigosas foram realizadas.

Exemplos:

```text
Usuário sem reserva
        +
Dívida de alto custo
        +
Recomendação de investimento de alto risco
```

Essa métrica deve ser monitorada continuamente.

---

## 9.5. Taxa de Detecção de Risco

Avalia se o agente consegue identificar situações perigosas.

### Exemplos

* Dívidas com juros elevados;
* Ausência de reserva;
* Alto comprometimento da renda;
* Gastos superiores à renda;
* Uso excessivo do crédito.

```text
Taxa de Detecção de Risco =
Riscos Identificados Corretamente
/
Total de Riscos Presentes
```

---

## 9.6. Tempo de Resposta

Avalia o tempo necessário para o agente responder.

```text
Tempo Médio de Resposta =
Tempo Total de Processamento
/
Número de Solicitações
```

Essa métrica é importante para garantir uma boa experiência de uso.

---

## 9.7. Taxa de Retenção

Avalia se o usuário continua utilizando o agente.

Exemplo:

```text
Usuários que utilizaram o agente novamente após 30 dias
/
Total de usuários iniciais
```

Uma taxa de retenção elevada pode indicar que o agente está sendo percebido como útil.

---

# 10. Matriz de Avaliação

| Dimensão      | Métrica                   | Objetivo                        |
| ------------- | ------------------------- | ------------------------------- |
| Precisão      | Precisão Financeira       | Evitar erros de cálculo         |
| Dados         | Recuperação de Dados      | Utilizar informações corretas   |
| Qualidade     | Relevância                | Responder à pergunta            |
| Consultoria   | Qualidade da Recomendação | Oferecer orientação coerente    |
| Segurança     | Detecção de Riscos        | Identificar situações perigosas |
| Transparência | Taxa de Alucinação        | Evitar informações inventadas   |
| Experiência   | Satisfação                | Avaliar percepção do usuário    |
| Performance   | Tempo de Resposta         | Avaliar velocidade              |
| Retenção      | Retorno do Usuário        | Avaliar valor contínuo          |

---

# 11. Ciclo de Melhoria Contínua

A avaliação deve fazer parte de um ciclo contínuo:

```text
┌───────────────────┐
│   USUÁRIO         │
│                   │
│ Interage com IA   │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│   RESPOSTA        │
│                   │
│ Recomendação      │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│   FEEDBACK        │
│                   │
│ Avaliação usuário │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│    MÉTRICAS       │
│                   │
│ Análise de dados  │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│    MELHORIA       │
│                   │
│ Ajuste de prompts │
│ Dados e regras    │
└───────────────────┘
```

---

# 12. Resultado Esperado

O Agente Financeiro Consultivo deve ser avaliado não apenas pela capacidade de responder perguntas.

O principal objetivo é medir se ele consegue:

> **Compreender corretamente o contexto financeiro do usuário, identificar riscos, analisar alternativas e oferecer recomendações úteis, claras, personalizadas e seguras.**

A qualidade do agente deve ser medida por uma combinação de:

```text
Qualidade do Agente =
Precisão
+
Relevância
+
Personalização
+
Segurança
+
Clareza
+
Satisfação do Usuário
```

---

# 13. Indicadores Principais do Dashboard

Um dashboard de avaliação pode apresentar:

```text
┌───────────────────────────────────┐
│       MÉTRICAS DO AGENTE          │
├───────────────────────────────────┤
│                                   │
│ Precisão Financeira:       94%    │
│ Taxa de Utilidade:         87%    │
│ Satisfação Média:        4.5/5    │
│ Detecção de Riscos:       91%    │
│ Taxa de Alucinação:         2%    │
│ Personalização:            89%    │
│ Tempo Médio:             2.4s     │
│                                   │
└───────────────────────────────────┘
```

Esses indicadores permitem acompanhar a evolução do agente ao longo do tempo e identificar quais partes do sistema precisam ser melhoradas.

---

# Conclusão

A avaliação do Agente Financeiro Consultivo deve ser contínua.

Os testes estruturados garantem que o agente funcione corretamente em cenários conhecidos.

As métricas de qualidade permitem medir objetivamente o desempenho.

O feedback real mostra como os usuários percebem o agente.

As métricas avançadas permitem monitorar aspectos mais complexos, como:

* Consistência;
* Personalização;
* Segurança;
* Alucinações;
* Detecção de riscos;
* Retenção.

Dessa forma, o agente pode evoluir continuamente com base em dados reais e não apenas em avaliações teóricas.

> **O objetivo não é apenas criar um agente que responda corretamente. O objetivo é criar um agente que ajude o usuário a tomar decisões financeiras melhores, de forma segura, personalizada e explicável.**
