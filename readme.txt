Phpmudnames - g�n�rateur de noms--------------------------------
Url     : http://codes-sources.commentcamarche.net/source/42869-phpmudnames-generateur-de-nomsAuteur  : JayadevaDate    : 23/08/2013
Licence :
=========

Ce document intitul� � Phpmudnames - g�n�rateur de noms � issu de CommentCaMarche
(codes-sources.commentcamarche.net) est mis � disposition sous les termes de
la licence Creative Commons. Vous pouvez copier, modifier des copies de cette
source, dans les conditions fix�es par la licence, tant que cette note
appara�t clairement.

Description :
=============

mudnames, originellement &eacute;crit par Ragnar Hojland Espinosa, est un petit 
daemon en C &eacute;coutant les connexions telnet sur le port 4004. Quand une co
nnexion est re&ccedil;ue, il va envoyer une liste de noms, g&eacute;n&eacute;r&e
acute; de mani&egrave;re al&eacute;atoire, pouvant &ecirc;tre utilis&eacute; sur
 beaucoup de jeu de type MUD.
<br>
<br>Ici, j'ai repris la partie g&eacute
;n&eacute;rant les noms et je l'ai adapt&eacute;e au PHP. Mudnames ne semble plu
s &ecirc;tre vraiment trouvable sur le net. Cependant, il est inclus dans les di
stributions bas&eacute;e debian, d'ailleurs une recherche google avec le mot cle
f &quot;mudnames&quot; le prouve ais&eacute;ment.
<br>
<br>Les fichiers .c
ap contiennent des listes de fonctions avec leurs arguments a appliquer sur le d
ictionnaire. Ils existent pour forcer certains param&egrave;tres li&eacute; au d
ictionnaire. Par exemple, forcer l'association des parties des noms...
<br><a
 name='source-exemple'></a><h2> Source / Exemple : </h2>

<br><pre class='cod
e' data-mode='basic'>
&lt;?php

$number = 5;

require('mudnames.php');

$
gname = new mudnames();

$names = array();
while ($number &gt; 0) {
	$names[
] = $gname-&gt;generate_name_from('random');
	$number--;
}

echo implode('&l
t;br /&gt;', $names);
</pre>
