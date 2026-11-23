# Portfolio — devuchoa.dev

My personal portfolio: Software Engineer focused on data analysis, Product Designer with a fullstack background. The dev projects section is synced live with my public GitHub repositories, and the product/UX cases open as PDFs right on the page.

**[devuchoa.dev](https://devuchoa.dev)** · [🇧🇷 Leia em português](#-português)

## What's on the site

| Section | Content |
| --- | --- |
| **Home** | Positioning, a code-style profile card, key metrics, process (observe → structure → build) and CV download. |
| **Dev projects** | Live data from the GitHub API: profile, language mix, and project cards with curated summaries, architecture layers and stack, "new project" badges and demo links. |
| **Product/UI** | UX and UI cases (Live Well Membership, Juritask, Tracksales, Me-ensina) with an integrated PDF viewer and links to Behance. |
| **Path** | Professional experience, education and certifications. |
| **Contact** | Quick message form that sends by e-mail or WhatsApp, plus LinkedIn, Behance and GitHub links. |

## How the GitHub sync works

- At runtime, `useGithubRepos` fetches the profile and repositories of the account set in `githubUser` (`src/data/portfolio.ts`) from the public GitHub API and caches them in `localStorage` for 6 hours.
- `src/data/github-snapshot.json` is a versioned snapshot used for the first paint and as a fallback when the API is rate-limited. `npm run sync:github` regenerates it, and it also runs automatically before every build (`prebuild`).
- Forks, archived and private repos are hidden, along with the profile README repo. `featuredRepoNames` pins repos to the top, `noNewBadgeRepoNames` keeps the site itself from showing up as "new", and `projectTechnologyStacks` plus `projectProfiles` add hand-written summaries and stacks; repos without a curated profile fall back to their language and topics.

## Features

- Portuguese and English for the whole site, with automatic browser-language detection and a language switcher.
- Integrated PDF viewer (react-pdf / pdf.js) in a fullscreen modal, with mobile detection, download and open-in-new-tab fallbacks.
- Light and dark themes, skeleton and shimmer loading, lazy images and Framer Motion animations.
- Vercel Web Analytics.

## Stack

React 18 · TypeScript · Vite · Tailwind CSS · Framer Motion · i18next · react-pdf / pdf.js · Lucide · GitHub REST API · Vercel

## Running locally

Requirements: **Node.js 18+** and npm.

```bash
npm install
npm run dev          # http://localhost:5173
```

```bash
npm run build        # builds to dist/ (runs sync:github first)
npm run preview      # serves the build locally
npm run lint         # code analysis
npm run sync:github  # refreshes src/data/github-snapshot.json
```

`sync:github` uses the public GitHub API. Setting `GITHUB_TOKEN` (optional) raises the limit from 60 to 5000 requests per hour. If the API fails, the build continues with the saved snapshot.

## Project structure

```text
src/
  App.tsx                        page composition and section navigation
  components/portfolio-sections.tsx  all page sections (home, projects, cases, path, contact, footer)
  components/ui/                 PDF viewer, skeletons, animated backgrounds, icons, language switcher
  data/portfolio.ts              GitHub user, curated project profiles and all PT/EN copy
  data/github-snapshot.json      versioned GitHub snapshot (fallback)
  hooks/useGithubRepos.ts        live GitHub fetch with cache and fallback
  types/github.ts                GitHub and locale types
public/
  pdfs/                          CVs and case study PDFs
  images/                        photos and thumbnails
scripts/sync-github.mjs          snapshot generator
```

## Deploy

The site is deployed on **Vercel**, connected to this repository: every push to `main` triggers a new deployment. `vercel.json` already has the SPA rewrite and long-lived cache headers for images. To set it up from scratch, import the repository on Vercel and use `npm run build` with `dist` as the output.

---

## 🇧🇷 Português

# Portfólio — devuchoa.dev

Meu portfólio pessoal: Software Engineer focado em análise de dados e Product Designer com background fullstack. A seção de projetos dev é sincronizada ao vivo com os meus repositórios públicos do GitHub, e os cases de produto/UX abrem em PDF na própria página.

**[devuchoa.dev](https://devuchoa.dev)**

### O que tem no site

| Seção | Conteúdo |
| --- | --- |
| **Início** | Posicionamento, cartão de perfil em formato de código, métricas, processo (observar → estruturar → construir) e download do CV. |
| **Projetos Dev** | Dados ao vivo da API do GitHub: perfil, mix de linguagens e cards de projeto com resumos curados, camadas de arquitetura e stack, selo de "novo projeto" e links de demo. |
| **Produto/UI** | Cases de UX e UI (Live Well Membership, Juritask, Tracksales, Me-ensina) com visualizador de PDF integrado e links para o Behance. |
| **Trajetória** | Experiência profissional, formação e certificações. |
| **Contato** | Formulário de mensagem rápida que envia por e-mail ou WhatsApp, mais links de LinkedIn, Behance e GitHub. |

### Como funciona a sincronização com o GitHub

- Em tempo de execução, o `useGithubRepos` busca o perfil e os repositórios da conta definida em `githubUser` (`src/data/portfolio.ts`) na API pública do GitHub e guarda em cache no `localStorage` por 6 horas.
- O `src/data/github-snapshot.json` é um snapshot versionado, usado na primeira pintura e como fallback quando a API limita as requisições. O `npm run sync:github` gera esse arquivo de novo, e ele também roda sozinho antes de cada build (`prebuild`).
- Forks, repositórios arquivados e privados ficam ocultos, assim como o repositório do README de perfil. O `featuredRepoNames` fixa projetos no topo, o `noNewBadgeRepoNames` impede o próprio site de aparecer como "novo", e o `projectTechnologyStacks` com o `projectProfiles` acrescentam resumos e stacks escritos à mão; repositórios sem perfil curado usam a linguagem e os tópicos do GitHub.

### Recursos

- Site inteiro em português e inglês, com detecção automática do idioma do navegador e seletor de idioma.
- Visualizador de PDF integrado (react-pdf / pdf.js) em modal de tela cheia, com detecção de celular e opções de baixar ou abrir em nova aba.
- Tema claro e escuro, skeleton e shimmer no carregamento, imagens lazy e animações com Framer Motion.
- Vercel Web Analytics.

### Stack

React 18, TypeScript, Vite, Tailwind CSS, Framer Motion, i18next, react-pdf / pdf.js, Lucide, API REST do GitHub e Vercel.

### Como rodar localmente

Pré-requisitos: **Node.js 18 ou mais novo** e npm.

```bash
npm install
npm run dev          # abre em http://localhost:5173
npm run build        # gera a pasta dist/ (antes, roda o sync:github)
npm run preview      # serve a build localmente
npm run lint         # análise de código
npm run sync:github  # atualiza o src/data/github-snapshot.json
```

O `sync:github` usa a API pública do GitHub. Definir a variável `GITHUB_TOKEN` (opcional) aumenta o limite de 60 para 5000 requisições por hora. Se a API falhar, a build continua com o snapshot já salvo.

### Estrutura

A estrutura de pastas está na versão em inglês acima: `App.tsx` monta a página, `components/portfolio-sections.tsx` tem todas as seções, `components/ui/` traz o visualizador de PDF, skeletons, fundos animados e ícones, `data/portfolio.ts` concentra o usuário do GitHub, os perfis curados e todos os textos PT/EN, e `hooks/useGithubRepos.ts` faz a busca ao vivo com cache e fallback. Os PDFs ficam em `public/pdfs/` e o gerador do snapshot em `scripts/sync-github.mjs`.

### Deploy

O site está publicado na **Vercel**, conectada a este repositório: cada push na `main` dispara um novo deploy. O `vercel.json` já tem o rewrite de SPA e cache longo para as imagens. Para configurar do zero, importe o repositório na Vercel e use `npm run build` com saída em `dist`.
