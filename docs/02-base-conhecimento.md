# Base de Conhecimento

## Dados Utilizados

A Base de Conhecimento da NOVA será responsável por fornecer informações confiáveis e contextualizadas para que o LLM possa compreender melhor a situação financeira do usuário e oferecer respostas consultivas.

A base será dividida entre:
- dados específicos do usuário;
- informações financeiras estruturadas;
- regras de negócio;
- conceitos financeiros;
- informações auxiliares;
- histórico relevante das interações.

**O LLM não deverá utilizar apenas seu conhecimento geral para responder às perguntas. Sempre que a resposta depender de informações específicas do usuário, deverá consultar os dados disponíveis na Base de Conhecimento.**

5.1 Dados Utilizados

Os dados utilizados pela NOVA poderão ser divididos em quatro categorias principais.

A. Dados do Usuário

Informações gerais necessárias para contextualizar a análise:

identificação do usuário;
faixa etária;
profissão;
quantidade de dependentes;
objetivos financeiros;
nível de conhecimento financeiro;
preferências de comunicação.

Exemplo:

{
  "usuario_id": 1001,
  "objetivo_principal": "organizar_financas",
  "nivel_conhecimento": "iniciante",
  "dependentes": 2
}
B. Dados Financeiros

Informações relacionadas à situação financeira do usuário:

renda;
receitas extras;
despesas;
contas;
cartões;
dívidas;
financiamentos;
investimentos;
patrimônio;
reservas financeiras.

Exemplo:

{
  "renda_mensal": 8000,
  "despesas_mensais": 5500,
  "dividas": {
    "saldo_total": 20000,
    "parcelas_mensais": 1000
  },
  "reserva_financeira": 10000
}
C. Dados Históricos

Informações que permitem identificar mudanças e padrões ao longo do tempo:

despesas dos meses anteriores;
evolução da renda;
evolução das dívidas;
evolução dos investimentos;
metas alcançadas;
metas não alcançadas;
histórico de perguntas feitas ao agente;
recomendações ou dicas apresentadas anteriormente.

Exemplo:

Junho:
Despesas: R$ 4.800

Julho:
Despesas: R$ 5.500

Variação:
+R$ 700

Esse histórico permite que a NOVA identifique tendências.

D. Base de Conhecimento Financeiro

Informações gerais utilizadas para explicar conceitos ao usuário:

conceitos de orçamento;
educação financeira;
juros;
inflação;
crédito;
endividamento;
reserva financeira;
planejamento financeiro;
conceitos básicos de investimentos.

Essas informações deverão ser utilizadas principalmente para fins educativos e explicativos.
| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `dados_usuarios.csv` | CSV | Informações gerais necessárias para contextualizar a análise |
| `dados_financeiros.csv` | CSV | Informações relacionadas à situação financeira do usuário |
| `dados_historicos.json` | JSON | Informações que permitem identificar mudanças e padrões ao longo do tempo |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados brutos não deverão ser enviados diretamente ao LLM sem tratamento.

Antes de serem utilizados, os dados deverão ser:
- organizados;
- normalizados;
- resumidos;
- categorizados;
- contextualizados;
- validados.

Exemplo de dados brutos
2026-07-01 MERCADO 350.00
2026-07-03 RESTAURANTE 180.00
2026-07-05 SALARIO 8000.00
2026-07-07 COMBUSTIVEL 250.00
2026-07-10 STREAMING 59.90
Dados adaptados

O sistema poderá transformar os dados em:

{
  "periodo": "Julho de 2026",
  "renda_total": 8000,
  "despesas": {
    "alimentacao": 530,
    "transporte": 250,
    "assinaturas": 59.90
  },
  "total_despesas": 839.90
}

A adaptação facilita a interpretação pelo LLM.

Tipos de adaptação
Categorização
"Supermercado ABC"
        ↓
Categoria: Alimentação
Agregação
10 transações de alimentação
        ↓
Total de alimentação no mês
Comparação
Junho: R$ 800
Julho: R$ 1.200
        ↓
Aumento: R$ 400
Resumo

Em vez de enviar centenas de transações, o sistema pode enviar:

"Os gastos com alimentação aumentaram 25% em relação ao mês anterior."
---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

[ex: Os JSON/CSV são carregados no início da sessão e incluídos no contexto do prompt]

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

A integração entre os dados e o LLM deverá seguir uma arquitetura baseada em contexto.

O fluxo poderá ser:

Usuário faz uma pergunta
          ↓
Sistema identifica a intenção
          ↓
Busca os dados relevantes
          ↓
Filtra e organiza as informações
          ↓
Calcula métricas necessárias
          ↓
Monta o contexto
          ↓
Envia o contexto para o LLM
          ↓
LLM interpreta as informações
          ↓
Validação da resposta
          ↓
