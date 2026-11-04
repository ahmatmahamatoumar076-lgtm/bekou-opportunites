# BEKOU ACADEMY – Opportunités hebdomadaires

Ce dépôt alimente la section bourses et opportunités de https://bekouacademy.com.
Hostinger déploie automatiquement ce dépôt dans `public_html/data/`, et la page d'accueil charge
`/data/opportunites.js`. Les éléments de ce fichier s'ajoutent aux bourses et opportunités déjà présentes sur le site.

## Fichier à modifier : `opportunites.js`

Il définit `window.BEKOU_AJOUTS = { "maj": "AAAA-MM-JJ", "bourses": [...], "opportunites": [...] };`.
Le contenu entre les accolades doit rester du JSON valide (guillemets doubles, pas de virgule finale).

### Format d'une bourse (`bourses`)

```json
{
  "id": 2001,
  "titre": "Nom officiel de la bourse – Pays",
  "pays": "France",
  "flag": "🇫🇷",
  "niveau": ["Licence", "Master", "Doctorat"],
  "cat": "Gouvernement",
  "resume": "Une ou deux phrases claires en français.",
  "couverture": ["Frais de scolarité", "Allocation mensuelle"],
  "conditions": ["Condition 1", "Condition 2"],
  "periode": "Candidatures jusqu'au 15 janvier 2027",
  "dateLimite": "2027-01-15",
  "lien": "https://site-officiel/page-de-la-bourse",
  "source": "https://site-officiel/page-de-la-bourse",
  "ajouteLe": "2026-11-06",
  "couleur": "#dbeafe"
}
```

- `cat` : `Gouvernement`, `Université` ou `Fondation`.
- `couleur` : une valeur parmi `#dbeafe`, `#fee2e2`, `#fef9c3`, `#ffe4e6`, `#f1f5f9`, `#e0e7ff`, `#ffedd5`, `#dcfce7`, `#ede9fe`.
- `id` : entier unique à partir de 2001 (bourses).

### Format d'une opportunité (`opportunites`)

```json
{
  "id": 3001,
  "type": "Stage",
  "titre": "Nom officiel du programme",
  "pays": "Sénégal",
  "flag": "🇸🇳",
  "niveau": ["Master"],
  "financement": "Stage rémunéré",
  "resume": "Une ou deux phrases claires en français.",
  "couverture": ["Indemnité mensuelle"],
  "conditions": ["Condition 1", "Condition 2"],
  "periode": "Candidatures jusqu'au 30 novembre 2026",
  "dateLimite": "2026-11-30",
  "lien": "https://site-officiel/page",
  "source": "https://site-officiel/page",
  "ajouteLe": "2026-11-06",
  "lieu": "Dakar",
  "court": "Titre court (3 à 4 mots)"
}
```

- `type` : `Stage`, `Formation`, `Cours en ligne` ou `Conférence`.
- `id` : entier unique à partir de 3001 (opportunités).

## Règles de vérification (obligatoires)

1. **Source officielle uniquement** : le site de l'organisme qui finance ou organise (gouvernement, ambassade, université, fondation, organisation internationale). Les agrégateurs servent seulement à découvrir une piste : on publie le lien officiel.
2. **Date limite** à au moins 14 jours de la date de publication, et confirmée sur la page officielle de l'édition en cours.
3. **Éligibilité** : ouverte aux ressortissants de la République centrafricaine, ou plus largement à l'Afrique subsaharienne ou aux pays en développement. Elle doit être confirmée sur la source.
4. **Aucuns frais suspects** : on exclut toute opportunité qui demande un paiement pour postuler, sauf les frais officiels d'une université reconnue.
5. **Pas de doublon** avec ce fichier ni avec les bourses déjà présentes sur le site (Eiffel, Chevening, etc.).
6. **Nettoyage** : retirer chaque semaine les éléments dont `dateLimite` est dépassée.
7. **Volume** : 3 à 8 nouveautés par semaine. On privilégie la qualité. Si rien n'est fiable, on n'ajoute rien.
8. **Rédaction** en français simple et neutre, sans promesse (« financement intégral » seulement si la source le confirme).
