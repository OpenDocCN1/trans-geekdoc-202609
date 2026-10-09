# Working with PHP Object-Oriented Programming

Here is the output for country list:

```
```
-----------------
Country List
-----------------
Afghanistan Albania Antarctica Algeria American Samoa Andorra Angola Antigua and
Barbuda Azerbaijan Argentina Australia Austria Bahamas Bahrain Bangladesh Armen
ia Barbados Belgium Bermuda Bhutan Bolivia, Plurinational State of Bosnia and He
rzegovina Botswana Bouvet Island Brazil Belize British Indian Ocean Territory So
lomon Islands Virgin Islands, British Burundi Burdusalam Bulgaria Myanmar Burundi
Belarus Cambodia Cameroon Canada Cape Verde Cayman Islands Central African Repu
blic Sri Lanka Chad Chile China Taiwan, Province of China Christmas Island Cocos
(Keeling) Islands Colombia Comoros Mayotte Congo, Congo, The Democratic Republic
of the Cook Islands Costa Rica Croatia Cuba Cyprus Czech Republic Benin Denmark
Dominica Dominican Republic Ecuador El Salvador Equatorial Guinea Eritrea Erit
rea Estonia Faroe Islands Falkland Islands (Malvinas) South Georgia and the Sout
h Sandwich Islands Fiji Finland Aaland Islands France French Guiana French Polyne
sia French Southern Territories Djibouti Gabon Georgia Gambia Palestine, State o
f Germany Ghana Gibraltar Kiribati Greece Greenland Grenada Guadeloupe Guam Guat	emala Guinea Guyana Haiti Heard Island and McDonald Islands Holy See (Vatican Ci
ty State) Honduras Hong Kong Hungary Iceland India Indonesia Iran, Islamic Repub
lic of Iraq Ireland Israel Italy Côte d'Ivoire Jamaica Japan Kazakhstan Jordan K\enemy Korea, Democratic People's Republic of Korea, Republic of Kuwait Kyrgyzstan
Lao People's Democratic Republic Lebanon Lesotho Latvia Liberia Libya Liechten
stein Lithuania Luxembourg Macao Madagascar Malawi Malaysia Maldives Mali Malta M
```
```

You can also use the factory method to generate a CustomerList object and use it:

```
```
$list = Application\Generic\ListFactory::factory(
    new Application\Generic\CustomerList(), $params);
foreach ($list->list() as $item) echo $item . ' ';
```
```

Here is the output for CustomerList:

```
```
-----------------
Customer List
-----------------
Conrad Perry Lonnie Knapp Darrel Roman Morgan Avila Lee McCray Spencer Sanford T
homas Kirby Brian Crawford Armando Barlow Jess Rocha Felix Blevins Jose Carter O
rlando Fulton Mitchell Roth Eduardo Wright Marc Ellis Joaquin Moses Morris Varja
n Gene Cruz Samuel Harding Lauri Grimes Ceeleen Walker Tabitha Foster Cecelia Ca
se Rhonda Kinney Elvira Giles Flossie Dyer Gabriela Davis Dolly Wong Krista Corte
z Leta Solomon Matilda Barrera Tommie Horter Lenne Gillespie Camille Perez Grac
iela Joyner Penelope Molina Celeste Justice Lena Conway Katrina Freeman Jeff Val
doz Leonardo Parrish Roland Chong Raymond Sanford Wilfredo Taylor Dominick Cline
Alonzo Sullivan Edmond Shepherd Omar Anthony Lonnie Eaton Peter Pugh Jesus Brig
ht Ramiro Bentley Derrick Hendricks Hans Page Garrett Campos Todd Lindsey Denis
Snyder Stan Rocha Dollie Hernandez Aileen Duncan Essie Shorti Ram Ruiz Isabel Ro
driguez Ingrid Santos Jaime Noel Geneva Case Lucille Bradford Josefina Hampton F
annie Moore Sorcorr Jemenes Elba Mccall Louella Allan Jeanette Merritt Lana Bur
ns Karyn Francis Blanca Le Renee Decker Obama C.T. Russel admin Leonard Nimoy
-----------------

(program exited with code: 0)
Press return to continue
```
```