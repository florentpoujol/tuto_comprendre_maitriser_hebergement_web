# Domaine : Transfert

> Ahhh ... les transferts de domaine...
> __Ou la source n°1 de stress et de drame sur le web !__ :-°

Un domaine est __transféré__ lorsqu'il change de titulaire et/ou de bureau d'enregistrement sans passer par la phase expiration/rédemption/rachat.

Cela arrive lorsque vous changez d'hébergeur, ou que vous donnez la gestion du domaine au webmaster qui vous fait votre nouveau site, ou lorsque vous vous séparez d'un domaine que vous possédiez mais que vous avez cédé à quelqu'un qui le souhaitait, etc...

Les domaines étant des propriétés, et souvent quelque chose de très impcritique dans la vie de ses propriétaires, il existe plusieurs mécanisme de protection contre les transferts non souhaités.  C'est l’absence de maîtrise de ces protections lors d'un transfert qui est responsable de délais anormaux lors des transferts.

# La préparation

> Transfert bien préparé, transfert assuré !

Pour qu'il se passe bien, il convient de connaître les étapes d'un transfert et de vérifier les différentes informations qui vont rentrer en ligne de compte.

## Code d'autorisation de transfert

Le __code d'autorisation de transfert__ (ou _code auth_, ou _auth code_, ou _auth-info_) est un mot de passe lié à chaque domaine, c'est la principale protection contre les transferts non souhaités. Ce code est demandé par l'interface de transfert de domaine sur le compte client/bureau d'enregistrement de destination. Si jamais le code rentré est faux, le transfert ne démarrera pas du tout ou échouera. Dans ce dernier cas, le code peut être corrigé par la suite.

## Adresse email du titulaire du domaine

On a déjà vu deux raisons pour lesquelles cette adresse email est très importante : le registre ou bureau d'enregistrement peuvent vous y envoyer des emails importants avec des instructions à suivre et vous y êtes informé du prochain renouvellement ou expiration du domaine.

Le transfert est une autre raison. Une deuxième protection contre les transferts non voulus est que dans tous les cas un email est envoyé à l'adresse du titulaire actuel. Cet email l'informe de la demande de transfert et lui demande de la confirmer en cliquant sur un lien présent à cet effet dans cet email.

> Que se passe-t-il si l'adresse n'est pas valide ?

En l'absence de confirmation, le transfert échoue automatiquement généralement au bout de 2 semaines.

Dans tous les cas, il faut alors que le titulaire actuel fasse le nécessaire pour modifier l'adresse email, puis que le nouveau bureau d'enregistrement relance la demande de transfert, ce qui renvoi l'email de validation.

Quand je dis _fasse le nécessaire_ cela signifie que dans le meilleur des cas, il suffit de se connecter à l'espace client. Mais dans le pire des cas, il faut envoyer un email au bureau d'enregistrement avec typiquement un formulaire et un justificatif d'identité du titulaire (pièce d'identité ou Kbis), puis attendre que la demande soit traitée, ce qui peut prendre plusieurs jours.

> Une adresse email de l'ancien titulaire non valide est la raison n°1 de délais anormaux dans le transfert de domaine. 

## Verrouillage du domaine

Pour la plupart des extensions, les domaines sont habituellement verrouillés, ce qui les protège par défaut des transferts, même avec un code auth valide. Il faut donc déverrouiller le domaine via l'espace client du bureau d'enregistrement actuel avant de lancer le transfert.

L'état de verrouillage du domaine est une information publique qui se voit en whois. Par exemple avec le domaine openclassrooms.com, on voit qu'il a un statut  clientTransferProhibited , ce qui signifie précisément qu'il ne peut être transféré. Lorsque le verrouillage est enlevé, ce statut disparaît.

Là encore si le transfert est lancé alors que le domaine est verrouillé, il va échouer mais peu être relancé par la suite.

> Les  .fr  sont les seuls domaines que je connaisse qui n'ont pas ce système de verrouillage.

## Date d'achat ou de dernier renouvellement

