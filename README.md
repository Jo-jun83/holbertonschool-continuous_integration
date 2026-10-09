# holbertonschool-continuous_integration
https://github.com/Jo-jun83/holbertonschool-continuous_integration/actions/runs/37014728651


## Pull Request CI Tests

[Failed CI test run](https://github.com/Jo-jun83/holbertonschool-continuous_integration/actions/runs/37898616605/job/113715678557?pr=1)

## Mise en cache des dépendances

Le workflow GitHub Actions utilise `actions/cache@v4` pour mettre en cache les dépendances Python installées avec `pip`.

L'objectif est d'éviter de télécharger à nouveau les mêmes dépendances à chaque exécution et ainsi de réduire le temps d'exécution du pipeline CI.

### Comparaison avant et après la mise en cache

| Exécution | Durée totale | Durée du job lint |
|---|---|---|
| Avant cache | 12 secondes | 9 secondes |
| Première exécution avec cache | 10 secondes | 7 secondes |
| Deuxième exécution (cache réutilisé) | 11 secondes | 7 secondes |

### Preuves des exécutions

- [Exécution avant la mise en cache](https://github.com/Jo-jun83/holbertonschool-continuous_integration/actions/runs/37901939229)
- [Exécution après la mise en cache — Cache Hit](https://github.com/Jo-jun83/holbertonschool-continuous_integration/actions/runs/37902607618)

### Résultats

- **Clé du cache :** `Linux-pip-flake8-v1`
- **Cache créé :** confirmation avec le message `Cache saved with key`.
- **Cache réutilisé :** confirmation avec le message `Cache restored successfully`.
- **Temps avant cache :** 12 secondes.
- **Temps après cache :** 11 secondes.
- **Gain observé :** 1 seconde, soit environ 8 %.

### Conclusion

La mise en cache des dépendances fonctionne correctement. GitHub Actions a réussi à sauvegarder puis à restaurer le cache lors d'une nouvelle exécution.

Le gain de temps observé reste faible, car le projet utilise peu de dépendances. Ces mesures ne suffisent pas à démontrer une accélération systématique, mais elles confirment le bon fonctionnement du mécanisme de cache.