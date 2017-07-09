# L'hébergement mutualisé en détails

Nous allons voir dans ce chapitre les principales technologies et fonctionnalités auxquelles vous allez avoir à faire lorsque vous possédez un hébergement mutualisé.

## L'espace web, se connecter en FTP

Quelque soit le type d'hébergement, vous pouvez avoir accès au bout de disque dur qui y est lié afin d'y mettre (héberger) les fichiers de votre site.

C'est donc en vous connectant au __serveur FTP__ que vous allez pouvoir transférer des fichiers depuis votre ordinateur vers l'hébergement ou l'inverse.

Afin de vous connecter au serveur, vous avez besoin d'un logiciel appelé un __client FTP__ à installer sur votre ordinateur. Il y en a plein, autant payants que gratuits, le plus connus étant certainement [Filezilla](https://filezilla-project.org), qui est gratuit, simple, efficace et fonctionne sous Windows, Mac et Linux.

A l'instar de la configuration d'un client de messagerie afin qu'il se connecte à un serveur email, vous devez configurer votre client FTP avec paramètres qui vous sont donnés par votre hébergeur sur votre espace client.

D'une manière générale, les paramètres sont les suivants :

- __Serveur, ou hôte__ : le plus souvent ce sera votre nom de domaine, parfois ce sera le sous-domaine _ftp.votredomaine.com_, parfois ce sera autre chose. Ne supposez pas : vérifiez l'hôte qui vous est fourni par votre hébergeur.
- __Protocole et port__ : comme pour les emails, il y a une relation entre les deux. Typiquement vous avez le choix entre protocole _FTP/port 21_ ou le protocole __SFTP/port 22__. Pour des raisons de sécurité dont le détail ne nous importent pas, préférez si possible utiliser le protocole SFTP. Là encore référez vous à la documentation de votre hébergeur, parfois le protocole SFTP s'utilise sur le port 21.
- __Identifiant, ou utilisateur__ : souvent, vous pourrez choisir au moins en partie l'identifiant. Dans tous les cas, référez-vous à votre hébergeur.
- __Mot de passe__ : si il n'est pas toujours défini par défaut par l'hébergeur, dans tous les cas vous pouvez le modifier via l'espace client.

> Notez bien que les hébergements web ne sont pas fait pour de l'hébergement de gros fichiers ou de fichiers en masse : ils sont fait pour des sites web. C'est pourquoi, même sur les hébergements qui sont affichés comme ayant un "espace disque illimité", il y a toujours une limite d'espace disque et de nombre de fichiers au total ou même par répertoire. Si vous atteignez l'un de ces quota, votre client FTP doit pouvoir vous afficher une erreur vous en informant. Le quota d'espace disque et/ou fichiers doit aussi être consultable via votre espace client.

Chaque utilisateur FTP est également lié à un dossier en particulier, __sa racine__. Celui-ci aura alors accès au contenu de ce dossier ainsi qu'a tous ses sous-dossiers, mais à aucun autre dossier de même niveau ni de niveau supérieur.

Ainsi sur un gros hébergement par exemple, vous pouvez créer plusieurs utilisateurs, chacun ayant accès à un dossier en particulier. Si chacun de ces dossiers sont au même niveau (ils sont eux-même créés dans le même dossier), chaque utilisateur n'aura pas du tout accès au contenu des autres dossiers.

## Rendre un dossier accessible via le web : pointer un nom de domaine

Maintenant que des fichiers sont sur l'hébergement, il faut qu'un domaine pointe vers le dossier dans lequel ils sont afin de pouvoir y accéder par le web. Il y a toutes les chances que les domaines pointent par défaut à la racine de l'espace web et donc que les fichiers qui y sont placés soient déjà accessibles.

Pour les fichiers qui sont placés dans des sous dossiers, vous pouvez bien sur y accéder en mettant le nom du dossier après le nom de domaine : _votreentreprise.com/monsupersite/lapage.html_. Mais vous pouvez aussi modifier __la destination (ou la racine) du domaine__ lui-même via votre espace client afin qu'il pointe directement dans le dossier _/monsupersite__. L'adresse pour accéder à la page sera alors _votreentreprise.com/lapage.html_.

