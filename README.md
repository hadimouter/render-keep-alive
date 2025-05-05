# Render Keep-Alive

Un simple service pour empêcher les instances Render gratuites de se mettre en veille.

## Problématique

Sur l'offre gratuite de Render, les instances web se mettent en veille après une période d'inactivité. Cela peut entraîner des temps de réponse très longs (jusqu'à 50 secondes) pour la première requête après cette mise en veille.

## Solution

Ce dépôt contient un workflow GitHub Actions qui envoie automatiquement une requête HTTP à votre application Render à intervalles réguliers (toutes les 10 minutes par défaut), empêchant ainsi la mise en veille.

## Comment ça fonctionne

Le workflow GitHub Actions est configuré pour:
- S'exécuter automatiquement toutes les 10 minutes
- Envoyer une simple requête HTTP GET à l'URL de votre application
- Pouvoir être déclenché manuellement si nécessaire

## Configuration

1. Clonez ce dépôt ou créez un nouveau dépôt avec le même fichier de workflow
2. Modifiez le fichier `.github/workflows/keep-alive.yml` pour remplacer l'URL par celle de votre application Render
3. Activez GitHub Actions sur votre dépôt si ce n'est pas déjà fait

## Personnalisation

- Pour modifier la fréquence des requêtes, changez la valeur du cron dans le fichier workflow
- Pour cibler un endpoint spécifique, modifiez l'URL dans la commande curl

## Avantages

- Solution 100% gratuite
- Ne nécessite pas de serveur supplémentaire
- Facile à configurer et à maintenir
- Logs disponibles dans l'interface GitHub Actions

## Limitations

- Soumis aux limites de minutes gratuites de GitHub Actions (largement suffisant pour cet usage)
- Ne garantit pas un temps de réponse instantané mais réduit considérablement les délais
