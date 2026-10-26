# Elliot Air · EA3010

Le site de date night d'Eunice, prêt à être publié sur GitHub Pages.

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | Le site complet (tout le code est dedans) |
| `captain.mp3` | L'annonce du commandant (ta voix, 77 Ko, chargée seulement au clic) |
| `favicon.svg`, `favicon-32.png` | Icône de l'onglet : l'avion jaune avec les deux E |
| `apple-touch-icon.png` | Icône sur iPhone (écran d'accueil, favoris) |
| `icon-192.png`, `icon-512.png`, `site.webmanifest` | Icônes Android |
| `og-image.png` | Image d'aperçu quand tu envoies le lien sur WhatsApp, iMessage, Instagram |

## Mise en ligne sur GitHub Pages (5 min)

1. Sur github.com, crée un nouveau dépôt, par exemple `elliot-air`. Il peut être public ou privé si tu as GitHub Pro.
2. Clique sur **Add file → Upload files**, glisse **tous les fichiers du dossier** (pas le dossier lui-même), puis **Commit changes**.
3. Va dans **Settings → Pages**. Dans *Source*, choisis **Deploy from a branch**, branche **main**, dossier **/ (root)**, puis **Save**.
4. Attends une minute. Le site est en ligne sur `https://TON-PSEUDO.github.io/elliot-air/`.

## Brancher ton domaine (ex. elliotair.com)

1. Dans **Settings → Pages → Custom domain**, écris `elliotair.com` et valide. GitHub crée un fichier `CNAME` tout seul.
2. Chez ton registrar (Namecheap, Cloudflare…), ajoute ces enregistrements DNS :
   - 4 enregistrements **A** sur `@` : `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 1 enregistrement **CNAME** sur `www` qui pointe vers `TON-PSEUDO.github.io`
3. Quand le domaine est vérifié, coche **Enforce HTTPS**. C'est indispensable : sans HTTPS, la copie de l'image de la carte d'embarquement ne marche pas.

## À modifier avant d'envoyer le lien

**L'aperçu du lien** : dans `index.html`, ligne `og:image`, remplace `https://elliotair.com/og-image.png` par l'adresse réelle de ton site suivie de `/og-image.png`. Sans ça, WhatsApp n'affichera pas l'image d'aperçu.

## Pour les prochaines dates

Tout se modifie en haut du bloc `<script>` dans `index.html` :

- **Historique des vols** : ajoute la date passée dans la liste `PREVIOUS_FLIGHTS` :
  ```js
  const PREVIOUS_FLIGHTS = [
    {code:"EA3010", date:"30 Oct 2026", dest:"Haunted house"}
  ];
  ```
- **Nouvelle date** : cherche `30` et `Oct` / `FRI 30 OCT` / `10月30日` pour changer la date affichée, et dans `takeoffTime()` change `Date.UTC(2026, 9, 30, …)` (le mois commence à 0, donc octobre = 9).
- **Nouveau numéro de vol** : remplace `EA3010` partout (par exemple `EA3011`).
- **Nouvelle annonce vocale** : remplace `captain.mp3` par ton nouvel enregistrement (même nom de fichier).
- **Récompenses des miles** : modifie la liste `rewards` (une version en anglais, une en cantonais).

## Tester en local

Ouvre un terminal dans le dossier et lance :

```
python3 -m http.server
```

Puis va sur `http://localhost:8000`. Ouvrir directement le fichier en double-cliquant marche aussi, mais la voix et la copie d'image peuvent être bloquées.
