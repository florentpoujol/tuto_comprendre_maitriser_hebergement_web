# De quoi est fait un site web

Avant de voir de quoi est fait un hébergement web, voyons de quoi est fait un site web, puisqu'ils servent principalement à en héberger.

Un site web est tout d'abord un ensemble de fichiers qui existent sur un bout du disque dur du serveur qui les hébergent. On appelle ce bout de disque dur __l'espace web__, ou par extension (on verra pourquoi un peu plus tard) le _FTP_.

Dans leur forme la plus simple ces fichiers sont principalement de type _HTML_ et ont l'extension _.html_. Lorsque vous tapez l'adresse d'une page d'un site dans votre navigateur (par exemple _http://votreentreprise.com/lapage.html_), celui-ci demande au serveur "envoi moi telle page".

Si la page existe, le serveur lui envoi, puis le navigateur l’interprète afin de l'afficher comme le créateur du site l'a souhaité. Si elle n'existe pas, le serveur renvoi le fameux code d'erreur 404, qui signifie _ce que tu m'as demandé n'existe pas chez moi_.

L'inconvénient (autant que l'avantage) de ce genre de site HTML, c'est qu'ils sont statiques. Chaque page envoyée est toujours la même, __le contenu du site ne change pas__ (sauf si le créateur le met à jour bien sur).

Afin d'ajouter un certains dynamisme à ces pages, elles peuvent faire appel à la technologie _Javascript_, qui est utilisée __par le navigateur__, typiquement pour ajouter certaines interactions ou effets, après que la page ai été reçue par le navigateur. Dans ce cas la page envoyée par le serveur est encore toujours la même, mais en fonction de vos actions sur celle-ci, son affichage par le navigateur peut changer dans le temps.

Il est également possible que la page HTML ne soit pas fixe mais soit en fait __construite par le serveur lui-même__, avant qu'il ne l'envoi vers votre navigateur. Dans ce cas le serveur fait usage de technologies __coté serveur__ telles que _PHP_ (là où Javascript et HTML sont des technologies __coté client__ puisqu'elle sont utilisée par le navigateur et non le serveur).

Lorsque ces fichiers PHP (extension _.php_) sont appelés, ils sont en fait exécutés par le serveur et construisent une page _HTML_ que le serveur va finalement envoyer au navigateur. Le serveur n’envoie donc pas la page PHP, __il envoi la page HTML qui a été construite par la page PHP__.

Dans leur utilisation la plus simple, le même fichier PHP renverra toujours la même page HTML. C'est juste que PHP aura permis de simplifier la construction du site puisqu'il permet de ne pas répéter du code HTML. Sur un site complètement en HTML, le code qui permet d'afficher le menu par exemple doit se trouver et être recopié dans chaque page. Un changement dans le menu implique un changement dans toutes les pages du sites. PHP permet de mettre le menu dans un fichier en particulier qui sera ensuite inclus automatiquement dans chaque page individuelle par une instruction PHP lorsqu'elle sera demandée par le navigateur.

Là où les langages de script coté serveur comme PHP trouvent toute leur utilité, c'est lorsque qu'ils travaillent avec des __bases de données__, qui sont d'autres technologies coté serveur telles que _MySQL_. Les bases données ont pour but de stocker des données de manière organisées. Sur un site, les données gardées en base de donnée sont typiquement le contenu textuel de chaque page, ainsi que tout contenu qui peut changer en fonction de l'action d'un utilisateur, comme quelqu'un qui publie un commentaire d'un article ou un message dans un forum.

Dans ce cas, les fichiers sont essentiellement un substrat qui apporte les fonctionnalités de création et d'utilisation du site. Ce sont eux qui font des requêtes vers la base de donnée afin d'écrire de nouvelle données ou de lire celles demandées par un visiteur.

Typiquement dans la majorité des CMS actuels, bien qu'ils soient composés de milliers de fichiers, il n'y en as qu'un seul qui soit appelé : le fichier _index.php_. Grâce à la __réécriture d'URL__, qui est une fonctionnalité apportée par le __serveur web__, c'est quelque chose de transparent pour vous. Tout ce que vous avez à écrire après le nom de domaine est le nom de la page que vous souhaitez voir (par exemple _http://votreentreprise.com/lapage_), le site s'occupe de tout le reste pour vous apporter le contenu désiré, bien que techniquement vous accédez en fait exactement au même fichier .php quelque soit la "page" demandée.

## Serveur physique ou logiciel

Encore un petit aparté sur le terme __serveur__ avant de vraiment continuer. Celui-ci désigne deux choses :

- Un ordinateur, une machine physique,
- ou bien un logiciel.

Il se trouve que les "serveurs logiciels" généralement tournent sur des "serveurs physiques", ce n'est pas une coïncidence.

Le but d'un serveur (logiciel) est de __servir des données à un client__ lorsque celui-ci est __connecté__ et qu'il en fait la __requête__ via un __protocole__ (en gros, lorsqu'il lui demande gentiment).

_Servir_ signifie autant recevoir que fournir. Un _client_ désigne généralement le logiciel sur votre ordinateur par lequel vous allez vous connecter au serveur.

Par exemple, un __serveur web__ va servir des __pages web__ (HTML) lorsqu'un __client web__ (votre navigateur) y fait une requête avec le __protocole HTTP__ (le même HTTP que dans _http://votreentreprise.com_). De la même manière un __serveur FTP__ va __servir des fichiers__ lorsqu'un __client FTP__ sur votre ordinateur y est connecté en utilisant le __protocole FTP__.

Dans le prochains chapitre, vous verrez un peu plus en détail les différentes technologies et aspects que vous pouvez rencontrer dans un hébergement web mutualisé.
