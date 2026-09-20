# Mod "Économie Complexe" — prototype

## Idée
Casser la prévisibilité linéaire de l'économie de base en ajoutant des **valeurs intermédiaires**
plutôt qu'en éditant directement les stats du jeu (plus sûr, plus facile à débugger).

- **CreditConditions** : le crédit ne se dégrade pas proportionnellement aux taux/dette, il
  s'effondre après un seuil (exposants `^1.6` / `^2.2`) → effet "credit crunch" brutal, pas graduel.
- **EconomicMomentum** : se nourrit de lui-même et du PIB avec une forte inertie → génère des
  cycles boom/bust qui se déclenchent en retard par rapport aux décisions du joueur, plutôt qu'une
  convergence lisse vers un équilibre. C'est le mécanisme qui casse vraiment la prévisibilité.
- **SupplyChainStress** : sketch non activé, à brancher sur une vraie politique (tarifs douaniers,
  etc.) une fois que tu as vérifié le nom exact dans ton `policies.csv`.

## Installation
1. Copie tout le dossier `economie_complexe` dans :
   `Documents\My Games\democracy4\mods\`
2. Lance le jeu → menu des mods → active `Économie Complexe (prototype)`.
3. Lance une nouvelle partie (les mods de simulation ne s'appliquent pas à une partie en cours).

## ⚠️ À vérifier avant de lancer
Les noms `GDP`, `Unemployment`, `Inflation`, `InterestRate`, `Debt` viennent de la doc officielle
et de la mémoire collective des moddeurs, mais Positech a pu changer des noms de colonnes ou de
valeurs depuis. Ouvre ton propre `Democracy 4\data\simulation\simulation.csv` (colonne B = nom
interne) et corrige si besoin — un nom qui ne matche pas ne plante rien, l'effet est juste ignoré
silencieusement, donc si rien ne se passe en jeu, c'est la première chose à checker.

## Pistes pour aller plus loin
- Remplacer `EconomicMomentum` par plusieurs boucles de rétroaction croisées (Inflation ↔ InterestRate
  ↔ CreditConditions) pour des cycles plus riches.
- Utiliser les `overrides` par pays (`data/missions/<pays>/overrides/`) pour tester sans toucher
  au fichier global, pays par pays.
- Utiliser un outil de traçage de courbes (type graphcalc) pour visualiser les équations avant
  de les mettre en jeu — avec des `^`, les surprises sont fréquentes.

## Limite honnête de ce prototype
C'est un point de départ pour tester la mécanique (valeurs intermédiaires + auto-référence +
seuils), pas un rééquilibrage complet et testé de l'économie. Il faudra jouer plusieurs parties
pour caler les coefficients (0.12, 1.6, etc.) — ce sont des ordres de grandeur de départ, pas
des valeurs calibrées.
