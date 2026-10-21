# TicketFoot — mode opératoire de l'apprenant

Pendant 10 jours, tu conçois avec Claude une équipe d'agents IA qui construit un site de billetterie de football. Tu ne codes pas : tu écris les définitions des agents, tu les lances, tu observes, tu corriges leurs définitions.

Le guide pas à pas du J0 et du J1 est dans `docs/demarrage.html` : télécharge-le et ouvre-le dans ton navigateur.

Ce dépôt contient le point de départ :

| Fichier | Rôle |
| --- | --- |
| `CLAUDE.md` | Le contexte que toute session Claude lit en premier : règles, stack, conventions |
| `docs/brief.md` | Le besoin à réaliser |
| `docs/gabarit-agent.md` | Le modèle pour écrire tes agents |
| `docs/journal.md` | Ton journal de bord, à tenir chaque jour |
| `docs/taches.md` | Le suivi des tâches, tenu par tes agents à partir du J3 |
| `.claude/agents/` | Tes agents. Un seul s'y trouve au départ : l'agent de vérification du J0 |
| `.claude/skills/` | Tes skills, à partir du J5 |

## J0 — Vérifier que tout fonctionne (une demi-journée)

### 1. Ouvrir une session

Ouvre une session Claude Code sur ce dépôt, avec l'accès fourni par ton formateur.

### 2. Vérifier que Claude a lu le contexte

Écris :

> Résume en 5 lignes le projet et les règles que tu dois respecter sur ce dépôt.

La réponse doit mentionner l'exercice de formation, l'interdiction de créer des agents de sa propre initiative et la stack imposée. Sinon, préviens ton formateur.

### 3. Lancer ton premier agent

Écris :

> Utilise l'agent verificateur-j0.

Un fichier `docs/verification-j0.md` doit apparaître, avec le nom du club, le nombre 5 et la phrase « Vérification J0 terminée ».

Si l'agent n'est pas trouvé, ferme la session, rouvre-la et recommence.

### 4. Faire ton premier commit

Écris :

> Fais un commit de l'état actuel avec le message « J0: environment check ».

### 5. Les bases à connaître

**Git en cinq mots**

| Mot | Ce que c'est |
| --- | --- |
| Commit | Une photo du projet à un instant donné, avec un message |
| Historique | La suite des commits ; on peut revenir à n'importe lequel |
| Diff | Ce qui a changé entre deux photos |
| Branche | Une ligne de travail parallèle |
| Revert | Annuler un commit en en créant un nouveau qui l'inverse |

**Le web en cinq mots**

| Mot | Ce que c'est |
| --- | --- |
| Serveur | Le programme qui fait tourner le site et répond aux demandes |
| Client | Le navigateur de l'utilisateur |
| URL | L'adresse d'une page ou d'une action, par exemple `/matchs/3` |
| Base de données | L'endroit où sont rangés les matchs, sièges et commandes |
| Test de bout en bout | Un robot qui utilise le site comme un humain et vérifie le résultat |

## J1 — Écrire ton premier vrai agent

1. Ouvre `docs/gabarit-agent.md` et lis-le avec Claude. Pose-lui toutes tes questions sur les champs.
2. Demande-lui de t'aider, sans écrire à ta place :

   > Je veux écrire un agent analyste-spec qui transforme docs/brief.md en spécification testable. Pose-moi les questions nécessaires pour remplir le gabarit, une rubrique à la fois.

3. Enregistre le résultat dans `.claude/agents/analyste-spec.md`.
4. Lance-le, lis `docs/spec.md` et `docs/questions.md`, et réponds aux questions.
5. Classe chaque bloc fonctionnel en Must, Should ou Could.
6. Note dans `docs/journal.md` ce qui t'a surpris, puis fais le commit du soir.

## Règles de chaque jour

- **Tu ne modifies jamais le code toi-même.** Si un résultat est faux, tu corriges la définition de l'agent fautif et tu relances.
- **Règle des 3 relances.** Au troisième échec d'un agent sur la même tâche, tu arrêtes de relancer et tu réécris sa définition.
- **Chaque dérive va dans le journal**, avant d'être corrigée.
- **Démo de 10 minutes chaque soir**, même si c'est cassé.
- **Commit chaque soir.**
- **Jamais de numéro de carte, de mot de passe ou de donnée personnelle réelle.** Le paiement est simulé.
