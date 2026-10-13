# TD1 

## Template démo pour préparer le TD1
- [https://github.com/AAP-26-27/template-td1](https://github.com/AAP-26-27/template-td1)


## Template du TD1
- [https://github.com/AAP-26-27/template-td1](https://github.com/AAP-26-27/template-td1)

## ATTENTION : Erreur dans l'exercice 6 du TD1 

Une erreur s'est glissée dans l'exercice 6 du TD1. 
- Merci à Nino Louvel de l'avoir signalée !
- Voici le texte correct :

### Exécution d'un processus externe : module `subprocess`

Pour demander en python à exécuter une commande shell dans un processus externe (on parle de *processus fils*) et récupérer son résultat, l'approche préconisée est de séparer *explicitement* la commande à utiliser de ses arguments, afin d'éviter tout risque *d'injection de commandes*. Le module `subprocess` permet de réaliser cela avec la fonction `run`. 
📌 **Injection de commandes** : technique consistant à faire exécuter par un programme des commandes supplémentaires fournies par un utilisateur, en exploitant une entrée insuffisamment contrôlée.

```python
import subprocess

resultat = subprocess.run(
    ["wc", "-c", "-w"],
    input="une chaine de 8 mots et 38 caractères",  # Ici, il était écrit input("une chaine de ...") et la virgule en fin de ligne manquait
    capture_output=True,
    text=True
)

print(resultat.stdout)
print(resultat.stderr)
print(resultat.returncode)
```

La description était également erronée, puisqu'elle décrivait la mauvaise commande. 
- Voici le texte corrigé :
  
Le premier élément de la liste correspond à la commande à exécuter (`wc`) et les éléments suivants à ses arguments (`-c`, `-w`). Le paramètre `capture_output=True` permet de récupérer les sorties standard et d'erreur du processus fils, tandis que `text=True` demande à Python de les représenter sous forme de chaînes de caractères et non pas d'octets. 
Le paramètre `input` permet de fournir une chaîne de caractères dans l'entrée standard du processus. 
