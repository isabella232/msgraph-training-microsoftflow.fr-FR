<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="338c2-101">Dans cet exercice, vous allez créer un connecteur personnalisé qui peut être utilisé dans Microsoft Power Automated ou dans Azure Logic apps.</span><span class="sxs-lookup"><span data-stu-id="338c2-101">In this exercise, you will create a new custom connector which can be used in Microsoft Power Automate or in Azure Logic Apps.</span></span> <span data-ttu-id="338c2-102">Le fichier de définition OpenAPI est prédéfini avec le chemin d’accès correct pour le `$batch` point de terminaison Microsoft Graph et les paramètres supplémentaires pour activer l’importation simple.</span><span class="sxs-lookup"><span data-stu-id="338c2-102">The OpenAPI definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="338c2-103">Il existe deux options pour créer un connecteur personnalisé pour Microsoft Graph :</span><span class="sxs-lookup"><span data-stu-id="338c2-103">There are two options to create a custom connector for Microsoft Graph:</span></span>

- <span data-ttu-id="338c2-104">Créer à partir d’un champ vierge</span><span class="sxs-lookup"><span data-stu-id="338c2-104">Create from blank</span></span>
- <span data-ttu-id="338c2-105">Importer un fichier OpenAPI</span><span class="sxs-lookup"><span data-stu-id="338c2-105">Import an OpenAPI file</span></span>

## <a name="option-1-create-custom-connector-from-blank-template"></a><span data-ttu-id="338c2-106">Option 1 : créer un connecteur personnalisé à partir d’un modèle vierge</span><span class="sxs-lookup"><span data-stu-id="338c2-106">Option 1: Create custom connector from blank template</span></span>

<span data-ttu-id="338c2-107">Ouvrez un navigateur et accédez à [Microsoft Power Automated](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="338c2-107">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="338c2-108">Connectez-vous à l’aide de votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="338c2-108">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="338c2-109">Choisissez **données** dans le menu de gauche, puis sélectionnez l’élément **connecteurs personnalisés** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="338c2-109">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Capture d’écran du menu déroulant dans Microsoft Power Automated](./images/custom-connectors.png)

<span data-ttu-id="338c2-111">Sur la page **connecteurs personnalisés** , sélectionnez le **nouveau lien connecteur personnalisé** dans le coin supérieur droit, puis sélectionnez **créer à partir d'** un élément vide dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="338c2-111">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Create from blank** item in the drop-down menu.</span></span>

![Capture d’écran du nouveau menu déroulant connecteur personnalisé dans Microsoft Power Automated](./images/new-connector.png)

<span data-ttu-id="338c2-113">Entrez `MS Graph Batch Connector` dans la zone de texte **nom du connecteur** .</span><span class="sxs-lookup"><span data-stu-id="338c2-113">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="338c2-114">Choose **Continue**.</span><span class="sxs-lookup"><span data-stu-id="338c2-114">Choose **Continue**.</span></span>

<span data-ttu-id="338c2-115">Dans la page configuration **générale** du connecteur, renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="338c2-115">On the connector configuration **General** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="338c2-116">**Schéma**: https</span><span class="sxs-lookup"><span data-stu-id="338c2-116">**Scheme**: HTTPS</span></span>
- <span data-ttu-id="338c2-117">**Hôte**: `graph.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="338c2-117">**Host**: `graph.microsoft.com`</span></span>
- <span data-ttu-id="338c2-118">**URL de base**: `/`</span><span class="sxs-lookup"><span data-stu-id="338c2-118">**Base URL**: `/`</span></span>

<span data-ttu-id="338c2-119">Cliquez sur le bouton **sécurité** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="338c2-119">Choose **Security** button to continue.</span></span>

![Capture d’écran de l’onglet général de la configuration du connecteur](./images/general-tab.png)

<span data-ttu-id="338c2-121">Dans la page **sécurité** , renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="338c2-121">On the **Security** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="338c2-122">**Choisissez l’authentification qui est implémentée par votre API**: `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="338c2-122">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="338c2-123">**Fournisseur d’identité**: `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="338c2-123">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="338c2-124">**ID client**: ID d’application que vous avez créé dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="338c2-124">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="338c2-125">Clé **secrète client**: la clé que vous avez créée dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="338c2-125">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="338c2-126">**URL de connexion**: `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="338c2-126">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="338c2-127">**ID de client**: `common`</span><span class="sxs-lookup"><span data-stu-id="338c2-127">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="338c2-128">**URL**de la ressource : `https://graph.microsoft.com` (sans finalisation/)</span><span class="sxs-lookup"><span data-stu-id="338c2-128">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="338c2-129">**Étendue**: laisser vide</span><span class="sxs-lookup"><span data-stu-id="338c2-129">**Scope**: Leave blank</span></span>

