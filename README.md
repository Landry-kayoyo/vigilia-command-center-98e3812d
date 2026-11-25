# Vigilia Command Center

Importe ce projets https://github.com/Landry-kayoyo/vigilia123 et connectés a une nouvelle bdd et fait la migration : PROMPT — ÉVOLUTION V1.1 : Centre personnel de commandement technique et équipe d'agents IA



Mission. Fais évoluer l'application EXISTANTE vers la V1.1. Ne repars pas de zéro, ne remplace pas l'architecture ou une technologie qui fonctionne sans justification technique solide. Application strictement personnelle (pas un SaaS). Priorité : fiabilité, sécurité, capacités réelles, préservation de l'existant. Jamais de démo visuelle ni de fausses données à la place d'une vraie fonctionnalité.



1. Audit obligatoire d'abord. Examine l'architecture, les technologies, routes, pages, composants, base de données (tables, relations, migrations), intégrations, authentification et permissions. Repère ce qui est incomplet, simulé ou inutilisé, ainsi que les risques de régression. Compare l'existant à cette V1.1. Ne supprime rien sans avoir vérifié ses dépendances. Prévois migrations et sauvegardes avant tout changement structurel.



2. Système multi-agents.



• Agent principal (mode COLLABORATOR) : directeur des opérations techniques. Il comprend les demandes en langage naturel, identifie le projet, choisit automatiquement les spécialistes, décompose en sous-tâches, coordonne, vérifie, consolide le rapport final. Il peut travailler seul si aucune délégation n'est utile. Il prend des initiatives d'analyse, mais demande mon approbation avant toute opération sensible.

• Spécialistes prédéfinis (vraies instructions, outils, permissions, contexte) : ingénieur logiciel, administrateur systèmes (Linux/Ubuntu), ingénieur réseaux, cybersécurité, surveillance et diagnostic, automatisation, chef de projet technique.

• Espace « Équipe IA » : créer, modifier, activer/désactiver des agents personnalisés (nom, spécialité, instructions, compétences, outils, projets accessibles, permissions), consulter leurs missions et résultats. Architecture extensible (ex. expert OpenMRS, HomeLab, Supabase).

• Collaboration : plusieurs agents par mission, informations partagées sans mélanger les permissions, dépendances entre tâches, états, résultats intermédiaires, relances contrôlées, historique des décisions. Pas de boucles infinies ni de dépense de tokens incontrôlée.



3. Mes projets. Fiche par projet : description, catégorie, URL, dépôt GitHub, technologies, environnements, services, intégrations, agents autorisés, missions, incidents, état. L'agent reconnaît MarketNet, Landry Net, HomeLab, etc., et charge le contexte du projet avant d'enquêter. Ne jamais supposer une technologie sans vérification.



4. Missions. Titre, description, projet, priorité, agents mobilisés, étapes, progression, résultats, approbations, historique. États : en attente, planification, en investigation, en cours, en attente d'approbation, en validation, terminée, échec, annulée. Exécution en arrière-plan, persistante et récupérable, sans bloquer l'interface ni les requêtes HTTP.



5. GitHub (mode approbation). Lecture libre sur les dépôts autorisés (fichiers, code, commits, branches, PR, issues, préparation de correctifs). Toute écriture (branche, fichier, commit, PR, merge, config) exige mon approbation explicite, avec : opération, dépôt, fichiers, risque, résultat attendu. Jamais de modification directe de la branche principale. Trace de chaque approbation.



6. Diagnostic approfondi. Ex. problème de connexion Google sur MarketNet : examiner le comportement, le code d'auth, les callbacks, les logs Supabase/Vercel (si permissions), les commits récents, les configs sans exposer les secrets, puis corréler. Le rapport sépare : faits observés, cause confirmée, hypothèses, informations manquantes, fichiers concernés, solution, risques. Jamais une hypothèse présentée comme cause confirmée. Jamais prétendre avoir consulté des logs ou lancé des tests sans accès réel.



7. Intégrations. GitHub, Supabase, Vercel, API externes, serveurs Ubuntu/SSH, webhooks, monitoring, réseau. Chacune : état de connexion, test, configuration, permissions, historique, gestion d'erreurs. Une URL ne donne pas tous les accès : n'utiliser que les accès réellement disponibles. Si non configuré : afficher « À configurer » / « Non connecté », jamais de connexion simulée.



