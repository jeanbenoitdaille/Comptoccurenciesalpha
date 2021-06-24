# Comptoccurenciesalpha
Compter le nombre d' occurences dans l' alphabet 
Dans cet exercice, le but était de compter le nombre d'occurrence de chaque lettre de l'alphabet dans le texte contenu dans la variable "lorem" pour obtenir le dictionnaire suivant :

{'a': 29, 'b': 3, 'c': 16, 'd': 19, 'e': 38, 'f': 3, 'g': 3, 'h': 1, 'i': 42, 'j': 0, 'k': 0, 'l': 22, 'm': 17, 'n': 24, 'o': 29, 'p': 11, 'q': 5, 'r': 22, 's': 18, 't': 32, 'u': 29, 'v': 3, 'w': 0, 'x': 3, 'y': 0, 'z': 0} 

Comme nous l'avons déjà fait, nous récupérons toutes les lettres de l'alphabet grâce au module string et la constante ascii_lowercase.

Pour commencer, nous créons une liste de la même longueur que notre variable "alphabet" :

    [0] * len(alphabet)

Ce qui nous donne donc la liste suivante :

    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Nous utilisons ensuite la fonction zip et la fonction dict pour créer un dictionnaire qui contient chaque lettre de l'alphabet comme clé et le nombre 0 comme valeur :

    resultat = dict(zip(alphabet, [0] * len(alphabet)))

Ce qui nous donne le dictionnaire suivant :

    {'a': 0, 'b': 0, 'c': 0, 'd': 0, 'e': 0, 'f': 0, 'g': 0, 'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0, 'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}

Nous passons ensuite avec une boucle for sur chaque lettre de notre variable "lorem" :

    for lettre in lorem.lower():

Nous faisons une petite vérification pour s'assurer que la lettre courante existe dans notre dictionnaire "resultat" (cela nous permet de filtrer les signes de ponctuation, les espaces etc) grâce à la méthode get.
L'intérêt de cette méthode est que si la clé n'existe pas, la méthode retourne None, ce qui nous permet de tester l'existence d'une clé dans un dictionnaire dans une structure conditionnelle sans risquer de faire planter notre script.

Il faut également faire attention de ne pas juste mettre if resultat.get(lettre) car la valeur de base que nous insérons dans le dictionnaire est 0. if 0 est équivalent à if False et la condition ne sera donc pas vérifiée.
Il faut donc explicitement vérifier si resultat.get(lettre) n'est pas égal à None pour que la structure conditionnelle soit vérifiée même si le get nous retourne 0 :

    if resultat.get(lettre) is not None:

Enfin, si cette lettre existe dans notre dictionnaire, nous ajoutons 1 à la valeur associée à la clé de la lettre contenue dans le dictionnaire :

    resultat[lettre] += 1

Ainsi, nous allons incrémenter à chaque fois cette valeur et ainsi compter le nombre d'occurrence de chaque lettre dans notre variable "lorem".

    SOLUTION ALTERNATIVE

Rappelez-vous qu'il est toujours possible de faire plus simple et plus concis. Pour le plaisir des yeux, voici donc une façon de résoudre cet exercice en une seule ligne, en utilisant la fonction count :

dict([(a, lorem.lower().count(a)) for a in string.ascii_lowercase])