<span data-ttu-id="338c2-130">Cliquez sur le bouton **définition** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="338c2-130">Choose **Definition** button to continue.</span></span>

![Capture d’écran de l’onglet sécurité dans la configuration du connecteur](./images/security-tab.png)

<span data-ttu-id="338c2-132">Sur la page **définition** , sélectionnez **nouvelle action** et renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="338c2-132">On the **Definition** page, select **New Action** and fill in the fields as follows.</span></span>

- <span data-ttu-id="338c2-133">**Résumé**: `Batch`</span><span class="sxs-lookup"><span data-stu-id="338c2-133">**Summary**: `Batch`</span></span>
- <span data-ttu-id="338c2-134">**Description**: `Execute Batch with Delegate Permission`</span><span class="sxs-lookup"><span data-stu-id="338c2-134">**Description**: `Execute Batch with Delegate Permission`</span></span>
- <span data-ttu-id="338c2-135">**ID d’opération**: `Batch`</span><span class="sxs-lookup"><span data-stu-id="338c2-135">**Operation ID**: `Batch`</span></span>
- <span data-ttu-id="338c2-136">**Visibilité**: `important`</span><span class="sxs-lookup"><span data-stu-id="338c2-136">**Visibility**: `important`</span></span>

![Capture d’écran de l’onglet définition dans la configuration du connecteur](./images/definition-tab.png)

<span data-ttu-id="338c2-138">Créez une **demande** en sélectionnant **Importer à partir d’un exemple** et renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="338c2-138">Create **Request** by selecting **Import from Sample** and fill in the fields as follows.</span></span>

- <span data-ttu-id="338c2-139">**Verbe**: `POST`</span><span class="sxs-lookup"><span data-stu-id="338c2-139">**Verb**: `POST`</span></span>
- <span data-ttu-id="338c2-140">**URL** :`https://graph.microsoft.com/v1.0/$batch`</span><span class="sxs-lookup"><span data-stu-id="338c2-140">**URL**: `https://graph.microsoft.com/v1.0/$batch`</span></span>
- <span data-ttu-id="338c2-141">**En-têtes**: laisser vide</span><span class="sxs-lookup"><span data-stu-id="338c2-141">**Headers**: Leave blank</span></span>
- <span data-ttu-id="338c2-142">**Body**: `{}`</span><span class="sxs-lookup"><span data-stu-id="338c2-142">**Body**: `{}`</span></span>

<span data-ttu-id="338c2-143">Sélectionnez **Importer**.</span><span class="sxs-lookup"><span data-stu-id="338c2-143">Select **Import**.</span></span>

![Capture d’écran de la boîte de dialogue Importer à partir de l’exemple de la configuration du connecteur](./images/import-sample.png)

<span data-ttu-id="338c2-145">Sélectionnez **créer un connecteur** en haut à droite.</span><span class="sxs-lookup"><span data-stu-id="338c2-145">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="338c2-146">Une fois le connecteur créé, copiez l' **URL de redirection** générée à partir de la page de **sécurité** .</span><span class="sxs-lookup"><span data-stu-id="338c2-146">After the connector has been created, copy the generated **Redirect URL** from **Security** page.</span></span>

![Capture d’écran de l’URL de redirection générée](./images/redirect-url.png)

