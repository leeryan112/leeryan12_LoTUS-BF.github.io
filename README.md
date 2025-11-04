[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/DZepDCgF)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=20773481&assignment_repo_type=AssignmentRepo)

# 🧠 LoTUS-BF (Location-or-Term Unified Search for Brain Functions)

## 🚀 Overview
This project provides an enhanced **interactive frontend** for the *LoTUS-BF* system — a Neurosynth-inspired brain function search interface.

The web app connects to the backend API hosted at  
[`https://mil.psy.ntu.edu.tw:5000`](https://mil.psy.ntu.edu.tw:5000),  
allowing users to browse neuroscience-related **terms**, **find their co-occurrences**, and **query studies** using logical expressions.

The interface is implemented in **React + Vite**, with real-time data fetching and dynamic rendering, requiring no page reloads.

---

## 🧩 API Endpoints

| Endpoint | Description | Example |
|-----------|-------------|----------|
| `/terms` | Retrieve all available neuroscience terms | [https://mil.psy.ntu.edu.tw:5000/terms](https://mil.psy.ntu.edu.tw:5000/terms) |
| `/terms/<term>` | Retrieve co-occurring related terms with counts and Jaccard indices | [https://mil.psy.ntu.edu.tw:5000/terms/amygdala](https://mil.psy.ntu.edu.tw:5000/terms/amygdala) |
| `/query/<query_string>/studies` | Search studies using logical expressions | [https://mil.psy.ntu.edu.tw:5000/query/amygdala%20not%20emotion/studies](https://mil.psy.ntu.edu.tw:5000/query/amygdala%20not%20emotion/studies) |

---

## 🧠 Features

### 🔍 Term Browser
- Displays all available terms grouped by **A–Z toggles**
- Supports **real-time filtering** via search input  
- Expands letter groups dynamically on click
- Optimized to load large term lists efficiently

### 🧩 Related Term Explorer
- Shows related terms for the selected keyword (e.g. `與「amygdala」相關的詞與出現次數`)
- Displays **co-occurrence counts**
- Supports **“Show all”** expansion and **click-to-add** integration with the Query Builder

### 🧮 Query Builder
- Supports complex logical expressions:  
  `amygdala AND memory`, `emotion OR reward`, `vision NOT motor`
- Boolean-safe parser with parentheses and operator precedence  
- Provides quick-append buttons (`AND`, `OR`, `NOT`, `(`, `)`, `Reset`, `Clear last`)

### 📚 Studies Viewer
- Displays related research articles with sortable columns:
  - **Year**, **Journal**, **Title**, **Authors**
- Integrates external links:
  - `PubMed 開啟` | `Google Scholar 搜尋`
- Paginated and responsive layout  
- Each study visually separated by clear dividers

### 🧬 NIfTI Viewer
- Visualizes activation maps in **coronal**, **sagittal**, and **axial** views
- Adjustable **threshold**, **percentile**, and **alpha blending**
- Linked dynamically with the current query

---

## 🛠️ Tech Stack

| Layer | Technology |
|--------|-------------|
| **Frontend** | React (Vite) + Tailwind CSS |
| **Logic & Data Fetching** | JavaScript (ES6), `fetch()`, `AbortController` |
| **Deployment** | GitHub Pages (`vite build` → upload `/dist`) |
| **Backend API** | [LoTUS-BF API – NTU Mind and Language Lab](https://mil.psy.ntu.edu.tw:5000) |

---

## ⚙️ Local Development

```bash
# Install Node (LTS)
nvm install --lts
nvm use --lts

# Install dependencies
npm install

# Run local development server
npm run dev

# Build for deployment
npm run build
