# Résolution des problèmes

Comme tous systèmes, les emails sont source de nombreux problèmes. Heureusement les moyens de les prévenir et les solutions sont aussi nombreux.

## Mes emails ne partent pas !

La première chose à vérifier est si vos emails partent effectivement bien. Si vous n'avez pas eu d'erreur lorsque vous avez appuyé sur le bouton Envoyer dans votre logiciel de messagerie favori et que l'email a quitté la boite d'envoi pour se ranger sagement dans les éléments envoyés, c'est qu'il est effectivement partit.

Si c'est un problème de paramétrage du logiciel de messagerie, il vous indiquera une erreur, et souvent vous renverra vers la page où vous pouvez modifier les paramètres de synchronisation. Dans ce cas, reportez-vous aux tutoriels de votre hébergeur et corrigez les paramètres.

Vérifiez aussi a tout hasard que vous êtes bien connecté à Internet. Surtout si vous êtes sur un téléphone mobile, __ne supposez pas : vérifiez en tentant d'aller par exemple sur Google ou le site de votre hébergeur__.

Si l'envoi marchait avant et qu'il n'y a que ça qui a cessé de fonctionné, il se peut que votre boite soit bloquée en envoi par votre hébergeur. Vérifiez le contenu de votre boite de réception et/ou l'adresse principale de contact de votre compte client pour y trouver un email informatif de la part de votre hébergeur concernant cette situation, avec la procédure à suivre afin d'être débloqué. Typiquement cela arrive lorsque vous avez dépassé les limites d'envoi ou que l'hébergeur a détecté que l'adresse est peu être utilisée pour envoyer du spam.

Vérifiez aussi le quota de votre boite, car les emails envoyés prennent autant de place que les emails reçut. Si votre quota est plein, vous ne pouvez plus créer de nouveaux emails envoyé, donc vous ne pouvez plus envoyer.

## Mes emails partent mais n'arrivent pas !

Là encore, vérifiez d'abord si l'email est bien partit. Une fois l'email partit, __l'hébergeur n'est plus responsable de ce qu'arrive à votre email__, ou dit autrement :

> __Votre hébergeur n'est pas responsable de la réception de vos emails.__

Un email ne peut pas se perdre en chemin (ou alors il y a vraiment un gros soucis), il y a donc toutes les chances que votre email soit bien arrivé dans les systèmes de votre destinataire, mais pas dans sa boite de réception.

Si pour X raison votre email est rejeté par le serveur qui le reçoit, c'est son boulot de vous en informer en vous envoyant un bounce. __En l'absence de bounce reçut dans les quelques minutes après l'envoi de votre email, on ne peut que supposer qu'il a été reçut.__

> Email dans les éléments envoyé + pas de bounce = email reçut.

> Mais mon destinataire ne l'a vraiment pas dans sa boite de réception, ni dans les spams !

Il est possible qu'il n'ai en effet pas atteint le logiciel de votre destinataire.

Suivant le cas il est possible que le dossier de spam du logiciel de messagerie ne soit pas synchronisé avec le serveur et que donc l'email soit bien arrivé dans la boite mais soit resté bloqué dans le dossier de spam du serveur. L'email est alors visible en se connectant au webmail.

> Même sur leur webmail, ils ne trouvent pas mon email !

Alors c'est qu'il n'est pas encore arrivé ou n'a pas encore été rejeté.

> Rien dans le système des emails ne garantit que l'envoi et la réception soient quasi-instantanés.

C'est le cas la plupart du temps mais si les serveurs d'envoi ou de réception sont surchargés, alors ils mettront du temps à s'occuper de votre email. Un délai pouvant aller jusqu'à un quart d'heure est à considérer comme normal. En cas de délai avéré, une analyse des entêtes de l'email reçut pourra déterminer quel système est lent.

## Mes emails arrivent en spam !

> Le principal facteur qui va déterminer si votre email arrive en spam chez votre destinataire est son contenu textuel.

D'une manière générale, l'idée pour ressembler le moins possible à un spammeur est d'avoir un ratio équilibré de texte par rapport au nombre de liens ou d'images.

Vous pouvez aussi rajouter un enregistrement SPF à votre domaine et si possible signer vos emails avec DKIM. Ces deux systèmes sont une bonne pratique et donc contribuent à augmenter un peu le score de vos emails dans les systèmes anti-spam. Ce n'est donc en aucun cas une recette miracle

> Votre hébergeur n'est pas responsable du classement en spam de vos emails.

Même si le même email n'est pas jugé comme spam lorsqu'il est envoyé depuis une autre adresse. __Votre hébergeur ne contrôle pas le fonctionnement de l'anti-spam de votre destinataire__.

Le seul cas où l'hébergeur peut avoir un impact sur le classement en spam de vos emails est si le système anti-spam de votre destinataire prend en compte des paramètres liés à __la réputation des serveurs d'envoi__. 

Si c'est bien un facteur qui peut limiter la délivrabilité de vos emails, votre hébergeur n'a pas de solution magique, _sinon il l'aurait déjà appliqué_. Si vraiment c'est quelque chose qui vous gène, vous n'avez d'autre choix que de changer d'hébergeur, au moins pour les emails.

