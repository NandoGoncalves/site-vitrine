# Site vitrine — Audit Dataiku / no-code

Site statique, un seul fichier HTML (+ une image), sans build, sans dépendance à installer.

## Avant de mettre en ligne — à personnaliser

Ouvrez `index.html` et remplacez :
- `votre.email@exemple.fr` (2 occurrences : section Contact + pied de page)
- `https://www.linkedin.com/in/votre-profil` (section Contact)

Recherchez simplement `votre.email` et `votre-profil` dans le fichier pour les repérer.

## Option recommandée — GitHub Pages (gratuit, ~5 minutes)

1. Sur github.com, créez un nouveau dépôt (par exemple `site-vitrine`), public.
2. Mettez-y les 2 éléments de ce dossier : `index.html` et le dossier `assets/`.
   - Via l'interface web : bouton **Add file → Upload files**, glissez `index.html` puis le dossier `assets`.
   - Ou en ligne de commande :
     ```
     git init
     git add index.html assets README.md
     git commit -m "Site vitrine"
     git branch -M main
     git remote add origin https://github.com/VOTRE-COMPTE/site-vitrine.git
     git push -u origin main
     ```
3. Dans le dépôt GitHub : **Settings → Pages**.
4. Sous **Build and deployment**, choisissez **Deploy from a branch**, branche `main`, dossier `/ (root)`. Enregistrez.
5. Au bout d'une à deux minutes, le site est en ligne à l'adresse indiquée en haut de la page Pages
   (généralement `https://VOTRE-COMPTE.github.io/site-vitrine/`).

Pour un nom de domaine personnalisé (ex. `votrenom.fr`), ajoutez-le dans **Settings → Pages → Custom domain**,
puis créez chez votre registrar un enregistrement CNAME pointant vers `VOTRE-COMPTE.github.io`.

## Option alternative — Azure Static Web Apps (avec votre abonnement Azure)

Azure Static Web Apps se branche directement sur un dépôt GitHub et redéploie automatiquement à chaque `git push` — pas plus compliqué que GitHub Pages, avec en plus un certificat HTTPS et un domaine personnalisé gérés automatiquement.

1. Poussez d'abord le site sur GitHub (étapes 1–2 ci-dessus).
2. Dans le [portail Azure](https://portal.azure.com), **Créer une ressource → Static Web App**.
3. Reliez votre compte GitHub, sélectionnez le dépôt et la branche `main`.
4. Paramètres de build : laissez tout vide / "Custom" — il n'y a **aucun build**, le site est déjà statique :
   - Emplacement de l'application : `/`
   - Emplacement de sortie : (laisser vide)
5. Validez. Azure crée automatiquement un fichier de workflow GitHub Actions dans votre dépôt
   qui redéploiera le site à chaque modification poussée sur `main`.

## Mettre à jour le site plus tard

Modifiez `index.html`, puis :
```
git add -A
git commit -m "Mise à jour du contenu"
git push
```
Le site se met à jour automatiquement (GitHub Pages en 1–2 min, Azure Static Web Apps via le workflow créé).

## Structure du projet

```
index.html              → tout le site (HTML + CSS + JS, un seul fichier)
assets/banniere-web.jpg → votre bannière, réutilisée en fond du haut de page
```

## Ce qui a été fait / pistes pour la suite

- Palette de couleurs extraite directement de votre bannière fournie (indigo → violet → magenta → rouge).
- La section "matrice de confusion" reprend littéralement le principe de votre motif de fond (Annoncé vs Réel)
  pour incarner visuellement votre conviction centrale.
- Les cas clients (banque, assurance, grand groupe) sont anonymisés — à vous de décider si vous voulez
  ajouter un nom de secteur plus précis, un logo, ou rester en l'état.
- Reste à faire quand vous serez prêt : tarification affichée ou non, éventuel formulaire de contact
  (nécessiterait un petit service externe type Formspree, car un site statique ne peut pas envoyer d'e-mail seul).