### Le domaine par défaut

Les hébergeurs mettent souvent à disposition gratuitement un domaine technique appelé __le domaine par défaut__ qui pointe vers l'hébergement. Vous pouvez vous en servir lorsque vous n'avez pas encore de domaine de disponible, ou lorsque vous voulez créer une nouvelle version de votre site par exemple.

Chez 1&1 et OVH, respectivement, il a le format _s123456789.onlinehome.fr_ et _votresite.cluster123.ovh.net_.

# Serveur web : Apache

Vous avez donc désormais au moins un fichier sur l'espace web, vers lequel pointe un domaine. Afin que vous puissiez l'afficher sur votre ordinateur, vous avez besoin qu'un client web se connecte à un serveur web. C'est le serveur web qui va recevoir les requêtes HTTP et répondre avec une page HTML.

Le client web est tout simplement votre navigateur : Chrome, Firefox, etc... Le serveur web a lui toutes les chances d'être appelé _Apache_. Ce n'est pas très important de retenir son nom, mais c'est parce que c'est celui-ci en particulier que vous allez trouver ou pouvoir utiliser des fichiers particuliers dont le nom est _.htaccess_. 

Ce sont des fichiers de configuration du serveur web Apache. Ces fichiers ne sont pas obligatoires pour un site simple, mais sont très utiles pour plein de choses. Typiquement ce sera soit votre CMS, soit vous même qui pourrez modifier ce ficher afin de :

- Forcer l'utilisation du sous domaine _www_ ou de _HTTPS_,
- bloquer l'accès au site à certaines adresses IP,
- mettre en place la réécriture d'URL,
- mettre en place des règles liées à l'amélioration des performances du site.

Leur mauvaise utilisation est la principale source des erreurs _500 Internal Server Error_.

> C'est parce que le nom du fichier commence par un point que vous ne le voyez pas forcément sur votre ordinateur parmi les autres fichiers de votre site.

## Langage de script coté serveur : PHP

On a déjà parlé un peu de PHP, c'est donc un langage de script coté serveur utilisé par tous les sites dont les pages sont dynamiques ou ont des fonctionnalités qui le requiert (comme un formulaire de contact ou bien un accès à une base de donnée).

Il y a bien d'autre technologies similaires à PHP (_ASP_ pour les serveurs Windows, ou encore _Ruby_ ou _NodeJS_ par exemple) mais votre hébergement a toutes les chances de faire tourner PHP. Et ça tombe bien puisque c'est nécessaire pour faire fonctionner la plupart des CMS majeurs tels que Wordpress, Joomla et Prestashop.

L'ensemble de la configuration par défaut de PHP peut être visible par un "PHPInfo". Concrètement c'est un fichier dont le nom n'importe pas mais dont le contenu est celui-ci :

```
<?php phpinfo();
```

Cela vous donne la version exacte utilisée, l'ensemble des modules qui sont activés et la valeur des différentes variables.

Une partie de la configuration par défaut peut être modifiée via des fichiers _php.ini_. A l'inverse des fichier .htaccess, les règles définies dans les php.ini ne sont pas récursives : elle s'appliquent uniquement aux scripts qui existent dans le même dossier que le fichier. Ce n'est généralement pas un soucis puisque en tout cas avec la majorité des CMS, il n'y a en fait que deux scripts qui tournent : les fichiers index.php à la racine du site et celui dans le dossier d'administration. Dans la majorité des cas, il suffit donc de placer au maximum deux fichiers php.ini.

Les raisons les plus classiques d'avoir à modifier soit-même ces fichiers sont les suivantes :

- Augmenter la taille limite des fichiers pouvant être uploadé via un formulaire sur le site (_upload_max_filesize_ et _post_max_size_),
- augmenter la mémoire allouée à chaque script (_memory_limit_),
- augmenter le nombre de champs pouvant exister à la fois dans un formulaire (_max_input_vars_),
- afficher et/ou mettre en place un journal des erreurs PHP.

