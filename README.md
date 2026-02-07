# Anti-Plagiat — Finary Scripts

Outil interne de vérification d'originalité pour les scripts vidéo Finary.

## Déploiement sur Vercel (2 min)

### Prérequis
- Un compte [Vercel](https://vercel.com) (gratuit)
- Une clé API Anthropic

### Étapes

1. **Pousse ce dossier sur GitHub**
   ```bash
   cd finary-antiplagiat
   git init
   git add .
   git commit -m "init"
   # Crée un repo sur GitHub puis :
   git remote add origin https://github.com/TON-USER/finary-antiplagiat.git
   git push -u origin main
   ```

2. **Connecte à Vercel**
   - Va sur [vercel.com/new](https://vercel.com/new)
   - Importe ton repo GitHub
   - Clique "Deploy"

3. **Ajoute la clé API**
   - Dans Vercel → Settings → Environment Variables
   - Ajoute : `ANTHROPIC_API_KEY` = `sk-ant-...`
   - Redéploie (Deployments → Redeploy)

4. **Partage l'URL**
   - Vercel te donne une URL type `finary-antiplagiat.vercel.app`
   - Partage-la à l'équipe sur Slack

### Structure
```
finary-antiplagiat/
├── api/
│   └── claude.js        ← Proxy API (cache la clé)
├── public/
│   └── index.html       ← Interface
├── vercel.json          ← Config Vercel
└── README.md
```

## Fonctionnalités
- **Sources YouTube** : colle des URLs, Claude récupère les transcriptions via web search
- **Sources texte** : URLs d'articles, références, citations
- **Analyse** : score d'originalité, passages à risque, verdict GO/ATTENTION/NO GO
- **Export** : copie le rapport en Markdown pour Notion/Handbook
