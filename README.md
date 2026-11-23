# Documentação do Projeto de Portfólio

## Introdução

Este documento fornece uma visão geral abrangente do projeto de portfólio, detalhando sua estrutura, as tecnologias utilizadas e as instruções para configuração e execução. O objetivo é servir como um guia para desenvolvedores que desejam entender, modificar ou contribuir para o projeto.

## Visão Geral do Projeto

O projeto de portfólio é uma aplicação web moderna desenvolvida para exibir os trabalhos e habilidades de um desenvolvedor. Ele apresenta uma interface de usuário interativa e responsiva, com suporte a múltiplos idiomas e a capacidade de visualizar documentos PDF diretamente no navegador. O portfólio é projetado para ser facilmente personalizável e extensível.

## Funcionalidades Principais

### Sistema de Skeleton Loading
O portfólio implementa um sistema avançado de skeleton loading similar ao YouTube, proporcionando uma experiência de carregamento suave com efeitos shimmer durante o carregamento das seções.

### Visualizador de PDF Integrado
O portfólio inclui um visualizador de PDF robusto que permite visualizar case studies diretamente no site, com funcionalidades como:
- Visualização em modal fullscreen
- Detecção automática de dispositivos móveis
- Fallback para dispositivos que não suportam visualização inline
- Botões de download e abertura em nova aba
- Interface responsiva com tema claro/escuro

### Sistema de Internacionalização (i18n)
Suporte completo para múltiplos idiomas (Português e Inglês) com:
- Detecção automática do idioma do navegador
- Switcher de idioma na interface
- Traduções completas de todos os textos

### 🆕 Seção "Novo Projeto" - Live Well Membership
Uma seção especial dedicada ao case study mais recente, localizada entre "Sobre" e "Portfólio":

#### Características da Seção:
- **Layout diferenciado**: Seção full-width com grid de 2 colunas
- **Background gradiente**: Azul claro para escuro com tema adaptável
- **Badge animado**: "Novo Projeto" com ponto pulsante
- **Imagem destacada**: Lado esquerdo com overlay e badge "Redesign Case"
- **Informações detalhadas**: Grade com 4 campos informativos
- **Botões de ação**: CTA principal para visualizar + botão de download
- **Animações**: FadeIn sequencial para entrada suave

#### Conteúdo Traduzido:
- **Português**: Foco em "experiência premium na costa da Flórida"
- **Inglês**: "Premium experience on Florida's coast"
- **Descrição completa**: Plataforma de membership exclusiva para a região costeira 30A da Flórida
- **Detalhes técnicos**: Foco em UX/UI, setor turismo & hospitalidade, tipo membership platform

#### Funcionalidades Especiais:
- **Visualizador PDF integrado**: Botão principal abre o case study
- **Download direto**: Botão secundário para download do PDF
- **Responsivo**: Adaptado para desktop, tablet e mobile
- **Tema escuro**: Totalmente compatível com modo escuro

### Portfólio de Projetos
#### Case Studies Disponíveis:
1. **🆕 Live Well Membership - UI Case** (2025) - **SEÇÃO ESPECIAL**
   - Categoria: Design de Interface 
   - Case study completo de redesign de plataforma de membership exclusiva para experiências na costa da Flórida (30A)
   - **Setor**: Turismo & Hospitalidade
   - **Foco**: Acesso privilegiado e benefícios únicos para membros
   - **Localização**: Seção dedicada entre "Sobre" e "Portfólio"
   - **Destaque**: Layout especial com animações e informações detalhadas

2. **Juritask - Gestão Jurídica** (2025)
   - Categoria: Desafio de Caso
   - Plataforma de gestão jurídica focada em processos legais

3. **Tracksales - Plataforma de Gestão** (2025)
   - Categoria: UI de App Móvel
   - Plataforma de gestão de vendas com interface móvel

4. **Me-ensina Smart Learning** (2024)
   - Categoria: Estudo de Caso
   - Plataforma educacional com tecnologia inteligente

5. **Benchmarking de Ferramentas de Fluxograma** (2024)
   - Categoria: Pesquisa UX
   - Análise comparativa de ferramentas de fluxograma

