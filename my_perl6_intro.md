# Instalación
[Cómo instalar Perl6 y empezar a usarlo](http://rakudo.org/how-to-get-rakudo/)

Para los ejemplos y decir lo que devuelven usaremos Emacs, por la facilidad a la hora de insertar caracteres Unicode, ya Perl6 tiene un amplio soporte a Unicode, y aprovecharemos ésto. Para iniciar Perl6 desde Emacs pulsamos Escape+x y escribimos shell, una vez en la terminal ponemos perl6 y ya estaría.

# Introducción
Perl6 es un lenguaje multiparadigma que soporta programación dirigida a objetos, funcional y procedural. Su lema es *TMTOWTDI (Pronounced Tim Toady): There is more than one way to do it.*, algo que comprobaremos es muy cierto, y con Perl6 la forma de hacer las cosas es muy simple y generalmente compacta, en una línea podemos conseguir hacer cosas complejas y apenas se necesita usar el bucle for.

# Variables
Se declaran de la siguiente manera:
~~~perl6
my $variable    #(Any)
~~~
Al pulsar Enter en Emacs escribirá (Any) dado que así declarada la variable puede ser de cualquier tipo. Para hacer luego referencia a ésta deberemos nombrarla tal cual, con el sigil $ y todo, sino da error. Cuando se declara de tipo my es porque tiene de ámbito el programa en el que la usamos, hay más formas de declarar las variables de las cuales destacamos:
~~~perl6
our $variable   #introduce variables de paquetes externos al programa propio, funcionan como my pero añadiendo un alias a la tabla de símbolos
has $!variable    #crea un atributo privado en una clase  
~~~
A partir de la primera variable ya declarada podemos obtener cierta información:
~~~perl6
?$variable    #Devuelve False ya que la variable no ha sido inicializada a nada todavía
$variable.WHAT    #(Any), como ya hemos dicho puede ser de cualquier tipo al no haberla igualado a nada
$variable.^name   #Any, más correcto usar este método que el anterior
$variable.defined   #False
~~~
Las variables pueden ser de tipo **Int** (Entero), **Rat** (Racional), **Bool**, **Str** (String), **Hash**, **Array**, **List**, **Seq** ... Si declaramos una variable especificando el tipo del que queremos que sea, al intentar asignarle un valor de otro tipo dará error:
~~~perl6
#Declaramos la variable
my Int $entero= 7
$entero = "patata"    #Type check failed in assignment to $entero; expected Int but got Str ("patata")
~~~
Si asignamos ahora un valor a la variable inicial, la información que obtenemos es:
~~~perl6
$variable= "algo"
?$variable    #True
$variable.^name   #Str
#Podemos convertir una variable a otra de tipo bool usando so
$variable= so "not true"    #True, al ser un string no vacío
$variable.WHAT    #(Bool)
~~~
Vemos así como perl6 es un lenguaje gradualmente tipado, se puede cambiar el tipo de una variable sin problema, a conveniencia.

En general el prefijo ? devuelve True si es un string no vacío, un número distinto de 0 o el bool True. El prefijo ! devuelve lo negación de ?.

Las variables de tipo Str se pueden declarar con doble comilla o comilla simple, ello dependerá de si en ésta usamos comillas simples o si vamos a usarla posteriormente para mezclarla o hacer operaciones con otro Str:
~~~perl6
$variable= "I'm Elena"  #Aquí hay que usar doble comilla sí o sí
$variable= 'α'
++$variable   #Devuelve β, perl6 reconoce qué caracter unicode es y procede según si es un número, ...
$variable= 'ω'
++$variable   #Devuelve αα, e igualmente si declaramos la variable como αω al incrementar devolverá βα, le da una vuelta al alfabeto, no devuelve el siguiente caracter unicode según su code point
#También podemos declarar variables booleanas
$variable= False
$variable= True   #la primera letra en mayúscula siempre!
~~~
Para insertar caracteres unicodes en Emacs se pulsa Control+x+8+Enter y se introduce el nombre deseado(α se llama GREEK SMALL LETTER ALPHA, por ejemplo, si no se sabe el nombre se encuentra muy fácilmente en internet). También se puede copiar el caracter de internet y pegarlo en donde deseemos. Otras formas:
~~~perl6
$variable= "\c[GREEK SMALL LETTER PI]"  #poniendo \c[nombre del caracter] devuelve su símbolo unicode, en este caso π
#Equivalentemente, usando su code point:
$variable= "\x03C0"
~~~
Por último, se pueden inicializar variables en bloque:
~~~perl6
my (Str $a, Int $b, Rat $c)= <a 2 2.3>    #Si se igualaran a cosas de tipo distinto al incicado daría error. Se inicializan en orden, el primero con el primero, y así.
#Algunos métodos que podemos usar con los Rat:
say $c.numerator    #23
say $c.denominator    #10
say $c.nude     #(23 10)
~~~
say "bla bla bla" imprime bla bla bla. Como pasaba con los strings, pueden usarse también comillas simples, si no hay implícita en la frase o palabra otra comilla simple.
~~~perl6
say 'something' ~ ' I am giving up on you'  #imprime: something I am giving up on you
say "s'thing" ~ " I'm givin' up on you"    #imprime: s'thing I`m givin' up on you
~~~













#