<span data-ttu-id="338c2-148">Revenez à l’application inscrite dans le [portail Azure](https://aad.portal.azure.com) que vous avez créé dans l’exercice précédent.</span><span class="sxs-lookup"><span data-stu-id="338c2-148">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="338c2-149">Sélectionnez **authentification** dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="338c2-149">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="338c2-150">Sélectionnez **Ajouter une plateforme**, puis **Web**.</span><span class="sxs-lookup"><span data-stu-id="338c2-150">Select **Add a platform**, then select **Web**.</span></span> <span data-ttu-id="338c2-151">Entrez l’URL de redirection copiée à partir de l’étape précédente dans les **URI de redirection**, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="338c2-151">Enter the redirect URL copied from the previous step in the **Redirect URIs**, then select **Configure**.</span></span>

![Capture d’écran du panneau URL de réponse dans le portail Azure](./images/update-app-reg.png)

## <a name="option-2-create-custom-connector-by-importing-openapi-file"></a><span data-ttu-id="338c2-153">Option 2 : créer un connecteur personnalisé en important un fichier OpenAPI</span><span class="sxs-lookup"><span data-stu-id="338c2-153">Option 2: Create custom connector by importing OpenAPI file</span></span>

<span data-ttu-id="338c2-154">À l’aide d’un éditeur de texte, créez un fichier vide nommé `MSGraph-Delegate-Batch.swagger.json` et ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="338c2-154">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="338c2-155">Ouvrez un navigateur et accédez à [Microsoft Power Automated](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="338c2-155">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="338c2-156">Connectez-vous à l’aide de votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="338c2-156">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="338c2-157">Choisissez **données** dans le menu de gauche, puis sélectionnez l’élément **connecteurs personnalisés** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="338c2-157">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

<span data-ttu-id="338c2-158">Sur la page **connecteurs personnalisés** , sélectionnez le **nouveau lien connecteur personnalisé** dans le coin supérieur droit, puis sélectionnez Importer un élément de **fichier openapi** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="338c2-158">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Import an OpenAPI file** item in the drop-down menu.</span></span>

<span data-ttu-id="338c2-159">Entrez `MS Graph Batch Connector` dans la zone de texte **nom du connecteur** .</span><span class="sxs-lookup"><span data-stu-id="338c2-159">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="338c2-160">Sélectionnez l’icône de dossier pour télécharger le fichier OpenAPI.</span><span class="sxs-lookup"><span data-stu-id="338c2-160">Choose the folder icon to upload the OpenAPI file.</span></span> <span data-ttu-id="338c2-161">Accédez au `MSGraph-Delegate-Batch.swagger.json` fichier que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="338c2-161">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="338c2-162">Choisissez **Continuer** pour charger le fichier openapi.</span><span class="sxs-lookup"><span data-stu-id="338c2-162">Choose **Continue** to upload the OpenAPI file.</span></span>

<span data-ttu-id="338c2-163">Sur la page Configuration du connecteur, cliquez sur le lien **sécurité** dans le menu de navigation.</span><span class="sxs-lookup"><span data-stu-id="338c2-163">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="338c2-164">Renseignez les champs comme suit.</span><span class="sxs-lookup"><span data-stu-id="338c2-164">Fill in the fields as follows.</span></span>

- <span data-ttu-id="338c2-165">**Choisissez l’authentification qui est implémentée par votre API**: `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="338c2-165">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="338c2-166">**Fournisseur d’identité**: `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="338c2-166">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="338c2-167">**ID client**: ID d’application que vous avez créé dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="338c2-167">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="338c2-168">Clé **secrète client**: la clé que vous avez créée dans l’exercice précédent</span><span class="sxs-lookup"><span data-stu-id="338c2-168">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="338c2-169">**URL de connexion**: `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="338c2-169">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="338c2-170">**ID de client**: `common`</span><span class="sxs-lookup"><span data-stu-id="338c2-170">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="338c2-171">**URL**de la ressource : `https://graph.microsoft.com` (sans finalisation/)</span><span class="sxs-lookup"><span data-stu-id="338c2-171">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="338c2-172">**Étendue**: laisser vide</span><span class="sxs-lookup"><span data-stu-id="338c2-172">**Scope**: Leave blank</span></span>

<span data-ttu-id="338c2-173">Sélectionnez **créer un connecteur** en haut à droite.</span><span class="sxs-lookup"><span data-stu-id="338c2-173">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="338c2-174">Une fois le connecteur créé, copiez l' **URL de redirection**générée.</span><span class="sxs-lookup"><span data-stu-id="338c2-174">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Capture d’écran de l’URL de redirection générée](./images/redirect-url.png)

<span data-ttu-id="338c2-176">Revenez à l’application inscrite dans le [portail Azure](https://aad.portal.azure.com) que vous avez créé dans l’exercice précédent.</span><span class="sxs-lookup"><span data-stu-id="338c2-176">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="338c2-177">Sélectionnez **authentification** dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="338c2-177">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="338c2-178">Sélectionnez **Ajouter une plateforme**, puis **Web**.</span><span class="sxs-lookup"><span data-stu-id="338c2-178">Select **Add a platform**, then select **Web**.</span></span> <span data-ttu-id="338c2-179">Entrez l’URL de redirection copiée à partir de l’étape précédente dans les **URI de redirection**, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="338c2-179">Enter the redirect URL copied from the previous step in the **Redirect URIs**, then select **Configure**.</span></span>

![Capture d’écran du panneau URL de réponse dans le portail Azure](./images/update-app-reg.png)
