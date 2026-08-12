# Gestion ALM d’un fonds de pension fermé

Travail dirigé — M. Sc. Finance mathématique et computationnelle  
Université de Montréal — sous la direction du Pr Fabian Bastin  
Auteur : Louckmane Alma Mousbahou

## Contenu

| Fichier | Rôle |
|---|---|
| `alm_pension_julia.ipynb` | Notebook Julia (phases 1–6 + 6 bis) |
| `td_alm_squelette.tex` | Source LaTeX du rapport |
| `travail_dirige.pdf` | Rapport compilé |
| `Project.toml` / `Manifest.toml` | Environnement Julia figé |
| `prix_ajustes_cache.csv` | Cache de prix (données gelées au 2026-06-30) |
| `prix_vsp_cache.csv` | Cache VSP (diagnostic de change) |
| `comparaison_benchmarks.pdf` | Figure du § résultats (vectorielle, incluse par pdflatex) |

## Reproduire les résultats

**Prérequis** : Julia 1.12.x

```bash
git clone https://github.com/Louckmane10/Gestion_ALM.git
cd Gestion_ALM
julia --project=. -e 'using Pkg; Pkg.instantiate()'
# Ouvrir alm_pension_julia.ipynb (IJulia) et « Run All »
# ou : julia --project=.  # puis inclure les cellules
```

La première cellule active l’environnement du projet et charge les paquets.
Les caches CSV évitent tout téléchargement Yahoo (re-normalisation rétroactive des cours ajustés).

**Reproductibilité** : générateur explicite `Random.Xoshiro` + graines documentées.
Cela reproduit l’*instance discrétisée* (arbre de scénarios), non la valeur optimale continue \(v^\star\) — voir le § biais Monte Carlo / SAA du rapport.

## Compilation du rapport

```bash
pdflatex td_alm_squelette.tex
pdflatex td_alm_squelette.tex
```

## Licence

Voir `LICENSE`.
