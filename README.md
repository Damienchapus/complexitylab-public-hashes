# Complexity Lab — empreintes publiques

Ce dossier ne contient **aucune donnée de recherche**. Il contient des
**empreintes cryptographiques** (SHA-256), publiées pour une seule raison :
prouver qu'un travail existait à une date donnée, sans révéler son contenu.

C'est le principe du pré-enregistrement. Une empreinte ne se remonte pas :
personne ne peut déduire une hypothèse de recherche de sa signature. Mais
l'auteur, lui, peut à tout moment produire le document original et montrer qu'il
donne exactement cette empreinte — ce qui prouve qu'il le détenait avant la
mesure.

> 📏 *Une preuve qu'on détient seul et qu'on peut réécrire ne prouve rien : ce
> qui compte, c'est la date qu'un tiers peut constater.*

## Ce qui est publié ici, et ce qui ne l'est pas

| | |
|---|---|
| ✅ Publié | les empreintes SHA-256, les dates, le nombre de critères de chaque prédiction scellée (annoncés et confrontés) et combien ont été tenus |
| ⛔ **Non** publié | le **titre** et le **contenu** des prédictions, les données de patients, les cohortes, le registre, le code |

Les titres sont volontairement absents. Un titre de pré-enregistrement décrit
l'hypothèse testée : le publier reviendrait à livrer la recherche en cours, ce
que l'empreinte permet justement d'éviter.

## L'état figé

| | |
|---|---|
| Chaîne de hachage | **651 637** maillons |
| Empreinte de tête | `eb4204c78ef07c21a4414a0246bec7c9b4f0e2b9600adec98578d750b82daefd` |
| Prédictions scellées | **41**, dont **40 jugées** (voir `scelles.tsv`) |
| Critères | **181** annoncés · **173** confrontés · **118** tenus · **55** démentis |
| Date de l'état | 2026-10-14T16:55Z |

⚠️ **Deux colonnes de critères, et c'est voulu.** `criteres_annonces` compte tous
les critères scellés ; `criteres_confrontes` ne compte que ceux qui ont reçu un
verdict. Les 8 de différence appartiennent à une prédiction posée dont le calcul
tourne encore. Avec un seul nombre, l'addition ne tombait pas juste : 118 + 55
font 173, pas 181.

> 📏 *Un compteur qui ne dit pas ce qu'il compte flatte celui qui le publie.*

Chaque maillon de la chaîne contient l'empreinte du précédent : modifier une
seule mesure passée invaliderait tous les maillons suivants. La chaîne est
revérifiée à chaque passage de l'outil de contrôle, et elle l'a été à
l'intérieur de chaque copie de sauvegarde.

## Les scellés d'antériorité du 14/10/2026

Il y en a deux, et ils s'additionnent — une pièce ne remplace jamais la
précédente.

**Celle de 00 h 23 UTC, ancrée dans Bitcoin :**

| | |
|---|---|
| Fichiers couverts | 242 (1 703 016 278 octets) |
| **Empreinte racine du contenu** | `397d0deb03105c8d7d3813924bb33a51abd98ede35a91ea92c4167b552f81094` |
| Empreinte de la pièce soumise | `14752a5d35a379b39904d0c440ecd8c6f03e627037bf08df612f3780847d8dcc` |
| État du code | commit git `4d6bad805350335d6b2520b178f9be148f01d742` |
| Bitcoin | **ancrée** · 4 calendriers sur 4 · blocs 971 315, 971 319, 971 354, 971 357 |

⚠️ Cette pièce fige un **chantier en cours**, et c'est voulu : à la seconde
où elle a été scellée, la prédiction n°32 était posée mais pas encore jugée
(son verdict, 5 critères tenus sur 6, est depuis inscrit au registre). Un
scellé d'antériorité prouve qu'un texte existait à une date ; il ne prouve
pas que le travail était fini, et il ne permet pas d'en choisir l'issue
après coup — les critères étaient écrits dans le texte scellé, avec leur
sens et leur seuil.

> 📏 *Une preuve de date n'est pas une preuve d'achèvement.*

**Celle de 07 h 55 UTC, soumise le même jour :**

