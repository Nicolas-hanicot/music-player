# Music du Monde — Music Codex

Application web musicale en **une seule page** (aucune installation, aucun serveur).
Ouvre `index.html` dans un navigateur moderne (Chrome, Edge, Firefox…).

## Fonctionnalités

- **Vraie barre de recherche** connectée au catalogue **iTunes Search API**
  (recherche avec délai anti-rebond à la frappe + touche Entrée + bouton) ;
- **Jusqu'à 200 résultats** par recherche (`limit=200`) ;
- Recherche par **titres / artistes / albums** (onglets dédiés) :
  - *Titres* : cartes avec pochette, durée, genre, extrait ;
  - *Artistes* : cliquer sur un artiste affiche ses titres ;
  - *Albums* : cliquer sur un album charge ses pistes (API Lookup) ;
- **Navigation par genres** (chips : pop, rock, rap, jazz, classique, variété FR, k-pop…)
  et **par origines** (sélecteur de plateforme iTunes : France, États-Unis, Japon,
  Corée du Sud, Brésil, Maroc…) ;
- **Playlist locale persistante** via `localStorage` (ajout ＋, retrait ✕, tout effacer,
  compteur dans l'en-tête) ;
- **Lecteur complet** : lecture/pause, précédent/suivant (avec retour au début du morceau
  si > 3 s écoutées), **volume** (+ muet), **barre de progression** avec recherche
  (seek) et temps écoulé / durée ;
- **Extraits audio** (~30 s) lus lorsque le catalogue fournit une URL de preview
  (`previewUrl`) ; les morceaux sans extrait sont signalés et désactivés ;
- **Import de fichiers audio locaux** (bouton 📁 Importer dans la playlist) pour tes
  propres MP3 — lus via URL d'objet, valables pour la session en cours uniquement ;
- **Page mentions légales** incluse (`mentions-legales.html`, lien discret en bas à droite)
  conforme LCEN — pense à compléter les champs `[à compléter]` avant la mise en ligne.

## Aspect légal

> Une application web ne peut pas légalement fournir gratuitement des milliers de
> morceaux complets protégés par le droit d'auteur. Le lecteur utilise donc les
> **extraits audio autorisés** par le catalogue iTunes. Pour une bibliothèque de
> fichiers MP3 **que tu possèdes ou que tu as le droit de diffuser**, utilise le
> module d'import local intégré.

## Technique

- HTML / CSS / JavaScript **vanilla** — zéro dépendance, zéro build ;
- API : `https://itunes.apple.com/search` et `https://itunes.apple.com/lookup`
  (compatibles CORS, appelées directement depuis le navigateur) ;
- Persistance : `localStorage` (clé `mdm_playlist_v1`) — les données restent sur ta machine ;
- Responsive : grille adaptable, playlist en panneau latéral coulissant.
