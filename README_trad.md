# Script post installation pour les serveurs CentOS 7 

(c) Niki Kovacs, 2020

Ce dépôt fournit un script "automagic" post installation pour les serveurs sous CentOS 7 composé d`une collection de scripts utiles et de fichier de configurations pour les services de base.

## En résumé

Il realise les actions suivantes.

  1. Installe un systeme Centos 7 en version minimal.

  2. Creer un utilisateur non root avec des droits administrateur.

  3. Installe Git: `sudo yum install git`

  4. Recupere le script: `git clone https://gitlab.com/kikinovak/centos-7.git`

  5. Ouvre le nouveau repertoire: `cd centos-7`

  6. Execute le script: `sudo ./centos-setup.sh --setup`

  7. Prenez une tasse de cafe pendant que le script fait tout le travail.

  8. Redemarrez.


## Personnaliser un serveur CentOS

Modifier une installation minimale de CentOS en serveur fonctionnel se resume a une serie d`operations plus ou moins longues. Votre procedure peut bien sur varier, mais voici ce que je fais habituellement sur une installation neuve de CentOS:

  * Personnaliser le shell Bash: Prompt, alias, etc.

  * personnaliser l`editeur de texte Vim.

  * Configurer les dépôts officiels et tiers.

  * Installer une liste d`outils en ligne de commande.

  * Supprimer plusieurs paquets inutiles.

  * Autoriser l`utilisateur admin a acceder aux journaux systeme.

  * Desactive l`ipv6 er reconfigurer quelques services en consequence.
  
  * Configurer un mot de passe persistant pour `sudo`.

  * Etc.

Le script `centos-setup.sh` effectue les operations suivantes.

Configure Bash et Vim et parametre une resolution de console par defaut plus lisible:

```
# ./centos-setup.sh --shell
```
Configuration des dépôts officiels et tiers:

```
# ./centos-setup.sh --repos
```
Installe les groupes de packet `core` et `base` avec des outils supplémentaires:

```
# ./centos-setup.sh --extra
```
Supprime plusieurs paquets inutiles:

```
# ./centos-setup.sh --prune
```
Active le droit d`acces aux journaux systeme pour le compte utilisateur admin:

```
# ./centos-setup.sh --logs
```
Desactive l`IPV6 et reconfigure des services de base en consequence:

```
# ./centos-setup.sh --ipv4
```
Configure la persistance du mot de passe pour sudo:

```
# ./centos-setup.sh --sudo
```
Effectue toutes les commandes ci-dessus en une seule fois:

```
# ./centos-setup.sh --setup
```
Supprime les packets et revient à un système de base:

```
# ./centos-setup.sh --strip
```
Affiche le message d`aide:

```
# ./centos-setup.sh --help
```
Si vous voulez savoir exactement ce qu`il se passe en arriere plan, ouvrez un second terminal et consultez les journaux:

```
$ tail -f /tmp/centos-setup.log
```

