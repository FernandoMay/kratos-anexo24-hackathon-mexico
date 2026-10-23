# KRATOS · Control de Anexo 24

**Proyecto para Hackathon México**

## Visão geral

KRATOS é uma aplicação web (frontend) para o controle do Anexo 24: acompanha o índice de cumprimento, lotes por vencer, diferenças entre SAT e agência aduanal, e o fechamento mensal com bitácora de quem fez cada ação. Cada perfil (gerente de planta, analista de comércio exterior, especialista aduanal, responsável de produção e auditoria) vê apenas o que lhe cabe. Funciona em desktop, tablet e celular, com modo claro e escuro.

O código atual é somente o frontend, com dados de demonstração.

**Tecnologias:** HTML5, CSS3 e JavaScript puro (sem framework nem etapa de build); fontes Archivo, Public Sans e JetBrains Mono via Google Fonts.

## Estrutura de pastas e arquivos

```
KRATOS - Anexo 24/
├── index.html   # Estrutura das telas: abertura, login por perfil, resumo, fechamento, viabilidade
├── style.css    # Estilos, temas claro/escuro e layout responsivo
├── app.js       # Lógica da aplicação: perfis e permissões, dados de demonstração, navegação, fechamento e bitácora, tour guiado
└── README.md    # Este arquivo
```

## Como executar

Não há dependências para instalar. Basta abrir o `index.html` no navegador, ou servir a pasta localmente:

```powershell
python -m http.server 8000
```

Depois acesse http://localhost:8000.

## Equipo

- Mariana
- Sergio
- Francisco
- May
