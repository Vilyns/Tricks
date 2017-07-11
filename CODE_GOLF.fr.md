# Code Golf

D'après [Wikipedia](https://fr.wikipedia.org/wiki/Code_golf)

> Le Code golf est une compétition de programmation récréative durant laquelle chaque participant s'efforce d'implémenter un algorithme donné en produisant un programme le plus court possible (à ne pas confondre avec le binary sizecoding, qui s’intéresse à la taille finale du binaire exécutable). Il se peut que l'on nomme ce type de défi à partir du langage utilisé (on parlera alors, par exemple, de Perl golf).

> Bien que le terme de « code golf » ait apparemment été utilisé en 1999 avec Perl, puis popularisé plus tard de par l'utilisation de ce même langage pour le développement de programmes de chiffrement RSA, on sait que des compétitions du même genre ont eu lieu avant, utilisant le langage APL et probablement d'autres.

Certaines techniques de Code Golf compatibles avec la norme peuvent être utilisés a 42 ou Le 101 quand vous avez besoin de sauver quelque ligne pour rendre heureuse la norminette

## Accolades inutiles

Lorsque vous n'avez qu'une seule instruction en dessous d'une structure de controle ( while, if, else, .. ) vous pouvez omettre les accolades

### Exemple

```c
if (143 == 42 + 101)
	ft_putstr("Hello World");
else
	ft_putstr("Wtf");
 ```  

## Incrémentation précoce


### Fin de boucle
```c
while (*str != '\0')
	ft_putchar(*str++);
```
Généralement lorsque l'on est logique on place notre incrémentation en fin de boucle comme ceci

```c
int i = 0;

while (i < 42) {
	ft_putnbr(i);
	i++;
}
```

Cependant, en utilisant intelligemment l'opérateur d'incrémentation (++ ou --) on peut sauver cette ligne

```c
int i = -1;

while (++i < 42) {
	ft_putnbr(i);
}
```

On assigne ici notre notre i a la valeur souhaitée moins 1, car on effectue l'incrémentation dans le teste de validité de la boucle (ici cette operation incremente puis retourne le résultat)

ps: ++i n'est pas egal a i++ en effet ++i effectue l'incrémentation puis retourne la valeur alors que i++ retourne la valeur puis effectue l'incrementation

ps 2: L'élimination de cette ligne nous permet de sauver encore deux lignes avec le tip d'au dessus ;)

### Valeur de l'index inutilisé
Si jamais vous n'avez pas besoin de la valeur de votre index dans le corps de votre boucle  vous pouvez utiliser l'opérateur d'incrémentation en forme suffixé (i++)

```c
char *str = "Hello World";
int len = 0;

while (*str++ != '\0')
	len++;
```

On utilise l'opérateur d'incrémenation en forme suffixé ici car il retourne la valeur puis incremente ce qui nous permet de tester notre condition


### Utilisation dans le corps

Un troisieme cas de figure peux se presenter, incrémenter la derniere utilisation de l'index dans le corps de la boucle

```c
while (*str != '\0')
	ft_putchar(*str++);

int i = 0;
while (i < 42)
{
	ft_putnbr(i / 10);
	ft_putnbr(i++ % 10);
}
```

## Operateurs ternaires

Les operateurs ternaires de forme `condition ? expr1 : expr2` permentent de remplacer la structure `if/else`

### Exemple

```c
if (i == 42)
	return (1);
else
	return (-42);
```
devient
```c
	return (i == 42 ? 1 : -42)
```
## Conditions inutiles

Le c n'a pas de boolean built-in donc le faux est representé par zero et le vrai par tout ce qui est diffèrent de zéro, ce qui implique que tous les tests != 0 ( '\0' == 0 et NULL = 0) sont inutiles

### Exemple
```c
while (*str)
	ft_putchar(*str++);
```

## Iterer sur la taille d'une chaine de charactère

Utiliser votre fonction ft_strlen est parfois inutile, nous pouvons utiliser la chaine de charactère et voir si à l'index courrant il n'y a pas un null terminator

### Exemple
```c
char *c = "Hello World";
int len = ft_strlen(c)
int i = -1;
while (++i < len)
	...
```
devient
```c
char *c = "Hello World";
int i = -1;
while (c[++i])
	...
```

## Stocker du code dans une macro

Bien que cette pratique est très puissante je ne la recommande pas, elle est a utiliser en ultime recours

### Exemples
```c
int a = 0;
int b = 32;
int c = 76;
int d = 45;

int minAB = a < b ? a : b;
int minCD = c < d ? c : d;
```
devient
```
#define MIN(a, b)       ((a) < (b) ? (a) : (b))

int a = 0;
int b = 32;
int c = 76;
int d = 45;

int minAB = MIN(a, b);
int minCD = MIN(c, d);
```

Répétition d'un acces à une variable

```c

int tab[10];
...
tab[i];
.... tab[i] ....
....
tab[i]
```

```c
#define TI tab[i]

int tab[10];
...
TI;
.... TI ....
....
TI
```
