# Badass Social Worker

Carnet de terrain pour travailleuse sociale. Une seule page, pensée pour le téléphone :
les enfants suivis en bulles tout en haut, la to-do du jour à la place du fil d'actualité,
et la saisie d'un compte rendu en une minute quand on sort d'un entretien.

**Toutes les données restent sur l'appareil.** Rien n'est envoyé nulle part, il n'y a ni compte,
ni serveur, ni base de données distante — voir « Vie privée » plus bas.

## Ce que fait l'application

- **Bulles enfants** en haut d'écran, avec un `+` pour en ajouter un (le prénom suffit).
  Une pastille rouge indique le nombre de tâches en attente pour cet enfant.
- **Fiche enfant** en trois onglets : *Profil* (mesure, lieu de vie, scolarité, référent,
  antécédents datés, « comment il/elle est », personnes ressources avec téléphone cliquable),
  *Journal* (tous ses comptes rendus en timeline), *À faire*.
- **Comptes rendus** : type de rencontre (VAD, entretien, école, audience, synthèse, appel,
  information préoccupante), date et heure, lieu, **personnes présentes** (avec suggestions
  qui s'enrichissent des saisies passées), les faits, puis les observations tenues à part
  des faits, et la suite à donner — convertible en tâche d'une case à cocher.
- **To-do** groupée En retard / Aujourd'hui / Cette semaine / Plus tard, avec **rappels à l'heure**.
- **Calendrier** (la date en haut à droite) : vue mois, navigation libre, points par jour
  (plein = tâche, creux = compte rendu), et ajout de tâches ou de comptes rendus à une date
  éloignée pour préparer une audience des mois à l'avance.
- **Recherche** dans les prénoms, les antécédents, le texte des comptes rendus, les personnes
  présentes et les tâches.
- **Français / English**, au choix dans les réglages.

## Vie privée

Le carnet enregistre tout dans le `localStorage` du navigateur, c'est-à-dire **sur l'appareil
et nulle part ailleurs**. Aucune requête réseau ne transporte de donnée : les seuls appels
sortants concernent les polices Google Fonts, et le service worker les met en cache pour que
l'application fonctionne ensuite hors connexion.

Conséquences à connaître :

- Effacer les données de navigation, changer de navigateur ou de téléphone **efface le carnet**.
  Les réglages proposent un export `.json` : à faire régulièrement.
- Les données ne se synchronisent pas entre appareils. C'est délibéré.
- Si le service de la professionnelle impose un logiciel métier (IODAS, Solis…), ce carnet
  reste un outil de terrain personnel, pas le dossier officiel de l'enfant.

## Mettre en ligne sur GitHub Pages

1. Créer un dépôt sur GitHub, puis y déposer le contenu de ce dossier (glisser-déposer via
   « Add file › Upload files » suffit, ou bien en ligne de commande) :

   ```bash
   git init
   git add .
   git commit -m "Badass Social Worker"
   git branch -M main
   git remote add origin https://github.com/VOTRE-COMPTE/carnet-reperes.git
   git push -u origin main
   ```

2. Dans le dépôt : **Settings › Pages**, source « Deploy from a branch », branche `main`,
   dossier `/ (root)`. Enregistrer.
3. Au bout d'une minute, l'adresse `https://VOTRE-COMPTE.github.io/carnet-reperes/` répond.

> Une page GitHub Pages est **publique**. Le code l'est donc aussi — ce n'est pas un problème,
> il ne contient aucune donnée. Les écrits sur les enfants, eux, restent sur le téléphone de
> la personne qui utilise l'application et ne sont jamais publiés.

## L'installer sur le téléphone

Une fois la page ouverte à son adresse `https://` :

- **iPhone (Safari)** : bouton Partager › *Sur l'écran d'accueil*.
- **Android (Chrome)** : menu ⋮ › *Installer l'application*.

Elle s'ouvre alors en plein écran comme une vraie application, et fonctionne sans réseau.

## Utiliser le fichier sans rien mettre en ligne

Un double-clic sur `index.html` l'ouvre directement dans le navigateur et tout fonctionne,
sauf le mode hors connexion installé (les service workers exigent `http(s)://`).
C'est la solution la plus privée si l'application n'est utilisée que sur un ordinateur.

## À propos des rappels

Une page web ne peut rien déclencher lorsqu'elle est fermée. Le rappel d'une tâche s'affiche
donc **à l'ouverture du carnet**, et sous forme de notification système si le navigateur
l'autorise et que la page tourne en arrière-plan. Pour un réveil garanti téléphone verrouillé,
mieux vaut doubler les rendez-vous importants dans l'agenda du téléphone.

## Contenu du dossier

| Fichier | Rôle |
| --- | --- |
| `index.html` | L'application entière : structure, styles et code, sans aucune dépendance à installer. |
| `manifest.webmanifest` | Nom, icônes et couleurs pour l'installation sur le téléphone. |
| `sw.js` | Service worker : mise en cache pour le fonctionnement hors connexion. |
| `icon.svg`, `icon-180.png`, `icon-192.png`, `icon-512.png` | Icônes de l'application. |

Aucune étape de compilation, aucun `npm install` : le dépôt se publie tel quel.

## Licence

MIT — voir `LICENSE`.
