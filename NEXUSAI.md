# Base SaaS NexusAI

Modèle de départ pour les SaaS de NexusAI Agency. Copie de [ixartz/SaaS-Boilerplate](https://github.com/ixartz/SaaS-Boilerplate) (licence MIT, garder le fichier LICENSE), version `e3952a7` du 21/08/2026, avec ces réglages :

- nom de l'app « NexusAI SaaS », français par défaut (anglais disponible), e-mail de support hello@nexusai-agency.fr ;
- configuration Codespaces (`.devcontainer/`, Node 24) ;
- retrait des fichiers de traduction Crowdin et des workflows Checkly et release du projet d'origine.

## Ce que la base contient déjà

| Brique | Outil |
|---|---|
| Framework | Next.js 16, React 19, TypeScript |
| Connexion, comptes, organisations (multi-entreprises) | Clerk |
| Base de données | Postgres avec Drizzle ; en local PGlite, sans rien installer |
| Langues | next-intl (fr, en) |
| Interface | Tailwind CSS, shadcn/ui |
| Qualité | Vitest, Playwright, ESLint, Storybook |
| Suivi d'erreurs | Sentry (facultatif) |

Pas inclus dans cette version gratuite : paiement Stripe et rôles avancés. Ils sont à ajouter par projet.

## Démarrer un nouveau SaaS à partir de cette base

1. Sur GitHub : **Use this template → Create a new repository** (dépôt privé, nom du SaaS).
2. Ouvre-le dans **Code → Codespaces → Create codespace**. L'installation se lance toute seule.
3. Crée une application sur [dashboard.clerk.com](https://dashboard.clerk.com) (gratuit), puis :
   - mets la clé publique `pk_test_…` dans `.env` (`NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`) ;
   - mets la clé secrète `sk_test_…` dans `.env.local` (`CLERK_SECRET_KEY`). Ce fichier n'est jamais envoyé sur GitHub ; ne colle jamais cette clé dans un chat.
   - active **Organizations** dans Clerk si le SaaS gère plusieurs entreprises (un salon = une organisation).
4. `npm run dev`, puis ouvre le port 3000.

## En ligne

Base de production : un Postgres (Supabase ou Neon) dans `DATABASE_URL`, réglé dans les variables d'environnement Vercel, pas dans le dépôt. Les migrations Drizzle s'appliquent au `npm run build`.
