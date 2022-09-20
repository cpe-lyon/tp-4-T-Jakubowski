## Exercice 1
---

1) Pour mettre à jour on utilise la commande ```sudo apt upgrade```
2) On utilise ```alias maj='apt upgrade'``` pour créer un alias et pour garder l'alias apres le redémarrage on doit le mettre dans le fichier bashrc.
    On le met dedans avec la commande ```echo "alias maj='apt upgrade'" >> ~/.bashrc```
3) Pour voir les 5 derniers paquets installés on va voir les dernières ligne de dpkg.log grâce à ```tail -n 5 /var/log/dpkg.log```
4) Les derniers paquet installés sont des paquets python.
5) Pour compter le nombre de paquets avec dpkg on fait ```dpkg -l > count; wc -l count```,  pour apt on fait ```apt list --installed | awk '{print $1}' | tee count; wc -l count```, la différence de ligne est la car il y a des ligne au départ de dpkg -l qui ne correspondent pas à des paquets.
6) Pour voir le nombre de paquet sur le debot ubuntu on utilise ```sudo apt list | wc -l```
7) Glances est un monitoring tool, tldr simplifie les pages du manuel, hollywood permet de simulé le fait d'être un hacker
8) Il faut utiliser la commande ```sudo snap install gnome-sudoku```

## Exercice 2
---

La commande permettant de retrouver de quel paquet vient une commande est ```dpkg -S ls```
On peut donc crée ce script

```
#!/bin/bash
which -a ls | xargs dpkg -S 2>/dev/null | cut -f1 -d:

```
which -a  $1 | xargs dpkg -S 2>/dev/null | cut -f1 -d
```

## Exercice 3
---

``` 
{
  pkg -L $1 > /dev/null 2>&1 &&
  echo "INSTALLER"
} || {
  echo "NON INSTALLER"
}

## Exercice 4
---


