# Règles du WAF de cette app

Ce dossier décrit le WAF Caddy + Coraza qui protège l'app. Il est construit par Coolify à chaque merge qui le touche, à partir de l'image `ghcr.io/incubateur-ademe/waf-base`, qui vérifie les règles avant de les servir.

| Fichier | Rôle |
|---|---|
| `Dockerfile` | deux lignes identiques dans chaque repo, à ne pas modifier |
| `waf.yaml` | contacts et zones de rate limit |
| `coraza/config.conf` | niveau de paranoïa, seuil de blocage, méthodes admises |
| `coraza/before.conf` | exclusions conditionnées par un chemin, règles de durcissement |
| `coraza/after.conf` | exclusions de cibles, chargées après la CRS |

Les règles s'écrivent en SecLang, la syntaxe de la doc CRS sur les exclusions, limitée à des formes en liste blanche. Chaque instruction est précédée d'un commentaire qui en donne la raison. Les formes admises et leurs bornes sont dans le design du WAF (section 6) et dans `policy/formes.yaml` de `incubateur-ademe/waf-base`.

Toute modification de ce dossier passe par une PR relue par l'équipe `secops`.

Pour vérifier en local :

```sh
docker build --build-arg WAF_BASE=ghcr.io/incubateur-ademe/waf-base:v1 waf/
```
