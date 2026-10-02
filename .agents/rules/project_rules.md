# Règles Fondamentales de Sécurité et de Workflow

Ces directives sont prioritaires et s'appliquent à tous les projets créés ou modifiés avec l'utilisateur :

1. **Dépôt GitHub Obligatoire** :
   - Pour chaque projet, initialiser Git, créer le repo GitHub correspondant, et pousser (`git push`) dès le début du projet.
   - S'assurer que le `.gitignore` protège tous les fichiers d'environnement et secrets.

2. **Clés API Côté Serveur Exclusivement** :
   - Le navigateur ne doit jamais recevoir ou stocker de clés API privées.
   - Les clés passent obligatoirement par un backend (API routes, proxy, cloud functions, etc.).

3. **Validation & Sanitisation Systématique** :
   - Nettoyer et valider chaque champ de saisie utilisateur (Zod / assainissement) avant toute transmission ou requête vers la base de données.

4. **Authentification Éprouvée (Zéro faille)** :
   - Utiliser exclusivement **Clerk**, **Supabase Auth** ou **Firebase Auth**.

5. **Excellence et Performance Maximale du Design (Stitch MCP & Stitch Skills)** :
   - Dès qu'un sujet touche au design/UI/UX, exploiter à 100% les capacités du serveur Stitch MCP et de la suite Stitch Skills.
   - Enrichissement systématique des prompts (`enhance-prompt`), standards esthétiques premium (`taste-design`, `design-md`), déploiement de Design Systems complets (`stitch-manage-design-system`) et conversion en composants modulaires de haute précision (`stitch-react-components`).
