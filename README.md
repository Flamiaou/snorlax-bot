# Discord-bot

Un simple bot discord sans commande pour la diffusion 24h / 24 et 7j / 7 de stations de radio Internet (par exemple SHOUTcast).

![Discobot](https://i.imgur.com/o3S9FRB.png)

## Requirements

- [Node] (https://nodejs.org/en/) 
- npm install
- npm i ffmpeg
- npm discord.js
- 
## Commencer

First make sure you have all the required tools installed on your machine then continue with these steps.

### Installation

```bash
# Cloner le référentiel
git clone https://github.com/Flamiaou/snorlax-bot.git

# Entrez dans le répertoire
cd snorlax-bot/

# Installez les dépendances
npm install
```

### Configuration

Après avoir cloné le projet et installé toutes les dépendances, fournissez le jeton d'API Discord approprié, l'ID de canal vocal par défaut, l'ID de canal de texte par défaut (pour la lecture des notifications) et l'URL d'un ou plusieurs flux musicaux dans le fichier config.json.
Pour acquérir l'ID de chaîne, activez le mode développeur dans Discord et cliquez avec le bouton droit sur n'importe quelle chaîne.

Exemple de configuration pour une station radio:
```json
{
    "prefix": "!a",
	"token":"TON TOKEN",
	"voicechannel":"ID SALON VOCAUX",
	"logchannel":"ID SALON LOGS",
	"activity":"Anime Radio",
	"list":[
	{
		"name":"Anime Radio",
		"url":"https://pool.anison.fm/AniSonFM(320)?nocache=0.05"
	}
	]
}
```

Exemple de configuration pour une playlist personnalisée:
```json
```json
{
    "prefix": "!a",
	"token":"TON TOKEN",
	"voicechannel":"ID SALON VOCAUX",
	"logchannel":"ID SALON LOGS",
	"activity":"Playlist Radio",
	"list":[
	{
		"name":"Shinkai Makoto - Five centimeters per second.",
		"url":"https://m17.akniga.club/b/54644/bIoDhyKuJ5rGPM_IFqIC3A,,/01.%20%D0%A1%D0%B8%D0%BD%D0%BA%D0%B0%D0%B9%20%D0%9C%D0%B0%D0%BA%D0%BE%D1%82%D0%BE%20-%20%D0%9F%D1%8F%D1%82%D1%8C%20%D1%81%D0%B0%D0%BD%D1%82%D0%B8%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2%20%D0%B2%20%D1%81%D0%B5%D0%BA%D1%83%D0%BD%D0%B4%D1%83.mp3"
	},
	{
		"name":"Aya Hazuki - And again, I say hello.",
		"url":"https://m17.akniga.club/b/55024/bIoDhyKuJ5rGPM_IFqIC3A,,/01.%20%D0%90%D1%8F%20%D0%A5%D0%B0%D0%B7%D1%83%D0%BA%D0%B8%20-%20%D0%98%20%D1%81%D0%BD%D0%BE%D0%B2%D0%B0%20%D0%B3%D0%BE%D0%B2%D0%BE%D1%80%D1%8E%20%D0%9F%D1%80%D0%B8%D0%B2%D0%B5%D1%82.mp3"
	},
	{
		"name":"Natsume Akatsky - The Goddess blesses this beautiful world.",
		"url":"https://m17.akniga.club/b/54240/bIoDhyKuJ5rGPM_IFqIC3A,,/01.%20%D0%9D%D0%B0%D1%86%D1%83%D0%BC%D1%8D%20%D0%90%D0%BA%D0%B0%D1%86%D0%BA%D0%B8%20-%20%D0%90%D1%85,%20%D0%BC%D0%BE%D1%8F%20%D0%B1%D0%B5%D1%81%D0%BF%D0%BE%D0%BB%D0%B5%D0%B7%D0%BD%D0%B0%D1%8F%20%D0%B1%D0%BE%D0%B3%D0%B8%D0%BD%D1%8F.mp3"
	},
	{
		"name":"Nagatsuki Tappei - Re:Zero. Living in an alternative world from scratch.",
		"url":"https://m17.akniga.club/b/55324/Od3Ak6Dt6YnLfHZMTZNTsg,,/01.%20%D0%9D%D0%B0%D0%B3%D0%B0%D1%86%D1%83%D0%BA%D0%B8%20%D0%A2%D0%B0%D0%BF%D0%BF%D1%8D%D0%B9%20-%20%D0%96%D0%B8%D0%B7%D0%BD%D1%8C%20%D0%B2%20%D0%B0%D0%BB%D1%8C%D1%82%D0%B5%D1%80%D0%BD%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D0%BC%20%D0%BC%D0%B8%D1%80%D0%B5%20%D1%81%20%D0%BD%D1%83%D0%BB%D1%8F.mp3"
	},
	{
		"name":"Jumpei Inuzuka - Café from another world",
		"url":"https://m17.akniga.club/b/55175/Od3Ak6Dt6YnLfHZMTZNTsg,,/01.%20Inuzuka%20Junpei%20-%20%D0%9A%D0%B0%D1%84%D0%B5%20%D0%B8%D0%B7%20%D0%B4%D1%80%D1%83%D0%B3%D0%BE%D0%B3%D0%BE%20%D0%BC%D0%B8%D1%80%D0%B0.mp3"
	}
	]
}
```

### Lancer l'application

Étant donné que le bot fonctionne même lorsqu'il n'y a personne dans le canal, je recommande fortement d'utiliser forever ou pm2 avec cron autorestart pour une diffusion non-stop (en raison des fonctionnalités de l'API Discord, le bot a tendance à transmettre le silence après 20-30 heures de disponibilité).

```bash
npm start index.js --name DiscoBot --log bot.log --time --restart-delay 5000 & npm start restart.js --name Restart
```

Ou vous pouvez le faire sans les gestionnaires de processus.

```bash
node index.js
```

##Auteur

Flamiaou 'Jørdan#5335'

## License

Ce projet est sous licence MIT - voir le fichier [LICENSE.md] (LICENSE) pour plus de détails
