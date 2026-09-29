# 123-finish-test-site

> ⚠️ **Ce repository est un environnement de test destiné à 1.2.3._Finish.**
> Les erreurs et imperfections SEO qu'il contient sont **volontaires**. Ne l'utilisez
> pas comme modèle pour un vrai site.

Il sert à valider le parcours complet de [1.2.3._Finish](../finish) — audit réel →
connexion GitHub → plan de corrections → application réelle sur une branche → commit →
Pull Request → vérification → re-scan — **sans jamais risquer un vrai site**.

Ce dépôt ne contient **aucune donnée sensible** : pas de secret, pas de clé API, pas
d'information personnelle réelle. La « Boulangerie Demo » est un commerce fictif.

## Pages

| Page | Rôle dans le test |
|---|---|
| `index.html` | Accueil, plusieurs problèmes SEO volontaires, lien cassé, lien vers `promo.html` hors navigation |
| `about.html` | Page « À propos » au contenu volontairement trop court |
| `services.html` | Page services avec double H1, titre trop long, maillage interne faible |
| `contact.html` | Formulaire sans labels, informations LocalBusiness incomplètes |
| `promo.html` | Page volontairement absente de la navigation (découverte par le crawler uniquement) |

## Problèmes volontairement introduits

| Où | Problème |
|---|---|
| Accueil | `<title>` trop générique (« Accueil »), meta description absente, **H1 absent**, image sans `alt`, Open Graph absent, données structurées absentes, canonical absente |
| Accueil | **Lien interne cassé** (`page-inexistante.html` → 404) |
| À propos | Title incorrect (« Page 2 »), meta description absente, image sans `alt`, contenu trop court (< 250 mots) |
| Services | **Deux H1**, titre trop long (> 65 caractères), liens internes insuffisants |
| Contact | Title trop court, description trop courte, **formulaire sans labels** (placeholders uniquement), téléphone/e-mail en texte brut (pas de `tel:`/`mailto:`), **aucune donnée structurée LocalBusiness** |
| Tout le site | `robots.txt` absent, `sitemap.xml` absent, canonical absente sur toutes les pages |

Ce qui est **volontairement correct** (pour ne pas générer de bruit) : `lang="fr"`,
meta viewport, encodage UTF-8, favicon, DOCTYPE, hiérarchie des titres ailleurs que
sur Services, page promo propre.

Remarque : en local (`http://…`), l'audit signalera aussi l'absence de HTTPS — normal.
Une fois le site publié sur GitHub Pages, il est servi en HTTPS.

## Utilisation

1. Publier ce dépôt sur GitHub (public) et activer **GitHub Pages** sur la branche `main` ;
2. auditer l'URL publique (ex. `https://<votre-compte>.github.io/123-finish-test-site/`)
   avec 1.2.3._Finish ;
3. vérifier que les problèmes ci-dessus sont **réellement détectés** ;
4. connecter GitHub, sélectionner ce dépôt, vérifier le mapping page → fichier,
   l'aperçu avant/après, puis appliquer les corrections sur la branche dédiée ;
5. vérifier sur GitHub : branche `finish/seo-fixes-*`, commit ne contant **que** les
   corrections, Pull Request « SEO improvements by 1.2.3._Finish », `main` inchangée ;
6. fusionner la PR, attendre le redéploiement Pages, puis **re-scanner** : les
   corrections appliquées doivent passer « vérifiées » et le score progresser.

La branche `release/v2` (identique à `main` à la création) permet de tester la
manipulation d'une **branche avec slash** comme base des corrections.

Aucun problème artificiel « dangereux » n'a été introduit : pas de `noindex`, pas de
redirection piégeuse, pas de contenu trompeur — uniquement des défauts SEO classiques.