Il y a plusieurs versions de PHP qui existent en même temps sur le serveur et vous pouvez choisir quelle version chacun de vos sites doit utiliser via l'espace client.

Pour des raisons de sécurité et de performance, __utilisez toujours la version la plus récente possible__. Une page dans votre espace client vous permet de modifier cette version par site et/ou par domaine. Si votre site ne supporte pas une version plus récente de PHP, alors c'est une bonne idée de voir à le mettre à jours prochainement afin que cela ne vous pose pas de problème lorsque la version qu'il utilise deviendra obsolète et que l'hébergeur souhaitera la supprimer.

## Base de donnée : MySQL

Une base de donnée est là où est souvent sauvegardée le contenu et la plupart des réglages d'un site web. Les fichiers ne représentent alors que le support permettant de modifier et d'afficher ces données. 

MySQL (prononcez _Maille SQL_) n'est qu'un de ces __systèmes de gestion de base de donnée__ parmi tant d'autres (_PostgreSQL_, _MariaDB_ par exemple), mai là encore c'est celui-ci qui a 99% de chances d'exister sur votre hébergement. La majorité des CMS l'utilise, il faut donc bien comprendre alors que __le site existe en deux parties distinctes__, les fichiers d'une part et la base de donnée d'autre part.

Suivant le type d'hébergement que vous possédez, vous pouvez créer une ou plusieurs bases de données. Elles se gèrent depuis une page dédiée de votre espace client où vous pouvez en créer, modifier le mot de passe et en supprimer.

Le lien entre les fichiers du site et la base de données se fait grâce au __fichier de configuration du site__ dans lequel est écrit les paramètres de connexion à celle-ci.

