# TP1 — Cadrage du projet

**Équipe : Zakaria Ben Mohamed, Aziz Sdiri, Feryel Ben Yahia**
**Classe : 3 BIS 2**
**Sujet 18 — Tournoi de football inter-facultés : classement** (dossier `tournoi-football/`)

> Les références P1 à P12 renvoient aux phrases de la demande client listées ci-dessous.

## 0. Référentiel de la demande client

- **Contexte** : association sportive d'une université ; 12 équipes de facultés, 6 arbitres bénévoles, 1 responsable du tournoi.
- **P1** — L'an dernier, le classement tenu à la main a été contesté deux fois.
- **P2** — L'association veut un site pour suivre le tournoi.
- **P3** — Les arbitres doivent saisir les résultats des matchs.
- **P4** — Le responsable du tournoi doit gérer les équipes et le calendrier.
- **P5** — Les capitaines veulent savoir quels joueurs ils peuvent aligner.
- **P6** — Les supporters veulent voir le classement en direct.
- **P7** — Le classement doit être calculé automatiquement.
- **P8** — Le classement doit être juste, même quand une équipe est sanctionnée.
- **P9** — Il faut sanctionner les équipes qui ne viennent pas et les joueurs violents.
- **P10** — Les capitaines veulent qu'à égalité, le match entre les deux équipes décide.
- **P11** — L'arbitre principal trouve plus juste de regarder la différence de buts sur tout le tournoi.
- **P12** — Le site doit être simple et toujours à jour.

---

## 1. Vision

### Q1 — Problème métier

> Le classement du tournoi, tenu manuellement, n'est pas fiable (il a été contesté deux fois l'an dernier) et ne permet pas de suivre facilement et de façon juste l'avancement du tournoi.

**Phrase de la demande qui décrit déjà une solution :** P2, « Elle veut un site pour suivre le tournoi ». C'est une solution (un site), pas le problème métier.

### Q2 — Parties prenantes

| Partie prenante | Statut | Attente / intérêt |
| --- | --- | --- |
| Association sportive (client) | Explicite | Organiser et suivre le tournoi avec un classement fiable |
| Responsable du tournoi | Explicite | Gérer les équipes et le calendrier |
| Arbitres bénévoles (6) | Explicite | Saisir les résultats des matchs |
| Arbitre principal | Explicite | Défendre la différence de buts sur tout le tournoi (rôle exact à préciser) |
| Capitaines | Explicite | Connaître les joueurs qu'ils peuvent aligner ; départage par le match direct |
| Supporters | Explicite | Consulter le classement en direct |
| Équipes de facultés (12) | Explicite | Être classées de façon juste, même en cas de sanction |
| Joueurs | Non citée, concernée | Concernés par leur éligibilité et par les sanctions |
| Service informatique de l'université | Non citée, potentielle | Hébergement et maintenance éventuels (à valider) |

### Q3 — Objectifs

