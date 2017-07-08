# Utilisations avancées, SPF, DKIM, bounces

## Utilisations avancées

### Envoi depuis d'autres serveurs SMTP

On vient de le voir, vous pouvez tout à fait envoyer un email lié à votre domaine via n'importe quel serveur d'envoi. La seule condition lorsque vous envoyez depuis un logiciel de messagerie est qu'il soit autorisé à utiliser ce serveur en s'authentifiant auprès de lui.

Vous pouvez donc très bien envoyer un email lié à un domaine enregistré chez 1&1 via le serveur d'envoi d'Orange si vous avez aussi une adresse _@orange.fr_. Il suffit que vous changiez le serveur SMTP, ainsi que l'identifiant et le mot de passe pour l'envoi dans les paramètres du compte dans le logiciel.

### Utiliser les services d'email d'un autre prestataire

J'en ai parlé rapidement dans le chapitre sur les paramètres DNS des noms de domaine, les enregistrements MX d'un domaine déterminent chez quel hébergeur sont hébergés vos emails. Si l'hébergeur chez qui vous achetez le domaine mets les siens par défaut, vous pouvez en changer.

### Envoi depuis n'importe quelle adresse d'expéditeur

De la même manière, vous pouvez envoyer des emails depuis n'importe quelle adresse, même une qui n'existe pas !

Lors de la configuration d'une boite dans un logiciel de messagerie, l'une des premières informations demandées est une adresse email. Mais c'est uniquement l'adresse qui sera indiquée par le logiciel en tant qu'adresse d'envoi de vos emails. Cette information n'est que du texte parmi les différentes données de l'email. Tant que vous indiquez un serveur d'envoi correct, votre email partira.

Attention toutefois si vous faites cela, et si vos destinataire vous répondent, leur email n'arrivera nulle part si l'adresse n'existe vraiment pas en tant que redirection ou boite quelque part.

> Mais heuuu, est-ce que ça veut dire que potentiellemnt n'importe qui peut envoer un email qui aura l'air de venir de mon adresse ?

En effet ! C'est l'une des vulnérabilité des emails : il est facile d'usurper l'adresse d'expéditeur. C'est bien pourquoi il y a des mécanisme de protection tels que l'enregistrement SPF.

### L'enregistrement SPF

L'__enregistrement SPF__ (Sender Policy Framework) est une __bonne pratique__ et un __mécanisme de protection__ contre l'usurpation d'email.

Concrètement c'est un enregistrement TXT parmi les paramètres DNS de votre domaine avec une valeur particulière qui a pour finalité d'indiquer que __seuls les serveurs d'envoi de votre prestataire ont le droit d'envoyer des emails liés à votre domaine__.

Lorsqu'un serveur reçoit un email, il va vérifier si un tel enregistrement existe sur le domaine et va ensuite comparer le serveur qui a envoyé celui qu'il vient de recevoir avec ceux listés par l'enregistrement SPF. Si le serveur d'envoi n'est pas listé, alors l'email sera probablement rejeté (l'action exacte dépend de la valeur de l'enregistrement) et un message d'erreur sera envoyé à l'expéditeur de l'email pour l'en informer.

Reportez-vous à la documentation de votre hébergeur pour connaitre l'enregistrement SPF à rajouter à votre domaine.

> Le terme _enregistrement SPF_ est un abus de langage puisque l'enregistrement est en fait de type TXT. Mais il existait avant un enregistrement de type SPF qui n'était utilisé que pour ça. Comme la valeur de l'enregistrement n'est que du texte brut, son utilisation a été dépréciée en faveur de l'enregistrement de type TXT qui est générique et sert à bien d'autres choses.

## L'entête DKIM

__DKIM__ (DomainKeys Identified Mail) est un moyen de __s'assurer que l'email reçut est bien le même que celui qui a été envoyé__. 

Concrètement, au moment de l'envoi, le serveur d'envoi __chiffre__ le contenu de l'email et quelques autres informations. C'est à dire qu'il les rend illisible en les transformant d'une manière qui n'est reproductible que par lui-même. Il rajoute ensuite ces informations chiffrées parmi les entêtes de l'email lui-même avant de l'envoyer.

Le serveur qui reçoit cet email doit __comparer la version chiffrée avec la version non chiffrée__. Si les deux sont identiques, c'est que l'email n'a pas été modifié par un pirate sur le chemin.

Afin de comparer les deux versions, le serveur qui reçoit cet email va __déchiffrer__ la partie chiffrée en utilisant une information qu'il trouve dans les paramètres DNS du domaine. Plus exactement, c'est la valeur d'un enregistrement TXT publié sur un sous-domaine particulier :  `_[sélecteur]._domainkey.votreentreprise.com`. La valeur de _[sélecteur]_ change suivant le cas.

La majorité des fournisseurs d'emails grand publiques (grands hébergeurs et FAI) n'implémentent pas ce système.

## Anatomie d'un email

Concrètement, un email est __un fichier texte qui voyage par Internet__. Il est constitué de deux parties :

### Le contenu

Le contenu est comme son nom l'indique le texte que vous tapez et qui sera lu par votre destinataire.

Aujourd'hui le contenu de quasiment tous les emails est en HTML (comme les pages web), ce qui permet d'avoir du contenu riche comme du texte en gras, des liens cliquables et des images.

Souvent une version texte brute est automatiquement générée par le logiciel de messagerie. C'est cette partie que le destinataire verra si il utilise un logiciel qui ne supporte pas le HTML ou qu'il a choisit de n'afficher que la version texte brute.

### Les entêtes

Les entêtes (ou la _source_, ou le _code source_) sont une série d'informations techniques telles que :

- L'adresse d'expéditeur,
- le ou les adresses de destination,
- l'entête DKIM lorsque l'email est signé,
- et surtout -lorsque l'email a été reçut- l'ensemble des serveurs par lesquels l'email a transité.

Tous les webmail et logiciels de messagerie permettent de voir les entêtes.

Leurs analyse est cruciale dans la résolutions de certains problèmes.

## Les bounces, ou emails d'erreur en cas de rejet

Lorsqu'un email est envoyé d'un serveur à un autre, celui qui le reçoit répond au serveur qui envoi avec un code. Ce code indique si l'email a bien été reçut et accepté ou au contraire si il est rejeté, le code correspond alors à la raison. C'est donc le serveur d'envoi (celui de votre hébergeur) qui va alors vous envoyer un __bounce__ (qui signfie _rebondir_ en anglais), c'est à dire un email explicatif reprenant la raison du rejet et les entêtes de l'email rejeté.

Ces emails sont envoyés depuis un expéditeur appelé souvent __Mail Delivery System_ et une adresse du type _mailer-daemon@herbergeur.com_.

Il contiennent une première partie, toujours en anglais, mais décrivant la situation et donnant le code d'erreur et son explication avec quelques informations techniques pertinentes. Il contient ensuite la source (entêtes + contenu) de l'email rejeté.

Ces emails sont techniques et ne sont pas facile à comprendre, mais la première partie contient la raison du rejet en plein anglais. Il suffit de connaitre les raisons les plus classiques et de les chercher afin que vous puissiez comprendre par vous-même pourquoi vous avez reçut un bounce. Vous pouvez trouver une partie des messages les plus fréquents‌ [sur le centre d'assistance de 1&1](https://assistance.1and1.fr/email-and-office-365-c65618/1and1-postmaster-c85266/messages-d-erreur-smtp-des-serveurs-de-messagerie-1and1-a793443.html).