Les paramètres de connexion aux bases de données sont typiquement les suivant (comme d'habitude, reportez-vous à votre hébergeur pour avoir les valeurs exactes pour vous) :

- __Hôte ou serveur__ : ce sera généralement soit _localhost_, soit un autre nom d'hôte si la base de donnée n'est pas sur le même serveur que les fichiers
- __Port__ : parfois il peut être nécessaire d'indiquer un port, il peut s'écrire alors après l'hôte séparé par un double point. Pour MySQL, le port sera souvent 3306. Exemple : _localhost:3306_.
- __Nom__ : le nom de la base de donnée. Suivant l'hébergeur, vous pouvez choisir tout ou partie du nom, ou alors il vous est imposé.
- __Utilisateur__ : l'utilisateur qui a le droit de modifier la base de donnée. Suivant l'hébergeur vous pourrez choisir tout ou partie de son nom ou il vous sera imposé. Suivant l'hébergeur, le même utilisateur pourra être lié à plusieurs bases de données ou chaque base de donnée aura son propre utilisateur.
- __Mot de passe__ : le mot de passe lié à l'utilisateur

> Notez bien que techniquement, les bases de données n'ont pas de mot de passe. 
> Mails elles sont liées à un (ou plusieurs) utilisateurs qui eux ont des mots de passe.

Avec un CMS vous n'aurez pas besoin de modifier ce fichier de configuration directement, le CMS vous demandera ces paramètres de configuration lors de son installation.

### PHPMyAdmin

PHPMyAdmin est un outil de gestion de bases de données MySQL accessible depuis l'espace client qui vous permet d'aller voir et modifier directement son contenu. Vous n'aurez pas besoin de trifouiller là dedans à moins qu'il y ai vraiment un soucis avec votre site.

L'hébergeur met à disposition un accès direct à PHPMyAdmin depuis l'espace client, mais sachez qu'il est généralement aussi possible d'installer PHPMyAdmin comme n'importe quel site web sur votre hébergement. Attention toutefois à la sécurité, il ne faudrait pas laisser accès à la base de donnée à n'importe qui...

---

Voilà pour les principales technologies et fonctionnalités que vous pouvez trouver sur un hébergement mutualisé. En aillant compris tout cela, vous avez déjà de quoi héberger un site, même installer un CMS.

Mais ça ne s'arrête pas là. Plusieurs autres technologies et fonctionnalités sont disponibles et complémentaires à celles déjà vues.

## Se connecter en ligne de commande : SSH

SSH est un moyen de se connecter au serveur et de le contrôler via __un terminal__, soit une interface en __ligne de commande__. Vous pouvez y faire les même choses que via d'autres interfaces comme déplacer ou supprimer des fichiers, faire des sauvegarde des bases de données, et bien plus encore.

Ce n'est que pour des utilisations très avancées, mais dans certains cas c'est très pratique, voire la seule solution. Comme toujours, les paramètres de connexion se trouvent dans votre espace client et son souvent les même que pour la connexion en SFTP.

## Sécuriser la visite sur votre site : certificat SSL

Un certificat SSL est ce qui va permettre à votre site d'avoir des adresses commençant par __HTTPS__ et non pas seulement HTTP (par exemple _https://votreentreprise.com_).

Pour un simple site vitrine ce n'est pas indispensable, mais sachez que la présence d'un certificat fait maintenant partie des critères de classement des sites dans les moteurs de recherche, en tout cas Google. Ça ne va pas vous faire gagner 10 pages mais ce serait dommage de vous en passer si votre hébergeur vous permet de mettre ça en place facilement.

Les certificats sont par contre indispensable lors de l'échange de données sensibles, tels que la connexion à un site (avec utilisateur + mot de passe) et surtout l'envoi de données de paiement.

Dans le cas des boutiques en ligne, le certificat n'est en fait pas strictement indispensable puisque le paiement se fait quasiment toujours sur le site d'une banque ou de Paypal et pas vraiment sur le site même de la boutique. Mais d'une part ça fait bien d'avoir une adresse qui commence en HTTPS (cela rassure le visiteur) et d'autre part, les systèmes qui gèrent le paiement requièrent souvent que le site ai un certificat afin de lui transmettre de manière sécurisée ne serait-ce que la confirmation que l'utilisateur a bien effectué son paiement (c'est le cas de Paypal depuis 2017).

Les certificats SSL apportent de la sécurité de deux manières :

- Ils permettent au serveur web et au navigateur de __chiffrer la communication entre eux__, afin qu'il n'y est que eux qui puissent se comprendre et déchiffrer les données que chacun s'envoi.
- Ils __donnent confiance__, dans le sens où ils permettent au navigateur de savoir qu'il est bien connecté au bon serveur, et pas à un pirate qui se fait passer pour lui à la place.

Ce deuxième point mérite plus d'explication : les certificats sont générés et signés par des société appelées des __autorités de certification__. Il n'est pas possible pour un pirate de "reproduire" la signature d'une autorité et de se générer un certificat en se faisant passer pour eux. Le certificat est aussi lié au nom de domaine pour lequel il est généré et parfois même à la société qui édite le site web.

Le navigateur possède une liste d'autorités de certification qu'il connaît et auxquelles il fait confiance. Lorsqu'il reçoit un certificat, il vérifie  :

- Par quelle autorité il a été signé et si il fait confiance à cette autorité,
- si le certificat a bien été généré pour le domaine auquel le visiteur tente d'accéder.

Si l'un de ces éléments n'est pas bon, le navigateur arrêtera tout de suite la communication et vous affichera une grosse erreur faisant très peur, avant même d'avoir transmis la requête pour la page au serveur.

Même si comme pour les domaines, les hébergeurs ne sont que des intermédiaires, puisque les certificats sont commandés auprès des autorités de certifications, ils vous permettent toujours d'en commander et d'en activer pour vos domaines de manière simplifiées. Il est possible qu'il vous en mettent un certain nombre à disposition gratuitement, mais d'une manière générale un certificat coûte de l'ordre de 50€ par an, ou plus suivant le type de certificat.

Techniquement parlant, un certificat SSL est représenté par deux fichiers présents sur le même serveur physique que le serveur web. Dans tous les cas, un certificat doit donc se commander __là où (chez qui) se trouve le site web__, et non le domaine.

On distingue aussi trois types de certificats :

- Les certificats __simples__ qui ne permettent de sécuriser que un domaine ou un sous-domaine.
- Les certificats __Wildcard__ qui permettent de sécuriser un domaine et l'ensemble de ses sous-domaines.
- Les certificats avec __validation étendue__ qui sont des certificats simples mais lié à votre entreprise. L'autorité de certification a alors une procédure par email, téléphone voire courrier postal pour vérifier la société existez bien. Le nom de la société sera alors affiché par le navigateur sur la même ligne que l'adresse du site. C'est le cas avec le certificat d'OpenClassrooms.com.

Avec les hébergements mutualisés, vous pouvez activer un certificat SSL en seulement quelques clics via l'espace client, la procédure dépend beaucoup de l'hébergeur. Généralement il faut commander un certificat si ce n'est pas déjà fait puis l'associer à un site ou un domaine en particulier.

### Demander au site d'avoir des adresses commençant par HTTPS

Mais ce n'est pas tout. Une fois que le certificat fonctionne, encore __faut-il que le site fasse en sorte de l'utiliser__. L'idée est que le site redirige automatiquement les visiteurs qui arrivent dessus via une adresse HTTP vers la même adresse mais commençant par HTTPS mais aussi qu'il change les liens, non seulement du menu, mais aussi des ressources (comme les images) par des adresses qui commencent toutes par HTTPS.

Si le site est fait avec un CMS il n'y a généralement que quelques clics de plus à faire dans son administration. Si le site est fait autrement, alors il faudra sans doute modifier manuellement son fichier .htaccess.

> J'ai fait tout cela mais le navigateur n'affiche pas le cadenas vert ? Que ce passe-t-il ?

Lorsque tout va bien, les navigateurs le signalent visuellement en montrant un cadenas vert juste à gauche de l'adresse du site. Lorsque le navigateur vous laisse atteindre un site mais affichent ce cadenas d'une autre couleur, c'est que __le certificat fonctionne bien mais le site fait des bêtises__.

Le plus souvent cela veut dire que la page web est bien chargée via HTTPS mais que des ressources (typiquement des images) qu'elle contient sont elles chargées via HTTP au lieu de HTTPS. Ce n'est en soit pas forcément un problème mais c'est considéré comme une mauvaise pratique et dans certains cas les navigateurs peuvent choisir de ne même pas charger ces ressources.

Dans ce cas, vous devez localiser quelles sont ces ressources dont il faut corriger l'URL et le faire si possible. Parfois ce sera aussi simple que de corriger l'adresse d'une image dans une page, ou de refaire la manipulation pour ajouter votre logo via les paramètres de votre thème par exemple. Parfois il faudra aller fouiller la documentation de votre thème ou des extensions qui chargent ces ressources pour savoir si il est possible de les charger via HTTPS.

## Accélérer la visite sur votre site : CDN

Dit d'une manière simple, un CDN (_Content Delivery Network_) permet d'accélérer la vitesse de visite sur votre site.

Ou plus exactement, il va _tendre à minimiser le temps de téléchargement des ressources statiques_ de votre site, particulièrement pour les visiteurs éloignés géographiquement du serveur qui l'héberge.

Un CDN est en fait un système de cache qui va recopier le contenu statique (typiquement les images) de votre site sur divers serveurs à travers le monde. Chaque visiteur va automatiquement télécharger les différentes parties du site idéalement depuis le serveur du CDN le plus proche géographiquement. Comme ces serveurs de CDN ont également une vitesse de téléchargement typiquement plus élevée que celle de votre hébergeur, cela fait en sorte que le site puisse s'afficher le plus rapidement possible.

Attention toutefois, un CDN ne change rien à la vitesse à laquelle le site et le serveur de votre hébergeur va générer la page HTML, ni ne change la vitesse de téléchargement de vos visiteurs. Ce sont les deux facteurs limitants qui font qu'un CDN aura dans la pratique plus ou moins d'impacts sur la vitesse de visite.

C'est également bien lorsque votre site commence à avoir pas mal de visiteur, parce qu'une partie du site est donc servi depuis les serveurs du CDN et non celui de l'hébergeur. Cela retarde le moment où le serveur de l'hébergeur sera "trop chargé" et vous devez changer de formule d'hébergement afin d'en prendre une plus performante.