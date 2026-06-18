# INC-002 – Imprimante réseau inacessible

## Contexte
Un utilisateur signale qu'il ne parvient plus à imprimer sur l'imprimante réseau partagée de l'entreprise.

## Symptômes
- L'imprimante n'apparaît plus dans la liste des périphériques
- Impossible d'imprimer un document
- Message d'erreur : "Imprimante indisponible"

## Diagnostic

### 1. Vérification de la connectivité réseau
```cmd 
ping 192.168.1.50
```

Résultat : 
* Réponse KO -> problème réseau OU imprimante hors ligne

### 2. Vérification de l'accès à l'imprimante

http://192.168.1.50

Observation :
* Interface web inaccessible

### 3. Vérification du spooler d'impression (poste client)

services.msc

Service "Spouleur d'impression" :
* arrêté / en erreur

Cause probable
* Imprimante hors réseau OU éteinte
* Service spooler Windows arrêté
* Problème DHCP / IP de l'imprimante changée

Résolution
Redémarrage du service spooler :

net stop spooler
net start spooler

Vérification réseau :
* Ping de l'imprimante restauré
* IP confirmé

Résultat
* Imprimante de nouveau détectée
* Impression fonctionnelle
* Service restauré

Compétences démontrées
* Diagnostic réseau
* Services Windows
* Gestion impression Windows
* TCP/IP
* Support utilisateur niveau 1


