<!-- markdownlint-disable MD002 MD041 -->

Le flux que vous avez créé au cours de l’exercice précédent utilise l' `$batch` API pour effectuer deux requêtes individuelles à Microsoft Graph. Le fait `$batch` d’appeler le point de terminaison de cette façon offre des avantages et une flexibilité, mais la véritable puissance du `$batch` point de terminaison est fournie lors de l’exécution de plusieurs demandes vers Microsoft Graph en un seul `$batch` appel. Dans cet exercice, vous allez étendre l’exemple de création d’un groupe unifié et associer une équipe pour inclure la création de plusieurs canaux par défaut pour l’équipe en une seule `$batch` requête.

Ouvrez [Microsoft Power automatez](https://flow.microsoft.com) -vous dans votre navigateur et connectez-vous avec votre compte d’administrateur client Office 365. Sélectionnez le flux que vous avez créé à l’étape précédente, puis cliquez sur **modifier**.

Choisissez **nouvelle étape** et tapez `Batch` dans la zone de recherche. Ajoutez l’action du **connecteur de lot MS Graph** . Sélectionnez les points de suspension et renommez cette action en `Batch POST-channels` .

Ajoutez le code suivant dans la zone de texte **Body** de l’action.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

Notez que les trois requêtes ci-dessus utilisent la propriété [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) pour spécifier un ordre séquentiel et chacune exécutera une requête post pour créer un nouveau canal dans la nouvelle équipe.

Sélectionnez chaque instance de l' `REPLACE` espace réservé, puis **expression** dans le volet de contenu dynamique. Ajoutez la formule suivante dans l' **expression**.

```js
body('Batch_PUT-team').responses[0].body.id
```

![Capture d’écran de l’expression dans le volet de contenu dynamique](./images/dynamic-expression.png)

Sélectionnez **Enregistrer**, puis **tester** pour exécuter le flux. Sélectionnez la case d’option **j’exécuterai le déclencheur** , puis choisissez **Enregistrer & test**. Entrez un nom de groupe unique dans le champ **nom** sans espaces, puis choisissez **exécuter le flux** pour exécuter le flux.

Une fois le flux démarré, cliquez sur le bouton **Terminer** pour afficher le journal d’activité. Une fois le flux terminé, la sortie finale de l' `Batch POST-channels` action est associée à une réponse d’état HTTP 201 pour chaque canal créé.

![Capture d’écran du journal d’activité de flux réussi](./images/batch-success.png)

Accédez à [Microsoft teams](https://teams.microsoft.com) et connectez-vous à l’aide de votre compte d’administrateur client Office 365. Vérifiez que l’équipe que vous venez de créer apparaît et inclut les trois canaux créés par la `$batch` demande.

![Capture d’écran de l’application teams avec la nouvelle équipe et les canaux qui apparaissent](./images/team-channels.png)

Bien que l’action ci-dessus `Batch POST-channels` ait été implémentée dans ce didacticiel séparément, les appels de création des canaux auraient pu être ajoutés comme appels supplémentaires dans l' `Batch PUT-team` action. Cela aurait créé l’équipe et tous les canaux dans un seul appel de lot. Donnez-lui votre choix.

Enfin, n’oubliez pas que les appels de [traitement par lots JSON](https://docs.microsoft.com/graph/json-batching) renvoient un code d’état HTTP pour chaque demande. Dans un processus de production, vous souhaiterez peut-être combiner post-traitement des résultats avec une [`Apply to each`](https://docs.microsoft.com/power-automate/apply-to-each) action et valider chaque réponse a un code d’état 201 ou compenser tous les autres codes d’état reçus.