Resposta consultiva
Exemplo
Pergunta do usuário

"Por que estou gastando mais este mês?"

O sistema poderá identificar que precisa buscar:
- despesas do mês atual;
- despesas do mês anterior;
- categorias de gastos;
- variações significativas.

O sistema não precisa enviar todo o banco de dados para o LLM.

Em vez disso, deverá enviar apenas as informações relevantes.

5.4 Estratégia de Recuperação de Dados

A NOVA deverá utilizar uma estratégia de recuperação contextual.

Quando o usuário fizer uma pergunta, o sistema deverá:

1. Identificar a intenção

Exemplo:

Pergunta:
"Estou gastando muito com alimentação?"

Intenção:
ANALISAR_CATEGORIA_DE_DESPESA
2. Identificar os dados necessários
Dados necessários:

✓ Gastos com alimentação
✓ Período atual
✓ Período anterior
✓ Renda mensal

3. Recuperar somente os dados relevantes
Junho:
Alimentação: R$ 800

Julho:
Alimentação: R$ 1.200

Renda:
R$ 5.000
4. Montar o contexto para o LLM

O LLM receberá informações específicas e organizadas.
---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

O contexto enviado ao LLM poderá ser estruturado da seguinte forma:

[PERSONA DO AGENTE]

Você é a NOVA, uma agente financeira consultiva.

Seu papel é ajudar o usuário a compreender melhor sua situação
financeira, apresentando informações, possibilidades, riscos e dicas.

Você não deve tomar decisões pelo usuário.

Não deve afirmar que existe uma única decisão correta.

Não deve inventar dados.

Quando não houver informações suficientes, informe a limitação
e solicite os dados necessários.

--------------------------------------------------

[INFORMAÇÕES DO USUÁRIO]

ID: 1001
Nível de conhecimento financeiro: Iniciante
Objetivo principal: Organizar as finanças

--------------------------------------------------

[PERFIL FINANCEIRO]

Renda mensal: R$ 5.000

Despesas médias mensais: R$ 3.800

Reserva financeira: R$ 4.000

Dívidas:
- Cartão de crédito: R$ 2.000
- Parcela mensal: R$ 400

--------------------------------------------------

[CONTEXTO DA PERGUNTA]

O usuário perguntou:

"Estou gastando muito com alimentação?"

--------------------------------------------------

[DADOS RELEVANTES]

Gastos com alimentação:

Junho: R$ 800
Julho: R$ 1.200

Variação:
+R$ 400

Percentual de aumento:
+50%

Participação na renda atual:
24%

--------------------------------------------------

[INSTRUÇÕES DE RESPOSTA]

Analise os dados disponíveis.

Explique o que foi observado.

Apresente possíveis pontos de atenção.

Não determine o que o usuário deve fazer.

Ofereça dicas e perguntas para reflexão.

Utilize linguagem simples e consultiva.
Possível resposta gerada pelo LLM

"Sim, houve um aumento significativo nos seus gastos com alimentação. Eles passaram de R$ 800 para R$ 1.200, um aumento de R$ 400, ou aproximadamente 50% em relação ao mês anterior. Atualmente, essa categoria representa cerca de 24% da sua renda mensal.

Vale investigar se esse aumento ocorreu por uma situação excepcional ou se está relacionado a um novo padrão de consumo. Uma possibilidade é separar os gastos entre supermercado, restaurantes e delivery para entender melhor o que contribuiu para essa mudança.

Se quiser, posso ajudar você a comparar essas categorias com os meses anteriores."

Princípio da Base de Conhecimento

A NOVA deverá seguir o princípio:

O LLM deve receber o contexto necessário para responder, e não todos os dados disponíveis.

Isso proporciona:

maior precisão;
menor custo de processamento;
menor risco de confusão;
maior privacidade;
respostas mais relevantes.
Resumo da Arquitetura da Base de Conhecimento
┌──────────────────────────┐
│ Dados do Usuário         │
├──────────────────────────┤
│ Dados Financeiros        │
├──────────────────────────┤
│ Histórico                │
├──────────────────────────┤
│ Conhecimento Financeiro  │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ Tratamento e Adaptação   │
│ dos Dados                │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ Recuperação de Dados     │
│ Relevantes               │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ Contexto Montado         │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ LLM                      │
│ Interpretação e Geração  │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ Validação                │
└─────────────┬────────────┘
              │
              ▼
┌──────────────────────────┐
│ Resposta Consultiva      │
└──────────────────────────┘
Princípio fundamental

Os dados financeiros são a fonte da verdade. O LLM é responsável por compreender o contexto e conversar com o usuário.

Isso significa que a NOVA não deve "imaginar" a situação financeira do usuário. Ela deve utilizar dados reais disponíveis, realizar cálculos de forma controlada e transformar os resultados em uma comunicação clara e consultiva.
