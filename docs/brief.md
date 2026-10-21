# Brief projet — TicketFoot

TicketFoot vend en ligne des billets pour les matchs d'un club fictif, le FC Côte d'Azur, dans un stade fictif de 4 tribunes.

Ce brief est volontairement incomplet. Il doit être transformé en spécification exploitable avant toute conception technique.

## Périmètre fonctionnel

| Bloc | Ce que l'utilisateur peut faire | Jour visé |
| --- | --- | --- |
| Catalogue | Voir les matchs à venir, la date, l'adversaire, les tribunes et les prix | J3 |
| Plan du stade | Choisir une tribune puis des sièges précis sur un plan | J4 |
| Panier et blocage | Bloquer jusqu'à 6 sièges pendant 10 minutes | J6 |
| Paiement | Valider la commande sur un écran de paiement fictif, qui permet de choisir « paiement accepté » ou « paiement refusé » | J9 |
| Billet | Recevoir un billet PDF avec QR code unique par siège | J9 |
| Back-office | Créer un match, fixer les prix par tribune, voir les ventes | J9 |
| Documentation | Guide utilisateur et guide du back-office | J10 |

## Règles de gestion

1. Un siège ne peut jamais être vendu deux fois, même si deux personnes valident au même instant.
2. Un siège bloqué et non payé redevient libre après 10 minutes.
3. Une commande est limitée à 6 sièges par match.
4. Un QR code identifie un seul siège pour un seul match et ne peut pas être deviné.
5. Un client ne peut voir que ses propres commandes.

## Contraintes

- La stack est imposée (voir `CLAUDE.md`).
- L'application se lance avec une seule commande.
- Les données de démo (club, stade, 5 matchs) sont générées par les agents.

## Hors périmètre

Comptes multi-rôles avancés, revente entre supporters, application mobile, mise en production réelle.
