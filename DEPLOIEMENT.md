# Mettre en ligne https://musicdumonde.fr

Le domaine **musicdumonde.fr** n'a aucun enregistrement DNS au 08/09/2026 → il est
**très probablement disponible** (à confirmer chez le registrar au moment de l'achat).

Un nom de domaine ne se « crée » pas dans le code : il faut **l'acheter** chez un
registrar accrédité par l'AFNIC (gestionnaire du .fr), puis le **relier à un
hébergement**. Voici les 3 étapes, ~15 minutes au total.

---

## Étape 1 — Acheter le domaine (≈ 8-12 €/an)

Registrars fiables pour un .fr : **OVH** (ovhcloud.com), **Gandi** (gandi.net),
**Infomaniak** (infomaniak.com), Scaleway, Ionos…

1. Crée un compte, cherche `musicdumonde.fr` dans la barre du registrar.
2. Vérifie la disponibilité, ajoute au panier, paie.
3. Conditions AFNIC pour un .fr : adresse postale dans l'UE (particulier ou société).

## Étape 2 — Héberger le site (gratuit)

Le site est 100 % statique (un seul `index.html`) → hébergement gratuit suffisant.

### Option A — GitHub Pages (recommandé)
1. Crée un compte sur github.com, puis un dépôt public (ex. `musique`).
2. Uploade `index.html`, `favicon.svg`, `404.html`, `README.md` (bouton *Add file → Upload files*).
3. Dans le dépôt : **Settings → Pages → Source : Deploy from a branch → main → / (root)**.
4. Le site est en ligne sur `https://<toncompte>.github.io/musique/` en ~1 min.

### Option B — Netlify Drop (le plus rapide)
1. Va sur app.netlify.com/drop (compte gratuit).
2. Glisse-dépose le dossier `Le_Monde_de_la_Musique`.
3. Site en ligne immédiatement sur une URL `*.netlify.app`.

### Option C — Vercel
Équivalent à Netlify : vercel.com, « Add New → Project », importe le dossier.

## Étape 3 — Relier le domaine (DNS) + HTTPS

Dans l'interface de l'hébergeur, ajoute le **custom domain** `musicdumonde.fr`,
puis crée ces enregistrements dans la **zone DNS** de ton registrar :

| Hébergeur    | Enregistrement racine (@)                     | www                     |
|--------------|-----------------------------------------------|-------------------------|
| GitHub Pages | `A` → 185.199.108.153 (+ .109 / .110 / .111)  | `CNAME` → compte.github.io |
| Netlify      | `A` → 75.2.60.5                               | `CNAME` → ton-site.netlify.app |
| Vercel       | `A` → 76.76.21.21                             | `CNAME` → cname.vercel-dns.com |

- Propagation DNS : 5 min à 24 h.
- Active ensuite **HTTPS** dans l'hébergeur (certificat Let's Encrypt gratuit,
  automatique chez les trois).
- Résultat : https://musicdumonde.fr ✅

## Alternative : tout-en-un chez un hébergeur français

Si tu préfères une seule facture : **o2switch** ou **OVH** (offre « Perso »,
≈ 4-7 €/mois) incluent domaine + hébergement + HTTPS. Tu uploades alors les
fichiers par FTP dans le dossier `www/`.

---

## Fichiers prêts pour la mise en ligne

| Fichier      | Rôle                                        |
|--------------|---------------------------------------------|
| `index.html` | L'application complète (page unique)        |
| `favicon.svg`| Icône d'onglet 🎵                           |
| `404.html`   | Page d'erreur (redirige vers l'accueil)     |
| `mentions-legales.html` | Mentions légales LCEN — **à compléter** |
| `README.md`  | Documentation                               |

Aucun serveur ni base de données nécessaire : l'app appelle l'API iTunes
directement depuis le navigateur et stocke la playlist dans le navigateur
de chaque visiteur (localStorage).

## ⚠️ Points d'attention

- **Marque / droit d'auteur** : le site diffuse uniquement les extraits ~30 s
  fournis légalement par l'API iTunes. Ne propose jamais de morceaux complets
  sans licence. La page `mentions-legales.html` est incluse : **complète les
  champs `[à compléter]`** (identité de l'éditeur, hébergeur choisi) avant la
  mise en ligne publique — c'est une obligation légale (LCEN art. 6).
- **Disponibilité du domaine** : à confirmer sur le registrar ; si
  `musicdumonde.fr` est pris entre-temps, alternatives : `musiquedumonde.fr`,
  `lemonde-de-la-musique.fr`, `musicdumonde.com`…
