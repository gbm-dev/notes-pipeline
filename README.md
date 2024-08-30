# 🚀 Obsidian Notes Hugo CI/CD Pipeline

Welcome to the CI/CD pipeline for my Obsidian Notes! This project automates the process of building and deploying a feature-rich static website using Hugo, with content sourced from a separate notes repository.

## 🎯 Goals

- Automate the build and deployment process for Obsidian Notes
- Maintain separation between content (notes) and site infrastructure
- Generate a dynamic knowledge graph from Markdown content
- Seamlessly integrate with Azure Static Web Apps
- Provide a customizable and extensible foundation for note-taking and knowledge management

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

## 🔧 Key Components

1. **Hugo Site Structure**: Customized PaperMod theme with additional layouts and shortcodes
2. **Knowledge Graph Generator**: Python script to analyze Markdown files and create a JSON representation of interconnected notes
3. **GitHub Actions Workflows**: 
   - Main workflow for building and deploying the Hugo site
   - Workflow for responding to updates in the Notes repository
4. **Azure Static Web Apps Configuration**: Seamless hosting and global content delivery

## 🚀 Deployment Process

1. New note is pushed to the Notes repository
2. Notes repository workflow triggers the Hugo repository workflow
3. Hugo repository workflow:
   - Checks out both Hugo and Notes repositories
   - Sets up Python environment and installs dependencies
   - Generates knowledge graph from Markdown files
   - Builds Hugo site with custom layouts and shortcodes
   - Deploys built site to Azure Static Web Apps

## 🎨 Customization

This pipeline is designed to be easily customizable:

- Modify `config.yaml` to adjust site parameters and menu structure
- Edit layouts in the `layouts/` directory to change page structure
- Add or modify shortcodes in `layouts/shortcodes/` for custom content elements
- Adjust the knowledge graph generation script in `scripts/generate_knowledge_graph.py`

## 📊 Features

- **📚 Dynamic Knowledge Graph**: Visualize connections between notes
- **🔍 Full-Text Search**: Quickly find relevant information
- **📊 Mermaid Diagrams**: Create flowcharts, sequence diagrams, and more directly in Markdown
- **🎨 Excalidraw Support**: Embed hand-drawn style diagrams
- **📁 Folder Structure**: Organized content with intuitive navigation

## 🛠️ Setup

1. Clone this repository
2. Set up secrets in this repository's settings:
   - `AZURE_STATIC_WEB_APP_TOKEN`: Your Azure Static Web App deployment token
3. In your Notes repository, set up a secret:
   - `HUGO_REPO_ACCESS_TOKEN`: A GitHub Personal Access Token with repo scope for this Hugo repository
4. Set up the workflow file in your Notes repository to trigger this repository's workflow on new commits

![image](https://github.com/user-attachments/assets/1a230cbd-8483-4278-b551-ca5e509328ee)


Happy note-taking and knowledge building! 🚀📚
