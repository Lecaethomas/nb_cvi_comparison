# Introduction
Ce rapport a pour but de présenter différentes données, en vue de composer un socle d'OCcupations du Sol (OCS) - orienté vignes - afin de fournir une donnée en vue de spatialiser les ventes de phytopharmaceutiques dans le cadre du projet Pestirives. 
En effet, la méthodologie employée habituellement pour produire la BNVD-s (Lardot, Benjamin, Pierre Cantelaube, Marie Carles, Claire Seard, et Camille Truche. 2022. *Construction d’une base de données géographiques exhaustive à échelle fine sur l’occupation agricole du sol : le RPG complété: Partie 1 : Production de la couche géographique des parcelles susceptibles d’accueillir les surfaces agricoles hors RPG*. HAL CCSD.) n'intègre pas la donnée du Casier Viticole Informatisé (CVI), lequel a été mis à disposition dans le cadre de ce projet afin d'améliorer la base d'OCS.
En effet, si l'occupation du sol utilisée couramment dans la BNVD-s  représente plutôt bien la classe vigne, c'est en grande partie grâce à l'apport de la couche Vigne de la BD Topo de l'Institut Géographique National (IGN), dont la production s'est terminée en 2015 et n'a pas été actualisée depuis.
 
# La donnée

Au regard de l’incomplétude du RPG sur le poste VIGNES et du manque de précision de l’OSO sur cette même classe l’ODR cherche une solution pour gagner en exhaustivité et en précision sur un type de culture primordial pour la compréhension de la répartition des Produits PhytoPharmaceutiques (PPP).
La présente note vise à synthétiser les avantages de cette donnée mais aussi ses limites ainsi que de mettre en exergue les atouts des données auxquelles elle est comparée en vue de composer une couche cohérente, interopérable et reproductible.
Important : Pour des questions de temps de calcul on a restreint les tests sur quatre départements viticoles ayant des caractéristiques différentes. (17 - Charentes-maritimes, 51 - Marne, 68 - Haut-Rhin, 33 – Gironde)

## Le casier Viticole Informatisé (CVI) – Douanes

**Source** : Douanes

**Millésime** : 08/2021

**Format** : table

**Description** : 

-	Le Casier Viticole Informatisé (CVI) est un fichier des douanes qui doit être renseigné par les états membres de l'UE. Il permet de connaître certaines informations pour un ensemble de parcelles cadastrales (géo), connues par leur identifiant « standard ». La plus importante étant que dès lors qu’elle existe dans le CVI on peut considérer qu’elle est en viticulture pour l’année N.
-	Hypothèse : les parcelles représentent celles qui ont été productives, qui ont servies à faire de l’alcool (d’où leur présence dans les données des douanes). Ne seront donc pas présentes les parcelles récemment replantées et non productives (mais qui a priori recevront quand même des traitements (?))

![alt text](supports/exemple_cvi.png "Exemple de parcelle viticole. Sources : IGN - Parcellaire Express (2021/07) | Douanes - Casier Viticole Informatisé (2021/08)")

*Exemple de parcelle viticole en Charente-maritime (17). Sources : IGN - Parcellaire Express (2021/07) | Douanes - Casier Viticole Informatisé (2021/08)*

## Le Parcellaire Express – IGN

**Source** : IGN – DGFiP

**Millésime** : 2021/07

**Format** : vecteur

**Description** :
Donnée de la DGFiP décrivant le parcellaire. Elle nous sert à associer une géométrie au CVI sur la base d’un identifiant de parcelle commun 

## Le Registre Parcellaire Graphique (RPG) – IGN

**Source** : IGN - ASP

**Millésime** : 2021

**Format** : vecteur

**Description** : 
Bien connu, déjà utilisé dans la production de la BNVD-s.
Limité car l’alcool ne donnant pas lieu à des aides de la PAC, les viticulteurs ne déclarent que très peu leurs parcelles.

## BD Topo – IGN

**Source** : IGN

**Millésime** : 2021

**Format** : vecteur

**Description** : 
Utilisé dans la production de la BNVD-s en particulier pour la couche Zone Végétation -> Vignes

## Statistique Agricole Annuelle – Agreste - Ministère de l'Agriculture

**Source** : Agreste

**Millésime** : 2021

**Format** : table

**Description** : 
Donnée tabulaire sans composante spatiale permettant d'avoir un aperçut de différents domaines agricole à l'échelle des territoires. Propose une estimation des surfaces de vignes, ici utilisée comme valeur repère pour comparer l'apport des différentes sources de données.

## OSO -CESBIO

**Source** : CESBIO

**Millésime** : 2021

**Format** : raster

**Description** : 
Produit de télédétection. Ne performe pas toujours sur les surfaces de vignes. Confusion particulière avec les vergers (voir ci-dessous)

![alt text](supports/matrice_oso.png "Matrice de confusion pour OSO 2018 Source : Cesbio" )

*Matrice de confusion pour OSO 2018 Source : Cesbio*