8. Telegram (canal principal). Bot token protégé côté serveur, webhook configuré automatiquement après validation du token (l'utilisateur ne saisit aucune URL), liaison sécurisée du compte propriétaire avec Chat ID vérifié, seuls les comptes approuvés autorisés, endpoints protégés (anti-replay, rate limiting). Notifications : incidents, fin de mission, approbations. Je peux lancer et suivre une mission depuis Telegram. Le web reste le centre de contrôle.



9. Fournisseurs IA et clés API. Gemini, OpenAI et autres. Plusieurs clés par fournisseur : test, état, usage, erreurs, quotas, modèles, routage, coûts. Basculement intelligent selon l'erreur : 401 (clé invalide), 403 (permission), 429 (quota), 5xx (indisponibilité), erreur réseau, erreur de prompt (pas de changement de clé). Réessais avec temporisation, circuit breaker, historique des bascules, modèle de secours, limites de consommation. Les clés d'un même projet peuvent partager le quota : ne pas le présenter comme capacité supplémentaire. Ne jamais contourner les limites du fournisseur. Secrets chiffrés côté serveur, jamais exposés (frontend, prompts, logs, réponses).



10. Surveillance. Contrôles périodiques configurables selon les intégrations dispo (disponibilité, erreurs, déploiements, logs, serveurs, ressources, réseau). Flux : détecter, rassembler, analyser, mobiliser les spécialistes, évaluer la gravité, proposer, notifier sur Telegram. Alertes sans répétition. Ne pas afficher « opérationnel » sans données réelles.



11. Mémoire. Mémoire par projet, historique des missions, décisions, résultats d'enquêtes, préférences, documentation, connaissances par agent. Séparer commun et propre au projet, permettre la correction des infos obsolètes. Jamais de secrets en mémoire.



12. Sécurité. Moindre privilège ; distinguer lecture, analyse, préparation, exécution. Approbation explicite pour : production, déploiement, suppression, migration de données, config sensible, écriture GitHub, permissions, opération irréversible. Approbation liée à une action précise, un périmètre et une durée limitée. Journal d'audit, permissions validées côté serveur, protection des endpoints, gestion des sessions. Aucune commande arbitraire exécutée sans contrôle ; outils à contrats structurés et validés.



13. Interface. Garder l'identité visuelle actuelle. Sections : Tableau de bord, Assistant IA, Équipe IA, Mes projets, Missions, Surveillance, Intégrations, Fournisseurs IA, Historique/journaux, Paramètres. Tableau de bord avec données réelles uniquement. Responsive (PC et smartphone).



14. À retirer (après vérification des dépendances). Abonnements, facturation, plans clients, fonctions SaaS multi-clients, rapports e-mail et SMTP associé. Telegram remplace l'e-mail.



15. Architecture et tests. S'adapter à la stack existante. Séparer : frontend, API, orchestrateur IA, agents, missions, connecteurs, fournisseurs IA, stockage, notifications, tâches de fond (file de tâches ou équivalent). Gérer erreurs, timeouts, réessais, traçabilité. Tests pour : agents, routage, collaboration, permissions, approbations, GitHub, Telegram, clés API et basculement, erreurs fournisseur, missions, surveillance, protection des secrets. Vérifier migrations et absence de régression.



16. Livraison par phases. (1) Audit, (2) Architecture, (3) Fondation (agent principal, agents, missions), (4) Intégrations, (5) Intelligence et surveillance, (6) Interface, tests, sécurité, documentation. Ne déclarer une phase terminée que si tests et intégrations sont réellement opérationnels. Avance progressivement sans casser l'existant.



Résultat attendu. L'agent principal est mon interlocuteur et responsable technique IA, les spécialistes ses collaborateurs, et je garde le contrôle des autorisations. Exemples de missions : « Examine MarketNet et trouve les erreurs », « Analyse mon infrastructure Ubuntu », « Surveille mes services et avertis-moi sur Telegram », « Crée un agent expert OpenMRS ».

This project was built with [Lovable](https://lovable.dev).

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/2447ddbc-4605-472f-845c-bbee9236c8bc).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