### Características Especiais do Live Well Membership
- **Badge "NOVO"**: Destaque visual para identificar o projeto mais recente
- **Imagem temática**: Imagem personalizada relacionada a saúde e bem-estar
- **Sem link externo**: Foco total no PDF case study completo
- **Visualizador otimizado**: Experiência de leitura aprimorada para o case study

### Animações e Transições
- Loading states com skeleton components
- Fade-in animations para seções
- Hover effects nos cards de projetos
- Transições suaves entre temas claro/escuro

### Responsividade
- Design adaptado para desktop, tablet e mobile
- Componentes otimizados para diferentes tamanhos de tela
- Touch-friendly interfaces para dispositivos móveis

## Tecnologias Utilizadas

O projeto de portfólio é construído com as seguintes tecnologias principais:

*   **React**: Uma biblioteca JavaScript para construir interfaces de usuário interativas.
*   **TypeScript**: Um superconjunto tipado de JavaScript que melhora a robustez e a manutenibilidade do código.
*   **Vite**: Um bundler de próxima geração que oferece uma experiência de desenvolvimento rápida e otimizada.
*   **Tailwind CSS**: Um framework CSS utilitário que permite a criação rápida de designs personalizados.
*   **i18next**: Uma estrutura de internacionalização para aplicações JavaScript, permitindo suporte a múltiplos idiomas.
*   **react-pdf**: Uma biblioteca para exibir documentos PDF em aplicações React.
*   **Framer Motion**: Uma biblioteca para animações de interface de usuário no React.

Além dessas, o projeto utiliza várias outras bibliotecas e ferramentas para desenvolvimento, linting e construção, conforme detalhado no arquivo `package.json`.

## Como rodar localmente

Pré-requisitos: **Node.js 18 ou mais novo** e npm.

```bash
npm install
npm run dev          # abre em http://localhost:5173
```

Outros comandos:

```bash
npm run build        # gera a pasta dist/ (antes, roda o sync:github)
npm run preview      # serve a build localmente
npm run lint         # análise de código
npm run sync:github  # atualiza src/data/github-snapshot.json com os repositórios públicos
```

O `sync:github` usa a API pública do GitHub. Definir a variável `GITHUB_TOKEN` (opcional) aumenta o limite de 60 para 5000 requisições por hora. Se a API falhar, a build continua com o snapshot já salvo.

Deploy: o projeto está pronto para a **Vercel** (o `vercel.json` já tem o rewrite de SPA). Basta importar o repositório e usar `npm run build` com saída em `dist`.

## Estrutura do Projeto

A estrutura de diretórios do projeto é organizada da seguinte forma:

```
Portfolio/
├── public/
│   ├── locales/
│   │   ├── en/
│   │   │   └── translation.json
│   │   └── pt/
│   │       └── translation.json
│   └── pdfs/
│       ├── benchmark.pdf
│       ├── juritask.pdf
│       ├── me-ensina.pdf
│       └── tracksales.pdf
├── src/
│   ├── components/
│   │   ├── ui/
│   │   │   ├── aurora-background.tsx
│   │   │   ├── behance-icon.tsx
│   │   │   ├── language-switcher.tsx
│   │   │   ├── moving-border.tsx
│   │   │   ├── pdf-viewer.tsx
│   │   │   ├── simple-pdf-viewer.tsx
│   │   │   └── text-shimmer.tsx
│   │   │   └── whatsapp-icon.tsx
│   ├── lib/
│   │   └── utils.ts
│   ├── App.tsx
│   ├── i18n.ts
│   ├── index.css
│   ├── main.tsx
│   └── vite-env.d.ts
├── .gitignore
├── index.html
├── package.json
├── package-lock.json
├── README.md
├── tailwind.config.js
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
└── ... (outros arquivos de configuração)
```

*   **`public/`**: Contém arquivos estáticos, como arquivos de localização (`locales/`) para internacionalização e documentos PDF (`pdfs/`) que são exibidos no portfólio.
*   **`src/`**: Contém o código-fonte principal da aplicação React.
    *   **`components/`**: Componentes React reutilizáveis, incluindo componentes de UI genéricos (`ui/`