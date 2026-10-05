# JavaChrist Mail Kit

Templates d'emails d'authentification, réutilisables par les applications JavaChrist.

## 1. Installation

```bash
git clone https://github.com/JavaChrist-apps/JavaChrist-Mail-Kit.git
cd JavaChrist-Mail-Kit
```

Aucune dépendance à installer.

## 2. Configurer une app

Chaque application a un fichier dans `apps/`. Les champs sont `appName`, `logoUrl`, `siteUrl`, `supportEmail` et `accent`. La couleur par défaut est `#ff6b01`.

`n8n-node-finder.json` est l'exemple complet. RideCloud, Parenty et AICCOS ont un nom et la couleur, sans URL ni logo tant qu'ils ne sont pas connus.

## 3. Générer les templates

```bash
npm run generate -- --app n8n-node-finder
```

Les six HTML sont écrits dans `templates/`.

## 4. Coller dans Supabase

Authentication → Emails. Un fichier par écran :

| Fichier | Écran |
| --- | --- |
| `confirmation.html` | Confirm sign up |
| `reset-password.html` | Reset password |
| `magic-link.html` | Magic link |
| `invite.html` | Invite user |
| `change-email.html` | Change email address |
| `password-changed.html` | Password changed |

`password-changed.html` part seulement si la notification Password changed est activée.

## 5. Sujets

Les sujets sont dans le commentaire HTML `Sujet :` de chaque fichier. Ils suivent le nom de l'app.

## 6. Logo

`logoUrl` doit être une image HTTPS. Elle s'affiche en 72 px. Sans URL, le bandeau affiche le mot JavaChrist.

## 7. SMTP

Voir `docs/smtp-ionos.md`. Aucun mot de passe n'est stocké ici.

## 8. Nouvelle app

1. Copier `apps/n8n-node-finder.json` vers `apps/nom-de-l-app.json`.
2. Remplacer le nom, le logo, le site et l'email de support.
3. Lancer `npm run generate -- --app nom-de-l-app`.
4. Coller les HTML dans le projet Supabase de cette app.
