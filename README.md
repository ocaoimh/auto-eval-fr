# Auto-évaluation français (CECR) — application autonome

Reconstruction hors-ligne de l'outil **« Auto-évaluez vos capacités linguistiques »**
de la Journée européenne des langues (CELV / Conseil de l'Europe),
limitée au **français**.

**Bilingue FR / Wolof** (bouton FR/WO en haut) : instructions, questions et
résultats en français ou en wolof — mais le test évalue **toujours le français**.

> ⚠️ **Wolof à valider.** Les textes wolof (interface + 30 descripteurs) sont une
> **traduction préliminaire** générée automatiquement. À faire relire par un·e
> locuteur·rice natif·ve avant tout usage réel. Un bandeau le rappelle en mode WO.
> Pour corriger : éditer `WO` dans le tableau `QUESTIONS` (fichier `index.html`) et
> l'objet `T.wo` (chaînes d'interface), ou repartir de `questions.json` (bilingue).

## Déroulé

1. **Profil** — prénom/pseudo, région (14 régions du Sénégal), tranche d'âge, genre.
2. **Auto-estimation** — curseur 1–10 (fixe le point de départ adaptatif).
3. **Test** — affirmations « Je peux… », réponse Oui / Pas encore (le niveau CECR
   de chaque item n'est **pas** affiché, comme dans l'outil d'origine).
4. **Résultats** — niveau CECR par domaine (Débutant → Maîtrise), + bouton copier
   (inclut le profil).

## Utilisation

- **En local :** ouvrir `index.html` par un double-clic. Aucun serveur, aucune dépendance.
- **Sur le web (GitHub Pages) :** placer ce dossier dans un dépôt, activer Pages
  (Settings → Pages → branche `main`, dossier racine). L'URL servira `index.html`.

Tout est contenu dans `index.html` (données + moteur + interface). Le fichier
fonctionne sans connexion.

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | L'application complète (autonome). Les 30 descripteurs sont **intégrés** dans le fichier. |
| `questions.json` | Les mêmes 30 descripteurs, en données réutilisables. **Non requis** par l'app (l'app est autonome). |
| `README.md` | Ce fichier. |
| `karibu-theme.css` | Jetons de design + composants Karibu Hub (couleurs, boutons, cartes…). Chargé par `index.html`. Réutilisable pour d'autres outils. |
| `karibu-tokens.json` | Les mêmes jetons en JSON (pour du code / d'autres apps). |

## Identité visuelle (Karibu Hub)

L'app applique l'identité **Karibu Hub** : couleurs extraites de la palette Figma
(échantillonnées sur les nuanciers — les étiquettes hex imprimées du board comportent
des erreurs de copier-coller), typographies **Poppins** (titres) + **Nunito** (corps)
via Google Fonts (repli sur polices système hors-ligne). Coral de marque `#FC6854`,
fond crème `#FFF7F0`, CTA vert `#61AC7E`. Chaque domaine de compétence reprend une
couleur d'activité Karibu (compréhension orale = magenta, écrite = bleu, etc.).
Voir `karibu-theme.css` / `karibu-tokens.json` pour tous les jetons.

## Comment ça marche

- **30 descripteurs** « Je peux… » = 5 domaines × 6 niveaux CECR :
  - Domaines : L'écoute, Lecture, Interaction orale, Production orale, Rédaction
  - Niveaux : A1, A2, B1, B2, C1, C2
- **Test adaptatif :** l'utilisateur auto-estime d'abord son niveau (curseur 1–10), ce qui
  fixe le point de départ. Chaque domaine est ensuite sondé par oui / « pas encore » ;
  l'algorithme (matrice de décision reprise de l'outil d'origine) monte ou descend en niveau
  jusqu'à converger. Un passage complet fait ~10 à 18 questions.
- **Résultat :** un niveau CECR estimé par domaine (dont « Pré-A1 » si en deçà de A1).

## Personnalisation

- **Modifier / traduire les descripteurs :** éditer le tableau `QUESTIONS` en haut du
  `<script>` dans `index.html` (ou régénérer depuis `questions.json`).
- **Autres langues cibles :** l'outil d'origine propose les mêmes 30 descripteurs traduits
  dans ~40 langues ; il suffirait de remplacer le tableau `QUESTIONS` par la version
  traduite pour créer une variante (anglais, espagnol, etc.).
- **Couleurs / marque :** variables CSS en haut du fichier (`:root`).

## Limites et attribution

- Ce n'est **pas** un test de compétence corrigé : c'est une **auto-évaluation**
  (l'utilisateur juge lui-même ce qu'il « peut faire »). Le résultat est indicatif.
- Les **descripteurs CECR** sont © Conseil de l'Europe ; l'algorithme et le format sont
  repris de l'outil public de la Journée européenne des langues (https://edl.ecml.at/).
  À réserver à un usage d'évaluation interne / éducatif.
