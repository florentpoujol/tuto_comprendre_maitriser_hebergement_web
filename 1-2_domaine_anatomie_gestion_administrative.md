# Domaine : Anatomie et gestion administrative

Dans cette toute première partie, nous verrons plus en détail de quoi est fait un domaine.

Nous mettrons cela en pratique dans le prochaine chapitre lorsque nous parleront effectivement de la commande, du renouvellement et de l'expiration d'un domaine.

## Les acteurs des noms de domaine

Nous allons d'abord voir comment et par qui les noms de domaines sont gérés.

Il y a tout d'abord le __titulaire__ (_registrant_ en anglais) du domaine qui est la personne physique ou morale qui le possède et l'utilise.

Le titulaire achète le domaine à un __bureau d'enregistrement__ (_registrar_ en anglais). Celui-ci est la société qui fourni les services basiques de gestion administrative et technique du domaine. Typiquement, c'est l'hébergeur mais nous le verrons plus tard, le site et a fortiori la partie technique du domaine peuvent être gérés ailleurs que chez le bureau d'enregistrement.

Le bureau d'enregistrement achète lui-même le domaine auprès d'un __registre__ (_registry_ en anglais), un organisme qui justement fourni les domaines pour une ou plusieurs extensions.

Le registre est aussi l'organisme qui fixe les règles, procédures et conditions d'utilisation des extensions dont il a la charge. Il a droit de vie ou de mort sur les domaines que vous possédez. Si vous ne respectez pas les conditions d'utilisation ou ne terminez pas une procédure qu'il a lancé, il peut mettre le domaine hors service voir vous le "reprendre". Les bureaux d'enregistrement peuvent ajouter une couche de règles, procédures et conditions d'utilisation qu'il conviendra aussi de respecter.

Le registre principal est l'[ICANN](https://www.icann.org). Il gère quelques extensions dont les `.com` et délègue la gestion des autres à divers organismes. Pour les `.fr` par exemple, c'est l'[Afnic](https://www.afnic.fr). (l'Association Française pour le Nommage Internet en Coopération).

## L'anatomie d'un domaine

Un domaine tel que _www.openclassrooms.com_ peut se décomposer en trois parties.

### L'extension

La partie à la fin est appelée l'__extension__, ou __domaine de premier niveau__ (_TLD ou Top Level Domain_ en anglais). C'est elle qui va déterminer le registre qui la fourni, si elle peut être achetée chez votre bureau d'enregistrement, et à quel prix.

Typiquement elle est courte et ne contient elle-même pas de point, mais il y a des exceptions.
Voici quelques exemples :  `.fr`, `.com`, `.paris`, `.international`, `.co.uk`, `.ninja`, `.xxx`, `.vin`.

Vous l'avez vu, certaines extensions sont un peu fantaisiste...

### Le (corps du) domaine

La partie juste à gauche du point avant l'extension est ce qu'on appelle le _domaine de second niveau_, ou plus communément : le domaine.

> Par extension, quand on dit le domaine, on désigne la plupart du temps cette partie là, plus l'extension.

C'est la partie que vous choisissez (en plus de l'extension) lorsque vous achetez un domaine auprès d'un bureau d'enregistrement.

La taille minimal est de deux caractères, et la taille maximale ... ne devrait jamais être atteinte. Un nom de domaine doit être retenu par un humain, il doit vous représenter au mieux, sans être trop long ni trop mystérieux.

Les caractères ne devraient être que des lettres non accentuées, des chiffres et des traits d'union (-). Techniquement, plusieurs extensions permettent néanmoins d'avoir des caractères non-ASCII tels que  é ,  ï ,  ç  par exemple. Mais je pense que c'est une mauvaise idée parce que peu de monde est habitué à voir ce type de caractères dans des domaines et c'est potentiellement source de bug dans les interfaces des bureaux d'enregistrement.

### Les sous-domaines

La ou les parties encore à gauche du point avant le domaine est (sont) le sous-domaine(s). La création de cette partie se fait via les paramètres techniques du domaine et est généralement gratuite et illimitée. 

Seuls certains sous-domaines "techniques" peuvent commencer par un tiret bas (_).

## Gestion administrative d'un domaine, données de contact et Whois

Nous avons vu que les domaines possédaient une partie administrative. Celle-ci contient des informations relatives au cycle de vie du domaine (telles que le bureau et la date d'enregistrement et de renouvellement par exemple) mais aussi et surtout les données de contact du domaine.

Il y a en fait trois séries de données de contact pour trois entités :

- Le __titulaire__ : c'est vous ou votre association/société.
- Le __contact administratif__ : la majorité du temps c'est le même que le titulaire.
- Le __contact technique__ : c'est soit à nouveau les même coordonnées que le titulaire, soit les coordonnées du bureau d'enregistrement.

Le plus important étant évidement le titulaire puisque ce sont ces données qui définissent qui est propriétaire du domaine. Ces données sont à chaque fois composées du nom de famille et prénom (et/ou nom de la personne morale), de l'adresse postale, du numéro de téléphone (et de fax) et de l'adresse email.

> Toutes ces données sont par défaut publiques et consultables gratuitement par n'importe qui sur Internet via les __Whois__ (prononcez _ouiz_, la contraction de _Who is_ qui signifie _Qui est_ en anglais).

Vous pouvez par exemple utiliser le site [who.is](https://who.is) pour rechercher les informations liées à [openclassrooms.com](https://who.is/whois/openclassrooms.com). On constate entre autre qu'il existe depuis le 05/12/2008 et qu'il appartient à OpenClassrooms SAS.

> Mais c'est terrible !
>
> Je n'ai pas envie que tout le monde sache que c'est moi qui possède le domaine _lesteletubbiespourlavie.fr_ et trouve aussi facilement mon numéro de téléphone et mon adresse email !

Très bon point ! Cela pose en effet __de gros soucis de vie privée, en plus d'une certitude de se faire spammer__...

Heureusement, tous les bureaux d'enregistrement proposent la possibilité d'activer l'__enregistrement privé__ afin d'__anonymiser__ tout ou partie de ces données en Whois, typiquement en les remplaçant par d'autres données factices ou liée au bureau d'enregistrement.

> Lorsque vous commandez un domaine, vous devez vous enquérir auprès du bureau d'enregistrement si oui, dans quelle mesure, et à quelles conditions, l'enregistrement privé peut être activé.
>
> C'est une encore plus mauvaise idée de mettre vous-même des données factices dans les données de contact de vos domaines car cela viole très certainement les CGV du bureau d'enregistrement et du registre.

Quasiment tous les registres exigent que les données de contact soient vraies et ils peuvent vous demander à tout moment de les prouver. Si vous ne pouvez pas, vous pouvez perdre le domaine. C'est d'autant plus important pour l'adresse email du titulaire, à cause des transferts que nous verrons plus tard.

## En résumé

- Les domaines font le lien entre un nom et un site web ou des adresses email.
- Les domaines sont des propriétés qui doivent être achetées pour une durée limitée auprès de bureaux d'enregistrement.
- La partie administrative (et technique) du domaine est publique, consultable via les Whois, mais les données de contact peuvent être anonymisées‌.
