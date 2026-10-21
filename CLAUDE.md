# TicketFoot — contexte projet

## Nature du projet

TicketFoot est un exercice de formation de 10 jours. Un apprenant, rédacteur technique de métier, conçoit une équipe d'agents IA qui construit un site de billetterie de football. Deux livrables ont le même poids : l'équipe d'agents (`.claude/agents/`, `.claude/skills/`) et le site.

Le besoin fonctionnel est décrit dans `docs/brief.md`. C'est la seule source des règles de gestion.

## Règles pour toute session Claude sur ce dépôt

1. **Ne crée aucun agent ni aucune skill de ta propre initiative.** Les définitions d'agents sont écrites par l'apprenant, avec ton aide s'il la demande. Tu peux proposer, critiquer, expliquer ; c'est lui qui décide et valide.
2. **Quand l'apprenant demande de corriger un résultat, aide-le à corriger la définition de l'agent fautif**, pas le code directement. Seuls les agents produisent le code.
3. **N'invente aucune règle de gestion.** Toute ambiguïté du brief va dans `docs/questions.md`.
4. **Ne lis jamais `.env`** et n'écris jamais de clé, de mot de passe ou de donnée personnelle réelle dans le dépôt.
5. **Paiement : simulé uniquement.** Aucun service de paiement externe (Stripe, PayPal ou autre), aucune saisie de numéro de carte.
6. Les tâches en cours sont suivies dans `docs/taches.md` ; les incidents d'agents dans `docs/journal.md`.

## Stack imposée

| Élément | Choix |
| --- | --- |
| Langage | Python 3.12 |
| Framework web | FastAPI |
| Base de données | SQLite, via SQLAlchemy 2 |
| Interface | Templates Jinja2 + HTMX, sans framework JavaScript |
| Tests unitaires et d'intégration | pytest |
| Tests de bout en bout | Playwright (Python) |
| Paiement | Simulé dans l'application, sans service externe |
| Billets | PDF avec QR code |

Ne change pas de stack sans accord écrit du formateur.

## Conventions

- **Lancement en une seule commande** : `./lancer.sh` installe les dépendances, crée la base, charge les données de démo et démarre le serveur sur le port 8000.
- **Tests en une seule commande** : `./tester.sh` lance tous les tests.
- **Arborescence** : `app/` pour le code, `tests/` pour les tests, `docs/` pour les documents de travail.
- **Langue** : documents en français ; code, noms de variables et messages de commit en anglais.
- **Données de démo** : club fictif « FC Côte d'Azur », stade fictif de 4 tribunes, 5 matchs. Aucune donnée réelle.
- **Commits** : un commit au minimum en fin de journée, avec un message qui dit ce qui a changé.
