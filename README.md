# DRIAS - Projections climatiques quotidiennes MULTI MODELES
## Calcul d'indicateur et de sa médiane multi modèles pour la moyenne des mailles choisies
https://github.com/loicduffar/

<b>Champ d'application de cette version du code:</b>
- indicateurs calculés : uniquement les quantiles de valeurs mensuelles et annuelles, pour apprécier la variabilité inter annuelle de 5 paramètres possibles.
- Les paramètres traités à ce jour sont: précipitations totales, températures (moy, min et max) et ETP Hargreaves-
- métropole uniquement: A termes les données DRIAS des DROM-COM pourront être traitées, pour la Réunion et les Antilles notamment (en attendant, la version mono modèle de ce code répond partiellement au besoin, car les données des DROM-COM inclent un modèle unique).

<b>Principe du code:</b>
- La version actuelle du script calcule à partir des données quotidiennes DRIAS la distribution de fréquence (quantiles) des valeurs mensuelles et annuelles, d'une part pour la référence 1976-2005 et d'autre part pour chacun des 3 horizons standards DRIAS 2021-2050, 2041-2070 et 2071-2100.
- L'indicateur est calculé ...
    - ... à chaque run pour un paramètre unique et un scénario unique, (et un unique indicateur est prévu pour chaque paramètre à ce jour)
    - ...sur la moyenne des points de maille définis par l'utilisateur par leur numéro DRIAS (à charge pour l'utilisateur d'en faire une liste car ce code ne gère pas les coordonnées géographiques dans le soucis de limiter l'effort de programmation),
    - ...pour la médiane de tous les modèles fournis par l'utilisateur (12 en principe),
    - ... avec une agrégation mensuelle et annuelle, adaptée automatiquement à la nature de chacun des 5 paramètres possibles: somme (précipitation, ETP),  moyenne, minimum ou maximum (température moyenne, min ou max quotidienne)
 
<b>Etapes à suivre par l'utilisateur:</b>
- 1. Télécharger les fichiers quotidiens sur le <a href="/media/examples/link-element-example.css"> site DRIAS</a> (voir ci-dessous les caractéristiques obligatoires des fichiers)
- 2. Stocker dans un même dossier tous les fichiers des différents modèles (12 en principe) et différents scénarios à traiter pour la zone géographique voulue
- 3. Faire tourner le code après avoir renseigné les options à personaliser (dossier, nom de fichier, paramètre climatique voulu, points de maille voulus etc...).
- 4. Les résultats sont stockés dans un fichier Excel

<b>Contraintes de téléchargement des données:</b>

<font color="red"> L'ergonomie du portail DRIAS impose un long processus de téléchargement de très nombreux fichiers</font><br>
En effet, pour une certaine étendue spatiale et pour chacun des 12 modèles, il est nécessaire de télécharger individuellement 1 fichier historique 1950-2005 et 1 fichier pour chaque scénario futur. Pour 12 modèles, cela fait donc 24 fichiers nécessaires pour un scénario unique et 36 pour 2 scénarios ! De plus, le portail impose un nombre maximum de lignes pour chaque fichier,  ce qui qui limite le choix de téléchargement en termes de nombre de paramètres et d'étendue spatiale . Pour 5 paramètres par exemple (précipitations, température moy/max/min, ETP), chaque fichier ne peut excéder l'étendue approximative d'un département français.

Les options de téléchargement suivantes doivent être respectées strictement:
- format CSV (en réalité extension TXT)
- séparateur point virgule
- Date sur 1 seul champ &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(et non dans plusieurs champs jour, mois et année) 
- champ idPoint &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(pour identifier les mailles voulues)
- champ Flag_terre&emsp;&emsp;&emsp;&emsp;(pour l'outre mer uniquement, car les fichiers contiennent également l'océan pour chaque archipel des Antilles ou du Pacifique)
- Chaque fichiers peut contenir des points multiples et des paramètres multiples, en s'assurant que les différents fichiers ont en commun les mêmes paramètres et points voulus ainsi que l'unité. DE PLUS le nombre de lignes d'entête doit également être commun à tous les fichiers, ce qui n'est pas le cas pour certains modèles dont il faut supprimer ou ajouter quelques lignes d'entête à la main à l'aide d'un éditeur de texte.
- NB: Le traitement utilise le nom de modèle présent dans le nom des fichiers, ainsi que le nom de scénario ou le mot 'Historical'.

<img src="https://github.com/loicduffar/DRIAS_Processing-of-daily-Climate-Change-data-in-France/blob/main/out/DRIAS%20Quantiles%20annuels%20(m%C3%A9diane%20des%20mod%C3%A8les).png" width="40%"></img>
<img src="https://github.com/loicduffar/DRIAS_Processing-of-daily-Climate-Change-data-in-France/blob/main/out/DRIAS%20Evolution%20de%20la%20valeur%20annuelle.png" width="40%"></img>
<img src="https://github.com/loicduffar/DRIAS_Processing-of-daily-Climate-Change-data-in-France/blob/main/out/Distribution%20de%20fr%C3%A9quence%20de%20la%20valeur%20annuelle%20pour%20tous%20les%20mod%C3%A8les.png" width="40%"></img>
