# Schéma des défibrillateurs
Ce schéma permet de modéliser les différents attributs des défibrillateurs 

## Contexte

Il existe un besoin d'harmonisation de la publication en open data de données essentielles produites par les administrations publiques wallonnes. En septembre 2023, plus de 700 jeux de données sont publiés sur le portail [Open Data Wallonie Bruxelles (ODWB)](https://www.odwb.be/explore/?sort=modified), qui sont très hétérogènes. 

Constatant la production de jeux de données disparates à l'échelle de la fédération Wallonie-Bruxelles, FuturoCité a réuni, dans le cadre d'un groupe de travail sollicité depuis mai 2021, une vingtaine de collectivités. La concertation de celles-ci a permis 1) d'identifier collectivement des jeux de données jugés prioritaires et 2) de s'accorder sur des spécifications des modèles de données. 
La standardisation de ces données prioritaires est en effet essentielle pour s'assurer de leur publication homogène et de faciliter leur exploitation (notamment leur agrégation) par les réutilisateurs. Elle facilitent l'exploitation des données publiées par les réutilisateurs (agrégation, consolidation et traitements automatiques).

## Construction du schéma de données 

Les membres du groupe de travail ont défini un schéma de données qui décrit le format des fichiers, les différents champs, les valeurs possibles… Ils se sont appuyés sur un état des lieux du patrimoine de données des collectivités wallonnes et sur une étude des modèles utilisés par des collectivités déjà productrices de ces données (notamment Liège et Namur), en prenant en compte les retours faits par les réutilisateurs de données. 

## Description du schéma