| ID | Objectif |
| --- | --- |
| **OBJ-01** | Réduire le nombre de contestations du classement de **2** (l'an dernier, donné par le client) à **[à valider]** d'ici **[à valider]**. |
| **OBJ-02** | Réduire le délai entre la saisie d'un résultat et son affichage dans le classement de **[à valider]** à **[à valider]** d'ici **[à valider]**. |

### Q4 — Objectif difficile à mesurer

Le plus difficile à mesurer est **« classement juste »** (P8) : « juste » est subjectif, et le client est en désaccord avec lui-même sur la règle de départage (P10 contre P11). Il faut d'abord que le client tranche la règle, puis choisir un indicateur (nombre de contestations, nombre de corrections du classement) et une cible avec lui.

« Simple » et « toujours à jour » (P12) sont aussi flous : il faut demander le délai maximal acceptable et des critères de simplicité (voir Q9).

---

## 2. Périmètre

### Q5 — Tableau connu / inconnu

| Élément | Catégorie | Source ou « à valider » |
| --- | --- | --- |
| Saisir les résultats des matchs | Dans le périmètre | P3 |
| Gérer les équipes | Dans le périmètre, à préciser (« gérer » ambigu) | P4 |
| Gérer le calendrier | Dans le périmètre, à préciser (« gérer » ambigu) | P4 |
| Consulter les joueurs alignables | Dans le périmètre, à préciser (règles d'éligibilité non données) | P5 |
| Afficher le classement | Dans le périmètre | P6 |
| Calculer automatiquement le classement | Dans le périmètre | P7 |
| Sanctionner une équipe absente | Dans le périmètre, à préciser (« sanction » non définie) | P9 |
| Sanctionner un joueur violent | Dans le périmètre, à préciser (« violent » et « sanction » non définis) | P9 |
| 12 équipes | Contrainte | Contexte |
| 6 arbitres bénévoles | Contrainte | Contexte |
| Classement « en direct » / site « toujours à jour » | Contrainte, à préciser (délai non défini) | P6, P12 |
| Site « simple » | Contrainte, à préciser (non mesurable) | P12 |
| Règle de départage (face-à-face ou différence de buts) | **Point ouvert** (contradiction) | P10 et P11 |
| Égalité de trois équipes ou plus | **Point ouvert** | à valider |
| Format du tournoi (championnat, poules, élimination) | **Point ouvert** | à valider |
| Points par victoire, nul, défaite | **Point ouvert** | à valider |
| Type et valeur des sanctions, qui sanctionne, durée de suspension | **Point ouvert** | à valider |
| Conditions pour aligner un joueur | **Point ouvert** | à valider |
| Connexion des utilisateurs (authentification) | **Point ouvert** | à valider |
| Modification et validation d'un résultat saisi | **Point ouvert** | à valider |
| Chaque équipe a un capitaine identifié | **Hypothèse** (donc aussi point ouvert) | à valider |
| Chaque match oppose deux équipes et a un résultat | **Hypothèse** (donc aussi point ouvert) | à valider |
| Les supporters consultent le classement sans compte | **Hypothèse** (donc aussi point ouvert) | à valider |
| Les joueurs sont enregistrés dans le système | **Hypothèse** (donc aussi point ouvert : qui les enregistre ?) | à valider |

### Q6 — Hors périmètre

- **Hors périmètre : la gestion de tournois d'autres sports.** La demande parle d'« un tournoi de football entre les facultés ».
- **Point ouvert : la billetterie / vente de billets.** Aucune information de la demande ne permet de la justifier ni de l'exclure avec certitude.

---

## 3. Exigences

### Q7 — Tableau des exigences

| ID | Exigence | Type | Source |
| --- | --- | --- | --- |
| REQ-F-01 | Le système doit permettre à un arbitre de saisir le résultat d'un match. | F | P3 |
| REQ-F-02 | Le système doit calculer automatiquement le classement. | F | P7 |
| REQ-F-03 | Le système doit permettre à un supporter de consulter le classement. | F | P6 |
| REQ-F-04 | Le système doit permettre à un capitaine de consulter les joueurs qu'il peut aligner [règles d'éligibilité à valider]. | F | P5 |
| REQ-NF-01 | Le système doit afficher le classement à jour [délai maximum à valider]. | NF | P12 (et P6 « en direct ») |
| REQ-NF-02 | Le système doit être simple à utiliser [indicateur et cible à valider]. | NF | P12 |

**Volontairement non rédigées (points ouverts)** : gestion des équipes et du calendrier (« gérer » ambigu), sanctions (« sanction » non définie), départage (contradiction du client).

### Q8 — Critique d'exigences

#### a) Les deux exigences de l'autre équipe (cas de la réservation de salles)

**REQ-F-06 — « Le système doit permettre à l'administration de gérer les salles. »**
- *Problème :* « gérer » est ambigu (ajouter, modifier, supprimer, rendre indisponible…).
- *Point ouvert :* « Quelles opérations l'administration doit-elle pouvoir effectuer sur les salles ? »

**REQ-NF-02 — « L'application doit être accessible depuis un ordinateur et un smartphone. »**
- *Problèmes :* la demande dit « ordinateur **ou** téléphone », pas « et » ; « smartphone » remplace « téléphone » ; la phrase ne commence pas par « Le système doit… ».
- *Version corrigée :* « Le système doit être accessible depuis un ordinateur ou un téléphone. »
- *Point ouvert :* « Les deux types d'appareils sont-ils nécessaires, ou l'un des deux suffit-il ? »

#### b) Même critique appliquée à notre sujet (tournoi)

**« Le système doit permettre au responsable du tournoi de gérer les équipes et le calendrier. » (P4)**
- *Problèmes :* « gérer » est ambigu (ajouter, modifier, supprimer, reporter, annuler ?) et l'exigence contient **deux idées** (équipes et calendrier), donc elle n'est pas atomique.
- *Correction :* la séparer en deux exigences, chacune avec ses opérations une fois connues.
- *Point ouvert :* « Quelles opérations exactes le responsable doit-il pouvoir faire sur les équipes, et sur le calendrier ? »

**« Le système doit sanctionner les équipes qui ne viennent pas et les joueurs violents. » (P9)**
- *Problèmes :* « sanctionner » n'est pas défini (forfait, points retirés, suspension ?) ; « violents » n'est pas défini ; deux idées (équipes et joueurs) ; on ne sait pas qui sanctionne ; non vérifiable en l'état.
- *Correction :* séparer sanction d'équipe et sanction de joueur, et ne les rédiger qu'après les réponses du client.
- *Points ouverts :* « Quelle sanction pour une équipe absente ? Qu'est-ce qu'un joueur violent, quelle sanction, qui la décide ? »

### Q9 — « Simple à utiliser »

Non vérifiable : « simple » est subjectif et sans indicateur. Questions au client, sans inventer de valeur :
- Quel temps maximum pour saisir un résultat ou consulter le classement ?
- Combien d'étapes maximum ?
- Le site doit-il être utilisable sans formation (arbitres bénévoles) ?
- Quel critère de réussite lors d'un test avec de vrais utilisateurs ?

Même démarche pour « toujours à jour » : quel délai maximal entre la saisie d'un résultat et la mise à jour du classement ?

---

## 4. Analyse IA

*Prompt du TP1 appliqué à la demande de notre sujet (tournoi) : « Analyse cette demande client pour un tournoi de football inter-facultés. Identifie les ambiguïtés, les informations manquantes et les questions qui devraient être posées au client. N'invente pas de nouvelles exigences. » La réponse de l'IA a été analysée **après** notre propre analyse (parties 1 à 3).*

### Q10 — Tableau de classement

| N° | Proposition IA | Décision | Justification |
| --- | --- | --- | --- |
| 1 | La règle de départage est contradictoire : face-à-face (capitaines) ou différence de buts (arbitre principal) ; il faut trancher et fixer l'ordre des critères. | **Acceptée** | Contradiction explicite entre P10 et P11. |
| 2 | Que faire en cas d'égalité entre trois équipes ou plus ? | **À valider** | Plausible mais absent de la demande : point ouvert. |
| 3 | « Sanctionner » n'est pas défini (forfait, points retirés, suspension) et on ne sait pas qui sanctionne. | **Acceptée** | Ambiguïté directement présente dans P9. |
| 4 | « Équipes qui ne viennent pas » et « joueurs violents » ne sont pas définis (retard toléré ? effectif minimum ? quels faits ?). | **Acceptée** | Termes vagues présents dans P9. |
| 5 | « Gérer les équipes et le calendrier » est ambigu. | **Acceptée** | Ambiguïté du mot « gérer » dans P4. |
| 6 | « Simple » et « toujours à jour » ne sont pas mesurables. | **Acceptée** | Problème réel de P12 ; indicateurs à définir avec le client. |
| 7 | Combien de points pour une victoire, un nul, une défaite ? | **À valider** | Nécessaire au calcul (P7) mais non précisé : point ouvert. |
| 8 | Quelles règles d'éligibilité pour aligner un joueur ? | **À valider** | P5 ne donne aucune règle : point ouvert. |
| 9 | Authentification : qui doit se connecter (arbitres, capitaines, responsable) ? | **À valider** | La demande n'en parle pas : point ouvert. |
| 10 | Envoyer des notifications SMS/e-mail aux supporters après chaque match. | **Rejetée** | Fonction inventée, aucune phrase de la demande ne la soutient. |
| 11 | Développer une application mobile native iOS/Android pour les supporters. | **Rejetée** | Choix technique non demandé (P2 parle d'un site). |
| 12 | Prévoir une billetterie en ligne pour les matchs. | **Rejetée** | Aucun support dans la demande. |

### Q11 — Proposition plausible mais inventée

**Proposition n°10 : notifications SMS/e-mail aux supporters après chaque match.** Elle est convaincante car courante et utile en apparence pour des supporters qui veulent suivre le tournoi. Elle est dangereuse si acceptée sans vérification : elle élargit le périmètre sans accord du client (P6 demande seulement de *voir* le classement), ajoute de l'infrastructure (envoi de messages, gestion des abonnés), des règles et des tests. Elle peut au mieux devenir une question au client.

### Q12 — Ambiguïté relevée par l'IA

Oui. L'IA a relevé que « les équipes qui ne viennent pas » (proposition n°4) n'est pas défini : retard toléré ? nombre minimum de joueurs pour que l'équipe soit considérée présente ? Nous avions vu que « sanction » n'était pas défini, mais pas que l'absence elle-même devait être définie.

Nous en retenons une question pour le client : « Qu'appelez-vous une équipe qui ne vient pas (retard toléré, effectif minimum) ? »

---

## 5. Traçabilité

| Besoin métier | Objectif | Exigence | Source |
| --- | --- | --- | --- |
| Éviter les contestations | OBJ-01 | REQ-F-02 : calcul automatique du classement | P7 |
| Suivre les matchs | OBJ-02 | REQ-F-01 : saisie des résultats | P3 |
| Avoir un classement actualisé | OBJ-02 | REQ-NF-01 : classement à jour | P6, P12 |
| Suivre le classement | OBJ-02 | REQ-F-03 : consultation par le supporter | P6 |
| Savoir quels joueurs aligner | (à valider avec le client) | REQ-F-04 | P5 |