La majorité des registres imposent le fait qu'un nom de domaine ne peut changer de bureau d'enregistrement dans les soixante jours suivant son achat ou son dernier renouvellement. Cela n'empêche donc toutefois pas un domaine de changer de titulaire et/ou de compte client si il reste chez le même bureau d'enregistrement.

Vous le verrez dans la prochaine partie, il reste possible d'utiliser un domaine chez un autre hébergeur mais sans le transférer.

Les .fr ne sont également pas concernés par cette règle.

## Exemples de transfert

On va prendre deux exemples, un avec un  .com, et un avec un  .fr  parce qu'apparemment on ne peut jamais rien faire comme les autre en France :D.

### Transfert d'un  .com 

Vous êtes une société qui change d'hébergeur parce que les prix sont plus attractifs chez un concurrent. Vous vous connectez donc à votre espace client chez votre hébergeur actuel et vous vous rendez sur la page de gestion de votre nom de domaine.

Vous __vérifiez que l'adresse email liée au titulaire est bien connue de vous, qu'elle est active et que vous pouvez la consulter__. Vous cliquez sur le bouton afin de __déverrouiller le domaine__ et vous copiez/collez quelque part le __code d'autorisation de transfert__ qui est affiché.

> Chez certains hébergeurs, le code auth est envoyé par email au lieu d'être affiché sur l'espace client.

> Chez certains hébergeurs, notamment OVH, le code auth a une durée limitée de sept jours partir du moment où vous le demandez. Donc si pour X raison, vous mettez trops de temps avant de lancer le transfert ou qu'il doit être relancé par la suite, il faudra redemander un code et repartir de zéro.

Vous vous rendez donc ensuite sur votre espace client chez le nouvel hébergeur, et vous demandez à transférer le domaine _otreentreeprise.com_. Vous rentrez le code d'autorisation lorsque l'interface vous le demande, vous terminez la procédure et le transfert se lance.

Quelques minutes à quelques heures après, vous recevez l'email qui vous informe et vous demande de confirmer le transfert. Vous cliquez donc sur le lien pour confirmer.

A partir de là, vous n'avez plus rien à faire d'autre qu'a attendre.

> Attendre quoi, et combien de temps?

Attendre que le domaine parte de l'ancien bureau d'enregistrement. Rarement, ça peut mettre seulement quelques heures. La plupart du temps, cela met __plusieurs jours__, le plus souvent quatre à huit.

Une fois que le domaine est transféré chez le nouvel hébergeur, il faut encore attendre la __propagation des paramètres DNS__ du nouvel hébergeur. Je reviendrais sur cette notion de propagation dans le chapitre suivant. Cette durée peu être mitigée en modifiant si possible les serveurs DNS du domaine chez l'hébergeur actuel avant que le domaine ne parte.

Et voilà, après quelques jours, le domaine a enfin changé de prestataire, de titulaire et de paramètres DNS !

> Dans le cas des transferts sans changement de bureau d'enregistrement, le délai de transfert est bien plus réduit, typiquement de l'ordre de quelques d'heures (après validation par l'ancien titulaire).

### Transfert d'un  .fr 

Maintenant, compliquons encore un peu les choses en transférant un  .fr.

On a déjà vu que la première particularité du  .fr est qu'il n'y a pas besoin de le déverrouiller.

La deuxième et la principale à comprendre est que le transfert technique d'un bureau d'enregistrement à un autre et le changement de titularité sont __deux opérations distinctes qui viennent l'une après l'autre__.

La troisième est qu'il n'y a pas de validation du transfert technique via email. C'est la validation du changement de titularité, que l'on appelle la __transmission__, qui se fait par email.

Voyons ça dans un exemple :

Vous vous connectez donc à votre espace client chez votre hébergeur actuel, vous vous rendez sur la page de gestion de votre nom de domaine. Vous vérifiez que l'adresse email liée au titulaire est bien connue de vous, qu'elle est active et que vous pouvez la consulter. Vous copiez/collez quelque part le code d'autorisation de transfert qui est affiché.

