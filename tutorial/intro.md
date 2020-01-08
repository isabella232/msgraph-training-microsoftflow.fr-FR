<!-- markdownlint-disable MD002 MD041 -->

Il y a plus de 5 à 230 connecteurs de boîte à disposition pour Microsoft Flow. Un grand nombre de ces connecteurs utilisent Microsoft Graph pour communiquer avec des points de terminaison spécifiques des produits Microsoft, mais il n’existe pas de connecteur qui communique directement avec Microsoft Graph pour traiter l’ensemble de l’API. Toutefois, il peut s’avérer nécessaire d’appeler Microsoft Graph directement à partir du flux à l’aide de blocs de construction de base du service.

Outre les scénarios permettant d’appeler directement Microsoft Graph, un certain nombre de points de terminaison d’API Microsoft Graph ne prend en charge que les [autorisations déléguées](https://docs.microsoft.com/graph/permissions-reference). Le connecteur HTTP de Microsoft Flow permet des intégrations très flexibles, notamment l’appel de Microsoft Graph. Toutefois, le connecteur HTTP ne dispose pas de la possibilité de mettre en cache les informations d’identification d’un utilisateur pour activer des scénarios d’autorisation délégués spécifiques. Dans ce cas, un connecteur personnalisé peut être créé pour fournir un wrapper pour l’API Microsoft Graph et permettre l’utilisation de l’API avec des autorisations déléguées.

Cet atelier couvre les deux défis ci-dessus. Tout d’abord, vous allez créer un connecteur personnalisé pour activer les intégrations avec Microsoft Graph qui nécessitent des [autorisations déléguées](https://docs.microsoft.com/graph/permissions-reference). Deuxièmement, vous utiliserez le [point de terminaison de la demande $batch](https://docs.microsoft.com/graph/json-batching)pour permettre l’accès à toute la puissance de Microsoft Graph tout en utilisant les autorisations déléguées qui nécessitent qu’une application dispose d’un utilisateur connecté.

> [!NOTE]
> Il s’agit d’un didacticiel sur la création d’un connecteur personnalisé pour une utilisation dans Microsoft Flow et Azure LogicApps. Ce didacticiel part du principe que vous avez lu la [rubrique Custom Connector Overview](https://docs.microsoft.com/connectors/custom-connectors/) pour comprendre le processus.

## <a name="prerequisites"></a>Conditions requises

Pour effectuer cet exercice dans ce billet, vous avez besoin des éléments suivants :

- Accès administrateur à une location Office 365. Si vous n’en avez pas, reportez-vous au programme pour les [développeurs Office 365](https://developer.microsoft.com/office/dev-program) pour vous inscrire à un client de développeur gratuit.
- Accès à [Microsoft Flow](https://flow.microsoft.com/).

## <a name="feedback"></a>Commentaires

Veuillez fournir des commentaires sur ce didacticiel dans le [référentiel GitHub](https://github.com/microsoftgraph/msgraph-training-microsoftflow).
