# Règles Fondamentales du Projet & Directives Globales

Ces règles sont strictes et doivent être respectées impérativement avant et pendant le développement de chaque projet :

---

## 1. Création et synchronisation systématique d'un dépôt GitHub
* **Avant de démarrer le code** d'un nouveau projet ou d'un composant majeur :
  * Initialiser le dépôt Git local (`git init`).
  * Configurer/créer le dépôt distant sur GitHub pour le projet.
  * Réaliser un commit initial et pousser le code sur GitHub (`git push -u origin main`).
  * Vérifier que le fichier `.gitignore` est bien en place dès le premier commit (notamment pour exclure `node_modules`, `.env`, `.env.local`, etc.).

---

## 2. Sécurité absolue des Clés API (Côté Serveur Uniquement)
* **Aucune clé API secrète ne doit transiter par le navigateur ou être exposée côté client.**
* Le client / navigateur ne doit **JAMAIS** voir les clés API secrètes (Stitch, OpenAI, Stripe, services IA, etc.).
* Toutes les requêtes vers des services tiers payants ou sécurisés doivent impérativement passer par une couche serveur :
  * API Routes / Server Actions (Next.js),
  * Backend intermédiaire (Express, Fastify, Cloudflare Workers, Supabase Edge Functions, Firebase Functions).
* Les variables sensibles doivent résider exclusivement dans les variables d'environnement serveur (ex: `.env.local`) et ne jamais être préfixées par `VITE_` ou `NEXT_PUBLIC_` si ce sont des secrets.

---

## 3. Validation et Nettoyage de chaque Saisie Utilisateur (Sanitization & Validation)
* **Avant toute écriture ou lecture en base de données :**
  * Valider strictement le schéma et le type des données reçues (ex: via **Zod**, **Yup** ou validation stricte).
  * Nettoyer, désinfecter et trimmer chaque champ texte saisi par l'utilisateur pour prévenir les injections SQL, injections NoSQL, et failles XSS.
  * Ne jamais faire confiance aveuglément aux payloads envoyés par le client.

---

## 4. Authentification Sécurisée (Zero DIY Auth)
* Ne jamais réinventer la roue ou créer un système d'authentification maison (pas de hashing de mots de passe artisanal).
* Pour toute gestion des utilisateurs, sessions et authentification, utiliser exclusivement l'un de ces trois services éprouvés et sécurisés :
  1. **Clerk**
  2. **Supabase Auth**
  3. **Firebase Auth**

---

## 5. Performance Maximale Obligatoire pour le Design (Stitch MCP & Stitch Skills)
* **Dès qu'il est question de design, d'interface (UI) ou d'expérience utilisateur (UX) :**
  * **Exploitation maximale du serveur Stitch MCP** : Ne jamais produire d'interfaces basiques ou génériques. Mobiliser l'ensemble des capacités de l'API Stitch (création de projet, génération d'écrans haute-fidélité, édition d'écrans, création de variantes et application de thèmes globaux).
  * **Mobilisation maximale des Stitch Skills** :
    * Activer systématiquement le pipeline d'enrichissement de prompts (`enhance-prompt`) pour convertir toute idée en prompt UI/UX exhaustif et professionnel.
    * Imposer les standards esthétiques stricts et anti-génériques via `taste-design` et `design-md` (typographie soignée, palettes HSL calibrées, micro-interactions, layouts asymétriques).
    * Générer et synchroniser un véritable Design System (`DESIGN.md`) appliqué à tous les écrans (`stitch-manage-design-system`).
    * Pour le passage au code, convertir les designs en composants React/Vite modulaires et pixel-perfect via `stitch-react-components` et `react-vite-dashboard`.
