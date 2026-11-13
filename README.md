# waf-pilote

Site statique de l'incubateur ADEME, servi par Scalingo, qui sert de pilote au WAF Caddy + Coraza par app et d'exemple aux équipes.

- `public/` : le site, servi par le buildpack Nginx de Scalingo (`nginx.conf`, `Procfile`).
- `waf/` : les règles du WAF de l'app, au contrat commun à toutes les startups (voir `waf/README.md`).
- `.github/CODEOWNERS` : `waf/`, la CODEOWNERS et les fichiers qui pilotent le clone git du build sont relus par l'équipe `secops`.

Le WAF lui-même est construit depuis [`incubateur-ademe/waf-base`](https://github.com/incubateur-ademe/waf-base).
