mudnames, originaly written by Ragnar Hojland Espinosa, is a small daemon
which will listen for incoming telnet connections on port 4004. When a
connection is received, it will output a randomly generated list of sample
character names suitable for use on many Multi-User-Dungeon type games.

Here, it's only the generator part.

I have added some .cap file to force capability of the dictionnary. Feel
free to explore all possibilities ;)

---

## Copie de Besançon 25

Ce dépôt est la copie de phpMudnames utilisée par Besançon 25 (B25_FR et B25_PRO,
`application/scripts/mudnames/`) pour générer des mots de passe : nom tiré au hasard,
puis substitutions leet et caractère spécial (`genererChainePasswordAleatoire()`).

### Provenance

- Code : [xrogaan/phpMudnames](https://github.com/xrogaan/phpMudnames), étiquette `1.2.0`
  (licence MIT, voir `LICENSE`). L'original a depuis été réécrit (1.4, API statique) :
  cette copie reste sur l'API objet de la 1.2.
- Dictionnaires `data/` : archive CommentCaMarche « Phpmudnames - générateur de noms »
  (voir `readme.txt`, licence Creative Commons). L'original GitHub n'en contient pas.

### Modifications de Besançon 25 sur la 1.2.0

- Espace de noms `Mudname` (`new \Mudname\mudnames()`).
- Dictionnaires lus dans `__DIR__ . '/data'`, quel que soit le dossier courant.
- Dictionnaire sans partie reconnue : liste de capacités vide au lieu d'une erreur.
- `$info['dictionnaries']` et `$info['capability']` initialisés en tableaux.

### Corrections (21 et 22/11/2026)

- Fins de ligne LF ou CRLF retirées à la lecture des dictionnaires (`rtrim($buffer, "\r\n")`,
  comme dans la 1.4) : en CRLF, chaque partie gardait son `\r` et les noms étaient faux.
- Propriétés déclarées (`currentcap`, `forced_cap`, `forced_capability`, `current_file`) :
  plus d'avertissement de propriété dynamique sous PHP 8.2 et suivants.
- `get_info('file used')` rend le dictionnaire utilisé (l'original retombait dans `capability`).
- Exemples de `contrib/` adaptés à l'espace de noms (fatal sinon).
- `.gitattributes` : dictionnaires et PHP en LF.

### Utilisation

```php
require __DIR__ . '/mudnames.php';
$gname = new \Mudname\mudnames();
echo $gname->generate_name_from('random'); // ou le nom d'un fichier de data/
```

Les noms font de 2 à 18 caractères environ : un appelant qui exige une longueur
minimale doit refaire un tirage.
