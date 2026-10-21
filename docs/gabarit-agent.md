# Gabarit de définition d'agent

Chaque agent est un fichier Markdown placé dans `.claude/agents/`. L'en-tête (entre les deux lignes `---`) est lu par la machine ; le corps est lu par l'agent lui-même.

Le champ `description` est décisif : c'est lui qui dit à l'orchestrateur quand appeler cet agent, et quand ne pas l'appeler.

## Le gabarit

Copie ce bloc dans un nouveau fichier `.claude/agents/<nom>.md`, puis remplace chaque `<…>`.

```markdown
---
name: <identifiant-court, en minuscules, avec des tirets>
description: <Quand utiliser cet agent, en une phrase. Commence par « Utiliser quand… »>
tools: <liste minimale des outils autorisés, par exemple Read, Grep, Write>
---

# Rôle
<Qui tu es et la seule responsabilité que tu portes.>

# Entrées
<Les fichiers que tu lis, et rien d'autre.>

# Sorties
<Le ou les fichiers que tu produis, leur emplacement et leur structure exacte.>

# Procédure
<Les étapes, dans l'ordre.>

# Interdits
<Ce que tu ne fais jamais, même si cela semble utile.>

# Condition d'arrêt
<Le critère vérifiable qui dit que ton travail est terminé.>

# En cas de blocage
<Ce que tu écris, et à qui tu rends la main.>
```

## Ce que vérifie chaque champ

| Champ | Question à se poser | Défaut typique |
| --- | --- | --- |
| description | L'orchestrateur saura-t-il quand m'appeler, et quand ne pas m'appeler ? | Trop vague : l'agent est appelé à tort |
| tools | Ai-je besoin de chacun de ces outils ? | Trop d'outils : l'agent sort de son rôle |
| Rôle | Une seule responsabilité ? | Deux métiers dans un seul agent |
| Sorties | Un autre agent peut-il lire ce fichier sans me demander ? | Format libre : le relais casse |
| Interdits | Quelle tentation naturelle dois-je bloquer ? | Absent : l'agent « rend service » hors périmètre |
| Condition d'arrêt | Un tiers peut-il vérifier que c'est fini ? | « Quand c'est bien » : jamais vérifiable |

## Outils courants

| Outil | Ce qu'il permet |
| --- | --- |
| Read | Lire un fichier |
| Grep, Glob | Chercher dans les fichiers |
| Write | Créer ou remplacer un fichier |
| Edit | Modifier une partie d'un fichier |
| Bash | Exécuter des commandes (lancer l'application, les tests) |

Règle du moindre privilège : un agent qui n'a pas besoin d'écrire n'a ni Write ni Edit ; un agent qui n'a pas besoin d'exécuter n'a pas Bash. Attention, Bash permet aussi d'écrire des fichiers : le retirer à un agent censé rester en lecture seule.
