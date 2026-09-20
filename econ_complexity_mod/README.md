# Mod "Économie Complexe" — prototype

## Idée
Casser la prévisibilité linéaire de l'économie de base en ajoutant des **valeurs intermédiaires**
plutôt qu'en éditant directement les stats du jeu (plus sûr, plus facile à débugger).

- **CreditConditions** : le crédit ne se dégrade pas proportionnellement à la dette, il s'effondre
  après un seuil (`_effectivedebt_` à la puissance `2.2`) → effet "credit crunch" brutal, pas
  graduel. `BusinessConfidence` (objet réel, ligne 10 de ton `simulation.csv`) amortit un peu le choc.
- **EconomicMomentum** : se nourrit de lui-même et du PIB avec une forte inertie → génère des
  cycles boom/bust qui se déclenchent en retard par rapport aux décisions du joueur, plutôt qu'une
  convergence lisse vers un équilibre. C'est le mécanisme qui casse vraiment la prévisibilité.
- **SupplyChainStress** : branché sur `ImportTarrifs` (le jeu orthographie "Tarrifs" avec deux r —
  ce n'est pas une coquille de ma part) et `Technology`. Monter les tarifs augmente le stress
  logistique de façon non-linéaire (`^1.8` : un petit tarif ne fait presque rien, un gros tarif
  fait très mal), la technologie l'atténue. Ce stress remonte ensuite dans l'inflation et le PIB.
- Un branchement optionnel (`_effectivedebt_` → EconomicMomentum) est présent mais **désactivé
  par défaut** dans le CSV, à activer une fois que tu as testé la version de base.

## ✅ Noms d'objets vérifiés
À partir des `policies.csv` et `simulation.csv` que tu as fournis, tous les noms utilisés dans ce
mod sont confirmés réels : `GDP`, `Unemployment`, `Inflation`, `Technology`, `BusinessConfidence`,
`ImportTarrifs`, et la variable spéciale `_effectivedebt_`. Plus rien à deviner — ce prototype
devrait se charger et produire un effet dès la première partie.

## Installation
1. Copie tout le dossier `economie_complexe` dans :
   `Documents\My Games\democracy4\mods\`
2. Lance le jeu → menu des mods → active `Économie Complexe (prototype)`.
3. Lance une nouvelle partie (les mods de simulation ne s'appliquent pas à une partie en cours).

## Pistes pour aller plus loin
- Remplacer `EconomicMomentum` par plusieurs boucles de rétroaction croisées (Inflation ↔
  BusinessConfidence ↔ CreditConditions) pour des cycles plus riches.
- Utiliser les `overrides` par pays (`data/missions/<pays>/overrides/`) pour tester sans toucher
  au fichier global, pays par pays.
- Utiliser un outil de traçage de courbes (type graphcalc) pour visualiser les équations avant
  de les mettre en jeu — avec des `^`, les surprises sont fréquentes.

## Limite honnête de ce prototype
C'est un point de départ pour tester la mécanique (valeurs intermédiaires + auto-référence +
seuils), pas un rééquilibrage complet et testé de l'économie. Il faudra jouer plusieurs parties
pour caler les coefficients (0.12, 1.6, etc.) — ce sont des ordres de grandeur de départ, pas
des valeurs calibrées.
