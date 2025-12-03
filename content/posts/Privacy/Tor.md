+++
title = "Presentation"
date = "2025-12-03T12:21:55+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "worri"
authorTwitter = "" #do not include @
cover = ""
tags = ["Crypto", ""]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
hideComments = false
+++

# Tor

## Présentation

Tor est un réseau de communication anonyme qui permet aux utilisateurs de naviguer sur Internet sans être identifiés.

## Etablir une connexion 
Une connexion se base sur trois noeuds différents pour assurer la confidentialité et la sécurité des données: 

1. Trouver le Guard Node : 

Consultation de la liste des noeuds auprès des Directory Authorities (DA) avec leur clé publique. Le client établit une connexion avec le Guard Node à partir de la clé publique `K1`. ( Diffie- Hellman ).

2. Trouver le Middle Node : 

Le client établit une connexion avec le Middle Node à partir de la clé publique du second noeud `K2`. ( Diffie- Hellman ) à travers le Guard Node. Ainsi, le traffic passe à travers le Guard Node est déchiffré à partir de la clé de session puis est addréssé au Middle Node.
Cela permet de négocier la clé de session avec le Middle Node `K2`.

3. Trouver le Exit Node : 

Le processus est répété à destination du Exit Node à travers le Guard Node et le Middle Node.

Ainsi, une fois les connexions établies, le client chiffre ses données avec `K1` `K2` et `K3`. Le premier noeud n'a aucun visibilité sur la destination du traffic ou son contenu, seule la source est connue. Le Middle Node n'a aucun visibilité sur la destination du traffic ou son contenu. L'Exit Node n'a aucun visibilité sur la source du traffic mais connaît sa destination et son contenu. 

| Noeud        | Guard Node | Middle Node | Exit Node |
|--------------|-----------|--------------|-----------|
| Source       | Connue    | Inconnue     | Inconnue  |
| Destination  | Inconnue  | Inconnue     | Connnue   |
| Contenu      | Inconnue  | Inconnue     | Inconnue  |
 
La situation dans laquelle un grand nombre de noeud sont contrôlées par une entité ( CIA par exemple ) alors il serait possible de corréler les timinig et les tailles de requêtes pour identifier les utilisateurs et leur traffic si celui-ci contrôle l'entrée et la sortie.
C'est pourquoi, le Guard Node est réutilisé pour un utilisateur pour une durée de 2 à 3 mois. Cela permet de réduire le nombre de noeud connaissant l'origine du traffic etréduit la probabilité qu'un traffic soit connu de A à Z bien que cela augmente parfois la durée de la compromission de la confidentialité des données. 

## Source : 

[Documentation à digger](https://spec.torproject.org/intro/index.html)