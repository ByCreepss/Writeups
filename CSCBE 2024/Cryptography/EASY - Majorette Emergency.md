### Scénario :

*I'm late for my cheerleading class, and I can't get my flags out of this awful lockbox! I remember I wrote how to open it in my diary, but I can't even read my own handwriting! What am I gonna do…*

### Contenu du challenge :

Un fichier .zip contenant un autre fichier zip protégé par mot de passe, et l’empreinte du mot de passe de ce fichier zip.

### Résolution :

Le hash dans secret_diary.txt est : 98b6a84b03f5aca7e23a13c627d62037

Première étape : le passer dans une base de données de hash (https://crackstation.net/ ou https://hashes.com/en/decrypt/hash).

Une fois fait, on voit qu’il se trouve dans cette base de donnée et que le mot de passe associé à ce hash est : Use_A_Key

On ouvre donc le fichier zip protégé et on entre simplement ce mot de passe.

<aside>
✅

Flag : **CSC{N0t_v3ry_57urdy_15_it_N0w}**

</aside>
