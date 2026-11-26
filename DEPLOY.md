# Déployer le site OFF MAPS

Le site est un build statique Vite + React : une fois compilé (le dossier `dist/`
est déjà fourni, il contient vos 3 photos), il se déploie gratuitement sur
Vercel, Netlify ou n'importe quel hébergeur statique. Aucun serveur ni base de
données n'est nécessaire.

## Option A — Vercel via GitHub (recommandée, URL permanente gratuite)

1. **Téléchargez** `offmaps-website.tar.gz` et décompressez-le : vous obtenez
   un dossier `frontend/`.
2. **Créez un dépôt GitHub** : sur github.com, cliquez « New repository »
   (compte gratuit), nommez-le par exemple `offmaps`.
3. **Envoyez le contenu de `frontend/`** dans le dépôt (pas le dossier parent) :
   - Sans terminal : sur la page du dépôt, « uploading an existing file »,
     puis glissez-déposez tous les fichiers et dossiers de `frontend/`
     (sans `node_modules` s'il est présent) → « Commit changes ».
   - Avec le terminal :
     ```bash
     cd frontend
     git init && git add . && git commit -m "OFF MAPS site"
     git remote add origin https://github.com/VOTRE-COMPTE/offmaps.git
     git branch -M main && git push -u origin main
     ```
4. **Déployez sur Vercel** : allez sur vercel.com, créez un compte gratuit avec
   « Sign Up with GitHub », puis « Add New… → Project » → « Import » votre
   dépôt `offmaps`.
5. Vercel détecte Vite automatiquement. Vérifiez ces réglages si besoin :
   - Framework Preset : **Vite**
   - Build Command : `npm run build`
   - Output Directory : `dist`
   - Si vous avez poussé tout le projet (avec le dossier `frontend/` dedans),
     réglez **Root Directory** = `frontend`.
6. Cliquez **Deploy**. En ~1 minute vous obtenez une URL permanente du type
   `https://offmaps.vercel.app` (HTTPS inclus).

Le fichier `vercel.json` fourni à la racine de `frontend/` sert `index.html`
pour les URLs inconnues : la page 404 « This page missed the departure »
s'affiche correctement, et `/blog/` reste servi tel quel.

## Option B — Vercel en ligne de commande (rapide si Node.js est installé)

```bash
npm install -g vercel
cd frontend
vercel login        # s'ouvre dans le navigateur, connexion gratuite
vercel --prod       # répondez aux questions (défauts OK, framework Vite)
```

La commande affiche l'URL de production à la fin. Pour les déploiements
suivants, `vercel --prod` depuis le même dossier suffit.

## Option C — Netlify (la plus simple, sans Git)

Sur app.netlify.com/drop, glissez-déposez le **dossier `dist/`** : le site est
en ligne immédiatement sur une URL Netlify. (Le plan gratuit Netlify suffit.)

## Domaine personnalisé (optionnel)

Sur Vercel : Settings → Domains → ajoutez votre nom de domaine et suivez les
instructions DNS. Sur Netlify : Domain settings → Add a domain.

## Mettre le site à jour

- Option A : modifiez les fichiers et `git push` → Vercel redéploie tout seul.
- Option B : relancez `vercel --prod`.
- Option C : re-glissez le nouveau `dist/` sur Netlify Drop.

## Rappel des emplacements d'images

Les photos à remplacer sont listées dans `IMAGE-SLOTS.md`. Les originaux
fournis sont dans `public/images/offmaps/originals/` ; après modification
d'une image dans `public/images/offmaps/`, relancez `npm run build` avant de
redéployer (ou servez `dist/` tel quel si vous déployez le build).
