<div align="center">

```
 █▀▀ ▀█▀ █▀▀█ █▀▀█ █▄ █ █▀▀▀  █▀▀▀ ▀█▀ █▀▀█ █▀▀█ █  █
 █▀▀  █  █▄▄▀ █  █ █ ▀█ █ ▀█  █▀▀   █  █▄▄█ █▄▄▀ █▀▄
 ▀▀▀  ▀  █ ▀█ █▄▄█ █  █ █▄▄▀  █▄▄▀  ▀  █  █ █ ▀▀ █ ▀▀
```

**Boîte à outils terminal — réseau, OSINT, comptes, système.**
**Terminal toolkit — network, OSINT, accounts, system.**

[![Python](https://img.shields.io/badge/python-3.8%2B-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Dépendances](https://img.shields.io/badge/d%C3%A9pendances-0-22c55e?style=flat-square)](#installation)
[![Fichiers](https://img.shields.io/badge/fichiers-1-3b82f6?style=flat-square)](#installation)
[![Outils](https://img.shields.io/badge/outils-123-a855f7?style=flat-square)](#les-six-pages)
[![Langues](https://img.shields.io/badge/fr%20%7C%20en-bilingue-f59e0b?style=flat-square)](#english)
[![Licence](https://img.shields.io/badge/licence-MIT-6b7280?style=flat-square)](#licence)

[**Français**](#-français) · [**English**](#-english)

</div>

---

## 🇫🇷 Français

### Le principe

Un seul fichier, zéro dépendance obligatoire, 123 outils rangés en six pages. Interface plein écran, bannière animée, thèmes de couleur, deux langues, tout au clavier.

STRONG STARK a un parti pris : **faire les choses pour de vrai**. Pas de fausse barre de progression, pas de « hacking » décoratif. Quand un outil interroge une API, il interroge une vraie API. Quand il dit qu'un compte existe, c'est un code HTTP 200 sur le profil. Quand il ne sait pas, il l'écrit en gris au lieu d'inventer.

### Sommaire

- [Avertissement](#avertissement)
- [Ce que c'est / ce que ce n'est pas](#ce-que-cest--ce-que-ce-nest-pas)
- [Installation](#installation)
- [Lancement](#lancement)
- [Les six pages](#les-six-pages)
- [Ce qui est réel, ce qui est heuristique](#ce-qui-est-réel-ce-qui-est-heuristique)
- [Fichiers générés](#fichiers-générés)
- [Compatibilité](#compatibilité)
- [Confidentialité](#confidentialité)
- [Licence](#licence)

### Avertissement

Tout ce qui est réseau est passif ou quasi passif : rien n'est modifié sur les cibles. Les outils de charge (`DoS`, `slowloris`, `flood`, `stress`) sont les seuls à taper fort, donc à utiliser sur tes propres services ou sur une cible qui accepte.

Scanner son propre réseau, sa propre box, son propre site : 100 % légal. Auditer le site d'un autre sans autorisation reste toléré dans la quasi-totalité des cas, mais la charge est la partie qu'on te reprochera si tu exagères.

### Ce que c'est / ce que ce n'est pas

**C'est :**
- un couteau suisse pour apprendre, en réseau comme en OSINT ;
- un outil de diagnostic quand ta box, ton site ou ta machine se comporte mal ;
- un moyen de retrouver l'empreinte publique d'un pseudo, la tienne comprise ;
- un générateur de rapports Markdown pour un dépôt ou un gist.

**Ce n'est pas :**
- un Burp Suite, un nmap complet ou un Metasploit ;
- un outil qui trouve les mots de passe par magie : il teste des dictionnaires, point ;
- un outil qui contourne une authentification à deux facteurs ;
- un outil qui fonctionne sans réseau : sans connexion, la moitié des pages ne sert à rien.

### Installation

Prérequis : Python 3.8 ou plus récent.

```bash
git clone https://github.com/<toi>/strongstark.git
cd strongstark
python strongstark.py
```

Aucun `pip install` n'est nécessaire. Trois fonctions savent se débrouiller seules et proposent l'installation à la volée quand tu les ouvres :

| Module | Pour quoi | Sans lui |
|---|---|---|
| `Pillow` | métadonnées EXIF | l'outil EXIF refuse de démarrer |
| `qrcode` | génération de QR code | l'outil QR refuse de démarrer |
| `PyInstaller` | compilation du verrou en `.exe` | le `.bat` fourni prend le relais |

Sur Windows, lance depuis **Windows Terminal**, **PowerShell** ou **cmd**. Un double-clic sur le fichier ouvre une fenêtre qui se ferme trop vite.

### Lancement

```bash
python strongstark.py
```

| Option | Effet |
|---|---|
| `--theme <nom>` | force un thème (`or`, `cyan`, `rouge`, `monochrome`…) |
| `--list-themes` | liste les 32 thèmes |
| `--lang fr` / `--lang en` | force la langue |
| `--no-color` | interface sans couleur |
| `--pseudo <nom>` | recherche de pseudo directe, sans interface |
| `--json` | sortie JSON avec `--pseudo` |

Navigation : `n` page suivante, `p` page précédente, `c` réglages, `0` quitter. Un numéro lance l'outil correspondant.

Exemple de recherche en ligne de commande, exploitable dans un script :

```bash
python strongstark.py --pseudo monpseudo --json > resultat.json
```

### Les six pages

#### 1 · Réseau — 21 outils

`Infos réseau + géoloc` · `Débloque-web (DNS)` · `Scan de ports` · `Lookup DNS` · `Wifi enregistrés` · `Mots de passe` · `Casseur de MD5` · `Chiffrement rapide` · `Métadonnées d'image` · `Broyeur de fichier` · `Infos système` · `Pluie de code` · `Générateur de QR code` · `Test de débit` · `Séquence de démo` · `Découverte du réseau` · `Contrôle à distance` · `Wifi alentour` · `Traceroute` · `Table ARP` · `Wake-on-LAN`

Le débloque-web applique un DNS public et vide le cache : c'est la première chose à faire quand un filtre d'établissement bloque un domaine. La découverte de réseau balaie les 254 adresses, croise la table ARP et signale les machines qui exposent SMB, RDP, SSH ou un serveur web.

#### 2 · Comptes — 12 outils

`Empreinte d'un pseudo` · `Boîte à outils Discord` · `Profil Instagram` · `Profil TikTok` · `Profil Snapchat` · `Profil Telegram` · `Analyse d'invitation` · `Vérif de lien cadeau` · `Analyse de webhook` · `Recherche de fuite` · `Analyseur de combo-list` · `Rapport Markdown`

La page qui impressionne, et celle qui marche vraiment :

- **Empreinte** interroge Instagram, TikTok, Snapchat et Telegram en parallèle et remonte nom, bio, abonnés, posts, comptes privés ou vérifiés, mail et téléphone professionnels quand ils sont publics.
- **Discord** : avec un token, sort l'identité complète (pseudo, e-mail, téléphone, 2FA, Nitro, date de création déduite du flocon), les serveurs avec ton rôle dedans, la facturation et les moyens de paiement masqués, les comptes liés, les conversations privées.
- **Invitation** : nom du serveur, description, membres, présence en ligne, salon, icône — sans rejoindre.
- **Cadeau Nitro** : dit si un lien est encore disponible ou déjà pris, et quelle offre il donne.
- **Fuite** : interroge une base publique, liste les sources, renvoie vers les autres.
- **Rapport** : croise la recherche de pseudo sur 68 sites et les profils publics, écrit un Markdown collable dans un readme.

#### 3 · Hack — 39 outils

`Recherche de pseudo` · `OSINT e-mail` · `OSINT IP` · `Recon GitHub` · `Recon de site` · `Note des en-têtes` · `Fuzzing de répertoires` · `Injection SQL` · `XSS réfléchie` · `LFI` · `Exposition .git` · `Énumération WordPress` · `CORS` · `Redirection ouverte` · `Analyse de JWT` · `Wayback` · `Subdomain takeover` · `Extraction JS` · `Dorks` · `Enquête DNS` · `Force brute Basic` · `Force brute de formulaire` · `Password spraying` · `Cookies` · `robots/sitemap` · `Transfert de zone` · `Faiblesses TLS` · `Sous-domaines` · `Identification de hash` · `Reverse shell` · `Payloads` · `Wordlist` · `Clone de page` · `Charge HTTP` · `Slowloris` · `Flood` · `Stress CPU/RAM` · `Audit local` · `Verrou .exe`

La note d'en-têtes chiffre la configuration d'un site de 0 à 100 et rend une lettre de A à F : HSTS et CSP pèsent le plus lourd, une version de serveur qui fuit coûte des points, un cookie sans `HttpOnly` aussi. L'analyse JWT décode l'en-tête et la charge, signale un `alg: none`, une expiration dépassée, et teste une liste de secrets faibles par HMAC.

Le verrou génère un programme Tkinter plein écran avec mot de passe aléatoire, compte à rebours de 72 heures et sortie de secours, puis le compile en `.exe` si PyInstaller est là. Alt+Tab et Ctrl+Alt+Del restent actifs : aucun verrou en espace utilisateur ne les bloque.

#### 4 · Système — 27 outils

`Serveur HTTP local` · `Client TCP` · `En-têtes HTTP` · `Certificat SSL` · `Enregistrement de domaine` · `Réputation d'IP` · `Météo` · `Cours crypto` · `Processus` · `Démarrage` · `Programmes installés` · `Pare-feu` · `Comptes utilisateurs` · `Batterie` · `Temps de marche` · `Presse-papiers` · `Synthèse vocale` · `Tâches planifiées` · `Services` · `Partages réseau` · `Variables d'environnement` · `Fichier hosts` · `Cache DNS` · `Proxy` · `Antivirus` · `État RDP` · `Pilotes`

Le serveur HTTP partage un dossier en un clic sur le réseau local, avec l'adresse déjà écrite. L'audit local recense les ports en écoute et commente les risques : Redis sans mot de passe, SMB exposé, RDP ouvert.

#### 5 · Fichiers — 17 outils

`Empreinte` · `Gros fichiers` · `Fichiers en double` · `Archives ZIP` · `Découpe/fusion` · `Recherche` · `Morse` · `Binaire/hexa` · `Base32/64` · `Vigenère` · `Atbash` · `ROT-N` · `CIDR` · `Unités` · `URL` · `Horodatage` · `UUID`

La détection de doublons compare d'abord les tailles, puis les empreintes SHA-1, ce qui évite de lire deux fois un disque entier.

#### 6 · Spectacle — 7 outils

`Séquence de démarrage` · `Tableau de bord live` · `Bannière ASCII` · `Machine à écrire` · `WarGames` · `Pluie de code` · `Radar`

Rien d'utile, tout pour l'ambiance et les captures d'écran.

### Ce qui est réel, ce qui est heuristique

Un README honnête le dit. Voici la vérité, outil par outil.

**Réel, sans réserve** — données d'API ou de protocole : infos réseau, scan de ports, DNS, TLS, certificat, RDAP, en-têtes, `.git`, `robots`, Wayback, JWT, géoloc IP, DNSBL, profils Instagram et TikTok, invitation et cadeau Discord, webhook, fuites, empreintes de fichier.

**Réel mais heuristique** — un signal, pas une preuve : SQLi (erreurs SQL et écart booléen), XSS (réflexion brute), LFI (lecture de `/etc/passwd`), force brute (redirection ou variation de taille), subdomain takeover (empreinte de page d'erreur), spray (même logique). Confirme toujours à la main.

**Simulé** — la séquence de démo, la pluie de code, le radar, WarGames. Ce sont des animations, elles ne mesurent rien.

**Limité par le service distant** — la recherche de pseudo dépend de 68 sites : certains bloquent, renvoient 429, ou exigent du JavaScript. Un résultat gris veut dire « je ne sais pas », pas « libre ». Le `--json` existe justement pour que tu puisses relancer les gris plus tard.

### Fichiers générés

| Outil | Fichier |
|---|---|
| Pseudo | `pseudo_<nom>_<date>.json` |
| Rapport | `rapport_<nom>_<date>.md` |
| Wayback | `wayback_<domaine>.txt` |
| Wordlist | `wordlist_<date>.txt` |
| Combo filtré | `combo_<domaine>.txt` |
| Wifi | `scan_wifi_<date>.csv` |
| Clone de page | `phish_<timestamp>.log` |
| Verrou | `strongstark_lock_*.py`, `.exe`, `mot_de_passe.txt` |

Tout tombe dans le dossier courant. Rien n'est envoyé ailleurs.

### Compatibilité

| Système | État |
|---|---|
| Windows 10 / 11 | complet, interface plein écran testée |
| Linux | complet, sauf les outils `netsh` et `reg` |
| macOS | partiel : wifi et quelques outils Windows manquent |

Les outils marqués Windows only s'annoncent et s'arrêtent proprement sur les autres systèmes.

### Confidentialité

Aucun compte, aucun serveur à nous, aucune télémétrie. Le fichier de configuration vit chez toi, dans `.strongstark.json`, et ne contient que le thème et la langue.

Les requêtes sortantes vont vers les services publics utilisés : `ip-api.com`, `crt.sh`, `rdap.org`, `ipify.org`, `discord.com`, `instagram.com`, `tiktok.com`, `snapchat.com`, `t.me`, `leakcheck.io`, `coingecko.com`, `wttr.in`, `speed.cloudflare.com`. Rien d'autre.

Un token Discord saisi n'est stocké nulle part : il est utilisé le temps de la requête puis oublié.

### Licence

MIT. Fais-en ce que tu veux, garde juste le nom et le lien.

<div align="center">— fin de la partie française —</div>

---

## 🇬🇧 English

### The idea

One file, no mandatory dependency, 123 tools across six pages. Full-screen interface, animated banner, colour themes, two languages, everything on the keyboard.

STRONG STARK has one stance: **actually do the thing**. No fake progress bars, no decorative hacking. When a tool calls an API, it calls a real one. When it says an account exists, that is a 200 on the profile. When it does not know, it prints grey instead of making something up.

### Contents

- [Disclaimer](#disclaimer)
- [What it is / what it is not](#what-it-is--what-it-is-not)
- [Install](#install)
- [Running](#running)
- [The six pages](#the-six-pages)
- [What is real, what is a heuristic](#what-is-real-what-is-a-heuristic)
- [Generated files](#generated-files)
- [Compatibility](#compatibility)
- [Privacy](#privacy)
- [Licence](#licence-1)

### Disclaimer

Everything network-related is passive or near-passive: nothing is changed on the target. The load tools (`DoS`, `slowloris`, `flood`, `stress`) are the only hard hitters, so keep them for your own services or a target that accepts them.

Scanning your own network, router or site: fully legal. Auditing someone else's site without permission is tolerated almost everywhere, but load is what people will complain about if you overdo it.

### What it is / what it is not

**It is:**
- a Swiss army knife for learning, networking and OSINT alike;
- a diagnostic tool when your router, site or machine misbehaves;
- a way to find the public footprint of a username, yours included;
- a Markdown report generator for a repo or a gist.

**It is not:**
- a Burp Suite, a full nmap or a Metasploit;
- a tool that magically finds passwords: it runs dictionaries, period;
- a tool that bypasses two-factor authentication;
- a tool that works offline: without a connection, half the pages are useless.

### Install

Requirement: Python 3.8 or newer.

```bash
git clone https://github.com/<you>/strongstark.git
cd strongstark
python strongstark.py
```

No `pip install` needed. Three functions handle it themselves and offer the install when you open them:

| Module | Purpose | Without it |
|---|---|---|
| `Pillow` | EXIF metadata | the EXIF tool refuses to start |
| `qrcode` | QR code generation | the QR tool refuses to start |
| `PyInstaller` | build the locker as `.exe` | the bundled `.bat` takes over |

On Windows, run from **Windows Terminal**, **PowerShell** or **cmd**. Double-clicking the file opens a window that closes too fast.

### Running

```bash
python strongstark.py
```

| Option | Effect |
|---|---|
| `--theme <name>` | force a theme (`or`, `cyan`, `rouge`, `monochrome`…) |
| `--list-themes` | list the 32 themes |
| `--lang fr` / `--lang en` | force the language |
| `--no-color` | colourless interface |
| `--pseudo <name>` | headless username search |
| `--json` | JSON output with `--pseudo` |

Navigation: `n` next page, `p` previous, `c` settings, `0` quit. A number runs the matching tool.

Scriptable search example:

```bash
python strongstark.py --pseudo myname --json > result.json
```

### The six pages

#### 1 · Network — 21 tools

`Network info + geoloc` · `Unblock-web (DNS)` · `Port scan` · `DNS lookup` · `Saved wifi` · `Passwords` · `MD5 cracker` · `Quick encryption` · `Image metadata` · `File shredder` · `System info` · `Code rain` · `QR generator` · `Speed test` · `Demo sequence` · `Network discovery` · `Remote control` · `Nearby wifi` · `Traceroute` · `ARP table` · `Wake-on-LAN`

Unblock-web applies a public DNS and flushes the cache: the first thing to do when a school filter blocks a domain. Network discovery sweeps all 254 addresses, cross-checks the ARP table and flags machines exposing SMB, RDP, SSH or a web server.

#### 2 · Accounts — 12 tools

`Username footprint` · `Discord toolkit` · `Instagram profile` · `TikTok profile` · `Snapchat profile` · `Telegram profile` · `Invite analysis` · `Gift link check` · `Webhook analysis` · `Breach lookup` · `Combo-list parser` · `Markdown report`

The page that impresses, and the one that genuinely works:

- **Footprint** queries Instagram, TikTok, Snapchat and Telegram in parallel and returns name, bio, followers, posts, private or verified flags, business e-mail and phone when public.
- **Discord**: with a token, prints the full identity (username, e-mail, phone, 2FA, Nitro, creation date derived from the snowflake), servers with your role in each, billing and masked payment methods, linked accounts, private conversations.
- **Invite**: server name, description, members, presence, channel, icon — without joining.
- **Nitro gift**: tells whether a link is still available or already claimed, and what it grants.
- **Breach**: queries a public database, lists sources, links to the others.
- **Report**: cross-references the 68-site username search and the public profiles, writes a Markdown file ready to paste into a readme.

#### 3 · Hack — 39 tools

`Username search` · `E-mail OSINT` · `IP OSINT` · `GitHub recon` · `Site recon` · `Header grade` · `Directory fuzzing` · `SQL injection` · `Reflected XSS` · `LFI` · `Exposed .git` · `WordPress enumeration` · `CORS` · `Open redirect` · `JWT analysis` · `Wayback` · `Subdomain takeover` · `JS extraction` · `Dorks` · `DNS investigation` · `Basic brute force` · `Form brute force` · `Password spraying` · `Cookies` · `robots/sitemap` · `Zone transfer` · `TLS weaknesses` · `Subdomains` · `Hash identification` · `Reverse shell` · `Payloads` · `Wordlist` · `Page clone` · `HTTP load` · `Slowloris` · `Flood` · `CPU/RAM stress` · `Local audit` · `Screen locker`

The header grade scores a site from 0 to 100 and returns an A to F letter: HSTS and CSP weigh the most, a leaking server version costs points, so does a cookie without `HttpOnly`. The JWT analyser decodes header and payload, flags `alg: none`, an expired claim, and tries a list of weak HMAC secrets.

The locker builds a full-screen Tkinter program with a random password, a 72-hour countdown and an escape hatch, then compiles it to `.exe` if PyInstaller is present. Alt+Tab and Ctrl+Alt+Del stay active: no userland lock blocks them.

#### 4 · System — 27 tools

`Local HTTP server` · `TCP client` · `HTTP headers` · `SSL certificate` · `Domain registration` · `IP reputation` · `Weather` · `Crypto prices` · `Processes` · `Startup` · `Installed programs` · `Firewall` · `User accounts` · `Battery` · `Uptime` · `Clipboard` · `Speech synthesis` · `Scheduled tasks` · `Services` · `Network shares` · `Environment variables` · `Hosts file` · `DNS cache` · `Proxy` · `Antivirus` · `RDP state` · `Drivers`

The HTTP server shares a folder on the LAN in one click, address already printed. The local audit lists listening ports and comments on the risks: passwordless Redis, exposed SMB, open RDP.

#### 5 · Files — 17 tools

`Fingerprint` · `Large files` · `Duplicate files` · `ZIP archives` · `Split/merge` · `Search` · `Morse` · `Binary/hex` · `Base32/64` · `Vigenère` · `Atbash` · `ROT-N` · `CIDR` · `Units` · `URL` · `Timestamp` · `UUID`

Duplicate detection compares sizes first, then SHA-1 hashes, so it never reads a whole disk twice.

#### 6 · Show — 7 tools

`Boot sequence` · `Live dashboard` · `ASCII banner` · `Typewriter` · `WarGames` · `Code rain` · `Radar`

Nothing useful, all atmosphere and screenshots.

### What is real, what is a heuristic

An honest readme says it. Here is the truth, tool by tool.

**Real, no caveat** — API or protocol data: network info, port scan, DNS, TLS, certificate, RDAP, headers, `.git`, `robots`, Wayback, JWT, IP geoloc, DNSBL, Instagram and TikTok profiles, Discord invite and gift, webhook, breaches, file hashes.

**Real but heuristic** — a signal, not a proof: SQLi (SQL errors and boolean delta), XSS (raw reflection), LFI (`/etc/passwd` read), brute force (redirect or size change), subdomain takeover (error-page fingerprint), spray (same logic). Always confirm by hand.

**Simulated** — the demo sequence, code rain, radar, WarGames. Those are animations, they measure nothing.

**Limited by the remote service** — the username search relies on 68 sites: some block, return 429, or need JavaScript. A grey result means "I do not know", not "free". The `--json` flag exists precisely so you can rerun the greys later.

### Generated files

| Tool | File |
|---|---|
| Username | `pseudo_<name>_<date>.json` |
| Report | `rapport_<name>_<date>.md` |
| Wayback | `wayback_<domain>.txt` |
| Wordlist | `wordlist_<date>.txt` |
| Filtered combo | `combo_<domain>.txt` |
| Wifi | `scan_wifi_<date>.csv` |
| Page clone | `phish_<timestamp>.log` |
| Locker | `strongstark_lock_*.py`, `.exe`, `mot_de_passe.txt` |

Everything lands in the current folder. Nothing is sent anywhere else.

### Compatibility

| System | State |
|---|---|
| Windows 10 / 11 | full, full-screen interface tested |
| Linux | full, except `netsh` and `reg` tools |
| macOS | partial: wifi and some Windows tools missing |

Windows-only tools announce themselves and exit cleanly elsewhere.

### Privacy

No account, no server of ours, no telemetry. The config file lives on your machine, in `.strongstark.json`, and only holds the theme and the language.

Outbound requests go to the public services in use: `ip-api.com`, `crt.sh`, `rdap.org`, `ipify.org`, `discord.com`, `instagram.com`, `tiktok.com`, `snapchat.com`, `t.me`, `leakcheck.io`, `coingecko.com`, `wttr.in`, `speed.cloudflare.com`. Nothing else.

A Discord token you paste is stored nowhere: used for the request, then forgotten.

### Licence

MIT. Do what you want with it, just keep the name and the link.

<div align="center">

```
 █▀▀ ▀█▀ █▀▀█ █▀▀█ █▄ █ █▀▀▀  █▀▀▀ ▀█▀ █▀▀█ █▀▀█ █  █
 █▀▀  █  █▄▄▀ █  █ █ ▀█ █ ▀█  █▀▀   █  █▄▄█ █▄▄▀ █▀▄
 ▀▀▀  ▀  █ ▀█ █▄▄█ █  █ █▄▄▀  █▄▄▀  ▀  █  █ █ ▀▀ █ ▀▀
```

`wardroque` · [discord.gg/zKf74fnXR](https://discord.gg/zKf74fnXR)

</div>
