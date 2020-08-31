<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="6da35-101">Dans cet exercice, vous allez créer un flux pour utiliser le connecteur personnalisé que vous avez créé dans les exercices précédents pour créer et configurer une équipe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6da35-101">In this exercise, you will create a flow to use the custom connector you created in previous exercises to create and configure a Microsoft Team.</span></span> <span data-ttu-id="6da35-102">Le flux utilisera le connecteur personnalisé pour envoyer une requête POST afin de créer un groupe unifié Office 365, sera suspendu pendant un délai pendant la création du groupe, puis enverra une demande PUT pour associer le groupe à une équipe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6da35-102">The flow will use the custom connector to send a POST request to create an Office 365 Unified Group, will pause for a delay while the group creation completes, and then will send a PUT request to associate the group with a Microsoft Team.</span></span>

<span data-ttu-id="6da35-103">À la fin, votre flux ressemblera à l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="6da35-103">In the end your flow will look similar to the following image:</span></span>

![Capture d’écran du flux terminé](./images/completed-flow.png)

<span data-ttu-id="6da35-105">Ouvrez [Microsoft Power automatez](https://flow.microsoft.com) -vous dans votre navigateur et connectez-vous avec votre compte d’administrateur client Office 365.</span><span class="sxs-lookup"><span data-stu-id="6da35-105">Open [Microsoft Power Automate](https://flow.microsoft.com) in your browser and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="6da35-106">Sélectionnez **mes flux** dans le volet de navigation de gauche.</span><span class="sxs-lookup"><span data-stu-id="6da35-106">Choose **My flows** in the left-hand navigation.</span></span> <span data-ttu-id="6da35-107">Sélectionnez **nouveau**, puis **instantané à partir d’un vide**.</span><span class="sxs-lookup"><span data-stu-id="6da35-107">Choose **New**, then **Instant--from blank**.</span></span> <span data-ttu-id="6da35-108">Entrez `Create Team` le **nom du flux**, puis sélectionnez **déclencher manuellement un flux** sous **Choisissez comment déclencher ce flux**.</span><span class="sxs-lookup"><span data-stu-id="6da35-108">Enter `Create Team` for **Flow name**, then select **Manually trigger a flow** under **Choose how to trigger this flow**.</span></span> <span data-ttu-id="6da35-109">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="6da35-109">Choose **Create**.</span></span>

<span data-ttu-id="6da35-110">Sélectionnez l’option **déclencher manuellement un** élément de flux, puis choisissez **Ajouter une entrée**, sélectionnez **texte** et entrez `Name` comme titre.</span><span class="sxs-lookup"><span data-stu-id="6da35-110">Select the **Manually trigger a flow** item, then choose **Add an input**, select **Text** and enter `Name` as the title.</span></span>

![Capture d’écran du déclenchement manuel d’un déclencheur de flux](./images/manually-trigger.png)

<span data-ttu-id="6da35-112">Choisissez **nouvelle étape** et tapez `Batch` dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="6da35-112">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="6da35-113">Ajoutez l’action du **connecteur de lot MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="6da35-113">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="6da35-114">Sélectionnez les points de suspension et renommez cette action en `Batch POST-groups` .</span><span class="sxs-lookup"><span data-stu-id="6da35-114">Choose the ellipsis and rename this action to `Batch POST-groups`.</span></span>

<span data-ttu-id="6da35-115">Ajoutez le code suivant dans la zone de texte **Body** de l’action.</span><span class="sxs-lookup"><span data-stu-id="6da35-115">Add the following code into the **body** text box of the action.</span></span>

```json
{
  "requests": [
    {
      "url": "/groups",
      "method": "POST",
      "id": 1,
      "headers": { "Content-Type": "application/json" },
      "body": {
        "description": "REPLACE",
        "displayName": "REPLACE",
        "groupTypes": ["Unified"],
        "mailEnabled": true,
        "mailNickname": "REPLACE",
        "securityEnabled": false
      }
    }
  ]
}
```

<span data-ttu-id="6da35-116">Remplacez chaque `REPLACE` espace réservé en sélectionnant la `Name` valeur du déclencheur manuel dans le menu **Ajouter du contenu dynamique** .</span><span class="sxs-lookup"><span data-stu-id="6da35-116">Replace each `REPLACE` placeholder by selecting the `Name` value from the manual trigger from the **Add dynamic content** menu.</span></span>

![Capture d’écran du menu contenu dynamique de Microsoft Flow](./images/dynamic-content.png)

<span data-ttu-id="6da35-118">Choisissez **nouvelle étape**, recherchez `delay` et ajoutez une action de **retard** et configurez pendant 1 minute.</span><span class="sxs-lookup"><span data-stu-id="6da35-118">Choose **New step**, search for `delay` and add a **Delay** action and configure for 1 minute.</span></span>

<span data-ttu-id="6da35-119">Choisissez **nouvelle étape** et tapez `Batch` dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="6da35-119">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="6da35-120">Ajoutez l’action du **connecteur de lot MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="6da35-120">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="6da35-121">Sélectionnez les points de suspension et renommez cette action en `Batch PUT-team` .</span><span class="sxs-lookup"><span data-stu-id="6da35-121">Choose the ellipsis and rename this action to `Batch PUT-team`.</span></span>

<span data-ttu-id="6da35-122">Ajoutez le code suivant dans la zone de texte **Body** de l’action.</span><span class="sxs-lookup"><span data-stu-id="6da35-122">Add the following code into the **body** text box of the action.</span></span>

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/groups/REPLACE/team",
      "method": "PUT",
      "headers": {
        "Content-Type": "application/json"
      },
      "body": {
        "memberSettings": {
          "allowCreateUpdateChannels": true
        },
        "messagingSettings": {
          "allowUserEditMessages": true,
          "allowUserDeleteMessages": true
        },
        "funSettings": {
          "allowGiphy": true,
          "giphyContentRating": "strict"
        }
      }
    }
  ]
}
```

<span data-ttu-id="6da35-123">Sélectionnez l' `REPLACE` espace réservé, puis **expression** dans le volet de contenu dynamique.</span><span class="sxs-lookup"><span data-stu-id="6da35-123">Select the `REPLACE` placeholder, then select **Expression** in the dynamic content pane.</span></span> <span data-ttu-id="6da35-124">Ajoutez la formule suivante dans l' **expression**.</span><span class="sxs-lookup"><span data-stu-id="6da35-124">Add the following formula into the **Expression**.</span></span>

```js
body('Batch_POST-groups').responses[0].body.id
```

![Capture d’écran de l’expression dans le volet de contenu dynamique](./images/flow-formula.png)

<span data-ttu-id="6da35-126">Cette formule spécifie que nous voulons utiliser l’ID de groupe à partir du résultat de la première action.</span><span class="sxs-lookup"><span data-stu-id="6da35-126">This formula specifies that we want to use the group ID from the result of the first action.</span></span>

![Capture d’écran du corps de l’action mise à jour](./images/updated-body.png)

<span data-ttu-id="6da35-128">Sélectionnez **Enregistrer**, puis **tester** pour exécuter le flux.</span><span class="sxs-lookup"><span data-stu-id="6da35-128">Choose **Save**, then choose **Test** to execute the flow.</span></span>

> [!TIP]
> <span data-ttu-id="6da35-129">Si vous recevez une erreur telle que `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'` , l’expression est incorrecte et peut faire référence à une action de flux qu’elle ne trouve pas.</span><span class="sxs-lookup"><span data-stu-id="6da35-129">If you receive an error like `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'`, the expression is incorrect and likely references a flow action it cannot find.</span></span> <span data-ttu-id="6da35-130">Vérifiez que le nom de l’action que vous référencez correspond exactement.</span><span class="sxs-lookup"><span data-stu-id="6da35-130">Ensure that the action name you are referencing matches exactly.</span></span>

<span data-ttu-id="6da35-131">Sélectionnez la case d’option **j’exécuterai le déclencheur** , puis choisissez **Enregistrer & test**.</span><span class="sxs-lookup"><span data-stu-id="6da35-131">Choose the **I'll perform the trigger** action radio button and choose **Save & Test**.</span></span> <span data-ttu-id="6da35-132">Choisissez **Continuer** dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6da35-132">Choose **Continue** in the dialog.</span></span> <span data-ttu-id="6da35-133">Fournissez un nom sans espaces, puis choisissez **exécuter le flux** pour créer une équipe.</span><span class="sxs-lookup"><span data-stu-id="6da35-133">Provide a name without spaces, and choose **Run flow** to create a Team.</span></span>

![Capture d’écran de la boîte de dialogue flux de série](./images/run-flow.png)

<span data-ttu-id="6da35-135">Enfin, choisissez le pour **afficher le journal d’activité** .</span><span class="sxs-lookup"><span data-stu-id="6da35-135">Finally, choose the **Done** to see the activity log.</span></span> <span data-ttu-id="6da35-136">Une fois le flux terminé, votre groupe et votre équipe Office 365 ont été configurés.</span><span class="sxs-lookup"><span data-stu-id="6da35-136">Once the flow completes, your Office 365 Group and Team have been configured.</span></span> <span data-ttu-id="6da35-137">Sélectionnez les éléments d’action de traitement par lots pour afficher les résultats des appels de lots JSON.</span><span class="sxs-lookup"><span data-stu-id="6da35-137">Select the Batch action items to view the results of the JSON Batch calls.</span></span> <span data-ttu-id="6da35-138">L' `outputs` `Batch PUT-team` action doit avoir un code d’état de 201 pour une association d’équipe réussie semblable à l’image ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6da35-138">The `outputs` of the `Batch PUT-team` action should have a status code of 201 for a successful Team association similar to the image below.</span></span>

![Capture d’écran du journal d’activité de flux réussi](./images/success.png)
