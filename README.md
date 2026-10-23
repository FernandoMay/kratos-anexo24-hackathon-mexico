# KRATOS · Control de Anexo 24

**Proyecto para Hackathon México** · AI Hackathon México 2026, by AI Lab School
Desafio: **Control de Anexo 24 para empresas IMMEX**

**Demo no ar:** https://kratos-anexo24.vercel.app

## O desafio do hackathon

As empresas maquiladoras com programa IMMEX importam materiais sem pagar impostos, desde que os transformem e os exportem dentro de um prazo legal (por exemplo, 18 meses para insumos). Para comprovar isso, a lei exige o controle de inventários chamado **Anexo 24**, atualizado a todo momento. Hoje muitas empresas o mantêm em planilhas ou em software de desktop difícil de usar, sem saber quais materiais estão por vencer nem quanto dinheiro está em risco. Se falham, enfrentam multas de $27.070 a $54.180 MXN, pagamento de impostos e até a perda do programa IMMEX.

**O que o desafio pedia**
- Uma plataforma em nuvem com um único registro de cada material importado: o pedimento o alimenta, a produção o consome e a exportação o fecha, cada material com seu "relógio legal".
- **Funções obrigatórias:** registro de entradas (pedimentos) e saídas (exportações); cálculo de vencimentos e alertas; painel com o valor em risco.
- **Objetivos:** visibilidade (um painel com o que há, o que vence e quanto custaria), simplicidade (fechamento mensal em menos de 2 horas), prevenção (alertas a 90, 60 e 30 dias) e confiança (cada mudança registrada: quem, quando e por quê).
- **Perfis de teste:** fábrica de moldagem por injeção (com refugo e material reciclado), fábrica de chicotes/eletrônicos e empresa com várias razões sociais (RFC).
- **Critérios de avaliação:** clareza (um gerente de planta entende em 5 minutos), economia de tempo no fechamento, inovação, facilidade de uso e viabilidade técnica.

## O que é o KRATOS

KRATOS transforma cada pedimento em um prazo-limite e em um valor em pesos, e diz ao gerente o que decidir hoje. Cada pessoa da equipe da empresa entra com seu perfil e vê só o que lhe cabe; tudo o que faz fica na bitácora com seu nome. Funciona em desktop, tablet e celular, em modo claro e escuro.

**Princípio de confiança:** os números vêm de regras auditáveis (PEPS, prazos do art. 108, IGI, IVA, DTA), não da IA. A IA só redige causas e responde perguntas com esses dados. O especialista aduaneiro revisa e assina cada fechamento.

### Funcionalidades

| Seção | O que faz |
|---|---|
| **Resumo** | Visão de 1 minuto para o gerente: índice de cumprimento, dinheiro em risco, economia e as 3 decisões da semana |
| **Painel tático** | Valor em risco por material e por data de vencimento; previsão "se nada for feito" a 30, 60 e 90 dias; alertas de vencimento (90/60/30); consumo real vs. plano; matriz de decisão e cenários "e se…?" |
| **Pergunte ao Métron** | Assistente de IA para consultar o inventário em linguagem simples, com o valor em pesos |
| **Registro** | Pedimentos de importação, lotes, exportações (descargas) e simulador de descargas PEPS que pode ser aplicado e revertido |
| **Fechamento do mês** | Fechamento guiado com cronômetro: só aparecem os problemas, cada um com causa e primeiro passo; revisão e assinatura do especialista |
| **Dados e conciliação** | Leitor de arquivos SAT Data Stage e do agente aduaneiro (CSV), conciliação entre os dois, completude dos pedimentos e linhagem dos dados |
| **Botão "¿Qué hago?"** | Em cada alerta: causa em linguagem simples, opções com custo em pesos (exportar, retornar, importar em definitivo ou não fazer nada) e primeiro passo concreto |
| **Informe** | Relatório Anexo 24 por pedimento e saldos por fração tarifária, e resumo de 1 página para o gerente |
| **Viabilidade técnica** | Mercado, modelo de negócio, arquitetura, aderência à norma (RGCE 2025), método de construção, protótipo vs. produto e riscos |
| **Bitácora** | Registro selado de cada mudança: quem, quando e por quê; nada é apagado |

