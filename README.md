# ansible-role-wordpress-ops

> Rôle Ansible réutilisable – Routines opérationnelles d'un WordPress dockerisé.

Ce repo contient **uniquement le rôle**. Il est conçu pour être appelé
depuis un repo playbook séparé via `requirements.yml`.

## Collections requises

```bash
ansible-galaxy collection install community.docker amazon.aws
```

## Variables

Voir [`defaults/main.yml`](defaults/main.yml) pour la liste complète et documentée.

### Variables S3 clés

| Variable | Défaut | Description |
|----------|--------|-------------|
| `s3_enabled` | `false` | Activer l'upload S3 |
| `s3_bucket` | `mon-bucket-wordpress-backup` | Nom du bucket |
| `s3_region` | `eu-west-1` | Région AWS |
| `s3_prefix` | `wordpress` | Préfixe des clés S3 |
| `aws_access_key` | `""` | Laisser vide si IAM role EC2 |
| `aws_secret_key` | `""` | Laisser vide si IAM role EC2 |

## Tags disponibles

| Tag | Routine |
|-----|---------|
| `backup_db` | Backup de la base de données (+ upload S3 optionnel) |
| `backup_files` | Backup fichiers + DB via handler (+ upload S3 optionnel) |
| `restore_db` | Restauration de la base de données |
| `restore_files` | Restauration fichiers + DB via handler |
| `update_plugins` | Mise à jour de tous les plugins WP |
| `manage_plugin` | Activation ou désactivation d'un plugin |
| `cleanup` | Suppression des backups locaux expirés |
