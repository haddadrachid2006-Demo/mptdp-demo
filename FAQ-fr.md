🛡️ MPTDP – FAQ Technique & Défense d’Architecture

Référence : draft-haddad-mptdp
Statut : Internet-Draft individuel (non encore adopté par un WG IETF)

1. Pourquoi ne pas juste utiliser un formulaire web ?

Les formulaires web forcent l’utilisateur à quitter son environnement de travail :

ouvrir un lien externe

remplir un formulaire isolé

revenir dans l’email

👉 MPTDP garde l’utilisateur dans son outil principal : l’email.
On conserve : conversations, signatures, archivage, habitudes…
avec la rigueur d’un formulaire structuré JSON.

2. Risque d’énumération d’emails ?

Non.

Le protocole repose sur un Manifeste de confidentialité :

/.well-known/mptdp-manifest.json

Ce fichier définit explicitement les adresses E-mail publiques exposant un template.

👉 Le client MPTDP n’a pas le droit d’interroger une adresse non listée.
→ Privacy by Design
→ GDPR compatible

3. Que se passe-t-il si le serveur destinataire ne répond pas ?

Le protocole est conçu en Fail-Safe :

si le manifest retourne 404 / 500

si l’API ne répond pas

si le HTTPS est indisponible

👉 Le client retourne en mode email classique.
L’utilisateur n’est jamais bloqué.

4. Quel est le lien entre MPTDP et l’IA ?

Les IA ont du mal à traiter :

des mails mal rédigés

incomplets

ambigus

non structurés

MPTDP impose une structure JSON typée, générée avant envoi.

Résultat :

agents IA → traitement sans hallucinations

CRM / PEGA / ServiceNow → ingestion automatique

workflows instantanés

👉 MPTDP est le pont entre l'intention humaine et les agents IA.

5. Comment prévenir le phishing (faux templates) ?

Le protocole intègre plusieurs mécanismes :

HTTPS obligatoire

signature cryptographique du payload JSON (clé privée du domaine)

clé publique exposée via DNS ou dans le manifest (DKIM-like)

Un attaquant ne peut pas générer un template JSON légitime sans la clé privée.

6. Peut-on générer un numéro de ticket unique ?

Oui, recommandé.

Format conseillé :

"ticket_id": "MPTDP-20250201-ABC123"


Génération possible :

via l’add-in

via le SaaS (recommandé)

via le template

via le backend destinataire

Le SaaS offre la meilleure traçabilité (logs, audit, suivi).

7. MPTDP modifie-t-il SMTP ?

Non.

MPTDP intervient avant l’envoi du mail :
c’est un “Pre-Flight”.

L’email envoyé reste un email standard SMTP.
Le JSON est :

dans le corps (commentaire invisible),

ou en pièce jointe .json,

ou dans un header X-MPTDP (option entreprise).

👉 Compatibilité totale.

8. Que voit un destinataire non compatible ?

Un email normal.

Aucune dégradation :

texte intact

PJ classique

commentaire HTML invisible

Backward-compatible à 100%.

9. Comment MPTDP devient une norme ?

Processus classique :

Concept & POC – terminé

Publication Internet-Draft – fait (draft-haddad-mptdp)

Recherche d’adoption par un Working Group IETF

Implémentations pilotes (Microsoft, Google, grandes entreprises)

RFC potentielle

👉 Le protocole peut être utilisé immédiatement, même sans adoption WG.

10. Fonctionne-t-il sans add-in Outlook ?

Oui.

MPTDP peut être utilisé via :

extension navigateur

client web

outils internes

copier-coller du JSON

L’add-in Outlook ou Gmail est un confort, pas une dépendance.

© 2025 – Rachid H., MPTDP Project