Un [gabarit au format tableur](https://github.com/FuturoCite/standard-defibrillateurs/blob/main/Schema_defibrillateur_gabarit.xlsx) est également prévu pour faciliter la publication d'un jeu de données conforme au format du schéma.

Un exemple valide au format CSV est consultable [ici](https://github.com/FuturoCite/standard-defibrillateurs/blob/main/exemple-valide.csv). 

La tableau ci-dessous donne un aperçu des champs du schéma. 

<table>
  <tr>
    <td><strong>Nom</strong></td>
    <td><strong>Remplissage obligatoire/optionnel</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td>Identifiant (id)</td>
    <td>Obligatoire</td>
    <td>Ce champ contient un identifiant unique local. Le producteur de données le génère en associant le code INS de la commune dans laquelle se situe le défibrillateur à un nombre. Ce champ permet d'éviter localement les doublons. Le code INS de la commune est accessible <a href="https://statbel.fgov.be/fr/open-data/code-refnis">ici</a>.</td>
  </tr>
  <tr>
    <td>Nom (name)</td>
    <td>Obligatoire</td>
    <td>Ce champ contient le nom du défibrillateur</td>
  </tr>
  <tr>
    <td>Nom de la commune (municipality)</td>
    <td>Obligatoire</td>
    <td>Ce champ contient le nom de la commune dans laquelle se situe le défibrillateur. Le nom de la commune provient de la base de données BeST Address : <a href="https://opendata.bosa.be/index.fr.html">https://opendata.bosa.be/index.fr.html</a> ou de la liste des codes INS : <a href="https://statbel.fgov.be/fr/open-data/code-refnis">https://statbel.fgov.be/fr/open-data/code-refnis</a>.</td>
  </tr>
  <tr>
    <td>Code INS (ins_code)</td>
    <td>Obligatoire</td>
    <td>Ce champ contient le code INS de la commune où se situe le défibrillateur. Il est accessible <a href="https://statbel.fgov.be/fr/open-data/code-refnis">ici</a> et doit correspondre à un format de cinq chiffres.</td>
  </tr>
  <tr>
    <td>Partie de commune (zone_address)</td>
    <td>Optionnel</td>
    <td>Ce champ contient le nom de la partie de commune où se situe le défibrillateur, conforme à l'appellation dans StatBel : <a href="https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie">https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie</a>.</td>
  </tr>
  <tr>
    <td>Code INS de la partie de commune (ins_zone_address)</td>
    <td>Optionnel</td>
    <td>Ce champ contient le code INS de la partie de commune où se situe le défibrillateur. La découpe géographique de StatBel Level 5 (NIS6) liste ces codes : <a href="https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie">https://statbel.fgov.be/fr/propos-de-statbel/methodologie/classifications/geographie</a>.</td>
  </tr>
  <tr>
    <td>Nom de rue (street_name)</td>
    <td>Obligatoire</td>
    <td>Ce champ renseigne le nom de la voirie où se situe le défibrillateur (ou de la voirie la plus proche s'il n'est pas en voirie).</td>
  </tr>
  <tr>
    <td>Code rue BeSTAddress (street_number)</td>
    <td>Obligatoire</td>
    <td>Ce champ contient le code de la voirie où se situe le défibrillateur dans la base de données BeSTAdress (ou de la voirie la plus proche s'il n'est pas en voirie) : <a href="https://opendata.bosa.be/index.fr.html">https://opendata.bosa.be/index.fr.html</a>.</td>
  </tr>
  <tr>
    <td>Code rue national (street_number_rrn)</td>
    <td>Optionnel</td>
    <td>Code de la voirie où se situe le défibrillateur dans le registre national (ou de la voirie la plus proche s'il n'est pas en voirie).</td>
  </tr>
  <tr>
    <td>Numéro de police le plus proche (house_number)</td>
    <td>Optionnel (recommandé)</td>
    <td>Il contient le numéro de police (numéro de maison) le plus proche du défibrillateur.</td>
  </tr>
  <tr>
    <td>Coordonnées (coordinates)</td>
    <td>Obligatoire</td>
    <td>Ce champ indique les coordonnées du défibrillateur au format GeoJSON. Les coordonnées peuvent également être générées <a href="https://www.coordonnees-gps.fr/carte/pays/BE">ici</a> en cas d'impossibilité d'exporter la donnée depuis un logiciel métier.</td>
  </tr>
  <tr>
    <td>Intérieur (Indoor)</td>
    <td>Obligatoire</td>
    <td>Ce champ précise si le défibrillateur est situé à l'intérieur.</td>
  </tr>
  <tr>
    <td>Bâtiment (building)</td>
    <td>Optionnel</td>
    <td>Ce champ contient le nom du bâtiment dans lequel se situe le défibrillateur, le cas échéant. Si non applicable ou inconnu, ne pas renseigner ce champ.</td>
  </tr>
  <tr>
    <td>Étage d'accessibilité du défibrillateur (floor)</td>
    <td>Optionnel</td>
    <td>Ce champ permet de fournir un complément d'information sur l'accès au défibrillateur.</td>
  </tr>
  <tr>
    <td>Complément d'information sur l'accès au défibrillateur (access_precision)</td>
    <td>Optionnel</td>
    <td>Ce champ permet de fournir un complément d'information sur l'accès au défibrillateur.</td>
  </tr>
  <tr>
    <td>Accessibilité (accessibility)</td>
    <td>Obligatoire</td>
    <td>Ce champ précise si le défibrillateur est accessible au public ou non. Les valeurs possibles sont "Public" (accessible au public) ou "Privé" (non accessible au public). Si non applicable ou inconnu, ne pas renseigner ce champ.</td>
  </tr>
  <tr>
    <td>Accessible en permanence (permanently_accessible)</td>
    <td>Obligatoire</td>
    <td>Ce champ précise si le défibrillateur est accessible en permanence. Les valeurs possibles sont "true" (accessible 24 heures sur 24) ou "false" (accessible à certains moments). Si non applicable ou inconnu, ne pas renseigner ce champ.</td>
  </tr>
  <tr>
    <td>Horaires (schedule)</td>
    <td>Optionnel (recommandé)</td>
    <td>Ce champ contient les horaires auxquels le défibrillateur est accessible. Il suit le format proposé par OpenStreetMap : <a href="https://wiki.openstreetmap.org/wiki/FR:Key:opening_hours">https://wiki.openstreetmap.org/wiki/FR:Key:opening_hours</a>.</td>
  </tr>
  <tr>
    <td>Photo (picture)</td>
    <td>Optionnel</td>
    <td>Ce champ contient une URL qui renvoie vers une photo du défibrillateur dans son environnement. Il est recommandé de fournir une image sous format Open Source.</td>
  </tr>
  <tr>
    <td>Gestionnaire (provider)</td>
    <td>Optionnel (recommandé)</td>
    <td>Ce champ renseigne le gestionnaire du défibrillateur, le cas échéant.</td>
  </tr>
  <tr>
    <td>Date d'installation (installation_date)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne la date d'installation du défibrillateur au format ISO 8601 (AAAA-MM-JJ).</td>
  </tr>
  <tr>
    <td>Nom du contact (contact_name)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le nom de la personne à contacter pour toute communication relative au défibrillateur.</td>
  </tr>
  <tr>
    <td>Email du contact (contact_email)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne l'adresse email de contact pour toute communication relative au défibrillateur.</td>
  </tr>
  <tr>
    <td>Fonction du contact (contact_function)</td>
    <td>Optionnel</td>
    <td>Ce champ précise la fonction de la personne de contact pour toute communication.</td>
  </tr>
  <tr>
    <td>Numéro de téléphone (phone_number)</td>
    <td>Optionnel (recommandé)</td>
    <td>Ce champ renseigne le numéro de téléphone pour toute communication relative au défibrillateur. Il respecte le code de rédaction interinstitutionnel européen : <a href="http://publications.europa.eu/code/fr/fr-390300.htm">http://publications.europa.eu/code/fr/fr-390300.htm</a></td>
  </tr>
  <tr>
    <td>Marque (brand)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne la marque du défibrillateur.</td>
  </tr>
  <tr>
    <td>Modèle (model)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le modèle du défibrillateur.</td>
  </tr>
  <tr>
    <td>Numéro de série (serial_number)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le numéro de série du défibrillateur.</td>
  </tr>
  <tr>
    <td>Péremption Electrodes Adulte (adult_electrodes_expiry_date)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne la date de péremption des électrodes adulte. Il respecte le format ISO 8601 : année-mois-jour (YYYY-MM-DD).</td>
  </tr>
  <tr>
    <td>Lot Electrode Adulte (adult_electrodes_batch)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le numéro du lot des électrodes adulte.</td>
  </tr>
  <tr>
    <td>Péremption Electrodes Enfant (child_electrodes_expiry_date)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne la date de péremption des électrodes enfant. Il respecte le format ISO 8601 : année-mois-jour (YYYY-MM-DD).</td>
  </tr>
  <tr>
    <td>Lot Electrode Enfant (child_electrodes_batch)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le numéro du lot des électrodes enfant.</td>
  </tr>
  <tr>
    <td>Péremption Batterie (battery_expiry_date)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne la date de péremption de la batterie. Il respecte le format ISO 8601 : année-mois-jour (YYYY-MM-DD).</td>
  </tr>
  <tr>
    <td>Lot Batterie (battery_batch)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le numéro du lot de la batterie.</td>
  </tr>
  <tr>
    <td>Temporairement indisponible (temporarily_unavailable)</td>
    <td>Optionnel</td>
    <td>Ce champ renseigne le statut du défibrillateur, permettant de renseigner qu'un défibrillateur est temporairement indisponible. Si le défibrillateur est disponible, utiliser la valeur 'Disponible'. Si le défibrillateur est temporairement indisponible, utiliser la valeur 'Indisponible'.</td>
  </tr>
  <tr>
    <td>Date de création de la donnée (created_date)</td>
    <td>Optionnel</td>
    <td>Ce champ indique la date et l'heure de création de la donnée dans le jeu. Il respecte le format ISO 8601 : année-mois-jourTheure:minute:seconde+02:00 (AAAA-MM-JJTHH:MM:SS-/+FF:ff). Si vous ne disposez pas de l'heure de création de la donnée, mettre 00:00:00+02:00.</td>
  </tr>
  <tr>
    <td>Date de dernière modification de la donnée (last_modified_date)</td>
    <td>Optionnel</td>
    <td>Ce champ indique la date et l'heure de la dernière modification de la donnée dans le jeu. Il respecte le format ISO 8601 : année-mois-jourTheure:minute:seconde+02:00 (AAAA-MM-JJTHH:MM:SS-/+FF:ff). Si vous ne disposez pas de l'heure de mise à jour de la donnée, mettre 00:00:00+02:00.</td>
  </tr>
</table>




## Format de fichier 

Le format de fichier retenu pour la publication des données est le CSV (Comma Separated Values, valeurs séparées par des virgules).

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de formatage suivantes :

* l’encodage des caractères est UTF-8,
* le séparateur des colonnes est la virgule,
* le séparateur des nombres décimaux est le point,
* le séparateur de valeurs multiples dans un champ est le point-virgule,
* si un champ contient une virgule, il doit être entouré de guillemets doubles,
* chaque ligne doit avoir le même nombre de champs,
* le type MIME ou Content-Type est text/csv.

### Recommandations pour le nommage des fichiers 

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de nommage suivantes :

* YYYY-MM-DD : Date de création du fichier
* idProducteur : code INS unique de la commune pour identifier le producteur
* emplacements-pmr : nom du fichier, en minuscules non accentuées
* territoire : Nom du territoire concerné, non accentué (exemple : Liege)
* extension : Si les règles de formatage sont respectées, l'extension est .csv

Exemple : 2023-09-11_62063_defibrillateurs_Liege.csv

### Recommandations pour la mise en conformité 

Ces conseils reprennent ceux des schémas standards de données français publié par [l'initiative de data.gouv.fr](https://schema.data.gouv.fr/).

Les fichiers doivent comporter :

* Toutes les colonnes, y compris celles dont les cellules ne sont pas renseignées, dans le bon ordre, et avec des en-têtes correctement nommées sur la première ligne (nom correspondant strictement au schéma)
* Autant de lignes que nécessaire comprenant des cellules dont les valeurs peuvent être obligatoires (elles doivent être impérativement renseignées) ou optionnelles (elles sont seulement recommandées ou soumises à condition de disponibilité / pertinence)
