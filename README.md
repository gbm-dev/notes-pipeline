# 🚀 Obsidian Notes Hugo CI/CD Pipeline

Welcome to the CI/CD pipeline for my Obsidian Notes! This project automates the process of building and deploying a feature-rich static website using Hugo, with content sourced from a separate notes repository.

## 🎯 Goals

- Automate the build and deployment process for Obsidian Notes
- Maintain separation between content (notes) and site infrastructure
- Generate a dynamic knowledge graph from Markdown content
- Seamlessly integrate with Azure Static Web Apps
- Provide a customizable and extensible foundation for note-taking and knowledge management
- Render Mermaid diagrams server-side for improved performance and SEO

## 🏗️ Architecture

This project uses a two-repository structure:
1. **Notes Repository**: Contains only Obsidian notes (Markdown files)
2. **Hugo Repository** (this repo): Contains Hugo templates, theme, and CI/CD scripts

## 🛠️ Technologies

This pipeline leverages a powerful stack of technologies:
- **[Hugo](https://gohugo.io/)**: Lightning-fast static site generator
- **[PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)**: Clean, responsive Hugo theme (customized)
- **[Azure Static Web Apps](https://azure.microsoft.com/services/app-service/static/)**: Serverless hosting platform
- **[GitHub Actions](https://github.com/features/actions)**: CI/CD automation
- **[Python](https://www.python.org/)**: Custom scripts for knowledge graph generation
- **[D3.js](https://d3js.org/)**: Interactive data visualizations
- **[Mermaid](https://mermaid-js.github.io/mermaid/#/)**: Diagramming and charting tool
- **[Puppeteer](https://pptr.dev/)**: Headless browser for server-side rendering of Mermaid diagrams

## 🔧 Key Components

1. **Hugo Site Structure**: Customized PaperMod theme with additional layouts and shortcodes
2. **Knowledge Graph Generator**: Python script to analyze Markdown files and create a JSON representation of interconnected notes
3. **GitHub Actions Workflows**: 
   - Main workflow for building and deploying the Hugo site
   - Workflow for responding to updates in the Notes repository
4. **Azure Static Web Apps Configuration**: Seamless hosting and global content delivery
5. **Mermaid Renderer**: Node.js script using Puppeteer to pre-render Mermaid diagrams as SVGs

## 🚀 Deployment Process

1. New note is pushed to the Notes repository
2. Notes repository workflow triggers the Hugo repository workflow
3. Hugo repository workflow:
   - Checks out both Hugo and Notes repositories
   - Sets up Node.js environment and installs dependencies
   - Pre-renders Mermaid diagrams found in Markdown files
   - Generates knowledge graph from Markdown files
   - Builds Hugo site with custom layouts and shortcodes
   - Deploys built site to Azure Static Web Apps

## 🎨 Customization

This pipeline is designed to be easily customizable:
- Modify `config.yaml` to adjust site parameters and menu structure
- Edit layouts in the `layouts/` directory to change page structure
- Add or modify shortcodes in `layouts/shortcodes/` for custom content elements
- Adjust the knowledge graph generation script in `scripts/generate_knowledge_graph.py`
- Customize Mermaid rendering in `scripts/render_mermaid.js`

## 📊 Features

- **📚 Dynamic Knowledge Graph**: Visualize connections between notes
- **🔍 Full-Text Search**: Quickly find relevant information
- **📊 Mermaid Diagrams**: Create flowcharts, sequence diagrams, and more directly in Markdown, pre-rendered for performance
- **🎨 Excalidraw Support**: Embed hand-drawn style diagrams
- **📁 Folder Structure**: Organized content with intuitive navigation

## 🛠️ Setup

1. Clone this repository
2. Set up secrets in this repository's settings:
   - `AZURE_STATIC_WEB_APP_TOKEN`: Your Azure Static Web App deployment token
3. In your Notes repository, set up a secret:
   - `HUGO_REPO_ACCESS_TOKEN`: A GitHub Personal Access Token with repo scope for this Hugo repository
4. Set up the workflow file in your Notes repository to trigger this repository's workflow on new commits
5. Ensure your build environment (GitHub Actions runner or local setup) has the necessary dependencies for Puppeteer. Note that we updated some dependencies to handle vulnerabilities:

   ```bash
   sudo apt-get update && sudo apt-get install -y \
       libasound2t64 libatk1.0-0t64 libc6 libcairo2 libcups2t64 libdbus-1-3 \
       libexpat1 libfontconfig1 libgcc-s1 libgdk-pixbuf2.0-0 libglib2.0-0t64 \
       libgtk-3-0t64 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 \
       libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 \
       libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation \
       libappindicator3-1 libnss3 lsb-release xdg-utils wget libgbm-dev
   ```

6. Update Node.js dependencies using the following commands to handle high-severity vulnerabilities:

   ```bash
   npm install puppeteer@latest puppeteer-core@latest ws@latest @mermaid-js/mermaid-cli@latest
   npm audit fix
   ```

   These steps help ensure that the environment is secure and up-to-date.