**Perfis de acesso:** gerente de planta, analista de comércio exterior, especialista aduaneiro, responsável de produção e auditoria em somente leitura.

**Dados de demonstração:** duas razões sociais (uma de moldagem por injeção e outra de ensamble de arneses/eletrônicos), com lotes, pedimentos e discrepâncias SAT vs. agente de exemplo.

## Tecnologias

- **Frontend:** HTML5, CSS3 e JavaScript puro, sem framework e sem etapa de build.
- **Fontes:** Archivo, Public Sans e JetBrains Mono (Google Fonts).
- **Motor de regras no navegador:** projeção PEPS, prazos legais, IGI, IVA e DTA, índice de cumprimento e conciliação.
- **IA opcional (Métron):** provedor à escolha, com a chave do próprio usuário: Gemini (Google), ChatGPT (OpenAI), Claude (Anthropic) ou outro compatível com OpenAI. Sem chave, o app usa regras locais.
- **Publicação:** Vercel (site estático).

## Metodologia

O KRATOS foi construído com o **método BMAD** (agentes especializados do Claude Code), que mantém um plano escrito para a IA não se desviar do que foi decidido: **Plan → Design → Build → Test → Deploy**.

| Agente | Artefato | No KRATOS |
|---|---|---|
| Analista | Brief do problema | Dores, perfis de teste e prioridades |
| PM | PRD | Cada requisito do desafio mapeado a uma tela |
| UX | Fluxos e design | 5 perfis, paleta sem vermelho-verde, claro e escuro, celular |
| Arquiteto | Arquitetura | Motor de regras + ledger + IA via servidor |
| Scrum Master | Histórias | "Como gerente quero aprovar o plano para evitar a multa" |
| Dev | Protótipo | Esta aplicação em HTML, CSS e JavaScript |
| QA | Testes | Fluxo completo, permissões, claro/escuro, 400 px e impressão |

Também usamos priorização **MoSCoW** (painel com dinheiro em risco e alertas primeiro; depois "¿Qué hago?", previsão e relatórios, fechamento guiado e, por último, o chat), uma análise **5W2H** da viabilidade e o fluxo de dados do desafio (pedimento → ledger → produção → exportação → relatório → assinatura).

## Protótipo hoje vs. produto

| Funciona hoje (protótipo) | No produto |
|---|---|
| Dados de teste de 2 razões sociais | Dados reais importados do SAT e do agente |
| Dados salvos no navegador de quem usa a demo | Banco de dados em nuvem com backup diário |
| Perfis com acesso de um clique | Login único e permissões por perfil |
| IA: regras locais ou a IA da equipe com chave própria | IA aprovada pela empresa, chamada pelo servidor |
| CSV com colunas simples | Formatos oficiais do Data Stage e do agente |

## Estrutura de pastas e arquivos

```
KRATOS - Anexo 24/
├── index.html   # Estrutura das telas: abertura, login por perfil, as 9 seções do menu e a viabilidade
├── style.css    # Estilos, temas claro/escuro e layout responsivo
├── app.js       # Dados de demonstração, motor de regras (PEPS, prazos, IGI/IVA/DTA), perfis e permissões,
│                # fechamento e bitácora, leitor de CSV, Métron (IA) e tour guiado
└── README.md    # Este arquivo
```

## Como executar

Não há dependências para instalar. Abra o `index.html` no navegador, ou sirva a pasta localmente:

```powershell
python -m http.server 8000
```

Depois acesse http://localhost:8000. Para usar o Métron com IA, clique no botão de IA no topo e informe a chave do provedor escolhido (ela fica só no seu navegador).

## Equipo

- Mariana Resende Maia
- Sergio Campos Medina
- Francisco Hernandez
- May Fuentes Fernando
