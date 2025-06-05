```bash
git clone [](https://github.com/Mihajaz/FDM)
cd FDM
docker compose up --build
```

Pour lancer l'application sur un serveur de développement, utiliser la commande ci-dessous :

```bash
docker compose build
docker compose up
```

Pour lancer l'application sur un serveur de production, utiliser la commande ci-dessous :

```bash
docker compose -f docker-compose.prod.yml --env-file .env up --build
```

Au niveau production, on n'envoie pas tous les codes dans le volumes pour avoir une **isolation** et **cohérence**

```
volumes:
  - .:/app
```

* Avec `- .:/app`, tu relies directement le dossier du code source local au dossier `/app` dans le conteneur.
* Ça marche super en développement (tu modifies ton code local, et les changements sont visibles instantanément dans le conteneur).
* **Mais en production, tu veux que ton conteneur soit immuable et reproductible :**

  Le conteneur doit contenir exactement ce qui est nécessaire, sans dépendre d’un dossier local externe.
