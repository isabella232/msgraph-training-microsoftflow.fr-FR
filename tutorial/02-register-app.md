<!-- markdownlint-disable MD002 MD041 -->

Dans cet exercice, vous allez créer une nouvelle application Azure Active Directory qui sera utilisée pour fournir les autorisations déléguées pour le connecteur personnalisé.

Ouvrez un navigateur et accédez au [Centre d’administration Azure Active Directory](https://aad.portal.azure.com). Choisissez le lien **Azure Active Directory** dans le menu de navigation de gauche, puis choisissez l’entrée **inscriptions des applications** dans la section **gérer** du panneau **Azure Active Directory** .

![Capture d’écran du panneau Azure Active Directory dans le centre d’administration Azure Active Directory](./images/app-registrations.png)

Choisissez l’élément de menu **nouvel enregistrement** en haut du panneau **inscriptions des applications** .

![Capture d’écran du panneau inscriptions des applications dans le centre d’administration Azure Active Directory](./images/new-registration.png)

Entrez `MS Graph Batch App` dans le champ **nom** . Dans la section **types de comptes pris en charge** , sélectionnez **comptes dans n’importe quel annuaire d’organisation**. Laissez la section **URI de redirection** vide, puis choisissez **inscrire**.

![Capture d’écran du Registre enregistrer une application dans le centre d’administration Azure Active Directory](./images/register-an-app.png)

Sur le panneau de l’application de **lot MS Graph** , copiez l' **ID d’application (client)**. Vous en aurez besoin dans l’exercice suivant.

![Capture d’écran de la page d’application inscrite](./images/app-id.png)

Choisissez l’entrée des autorisations de l' **API** dans la section **gérer** du panneau d' **application de commandes MS Graph** . Sélectionnez **Ajouter une autorisation** sous **autorisations d’API**.

![Capture d’écran du panneau autorisations d’API](./images/api-permissions.png)

Dans le panneau **autorisations d’API de demande** , sélectionnez **Microsoft Graph**, puis **autorisations déléguées**. Recherchez `group` , puis sélectionnez l’autorisation de **lecture et d’écriture de tous les groupes** . Sélectionnez **Ajouter des autorisations** au bas du panneau.

 ![Capture d’écran du panneau des autorisations d’API de demande](./images/select-permissions.png)

Choisissez l’entrée **certificats et secrets** dans la section **gérer** du panneau d' **application de commandes MS Graph** , puis choisissez **nouvelle clé secrète client**. Entrez `forever` dans la **Description** et sélectionnez **jamais** sous **expire**. Sélectionnez **Ajouter**.

![Capture d’écran du panneau certificat et secrets](./images/create-client-secret.png)

Copiez la valeur de la nouvelle clé secrète. Vous en aurez besoin dans l’exercice suivant.

![Capture d’écran de la nouvelle clé secrète client](./images/copy-client-secret.png)

> [!IMPORTANT]
> Cette étape est essentielle, car le secret ne sera pas accessible une fois que vous aurez fermé cette Blade. Enregistrez cette clé secrète dans un éditeur de texte pour l’utiliser dans les exercices à venir.

Pour permettre la gestion des services supplémentaires accessibles via Microsoft Graph, y compris les propriétés Teams, vous devez sélectionner des étendues supplémentaires appropriées pour activer la gestion de services spécifiques. Par exemple, pour étendre notre solution afin de créer des blocs-notes ou des plans de planification, des compartiments et des tâches OneNote, vous devez ajouter les étendues d’autorisation requises pour les API pertinentes.
