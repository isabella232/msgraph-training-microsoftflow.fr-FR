<!-- markdownlint-disable MD002 MD041 -->

L'étape de configuration finale permettant de s'assurer que le connecteur est prêt à être utilisé est d'autoriser et de tester le connecteur personnalisé afin de créer une connexion mise en cache.

> [!IMPORTANT]
> Pour suivre les étapes suivantes, vous devez être connecté avec des privilèges d'administrateur.

Dans [Microsoft Flow](https://flow.microsoft.com), accédez à l'écran de configuration du connecteur et cliquez sur le lien **test** dans le menu de navigation. Sélectionnez le lien **nouvelle connexion** . Connectez-vous à l'aide de votre compte Azure Active Directory de l'administrateur client Office 365.

Lorsque vous êtes invité à entrer les autorisations demandées, vérifiez le **consentement au nom de votre organisation** , puis choisissez **accepter** pour autoriser les autorisations.

![Capture d'écran de l'invite d'autorisation](./images/flow-conn8.png)

Une fois que vous avez autorisé les autorisations, une connexion est créée dans le flux.

![Capture d'écran de la connexion créée dans Microsoft Flow](./images/flow-conn9.png)

Le connecteur personnalisé est maintenant configuré et activé. Il peut y avoir un retard dans les autorisations appliquées et disponibles, mais le connecteur est maintenant configuré.