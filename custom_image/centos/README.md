# Avant de build l’image, il est nécessaire de créer deux fichiers localisés au même endroit que le Dockerfile.
- passwd
- shadow

# Build de l’image custom :
$docker build -t <nom_image> .

# Démarrage du container :
$docker run --name ssh  -d  <nom_image>
