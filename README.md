# Linktree — Alicia Cavallo

Ma page de liens personnelle, conçue dans Figma puis codée à la main en HTML et CSS, sans framework ni outil payant.

**🔗 Voir la page en ligne : [aliciacavallo.github.io/linktree](https://aliciacavallo.github.io/linktree/)**

## Pourquoi ce projet

- Remplacer un service payant (Linktree, Karde…) par une page que je contrôle entièrement.
- Avoir des statistiques : combien de visites, quels liens sont cliqués.
- M'entraîner à écrire du CSS propre et maintenable, relié à un vrai design system.

L'objectif n'est pas l'effet visuel, mais **la qualité du code**.

## Contraintes que je me suis fixées

- Toutes les valeurs (couleurs, espacements, tailles…) viennent de **design tokens**, avec les mêmes noms que les variables Figma.
- Architecture CSS en **`@layer`** : aucun `!important`, aucun `id` dans le CSS, aucun sélecteur de plus de 3 niveaux.
- Classes **BEM** identiques aux noms des composants Figma.
- **Accessibilité** : HTML sémantique, contrastes AA vérifiés (4.5:1 minimum), focus visible, navigation au clavier, respect de `prefers-reduced-motion`.
- Page compréhensible **sans CSS**.
- Code formaté avec **Prettier** et vérifié avec **Stylelint**.

## Du design au code

| Figma | CSS |
|---|---|
| Collection de variables `Primitives` (`color/coral/500`) | `css/tokens/primitives.css` (`--color-coral-500`) |
| Collection de variables `Semantic` (`color/text/default`) | `css/tokens/semantic.css` (`--color-text-default`) |
| Composant `Link card` · Variant `Default` / `Featured` | `.link-card` · `.link-card--featured` |
| States `Hover` / `Pressed` / `Focus` | `:hover` / `:active` / `:focus-visible` |

Les variants ne réécrivent aucune propriété : ils changent seulement la valeur des variables du composant.

## Architecture

```
css/
├─ main.css            ordre des @layer + imports
├─ tokens/             niveau 1 (primitives) et niveau 2 (semantic)
├─ base/               reset + styles par défaut des balises
├─ layout/             mise en page (colonne mobile, carte desktop)
└─ components/         un fichier par composant Figma (+ ses tokens)
```

Ordre des couches, de la plus faible à la plus forte :
`reset → tokens → base → layout → components → utilities`

## Statistiques

Mesure d'audience avec [GoatCounter](https://www.goatcounter.com/) : gratuit pour un usage personnel, open source, **sans cookies** (donc sans bandeau de consentement). Chaque lien porte un nom stable (`data-goatcounter-click`) pour suivre les clics.

## Lancer le projet en local

```bash
npm install          # installe Prettier et Stylelint
npm run format       # formate tout le code
npm run lint:css     # vérifie le CSS
```

Puis ouvrir `index.html` dans le navigateur.

## Pistes d'amélioration

- [ ] Héberger les polices en local (WOFF2)
- [ ] Bouton pour mettre en pause l'animation des bulles
- [ ] Protéger l'adresse e-mail du spam avec un peu de JavaScript

## Crédits

- Reset CSS adapté du [Modern CSS Reset](https://www.joshwcomeau.com/css/custom-css-reset/) de Josh Comeau.
- Polices : [Baloo 2](https://fonts.google.com/specimen/Baloo+2) et [Work Sans](https://fonts.google.com/specimen/Work+Sans) (licence OFL).

---

Conçu et codé par **Alicia Cavallo**, designer UI et développeuse front · [Portfolio](https://aliciacavallo.github.io/my-portfolio/) · [LinkedIn](https://www.linkedin.com/in/alicia-cavallo/)