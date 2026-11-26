# ⭐ Mini Héros

Application familiale (missions, étoiles, boutique, malus, chronos tablette) en **un seul fichier** `index.html`, synchronisée en temps réel entre la tablette des enfants et les GSM des parents via Firebase Realtime Database (plan gratuit Spark). Sans configuration, elle fonctionne en **mode local** (localStorage).

## Mise en route Firebase (5 étapes)
1. https://console.firebase.google.com → **Ajouter un projet** (Analytics inutile).
2. Menu **Créer → Realtime Database → Créer une base** (région `europe-west1`), démarrer en mode verrouillé.
3. Onglet **Règles** → coller (remplacer `famille-mini-heros` par votre `FAMILY_KEY`) puis **Publier** :
   ```json
   { "rules": { ".read": false, ".write": false,
       "famille-mini-heros": { ".read": true, ".write": true } } }
   ```
4. **Paramètres du projet ⚙️ → Vos applications → `</>` Web** → copier l'objet `firebaseConfig` dans `const FIREBASE_CONFIG = { … }` en haut du `<script>` de `index.html` (vérifier que `databaseURL` est rempli). Choisir un `FAMILY_KEY` unique et difficile à deviner.
5. Publier sur GitHub Pages (Settings → Pages → branche), ouvrir le lien sur les 3 appareils → **Ajouter à l'écran d'accueil**, puis Mode Parent → Réglages → choisir le rôle de chaque appareil (PIN par défaut : `1234`).
