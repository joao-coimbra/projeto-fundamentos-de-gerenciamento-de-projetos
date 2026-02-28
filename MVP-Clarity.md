# Documento de MVP — ClarityAI

> **Produto:** ClarityAI — Plataforma de Inteligência de Atendimento ao Cliente  
> **Versão:** 1.0 — MVP  
> **Metodologia de Priorização:** MoSCoW + Value vs Effort

---

## Contexto

O MVP do ClarityAI tem como objetivo validar uma única hipótese central:

> *"Um time de suporte com volume massivo de interações consegue agir mais rápido e com mais precisão quando recebe insights priorizados gerados por IA — sem precisar de analistas de dados."*

O MVP **não** é o produto final. É o menor experimento funcional que nos permite aprender se o insight gerado é realmente acionável. Por isso, algumas funcionalidades importantes foram conscientemente deixadas fora do escopo desta fase.

---

## Funcionalidades do MVP

### MUST HAVE — Obrigatórias para o MVP ser válido

| ID | Funcionalidade | Descrição | Critério de Aceitação |
|----|---------------|-----------|----------------------|
| F01 | **Importação de dados via CSV** | Upload de tickets, chats e e-mails exportados de ferramentas como Zendesk, Freshdesk ou planilhas | Usuário consegue fazer upload de arquivo CSV com até 50k linhas e o sistema processa em menos de 3 minutos |
| F02 | **Classificação automática por tema** | O modelo de IA agrupa as interações em categorias semânticas automaticamente | Pelo menos 80% das classificações são consideradas corretas pelos usuários-teste na sessão de validação |
| F03 | **Dashboard de insights prioritários** | Painel com os top 10 temas críticos, rankeados por frequência e intensidade de sentimento negativo | Dashboard carrega em menos de 5 segundos; temas são exibidos com frequência absoluta e % do total |
| F04 | **Geração de plano de ação por tema** | Para cada tema no top 10, a IA gera um plano de ação estruturado com: proprietário sugerido, prazo estimado e ação recomendada | Ao menos 70% dos usuários-teste classificam o plano como "diretamente utilizável" sem edições |
| F05 | **Autenticação básica** | Login com e-mail/senha e controle de acesso por organização | Usuários de organizações diferentes não conseguem ver dados uns dos outros |

---

### SHOULD HAVE — Importante, mas não bloqueia o MVP

| ID | Funcionalidade | Justificativa | Quando? |
|----|---------------|---------------|---------|
| F06 | Filtro por período (últimos 7, 30, 90 dias) | Aumenta utilidade do painel sem alto esforço | Sprint 2 ou 3 |
| F07 | Filtro por canal (ticket / chat / e-mail) | Permite análise segmentada por tipo de interação | Sprint 3 |
| F08 | Exportação do relatório em PDF | Facilita compartilhar insights com lideranças | Sprint 3 |
| F09 | Indicador de tendência (comparativo semana a semana) | Permite avaliar se problema está melhorando ou piorando | Fase 2 |

---

### COULD HAVE — Desejável, baixa prioridade

| ID | Funcionalidade | Observação |
|----|---------------|------------|
| F10 | Tema customizável (usuário cria categorias manuais) | Interessante, mas adiciona complexidade de UX |
| F11 | Resumo executivo automático por e-mail (semanal) | Demanda automação de envio, fora do foco da validação |
| F12 | Dark mode / personalização de interface | Visual, baixo impacto no valor central |

---

### WON'T HAVE (neste MVP) — Conscientemente fora do escopo

| ID | Funcionalidade | Por que não agora? |
|----|---------------|-------------------|
| F13 | Integração nativa com Zendesk/Salesforce via API | Alto esforço técnico e risco de integração. Validar o valor dos insights primeiro |
| F14 | Módulo de resposta automática ao cliente | Fora do escopo do problema central. Adiciona risco ético significativo |
| F15 | Análise preditiva de churn | Requer histórico longo de dados e modelos adicionais. É Fase 3 |
| F16 | App mobile | Caso de uso primário é desktop (trabalho de gestão) |
| F17 | Suporte multi-idioma | Focar no português no MVP para reduzir complexidade |

---

## Justificativa de Priorização

A priorização das funcionalidades Must Have foi realizada combinando dois frameworks estudados no curso:

### MoSCoW — Criticidade para o produto funcionar

As funcionalidades F01 a F05 foram classificadas como Must Have porque formam a espinha dorsal do produto. Sem F01 (importação), não há dados. Sem F02 (classificação), não há insight. Sem F03 e F04 (dashboard + plano de ação), a proposta de valor não existe. Sem F05 (autenticação), o produto não pode ser entregue para um cliente real.

### Value vs Effort — Onde investir primeiro

| Funcionalidade | Valor | Esforço | Quadrante | Decisão |
|---------------|:-----:|:-------:|-----------|---------|
| F01 — Importação CSV | Alto | Baixo | ✅ Fazer agora | MVP |
| F02 — Classificação IA | Alto | Médio | ✅ Fazer agora | MVP |
| F03 — Dashboard insights | Alto | Médio | ✅ Fazer agora | MVP |
| F04 — Plano de ação IA | Alto | Médio | ✅ Fazer agora | MVP |
| F13 — Integração Zendesk | Alto | Alto | 📅 Planejar | Fase 2 |
| F15 — Predição de churn | Médio | Alto | ⚠️ Evitar agora | Fase 3 |
| F12 — Dark mode | Baixo | Baixo | 🎯 Oportunidade rápida | Backlog |
| F14 — Resposta automática | Baixo | Alto | ❌ Evitar | Fora do escopo |

---

## Critérios de Aceitação do MVP (Go/No-Go)

O MVP será considerado bem-sucedido se, ao fim da Fase 1 (6 semanas), atender **todos** os seguintes critérios:

- [ ] Taxa de classificação correta dos temas ≥ 80% nas sessões de teste
- [ ] Ao menos 70% dos usuários-teste consideram o plano de ação "diretamente utilizável"
- [ ] Mínimo de 3 sessões de uso espontâneo (sem provocação) nos 14 dias após o lançamento
- [ ] Zero incidentes de segurança ou vazamento de dados durante o período de testes
- [ ] Tempo de processamento de upload ≤ 3 minutos para arquivos de até 50k linhas

Se esses critérios **não** forem atingidos, a hipótese central é invalidada e o produto deve ser repivotado antes de avançar para a Fase 2.

---

## Cronograma do MVP

| Sprint | Duração | Foco |
|--------|---------|------|
| Sprint 1 | Semanas 1–2 | Infraestrutura base, pipeline de ingestão, autenticação (F01, F05) |
| Sprint 2 | Semanas 3–4 | Classificação por tema via LLM, testes com dados reais do cliente (F02) |
| Sprint 3 | Semanas 5–6 | Dashboard de insights, geração de plano de ação, sessões de validação (F03, F04) |
| Review | Semana 6 | Sprint Review com time do cliente + coleta de métricas de aceitação |
