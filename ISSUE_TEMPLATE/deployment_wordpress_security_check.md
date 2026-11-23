---
name: 🚀 Checklist de Sécurité WorpPress
about: À valider impérativement avant toute bascule en production ou changement d'hébergeur.
title: "[PROD] Audit Sécurité - [Date]"
labels: security, deployment
assignees: ''
---

## 🛑 Fichiers & Nettoyage

- [ ] **Aucun dump SQL** (`.sql`) n'est présent à la racine ou dans les sous-dossiers.
- [ ] **Aucun script de debug** (`phpinfo()`, `test.php`, ...) n'est présent.
- [ ] **Fichiers de build supprimés** : Les fichiers `.sh`, `.md`, `.txt` et `composer.lock` sont retirés du dossier public.
- [ ] **Dossiers d'infra nettoyés** : Aucun dossier de backup, `.git` ou `infogerance` n'est accessible via le navigateur.
- [ ] **Fichiers sensibles** : Les fichiers `.env`, `.ini` ou de configuration IDE ne sont pas accessibles.

## 🔒 Configuration WordPress 

- [ ] **Debug OFF** : `define('WP_DEBUG', false);` est bien configuré dans `wp-config.php`.
- [ ] **Salts régénérés** : Les clés de salage ont été changées (pour invalider les sessions précédentes).
- [ ] **Édition de fichier désactivée** : `define('DISALLOW_FILE_EDIT', true);` est actif.
- [ ] **Compte Admin** : L'utilisateur "admin" par défaut n'existe pas. Les admins ont le 2FA activé.
- [ ] **Secrets API** : Aucune clé API (Salesforce, Stripe, etc.) n'est codée en dur dans le thème.

## 🛡️ Serveur & Réseau
*Protection de l'infrastructure.*

- [ ] **Permissions fichiers** : Dossiers en `755`, Fichiers en `644`. `wp-config.php` en `440` (ou `400`).
- [ ] **PHP** : Version à jour en LTS et fonctions dangereuses (`exec`, `system`...) désactivées.
- [ ] **Points d'entrée** : `/xmlrpc.php` est bloqué.
- [ ] **Accès Admin** : L'accès à `/wp-admin` est restreint (IP ou Captcha) ou protégé par WAF.
- [ ] **HTTPS** : Le mode SSL est "Strict" (Cloudflare/Proxy) et HSTS est activé.

## 🔄 Validation Finale
- [ ] **Sauvegarde** : Une sauvegarde manuelle a été faite ET testée (restauration sur staging réussie).
- [ ] **Scan** : Un scan rapide (ex: WPScan) n'a révélé aucune vulnérabilité majeure.

---
*Coché par : @handle_github*
