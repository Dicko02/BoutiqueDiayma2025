# Boutique Diayma

## Tâche 8 : namespaces, classes et méthodes visités avant l'affichage des produits (GET /)

Modes utilisés dans VS Code : **détaillé** = F11 (Step Into), **principal** = F10 (Step Over), **sortant** = Maj+F11 (Step Out).

| # | Namespace | Classe | Méthode | Mode | Pourquoi |
|---|---|---|---|---|---|
| 1 | `P2FixAnAppDotNetCode` | `Program` | `Main`, `BuildWebHost` | Principal | Point d'entrée. Le code du framework appelé n'apporte rien. |
| 2 | `P2FixAnAppDotNetCode` | `Startup` | constructeur (ligne 20) | Principal | Premier point d'arrêt atteint. |
| 3 | `P2FixAnAppDotNetCode` | `Startup` | `ConfigureServices` | Principal | Enregistrement des services. Inutile d'entrer dans `AddMvc`. |
| 4 | `P2FixAnAppDotNetCode` | `Startup` | `Configure` | Principal | Construction du pipeline et de la route par défaut. |
| 5 | `P2FixAnAppDotNetCode.Models.Repositories` | `ProductRepository`, `OrderRepository` | constructeurs | Détaillé | Créés par l'injection de dépendances. On voit où la liste des produits est construite. |
| 6 | `P2FixAnAppDotNetCode.Models.Services` | `ProductService`, `LanguageService` | constructeurs | Principal | Simples affectations de dépendances, nécessaires au contrôleur. |
| 7 | `P2FixAnAppDotNetCode.Controllers` | `ProductController` | constructeur (ligne 15) | Principal | Contrôleur créé pour la requête `GET /`. |
| 8 | `P2FixAnAppDotNetCode.Controllers` | `ProductController` | `Index` | Détaillé | On entre dans le code du projet. |
| 9 | `P2FixAnAppDotNetCode.Models.Services` | `ProductService` | `GetAllProducts` | Détaillé | On suit l'appel vers le dépôt. |
| 10 | `P2FixAnAppDotNetCode.Models.Repositories` | `ProductRepository` | `GetAllProducts` | Sortant | Filtre et tri compris : on remonte à l'action. |
| 11 | `AspNetCore` (code généré) | `Views_Product_Index` | `ExecuteAsync` | Principal | Vue `Index.cshtml` compilée, rien à lire. |
| 12 | `P2FixAnAppDotNetCode.Components` | `CartSummaryViewComponent` | constructeur (ligne 12), `Invoke` | Principal | Appelé par `_Layout.cshtml`. |
| 13 | `P2FixAnAppDotNetCode.Components` | `LanguageSelectorViewComponent` | `Invoke` | Principal | Sélecteur de langue de la mise en page. |

`CartController` (ligne 15) et `OrderController` (ligne 17) ne sont **pas** atteints sur l'écran d'accueil. Leurs constructeurs ne s'exécutent qu'après un clic sur le panier, puis sur *Checkout*.