Dans la majorité des cas, vous pouvez demander à votre correspondant d'ajouter votre adresse à la liste blanche de son anti-spam afin que les adresses de votre domaine ne soient jamais évalués par celui-ci.

Mais là aussi ça ne garantit rien car l'hébergeur lui-même aura sans doute un anti-spam évaluant les emails entrants (et sortants) avant même l'évaluation par l'anti-spam de la boite du destinataire.

## Je ne reçois rien !

La première chose à vérifier dans ce cas est le domaine et ses enregistrements MX. Le domaine existe-il toujours, est-il bloqué, les enregistrement MX existent-ils, sont-ils corrects ? Si ils sont corrects, il faut vérifier si les expéditeurs ont reçut un bounce. 

Si oui, c'est que leur email a été rejeté par le serveur de votre hébergeur. Il faut alors l'analyser pour trouver la raison (votre boite est pleine, mauvais enregistrement SPF sur leur domaine, etc...).

Si non, l'email a bien été reçut dans votre boite. Si vous ne le voyez pas c'est peut être qu'il a été classé ailleurs que la boite de réception par une règle de filtrage ou bien il a été classé comme spam, et donc vous ne l'avez peu être pas reçut dans votre logiciel de messagerie (cf paragraphe ci-dessus).

> Les spams sont un fléau dont vous devez vous protéger grâce à un système anti-spam. Néanmoins vous devez vous assurer de pouvoir consulter régulièrement le dossier de spam de votre boite, car les faux-positif (un email légitime classé par erreur en spam) arrivent plus souvent que vous ne le pensez.
>
> Lorsque vous semblez ne pas avoir reçut un email que vous attendiez, le dossier de spam du serveur (donc sur le webmail) est le premier endroits où vous devez le chercher.‌

## Je reçois plein de bounces alors que je n'envois rien !

> Votre hébergeur n'est pas responsable des emails que vous recevez.

> Ce n'est pas à lui de résoudre ce problème, mais son Support peut néanmoins vous aider à analyser la situation.

Lorsque vous recevez des bounces alors que vous n'envoyez pas vous même d'email, cela peut être dû généralement par trois situations :

### Votre adresse se fait usurpée par un spammeur

Lorsque vous recevez un bounce, ça veut dire qu'un email a été envoyé avec votre adresse en tant qu'adresse d'expéditeur puis qu'il a été refusé par le serveur qu'il l'a reçut. Il en informe donc "l'expéditeur" apparent en envoyant un bounce à votre adresse.

L'adresse d'expéditeur est juste une ligne dans le "fichier texte" que représente l'email, c'est pourquoi il est si facile d'y mettre n'importe quoi. Cela est souvent utilisé par des spammeurs qui vont mettre votre adresse en tant qu'expéditeur de leurs emails afin de paraître un tant soit peu plus légitime dans les systèmes anti-spam qui vont les recevoir. Généralement cela ne marche pas très bien et beaucoup de serveurs refusent quand même leurs emails, ce qui génère ces bounces.

Dans ce cas, il n'y a aucun moyen d'empêcher les spammeurs de faire cela ! Vous pouvez (et devez) néanmoins contribuer à ce que ces spams soient systématiquement rejetés par les serveurs qui les reçoivent afin de ne pas importuner les destinataires. La solution dans ce cas est de mettre en place un enregistrement SPF.

Notez bien que cela ne contribue que à ce que la majorité des spams envoyés en votre nom soient rejetés et que donc cela augmente le nombre de bounce que vous recevez tant que les spammeurs n’arrêteront pas d'envoyer.

Si vous recevez vraiment beaucoup de bounce, une bonne idée est alors de mettre en place une règle de filtrage afin de déplacer automatiquement ces emails directement dans la corbeille par exemple, afin qu'ils soient facile à supprimer et ne vous importunent pas dans la boite de réception. Il est important de surveiller la fréquence de réception des bounces et supprimer la règle de filtrage lorsque les spammeurs ce sont lassés de votre adresse.

> En temps normal il est important de s'assurer de recevoir des bounces afin d'y réagir.

## Un autre système légitime -comme le site web- envoi effectivement des emails

Votre site peut se faire attaquer par des robots qui généralement tentent de remplir n'importe quel formulaire accessible (de contact, d'inscription, de commentaire, etc...). Cela génère souvent de la part du site des emails envoyés à l'adresse renseignée par les robots. De la même manière que les spammeurs vus juste au dessus, le site fait en sorte que l'adresse d'expéditeur de ces emails soit celle que vous avez configurée, souvent une adresse liée à votre domaine.

Dans certains cas, ces emails sont tellement nombreux qu'ils se font rejeter par le serveur qui est sensé les recevoir, d'où les bounces que vous recevez. La solution dans ce cas est de sécuriser les formulaires du site en ajoutant des systèmes anti-robots comme des captchas ou bien carrément de les désactiver.

## Le mot de passe de votre boite est compromis

‌Plus rarement -__mais ça arrive quand même plus que vous ne le pensez__-, c'est le mot de passe de votre boite qui a été trouvé. Quelqu'un d'autre envoi donc effectivement des emails depuis votre boite. La solution est donc de modifier le mot de passe par quelque chose de bien plus sécurisé qu'avant et par exemple de demander à votre anti-virus de faire un scan de votre ordinateur.
