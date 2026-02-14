# LAB-2-Rooting-Android

## Étape 1 : Rooter l'AVD

![Import OVA](https://github.com/user-attachments/assets/5773c1e6-a159-490b-b157-1811738590e4)
![Import OVA](https://github.com/user-attachments/assets/4a6d8ea8-9e65-4cdd-848d-496373556c36)
![Import OVA](https://github.com/user-attachments/assets/ef8b1296-4098-4c44-bef6-cbbe1881ddaa)


## Étape 2 : Fiche périmètre (5 lignes)

- Application : LabApp v1.0  
- Support : AVD (Android Virtual Device, userdebug)  
- Objectif : Comprendre rooting et impacts sur sécurité mobile  
- Données : aucune donnée réelle utilisée
- Réseau : Test isolé (pas de connexion externe)

## Étape 3 : Démarrer un AVD propre

![Import OVA](https://github.com/user-attachments/assets/f74eee9a-4ad6-4ecc-bb8b-153acd15fb6e)


## Étape 4 : Installer et lancer l'app de test

![Import OVA](https://github.com/user-attachments/assets/d05195e4-bc5f-48cf-8a44-18e59ee878aa)
![Import OVA](https://github.com/user-attachments/assets/6f59f445-e9af-4ff4-8dc0-105e54ecebc6)


## Étape 5 : Définir 3 scénarios simples

![Import OVA](https://github.com/user-attachments/assets/708a7e66-81cb-4823-b3cf-e9fba8c65377)
![Import OVA](https://github.com/user-attachments/assets/ed80abcc-4b72-4ee4-bb36-4afd460adb62)
![Import OVA](https://github.com/user-attachments/assets/7a510e6d-d2ac-430c-ab05-fff10f7de72d)

## Étape 6 : Lire Android Security 


Android repose sur plusieurs couches de sécurité, comme un oignon.

Chaque application est isolée grâce au sandboxing.

Le modèle de permissions contrôle l’accès aux ressources sensibles.

L’OS protège l’intégrité globale du système contre les modifications non autorisées.

Analogie : chaque app est dans sa propre salle de classe fermée.

Les permissions = demander au professeur avant d’utiliser un outil, et l’intégrité système verrouille le bâtiment entier.

## Étape 7 : Verified Boot (idée générale + check AVD)


La propriété ro.boot.verifiedbootstate n’a pas retourné de valeur sur l’AVD utilisé. Cela est attendu car certains émulateurs ne simulent pas Verified Boot


## Étape 8 : AVB (Android Verified Boot)

La commande fastboot getvar avb_boot_state n’a pas retourné de valeur sur l’AVD, ce qui est attendu car AVB n’est pas simulé. Sur un device réel, la valeur indiquerait l’état d’intégrité (green/orange/red)

## Étape 9 : Définir le rooting (4 phrases)

Le rooting correspond à l’obtention des privilèges super-utilisateur sur Android. Cela modifie les protections et la confiance du système. En laboratoire, il est utile pour observer certains comportements, mais il reste risqué et nécessite isolement, traçabilité et reset. Le terme "root" vient d’UNIX, où l’administrateur s’appelle "root" ; sur Android, cela signifie devenir cet administrateur tout-puissant. Analogie : le rooting est comme un passe-partout pour toutes les portes d’un bâtiment, utile pour la maintenance mais dangereux s’il tombe entre de mauvaises mains


## Étape 10 : Intérêt labo (non opérationnel)
En labo, un environnement privilégié peut aider à observer des artefacts système normalement inaccessibles, analyser les comportements runtime de l’application à bas niveau et tester la robustesse du stockage face à un attaquant privilégié. Par exemple, avec les privilèges root, il est possible d’examiner comment une application stocke ses données sensibles et vérifier si elle repose uniquement sur la protection du système (mauvaise pratique) ou si elle implémente son propre chiffrement (bonne pratique). Labo autorisé uniquement. Contexte légal : dans certains pays, le rooting peut violer les conditions d’utilisation du fabricant ou même des lois sur la protection des mesures techniques. Il faut toujours disposer d’une autorisation explicite pour ces tests

## Étape 11 : Matrice de risques (8 risques, 1 phrase chacun)

Intégrité non garantie → conclusions biaisées sur la sécurité réelle

Surface d’attaque accrue si l’appareil sort du labo → exposition à des menaces externes

Données sensibles exposées si présentes → violation potentielle de confidentialité

Instabilité système → tests non reproductibles et résultats incohérents

Mélange comptes perso/test → fuite possible d’informations personnelles

Mauvais nettoyage fin de séance → persistance de données sensibles

Réseau non isolé → effets involontaires sur systèmes externes

Traçabilité insuffisante → impossible de reproduire ou d’auditer les tests

## Étape 12 : Mesures défensives (8 mesures, 1 phrase chacune)


Réseau isolé	Éviter toute communication non contrôlée avec l’extérieur

Données fictives uniquement	Éliminer tout risque de fuite réelle

Device/AVD dédié	Utiliser exclusivement pour les tests de sécurité

Snapshots ou wipe	Nettoyer en fin de séance pour ne laisser aucune trace

Journal de configuration	Assurer la reproductibilité des tests

Aucun compte personnel	Éviter tout mélange de données sensibles

Contrôle strict des APK	Limiter les risques liés aux applications installées

Horodatage + captures	Garantir une traçabilité complète des étapes

## Étape 13 : OWASP MASVS (2 exigences)


