# Plume

Éditeur Markdown léger avec **révision assistée par IA** : correction orthographique et grammaticale, révision du style et propositions de vocabulaire — sans interface de chat. Tout tient dans un seul fichier `index.html`, sans build ni serveur.

## Fonctionnement

- Éditeur Markdown avec aperçu en temps réel, barre de formatage, zoom et vue partagée redimensionnable.
- Sélectionne un passage (ou laisse le curseur dans un paragraphe), puis lance **Corriger**, **Réviser le style** ou **Vocabulaire**.
- La proposition s'affiche dans le panneau de droite avec le détail des modifications. **Rien n'est modifié tant que tu ne cliques pas sur « Appliquer ».**
- Le document est sauvegardé automatiquement dans le navigateur (`localStorage`).

## Fournisseurs et modèles

Tu fournis ta propre clé API dans les réglages (⚙). Fournisseurs pris en charge :

| Fournisseur | Exemples de modèles |
|---|---|
| Anthropic (Claude) | `claude-sonnet-4-6`, `claude-opus-4-8`, `claude-haiku-4-5` |
| OpenAI | `gpt-4o`, `gpt-4o-mini` |
| Mistral | `mistral-large-latest`, `mistral-small-latest` |
| Google (Gemini) | `gemini-2.5-flash`, `gemini-2.5-pro` |
| **OpenRouter** | `qwen/qwen-2.5-72b-instruct`, `deepseek/deepseek-chat`, `meta-llama/llama-3.3-70b-instruct`… |
| **Qwen (DashScope)** | `qwen-plus`, `qwen-max`, `qwen-turbo` |
| **Perplexity** | `sonar`, `sonar-pro` |
| **DeepSeek** | `deepseek-chat`, `deepseek-reasoner` |
| **xAI (Grok)** | `grok-2-latest` |

> **Astuce :** OpenRouter est le plus simple pour tester plusieurs familles de modèles (Qwen, Llama, DeepSeek, etc.) avec une seule clé, et il autorise explicitement les appels depuis le navigateur.

### À propos des appels depuis le navigateur (CORS)

Plume appelle les API directement depuis ton navigateur, sans intermédiaire. Anthropic, OpenAI, Mistral, Gemini et OpenRouter le permettent. Certains fournisseurs (Perplexity, DeepSeek, xAI, DashScope) peuvent bloquer ces appels selon leur politique CORS du moment ; si une requête échoue avec une erreur réseau/CORS, passe par OpenRouter.

## Sécurité

- **Ta clé API reste dans ton navigateur** (`localStorage`) et n'est transmise qu'au fournisseur choisi. Ne l'inscris jamais en dur dans le fichier. Évite les ordinateurs partagés.
- Le rendu Markdown est **assaini avec [DOMPurify](https://github.com/cure53/DOMPurify)** : un document contenant du HTML/JS malveillant ne peut pas s'exécuter ni voler ta clé.
- Les scripts CDN sont chargés avec **Subresource Integrity (SRI)** : une altération du fichier distant est rejetée par le navigateur.
- Une **Content-Security-Policy** restreint les destinations réseau aux seules API des fournisseurs supportés.

## Utilisation

Ouvre `index.html` dans un navigateur, ou héberge-le (GitHub Pages, etc.). Aucune installation.

## Licence

[MIT](LICENSE)
