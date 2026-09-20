# d4-mod-test

# Installer le mod "Économie Complexe" (Democracy 4)

## 1. Dézipper
Dézippe `economie_complexe_mod.zip`. Tu dois obtenir un dossier nommé `economie_complexe`
contenant directement `config.txt`, `README.md`, `data/` et `svg/` (pas un sous-dossier en plus).

## 2. Placer le dossier
Copie le dossier `economie_complexe` dans :
```
Documents\My Games\democracy4\mods\
```
Si le dossier `mods` n'existe pas encore, crée-le.

## 3. Activer le mod
1. Lance Democracy 4.
2. Au menu principal, va dans l'onglet des mods.
3. Active `Économie Complexe (prototype)`.

## 4. Lancer une nouvelle partie
Les mods qui touchent la simulation ne s'appliquent **pas** à une partie déjà en cours.
Il faut démarrer une nouvelle partie pour que les nouvelles valeurs économiques soient chargées.

## Problèmes fréquents
- **Le mod n'apparaît pas dans la liste** → vérifie que `config.txt` est bien à la racine du
  dossier `economie_complexe`, pas dans un sous-dossier créé par le dézippage.
- **Rien ne change en jeu** → ouvre ton `Democracy 4\data\simulation\simulation.csv` et compare
  les noms `GDP`, `Unemployment`, `Inflation`, `InterestRate`, `Debt` (colonne B) avec ceux utilisés
  dans le mod ; un nom qui ne correspond pas fait que l'effet est ignoré silencieusement.