| | |
|---|---|
| Fichiers couverts | 253 (1 830 395 Ko environ, 1 745,7 Mo) |
| **Empreinte racine du contenu** | `04d03caa28f19cd9e891789a1a870e2587c179e12a89eb78539fafe9cb652619` |
| Empreinte de la pièce soumise | `e3660383a9e269b76861f2e41b978bffa018e54da898cd1c39365317dbaf1d6f` |
| Bitcoin | soumise aux 4 calendriers · **pas encore mûre** |

Méthode : SHA-256 de chaque fichier, puis les lignes `<sha256> <octets> <chemin>`
triées par chemin et jointes — l'empreinte racine est le SHA-256 de cet ensemble.
Elle est donc recalculable par quiconque détient les mêmes fichiers.

### Horodatage par la chaîne Bitcoin

L'empreinte de la pièce a été soumise à **quatre calendriers OpenTimestamps
indépendants**, qui l'agrègent puis l'inscrivent dans une transaction Bitcoin :

- `a.pool.opentimestamps.org`
- `b.pool.opentimestamps.org`
- `a.pool.eternitywall.com`
- `ots.btc.catallaxy.com`

Les quatre ont accusé réception (4 reçus sur 4, aucun échec). **Seule
l'empreinte a quitté la machine — jamais un fichier.**

Les calendriers agrègent les demandes avant de les inscrire dans un bloc ;
l'opération prend de quelques heures à quelques jours. **La pièce de 00 h 23
est désormais mûre** : ses quatre attestations ont été récoltées, blocs
971 315, 971 319, 971 354 et 971 357. Les deux pièces du 11/10/2026 le sont
également (bloc 971 087). Celle de 07 h 55 ne l'est pas encore, et tant
qu'elle ne l'est pas, elle est *soumise*, pas *prouvée* — c'est écrit ici
plutôt que supposé.

## Ce qui a changé depuis la première publication

Ce dépôt a été publié le 14/10/2026 avec 32 prédictions. Il en porte **41**
le même jour : neuf de plus en une journée, dont les premières mesures de ce
laboratoire sur une **issue clinique** (réponse à un traitement, survie) et
plusieurs **démentis** — dont un qui retire les trois quarts de la portée du
résultat le plus cité, et un autre qui montre qu'une correction d'un biais
réel **dégrade** le classement.

Le détail de chaque prédiction, son titre et son verdict critère par critère
sont sur <https://complexity-lab.org/anteriorite.html>. Ici ne figurent que
les empreintes : elles prouvent les dates, pas les conclusions.

## Vérifier soi-même

```bash
# L'empreinte d'une pièce d'antériorité
sha256sum anteriorite-20261013-222345.txt
# -> 14752a5d35a379b39904d0c440ecd8c6f03e627037bf08df612f3780847d8dcc

# L'attestation OpenTimestamps (outil `ots`) : elle nomme le bloc Bitcoin
ots verify anteriorite-20261013-222345.txt.ots
```

## Le taux de réussite n'est pas publié ici, et c'est volontaire

`scelles.tsv` donne, pour chaque prédiction, le nombre de critères posés et le
nombre tenus. Le total s'en déduit — mais il dépend de conventions de comptage
(que fait-on d'un critère « mal posé », d'une prédiction partiellement
vérifiée ?). Deux comptages indépendants du même registre ont donné des totaux
différents le 14/10/2026 — l'un d'eux lisait les verdicts dans une forme de
maillon que le registre n'écrit plus, et rendait « rien » au lieu de « je ne
sais pas lire ça ». Le chiffre agrégé est donc publié sur
<https://complexity-lab.org>, avec sa définition, et recalculé automatiquement
à partir du registre — pas recopié à la main ici.

> 📏 *Un compteur qui ne dit pas ce qu'il compte flatte celui qui le publie.*

## Ce que ces empreintes ne prouvent pas

- Elles ne prouvent **pas** qu'un résultat est juste. Elles prouvent qu'une
  prédiction a été écrite **avant** d'être confrontée à la mesure.
- Elles ne prouvent **pas** une invention, ni n'en réservent la propriété.
- Une empreinte prouve un **contenu**. La **date** devient opposable grâce au
  dépôt hors du poste de travail — c'est le rôle de l'ancrage Bitcoin ci-dessus.

---

*Complexity Lab — Damien Chapus (EI). Les sources de données externes utilisées
par ce laboratoire, leurs licences et leurs limites sont documentées
publiquement sur <https://complexity-lab.org>.*
