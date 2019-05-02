<!-- markdownlint-disable MD002 MD041 -->

Dans cet exercice, vous allez créer un connecteur personnalisé qui peut être utilisé dans le flux ou dans les applications de logique Azure. Le fichier de définition de l’API Open est prédéfini avec le chemin d’accès correct `$batch` pour le point de terminaison Microsoft Graph et les paramètres supplémentaires pour activer l’importation simple.

À l’aide d’un éditeur de texte, créez un `MSGraph-Delegate-Batch.swagger.json` fichier vide nommé et ajoutez le code suivant.

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

Ouvrez un navigateur et accédez à [Microsoft Flow](https://flow.microsoft.com). Connectez-vous à l’aide de votre compte d’administrateur client Office 365. Sélectionnez l’icône d’engrenage dans le coin supérieur droit, puis sélectionnez l’élément **connecteurs personnalisés** dans le menu déroulant.

![Capture d’écran du menu déroulant dans Microsoft Flow](./images/flow-conn1.png)

Sur la page **connecteurs personnalisés** , cliquez sur le lien **créer un connecteur personnalisé** dans le coin supérieur droit, puis sélectionnez l’élément **Importer un fichier d’API ouvert** dans le menu déroulant.

 ![Capture d’écran du menu déroulant créer un connecteur personnalisé dans Microsoft Flow](./images/flow-conn2.png)

Entrez `MS Graph Batch Connector` dans la zone de texte **nom du connecteur personnalisé** . Choisissez l’icône de dossier pour télécharger le fichier d’API ouvert. Accédez au `MSGraph-Delegate-Batch.swagger.json` fichier que vous avez créé. Choisissez **Continuer** pour charger le fichier d’API ouvert.

 ![Capture d’écran de la boîte de dialogue créer un connecteur personnalisé](./images/flow-conn3.png)

Sur la page Configuration du connecteur, cliquez sur le lien **sécurité** dans le menu de navigation. Renseignez les champs comme suit.

- **Choisissez l’authentification qui est implémentée par votre API**:`OAuth 2.0`
- **Fournisseur d’identité**:`Azure Active Directory`
- **ID client**: ID d’application que vous avez créé dans l’exercice précédent
- Clé **secrète client**: la clé que vous avez créée dans l’exercice précédent
- **URL de connexion**:`https://login.windows.net`
- **ID de client**:`common`
- **URL**de la `https://graph.microsoft.com` ressource: (sans finalisation/)
- **Étendue**: laisser vide

Sélectionnez **créer un connecteur** dans la partie supérieure droite.

![Capture d’écran de l’onglet sécurité dans la configuration du connecteur](./images/flow-conn4.png)

Une fois le connecteur créé, copiez l' **URL**de redirection générée.

![Capture d’écran de l’URL de redirection générée](./images/flow-conn5.png)

Revenez à l’application inscrite dans le [portail Azure](https://aad.portal.azure.com) que vous avez créé dans l’exercice précédent. Sélectionnez **URL de réponse** dans le panneau **paramètres** . Ajoutez l' **URL** de redirection que vous avez copiée en tant qu' **URL de réponse**supplémentaire. Enregistrez l’application dans le portail Azure Active Directory.

![Capture d’écran du panneau URL de réponse dans le portail Azure](./images/flow-conn6.png)