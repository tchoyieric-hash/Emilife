# ApexLife — Modern Life OS

ApexLife est une PWA mobile-first pour organiser projets, tâches, habitudes, budget et bilan quotidien. Stack : Next.js App Router, React 19, TypeScript, Tailwind CSS v4, Supabase/PostgreSQL et TanStack Query.

## Fonctionnalités du MVP
- Cockpit : priorité North Star, plage d'énergie, statistiques et minuteur Pomodoro.
- Projets et tâches : création rapide, priorités, échéances, vue liste / Kanban.
- Habitudes : validation quotidienne et calcul de séries de base.
- Finances : budget consommé, dépenses, épargne et objectif.
- Bilan quotidien : victoires et obstacles enregistrés localement; synthèse initiale heuristique.
- Mode démo utilisable sans compte Supabase; données démo stockées sur l'appareil.
- PWA : manifest et service worker minimal.

## Lancer localement
1. Installer Node.js 20+.
2. Copier `.env.example` vers `.env.local`.
3. Renseigner les clés Supabase (facultatif pour explorer le mode démo).
4. Exécuter `npm install`, puis `npm run dev`.
5. Ouvrir `http://localhost:3000`.

## Déploiement Vercel
Importer le dépôt GitHub dans Vercel, choisir Next.js et définir `NEXT_PUBLIC_SUPABASE_URL` et `NEXT_PUBLIC_SUPABASE_ANON_KEY` dans les variables d'environnement. Déployer.

## Supabase
1. Créer un projet Supabase.
2. Ouvrir SQL Editor et exécuter `supabase/schema.sql`.
3. Activer Email dans Authentication > Providers. Configurer les URL de redirection de l'app.
4. Ajouter les variables dans `.env.local` et Vercel.

## Sécurité
- Les tables contenant des données privées ont RLS activé.
- Les politiques s'appuient sur `auth.uid()`.
- Ne jamais committer `.env.local` ou la clé `service_role`.
- Les fonctions de synthèse IA ne sont pas connectées à un fournisseur externe dans ce MVP : le résumé est heuristique et local. Ajouter un endpoint serveur sécurisé avant d'utiliser un fournisseur IA.

## Limites du MVP
Le mode démo conserve ses données dans `localStorage` sur un seul appareil. La synchronisation multi-appareil, OAuth Google, notifications, et la file de synchronisation offline avancée doivent être activées/configurées pour une production complète. La PWA nécessite HTTPS en production.
