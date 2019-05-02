<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="9b7d5-101">Dans cet exercice, vous allez créer un connecteur personnalisé qui peut être utilisé dans le flux ou dans les applications de logique Azure.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="9b7d5-102">Le fichier de définition de l’API Open est prédéfini avec le chemin d’accès correct `$batch` pour le point de terminaison Microsoft Graph et les paramètres supplémentaires pour activer l’importation simple.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="9b7d5-103">À l’aide d’un éditeur de texte, créez un `MSGraph-Delegate-Batch.swagger.json` fichier vide nommé et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="9b7d5-104">Ouvrez un navigateur et accédez à [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="9b7d5-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="9b7d5-105">Connectez-vous à l’aide de votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="9b7d5-106">Sélectionnez l’icône d’engrenage dans le coin supérieur droit, puis sélectionnez l’élément **connecteurs personnalisés** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Capture d’écran du menu déroulant dans Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="9b7d5-108">Sur la page **connecteurs personnalisés** , cliquez sur le lien **créer un connecteur personnalisé** dans le coin supérieur droit, puis sélectionnez l’élément **Importer un fichier d’API ouvert** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Capture d’écran du menu déroulant créer un connecteur personnalisé dans Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="9b7d5-110">Entrez `MS Graph Batch Connector` dans la zone de texte **nom du connecteur personnalisé** .</span><span class="sxs-lookup"><span data-stu-id="9b7d5-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="9b7d5-111">Choisissez l’icône de dossier pour télécharger le fichier d’API ouvert.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="9b7d5-112">Accédez au `MSGraph-Delegate-Batch.swagger.json` fichier que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="9b7d5-113">Choisissez **Continuer** pour charger le fichier d’API ouvert.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Capture d’écran de la boîte de dialogue créer un connecteur personnalisé](./images/flow-conn3.png)

<span data-ttu-id="9b7d5-115">Sur la page Configuration du connecteur, cliquez sur le lien **sécurité** dans le menu de navigation.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="9b7d5-116">Renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="9b7d5-117">**Choisissez l’authentification qui est implémentée par votre API**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="9b7d5-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="9b7d5-118">**Fournisseur d’identité**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="9b7d5-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="9b7d5-119">**ID client**: ID d’application que vous avez créé dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="9b7d5-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="9b7d5-120">Clé **secrète client**: la clé que vous avez créée dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="9b7d5-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="9b7d5-121">**URL de connexion**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="9b7d5-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="9b7d5-122">**ID de client**:`common`</span><span class="sxs-lookup"><span data-stu-id="9b7d5-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="9b7d5-123">**URL**de la `https://graph.microsoft.com` ressource: (sans finalisation/)</span><span class="sxs-lookup"><span data-stu-id="9b7d5-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="9b7d5-124">**Étendue**: laisser vide</span><span class="sxs-lookup"><span data-stu-id="9b7d5-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="9b7d5-125">Sélectionnez **créer un connecteur** dans la partie supérieure droite.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-125">Choose **Create Connector** on the top-right</span></span>

![Capture d’écran de l’onglet sécurité dans la configuration du connecteur](./images/flow-conn4.png)

<span data-ttu-id="9b7d5-127">Une fois le connecteur créé, copiez l' **URL**de redirection générée.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Capture d’écran de l’URL de redirection générée](./images/flow-conn5.png)

<span data-ttu-id="9b7d5-129">Revenez à l’application inscrite dans le [portail Azure](https://aad.portal.azure.com) que vous avez créé dans l’exercice précédent.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="9b7d5-130">Sélectionnez **URL de réponse** dans le panneau **paramètres** .</span><span class="sxs-lookup"><span data-stu-id="9b7d5-130">Select **Reply URLs** in the **Settings** blade.</span></span> <span data-ttu-id="9b7d5-131">Ajoutez l' **URL** de redirection que vous avez copiée en tant qu' **URL de réponse**supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-131">Add the **Redirect URL** you copied as an additional **Reply URL**.</span></span> <span data-ttu-id="9b7d5-132">Enregistrez l’application dans le portail Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9b7d5-132">Save the application in Azure Active Directory portal.</span></span>

![Capture d’écran du panneau URL de réponse dans le portail Azure](./images/flow-conn6.png)