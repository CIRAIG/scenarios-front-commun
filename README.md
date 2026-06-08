# Scénarios de transition énergétique — Front commun pour la transition énergétique du Québec

> **🌐 Accéder à l'application : [ciraig.github.io/scenarios-front-commun](https://ciraig.github.io/scenarios-front-commun/)**

Tableau de bord interactif présentant les résultats de modélisation des scénarios de transition énergétique développés dans le cadre du [Front commun pour la transition énergétique du Québec](https://www.pourlatransitionenergetique.org/).

---

## À propos

Les scénarios combinent deux outils de modélisation complémentaires :

- **[EnergyScope-Québec](https://github.com/CIRAIG/EnergyScope-Quebec)** — modélisation du système énergétique québécois à l'horizon 2050
- **[mescal](https://mescal.readthedocs.io/en/latest/)** — couplage avec l'analyse du cycle de vie (ACV) via le framework Brightway

Les résultats couvrent le mix énergétique, les coûts système, les impacts environnementaux (santé humaine, qualité des écosystèmes, changement climatique) et les flux de carbone pour neuf scénarios contrastés.

## Scénarios

| Identifiant | Description | Contrainte |
|---|---|---|
| `actuel` | État du système en 2023 | Référence |
| `brut` | Croissance non contrainte | — |
| `brut_nz` | Croissance non contrainte | Zéro net |
| `acc_verte` | Accélération verte | — |
| `acc_verte_nz` | Accélération verte | Zéro net |
| `sobre` | Sobriété énergétique | — |
| `sobre_nz` | Sobriété énergétique | Zéro net |
| `sobre_lim_cc_nz` | Sobriété + CCS limité | Zéro net |
| `energyscope_nz` | Optimum EnergyScope (Canada's Energy Future 2023) | Zéro net |

## Structure du dépôt

```
├── index.html        # Application web (page unique)
├── Results/          # Graphes Plotly auto-contenus (.html)
│   ├── configuration_*.html
│   ├── contributions_*.html
│   ├── costs_system.html
│   ├── sankey_*.html
│   └── sankey_carbon_flows_*.html
└── README.md
```

## Déploiement

L'application est hébergée via **GitHub Pages** (branche `main`, dossier racine). Tout push sur `main` met à jour le site automatiquement.

Pour tester en local :

```bash
cd scenarios-front-commun
python -m http.server 8080
# → ouvrir http://localhost:8080
```

> Note : les iframes Plotly nécessitent un serveur HTTP. L'ouverture directe via `file://` ne fonctionne pas dans Chrome/Safari.

## Ajouter un scénario ou un graphe

Voir les instructions détaillées dans le fichier [`CONTRIBUTING.md`](CONTRIBUTING.md) (ou la section *README technique* ci-dessous).

### Ajouter un scénario (résumé)

1. Déposer `Results/sankey_<id>.html` et `Results/sankey_carbon_flows_<id>.html`
2. Ajouter une `<option value="<id>">` dans le `<select id="scenario-select">` de `index.html`
3. Ajouter une entrée dans `const SANKEY_MAP` dans le `<script>` de `index.html`

### Ajouter un graphe comparatif (résumé)

1. Déposer `Results/mon_graphe.html`
2. Ajouter un `<div class="nav-item" onclick="loadChart(this, 'Results/mon_graphe.html', 'Titre', 'Description')">` dans la `<aside>` de `index.html`

---

## Auteurs

| Auteur·e | Contributions |
|---|---|
| **Matthieu Souttre** | Conception du site, Modélisation, Résultats, Analyse |
| **Titouan Greffe** | Résultats, Analyse |
| **Éric Pineault** | Narratifs |
| **Cécile Bulle** | Supervision |

---

*Développé au [CIRAIG](https://ciraig.org/), Polytechnique Montréal.*