Vous vous rendez donc ensuite sur votre espace client chez le nouvel hébergeur, et vous demandez à transférer le domaine _votreentreeprise.fr_. Vous rentrez le code d'autorisation lorsque l'interface vous le demande, vous terminez la procédure et le transfert se lance.

A partir de là, vous n'avez plus rien à faire d'autre qu'à attendre (jusqu'à plusieurs jours) le transfert. Le transfert est lancé, le domaine change de bureau d'enregistrement et __juste après__ la transmission (le changement de titularité) se lance enfin.

Et là il n'y a pas un email envoyé par l'hébergeur, mais __trois emails envoyés par l'Afnic__ (depuis l'adresse nic@nic.fr).

- Un est envoyé à l'ancien titulaire (le __cédant__) et lui demande de confirmer la transmission.
- Un est envoyé à l'ancien contact administratif et l'informe seulement de la transmission.
- Le dernier email est lui envoyé au nouveau titulaire (le __repreneur__) qui doit lui aussi confirmer la transmission en cliquant sur le lien approprié dans cet email.

Il y a donc __deux emails__ importants qu'il faut s'assurer d'avoir reçut (celui envoyé au contact administratif ne compte pas puisqu'il est juste informatif). Lorsque la transmission est terminée parce que le lien a été cliqué dans ces deux emails, alors le repreneur et le cédant reçoivent un dernier email les informant du succès de la transmission.

Même si le domaine est déjà chez le nouvel hébergeur, il est important de terminer l'étape de transmission car sinon l'hébergeur ne vous donnera sans doute pas la main dessus puisque vous n'en êtes pas propriétaire. Vous ne pourrez donc rien en faire, ce qui est plutôt dommage.

> Il ne faut en aucun cas que l'adresse email du titulaire du domaine (nouveau ou ancien) ne soit liée à ce même domaine.

C'est à dire que si vous transférez le domaine _votreentreprise.fr_, il ne faut pas que l'adresse de contact soit par exemple _contact@votreentreprise.fr_ car __les emails de l'Afnic ne seront pas reçut__ puisque le domaine sera déjà transféré et que l'adresse email ‌n'aura probablement pas encore été recréé du coté du nouvel hébergeur.

> Comment ça "pas recréé du coté du nouvel hébergeur" ? Le site web et les adresses emails ne sont pas transférés avec le domaine ?

Eh non grand fou ! o_O L'informatique, c'est pas magique !

Transférer un domaine ne transfert que le nom de domaine, pas les adresses email, ni le site web, ni les paramètres techniques (DNS) (sauf pour ces derniers si l'interface du nouvel hébergeur le permet).

## En résumé

- Il y a trois choses à faire pour préparer un transfert : vérifier l'adresse email du titulaire, noter le code auth et déverrouiller le domaine (pas de déverrouillage pour les  .fr ).
- Le transfert se demande depuis le nouveau bureau d'enregistrement.‌
- Pour la plupart des domaines l'ancien titulaire reçoit alors un email lui demandant de confirmer (ou de refuser) le transfert.
- Pour les  .fr , c'est l'Afnic qui envoi deux emails, un au cédant et un au repreneur (l'ancien et le nouveau titulaire) leur demandant de confirmer spécifiquement la transmission, c'est à dire le changement de titulaire.

> Attention si l'email de contact du domaine (tant l'ancien que le nouveau) utilise un système anti-spam intermédiaire tels que spamsenmoins.com ! Ces systèmes bloquent les emails reçut de destinataires non connus et leur demandent de s'authentifier en leur répondant avec un email dans lequel ils doivent cliquer sur un lien les emmenant sur une page web où ils doivent remplir un captcha.
>
> Les robots envoyant les emails de validation de transfert ou de transmission ne feront pas tout ça !
> 
> Donc si vous utilisez ce genre d'anti-spam, pensez bien a aller trouver ces emails de confirmation de transfert dans leur boite de spam.‌
