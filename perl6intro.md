# Introduction

Perl6 supports the three most popular programming paradigms:
+ Object-Oriented
+ Functional
+ Procedural

Perl 6 is a **high-level**, **general-purpose**, **gradually typed** language.
Its motto is:
> *TMTOWTDI (Pronounced Tim Toady): There is more than one way to do it.*

> *Easy things should stay easy, hard things should get easier, and impossible things should get hard.*

# Installing Perl 6
## Linux
To install Rakudo Star, which includes release 2018.01 of the Rakudo Perl 6
compiler, version 2018.01 MoarVM, plus various modules, documentation,
and other resources collected from the Perl 6 community, run the following commands from your terminal:

~~~shell
wget https://rakudo.perl6.org/downloads/star/rakudo-star-2018.01.tar.gz
tar xfz rakudo-star-2018.01.tar.gz
cd rakudo-star-2018.01
perl Configure.pl --gen-moar --prefix /opt/rakudo-star-2018.01
make install
~~~

For other options, go to http://rakudo.org/how-to-get-rakudo/#Installing-Rakudo-Star-Linux
macOS. Four options are available:

+ Follow the same steps listed for installing on Linux

+ Install with homebrew: `brew install rakudo-star`

+ Install with MacPorts: `sudo port install rakudo`

+ Download the latest installer (file with .dmg extension) from https://rakudo.perl6.org/downloads/star/

## Windows
Download the latest installer (file with .msi extension) from https://rakudo.perl6.org/downloads/star/
If your system architecture is 32-bit, download the x86 file; if it’s 64-bit, download the x86_64 file.

After installation, make sure C:\rakudo\bin is in the PATH


Rakudo Star bundles a line editor that helps you get the most out of the REPL.

If you installed plain Rakudo instead of Rakudo Star then you probably don’t have line editing features enabled (using the up and down arrows for history, left and right to edit input, TAB completion). Consider running the following command and you shall be all set:

 `zef install Linenoise` would work on Windows, Linux and macOS

 `zef install Readline` if you are on Linux and prefer the Readline library

 # Running Perl 6 code

 Running Perl 6 code can be done using the REPL (Read-Eval-Print Loop). To do this, open a terminal, type perl6 into the terminal window, and hit [Enter]. This will cause a prompt of > to appear. Next, type a line of code and hit [Enter]. The REPL will print out the value of the line. You may then type another line, or type exit and hit [Enter] to leave the REPL.

 Alternatively, write your code in a file, save it and run it. It is recommended that Perl 6 scripts have a .pl6 file name extension. Run the file by typing perl6 filename.pl6 into the terminal window and hitting [Enter]. Unlike the REPL, this will not automatically print the result of each line: the code must contain a statement like say to print output.

 The REPL is mostly used for trying a specific piece of code, typically a single line. For programs with more than a single line it is recommended to store them in a file and then run them.

 Single lines may also be tried non-interactively on the command-line by typing perl6 -e 'your code here' and hitting [Enter].

 For the examples, we will be using **GNU Emacs 24(GUI)**, by pressing Escape, x and then writing shell. Once that has been done, we just write perl6 and we are in! In order to use Unicode characters, we will have to press control+x+8+enter and then look for the desired character.

# Operators
>Perl 6 is **free form**: Most of the time you are free to use any amount of whitespace, although in certain cases whitespace carries meaning.

>**Statements** are typically a logical line of code, `say "Indeed" if True` will return Indeed.

>**Expressions** are a special type of statement that returns a value: 1+2 will return 3. THey are made of **Terms** and **Operators**.

>Terms are:
+ Variables: A value that can be manipulated and changed.
+ Literals: A constant value like a number or a string.

Types of operators:
+ **Prefix**:
  + **++**  
  ~~~perl6
  my $variable= "\c[GREEK SMALL LETTER ALPHA]"
  =begin comment
  That declaration is equivalent to:
  my $variable= "α"
  my $variable= 'α'
  created by copying and pasting the symbol, or:
  my $variable= "\x03B1"
  using its codepoint
  =end comment
  ++$variable #This will return β
  ~~~

  + **\--**
  ~~~perl6
  my $number= 'VII' # same as my $number= "\x2167" or my $number= "\c[ROMAN NUMERAL SEVEN]"
  --$number #This will return VI
  ~~~

  + **+** *Coerces the operand to a numeric value*
  ~~~perl6
  +"23" #Returns 23
  +True #Returns 1
  +False #Returns 0
  ~~~

  + **-** *Coerces the operand to a numeric value and returns the negation*
  ~~~perl6
  -"23" #Returns -23
  -True #Returns -1
  -False #Returns 0
  ~~~

  +

               Infix


               Between terms


               1+2

               Postfix


               After the term


               1++

               Circumfix


               Around the term


               (1)

               Postcircumfix


               After one term, around another


               Array[1]



Identifiers are the names given to terms when you define them.
Rules:

    They must start with an alphabetic character or an underscore.

    They can contain digits (except the first character).

    They can contain dashes or apostrophes (except the first and last character), provided there’s an alphabetic character to the right side of each dash or apostrophe.

Valid


Invalid

var1


1var

var-one


var-1

var’one


var'1

var1_


var1'

_ var


-var



Comments are divided into 3 types:

    Single line:

    # This is a single line comment

    Embedded:

    say #`(This is an embedded comment) "Hello World."

    Multi line:

    =begin comment
    This is a multi line comment.
    Comment 1
    Comment 2
    =end comment



    Strings need to be delimited by either double quotes or single quotes.

    Always use double quotes:

        if your string contains an apostrophe.

        if your string contains a variable that needs to be interpolated.

    say 'Hello World';   # Hello World
    say "Hello World";   # Hello World
    say "Don't";         # Don't
    my $name = 'John Doe';
    say 'Hello $name';   # Hello $name
    say "Hello $name";   # Hello John Doe



    Perl 6 variables are classified into 3 categories: Scalars, Arrays and Hashes.

    A sigil (Sign in Latin) is a character that is used as a prefix to categorize variables.

        $ is used for scalars

        @ is used for arrays

        % is used for hashes

        my $name = 'John Doe';
        say $name.uc;
        say $name.chars;
        say $name.flip;

        JOHN DOE
        8
        eoD nhoJ



        my $age = 17;
        say $age.is-prime;

        True

        routine uniparse

        sub    uniparse(Str:D $names  --> Str:D)
        method uniparse(Str:D $names: --> Str:D)

        Takes string with comma-separated Unicode names of characters and returns a string composed of those characters. Will fail if any of the characters' names are empty or not recognized. Whitespace around character names is ignored.

        say "I {uniparse 'TWO HEARTS'} Perl"; # OUTPUT: «I 💕 Perl␤»
        'TWO HEARTS, BUTTERFLY'.uniparse.say; # OUTPUT: «💕🦋␤»

        Note that unlike \c[...] construct available in string interpolation, uniparse does not accept decimal numerical values. Use chr routine to convert those:

        say "\c[1337]"; # OUTPUT: «Թ␤»
        say '1337'.chr; # OUTPUT: «Թ␤»

        my $age = 2.3;
        say $age.numerator;
        say $age.denominator;
        say $age.nude;

        23
        10
        (23 10)



        Arrays are lists containing multiple values.

        my @animals = 'camel','llama','owl';
        say @animals;

        Many operations can be performed on arrays as shown in the below example:
        	The tilde ~ is used for string concatenation.
        Script

        my @animals = 'camel','vicuña','llama';
        say "The zoo contains " ~ @animals.elems ~ " animals";
        say "The animals are: " ~ @animals;
        say "I will adopt an owl for the zoo";
        @animals.push("owl");
        say "Now my zoo has: " ~ @animals;
        say "The first animal we adopted was the " ~ @animals[0];
        @animals.pop;
        say "Unfortunately the owl got away and we're left with: " ~ @animals;
        say "We're closing the zoo and keeping one animal only";
        say "We're going to let go: " ~ @animals.splice(1,2) ~ " and keep the " ~ @animals;



        A basic array is declared as following:

        my @array;

        The basic array can have indefinite length and thus is called auto-extending.
        The array will accept any number of values with no restriction.

        In contrast, we can also create fixed-size arrays.
        These arrays cannot be accessed beyond their defined size.

        say 'hello world';

        that can also be written as:

        'hello world'.say;
        To declare an array of fixed size, specify its maximum number of elements in square brackets immediately after its name:

        my @array[3];

        This array will be able to hold a maximum of 3 values, indexed from 0 to 2.

        my @array[3];
        @array[0] = "first value";
        @array[1] = "second value";
        @array[2] = "third value";

        You will not be able to add a fourth value to this array:

        my @array[3];
        @array[0] = "first value";
        @array[1] = "second value";
        @array[2] = "third value";
        @array[3] = "fourth value";

        Index 3 for dimension 1 out of range (must be 0..2)



        The arrays we saw until now are one-dimensional.
        Fortunately, we can define multi-dimensional arrays in Perl 6.

        my @tbl[3;2];

        This array is two-dimensional. The first dimension can have a maximum of 3 values and the second dimension a maximum of 2 values.

        Think of it as a 3x2 grid.

        my @tbl[3;2];
        @tbl[0;0] = 1;
        @tbl[0;1] = "x";
        @tbl[1;0] = 2;
        @tbl[1;1] = "y";
        @tbl[2;0] = 3;
        @tbl[2;1] = "z";
        say @tbl

        [[1 x] [2 y] [3 z]]

# HASHES
        A Hash is a set of Key/Value pairs.

        my %capitals = ('UK','London','Germany','Berlin');
        say %capitals;

        Another succinct way of filling the hash:

        my %capitals = (UK => 'London', Germany => 'Berlin');
        say %capitals;

        Some of the methods that can be called on hashes are:
        Script

        my %capitals = (UK => 'London', Germany => 'Berlin');
        %capitals.push: (France => 'Paris');
        say %capitals.kv;
        say %capitals.keys;
        say %capitals.values;
        say "The capital of France is: " ~ %capitals<France>;

        .WHAT will return the type of value held in a variable.

        my $var = 'Text';
        say $var;
        say $var.WHAT;

        $var = 123;
        say $var;
        say $var.WHAT;

        Hash assignment

Assigning a list of elements to a hash variable first empties the variable, and then iterates the elements of the right-hand side. If an element is a Pair, its key is taken as a new hash key, and its value as the new hash value for that key. Otherwise the value is coerced to Str and used as a hash key, while the next element of the list is taken as the corresponding value.

my %h = 'a', 'b', c => 'd', 'e', 'f';
# same as
my %h = a => 'b', c => 'd', e => 'f';
# or
my %h = <a b c d e f>;

If a Pair is encountered where a value is expected, it is used as a hash value:

my %h = 'a', 'b' => 'c';
say %h<a>.^name;            # OUTPUT: «Pair␤»
say %h<a>.key;              # OUTPUT: «b␤»

If the same key appears more than once, the value associated with its last occurrence is stored in the hash:

my %h = a => 1, a => 2;
say %h<a>;                  # OUTPUT: «2␤»

To assign a hash to a variable which does not have the % sigil, you may use the %() hash constructor:

my $h = %( a => 1, b => 2 );
say $h.^name;               # OUTPUT: «Hash␤»
say $h<a>;                  # OUTPUT: «1␤»

NOTE: Hashes can also be constructed with { }. It is recommended to use the %() hash constructor, as braces are reserved for creating Block objects and therefore braces only create Hash objects in specific circumstances.

If one or more values reference the topic variable, $_, the right-hand side of the assignment will be interpreted as a Block, not a Hash:

my @people = [
    %( id => "1A", firstName => "Andy", lastName => "Adams" ),
    %( id => "2B", firstName => "Beth", lastName => "Burke" ),
    # ...
];

sub lookup-user (Hash $h) { #`(Do something...) $h }

my @names = map {
    # While this creates a hash:
    my  $query = { name => "$person<firstName> $person<lastName>" };
    say $query.^name;      # OUTPUT: «Hash␤»

    # Doing this will create a Block. Oh no!
    my  $query2 = { name => "$_<firstName> $_<lastName>" };
    say $query2.^name;       # OUTPUT: «Block␤»
    say $query2<name>;       # fails

    CATCH { default { put .^name, ': ', .Str } };
    # OUTPUT: «X::AdHoc: Type Block does not support associative indexing.␤»
    lookup-user($query);   # Type check failed in binding $h; expected Hash but got Block
}, @people;

This would have been avoided if you had used the %() hash constructor. Only use curly braces for creating Blocks.

Slices

You can assign to multiple keys at the same time with a slice.

my %h; %h<a b c> = 2 xx * ; %h.perl.say;  # OUTPUT: «{:a(2), :b(2), :c(2)}␤»
my %h; %h<a b c> = ^3;     %h.perl.say;  # OUTPUT: «{:a(0), :b(1), :c(2)}␤»

#TYPES
Types

In the previous examples, we did not specify what type of values the variables should hold.
	.WHAT will return the type of value held in a variable.

my $var = 'Text';
say $var;
say $var.WHAT;

$var = 123;
say $var;
say $var.WHAT;

As you can see in the above example, the type of value in $var was once (Str) and then (Int).

This style of programming is called dynamic typing. Dynamic in the sense that variables may contain values of Any type.

Now try running the below example:
Notice Int before the variable name.

my Int $var = 'Text';
say $var;
say $var.WHAT;

It will fail and return this error message: Type check failed in assignment to $var; expected Int but got Str

What happened is that we specified beforehand that the variable should be of type (Int). When we tried to assign an (Str) to it, it failed.

This style of programming is called static typing. Static in the sense that variable types are defined before assignment and cannot change.

Perl 6 is classified as gradually typed; it allows both static and dynamic typing.
Arrays and hashes can also be statically typed:

my Int @array = 1,2,3;
say @array;
say @array.WHAT;

my Str @multilingual = "Hello","Salut","Hallo","您好","안녕하세요","こんにちは";
say @multilingual;
say @multilingual.WHAT;

my Str %capitals = (UK => 'London', Germany => 'Berlin');
say %capitals;
say %capitals.WHAT;

my Int %country-codes = (UK => 44, Germany => 49);
say %country-codes;
say %country-codes.WHAT;

Type


Description


Example


Result

Mu


The root of the Perl 6 type hierarchy


Any


Default base class for new classes and for most built-in classes


Cool


Value that can be treated as a string or number interchangeably


my Cool $var = 31; say $var.flip; say $var * 2;


13 62

Str


String of characters


my Str $var = "NEON"; say $var.flip;


NOEN

Int


Integer (arbitrary-precision)


7 + 7


14

Rat


Rational number (limited-precision)


0.1 + 0.2


0.3

Bool


Boolean


!True


False

my Int $var;
say $var.WHAT;    # (Int)
my $var2;
say $var2.WHAT;   # (Any)
$var2 = 1;
say $var2.WHAT;   # (Int)
$var2 = "Hello";
say $var2.WHAT;   # (Str)
$var2 = True;
say $var2.WHAT;   # (Bool)
$var2 = Nil;
say $var2.WHAT;   # (Any)

The type of a variable holding a value is correlated to its value.
The type of a strongly declared empty variable is the type with which it was declared.
The type of an empty variable that wasn’t strongly declared is (Any)
To clear the value of a variable, assign Nil to it.


# Scoping

Before using a variable for the first time, it needs to be declared.

Several declarators are used in Perl 6. We’ve been using my, so far.

my $var=1;

The my declarator give the variable lexical scope. In other words, the variable will only be accessible in the same block it was declared.

A block in Perl 6 is delimited by { }. If no block is found, the variable will be available in the whole Perl 6 script.

{
  my Str $var = 'Text';
  say $var;   # is accessible
}
say $var;   # is not accessible, returns an error

Since a variable is only accessible in the block where it is defined, the same variable name can be used in another block.

{
  my Str $var = 'Text';
  say $var;
}
my Int $var = 123;
say $var;



On the other hand, we cannot change the value bound to a variable.
Binding is done using the := operator.
# Binding

my Int $var := 123;
say $var;
$var = 999;
say $var;

# Sigils

There are four sigils. The scalar-sigil $, the positional-sigil @, the associative-sigil % and the callable-sigil &.

Sigils provide a link between syntax, the type system and containers. They provide a shortcut for the most common type constraints when declaring variables and serve as markers for string interpolation. The positional-sigil and the associative-sigil provide type constraint that enforce a base type subscripts require to know what methods to dispatch to. The callable-sigil does the same for function calls. The latter also tells the compiler where parentheses for calls can be omitted. The positional and associative-sigil also simplify assignment by flattening by default.
Sigil 	Type constraint 	Default type 	Assignment 	Examples
$ 	Mu (no type constraint) 	Any 	item 	Int, Str, Array, Hash
@ 	Positional 	Array 	list 	List, Array, Range, Buf
% 	Associative 	Hash 	list 	Hash, Map, Pair
& 	Callable 	Callable 	item 	Sub, Method, Block, Routine

# Sigilless variables

Using the \ prefix, it's possible to create variables that do not have a sigil:

my \degrees = pi / 180;
my \θ       = 15 * degrees;

Note that sigilless variable do not have associated containers. This means degrees and θ, above, actually directly represent Nums. To illustrate, try assigning to one after you've defined it:

θ = 3; # Dies with the error "Cannot modify an immutable Num"

Sigilless variables do not enforce context, so they can be used to pass something on as-is:

sub logged(&f, |args) {
    say('Calling ' ~ &f.name ~ ' with arguments ' ~ args.perl);
    my \result = f(|args);
    #  ^^^^^^^ not enforcing any context here
    say(&f.name ~ ' returned ' ~ result.perl);
    return |result;
}

Sigilless variables can also be used for binding:
Sigilless variables also bind by default and so do parameters with the trait is raw.

my $a = 42;
my \b = $a;
b++;
say $a;         # OUTPUT: «43␤»

sub f($c is raw) { $c++ }
f($a);
say $a;         # OUTPUT: «44␤»

# Scalar containers and listy things

There are a number of positional container types with slightly different semantics in Perl 6. The most basic one is List It is created by the comma operator.

say (1, 2, 3).^name;    # OUTPUT: «List␤»

A list is immutable, which means you cannot change the number of elements in a list. But if one of the elements happens to be a scalar container, you can still assign to it:

my $x = 42;
($x, 1, 2)[0] = 23;
say $x;                 # OUTPUT: «23␤»
($x, 1, 2)[1] = 23;     # Cannot modify an immutable value
CATCH { default { say .^name, ': ', .Str } };
//OUTPUT: «X::Assignment::RO: Cannot modify an immutable Int␤»

So the list doesn't care about whether its elements are values or containers, they just store and retrieve whatever was given to them.

Lists can also be lazy, so elements at the end are generated on demand from an iterator.

An Array is just like a list, except that it forces all its elements to be containers, which means that you can always assign to elements:

my @a = 1, 2, 3;
@a[0] = 42;
say @a;         # OUTPUT: «[42 2 3]␤»

@a actually stores three scalar containers. @a[0] returns one of them, and the assignment operator replaces the integer value stored in that container with the new one, 42.

# Flattening, items and containers

The % and @ sigils in Perl 6 generally indicate multiple values to an iteration construct, whereas the $ sigil indicates only one value.

my @a = 1, 2, 3;
for @a { };         # 3 iterations
my $a = (1, 2, 3);
for $a { };         # 1 iteration

@-sigiled variables do not flatten in list context:

my @a = 1, 2, 3;
my @b = @a, 4, 5;
say @b.elems;               # OUTPUT: «3␤»

There are operations that flatten out sublists that are not inside a scalar container: slurpy parameters (*@a) and explicit calls to flat:

my @a = 1, 2, 3;
say (flat @a, 4, 5).elems;  # OUTPUT: «5␤»

sub f(*@x) { @x.elems };
say f @a, 4, 5;             # OUTPUT: «5␤»

As hinted above, scalar containers prevent that flattening:

sub f(*@x) { @x.elems };
my @a = 1, 2, 3;
say f $@a, 4, 5;            # OUTPUT: «3␤»

The @ character can also be used as a prefix to coerce the argument to a list, thus removing a scalar container:

my $x = (1, 2, 3);
.say for @$x;               # 3 iterations

However, the <> is more appropriate to decontainerize items that aren't lists:

my $x = ^Inf .grep: *.is-prime;
say "$_ is prime" for @$x;  # WRONG! List keeps values, thus leaking memory
say "$_ is prime" for $x<>; # RIGHT. Simply decontainerize the Seq

my $y := ^Inf .grep: *.is-prime; # Even better; no Scalars involved at all

Methods generally don't care whether their invocant is in a scalar, so

my $x = (1, 2, 3);
$x.map(*.say);              # 3 iterations

maps over a list of three elements, not of one.
# A LITTLE BIT ABOUT SCALAR CONTAINERS
sub f($a is rw) {
    $a = 23;
}
my $x = 42;
f($x);
say $x;         # OUTPUT: «23␤»

Inside the subroutine, the lexpad entry for $a points to the same container that $x points to outside the subroutine. Which is why assignment to $a also modifies the contents of $x.

Likewise a routine can return a container if it is marked as is rw:

my $x = 23;
sub f() is rw { $x };
f() = 42;
say $x;         # OUTPUT: «42␤»

For explicit returns, return-rw instead of return must be used.

Returning a container is how is rw attribute accessors work. So

class A {
    has $.attr is rw;
}

is equivalent to

class A {
    has $!attr;
    method attr() is rw { $!attr }
}

Scalar containers are transparent to type checks and most kinds of read-only accesses. A .VAR makes them visible:

my $x = 42;
say $x.^name;       # OUTPUT: «Int␤»
say $x.VAR.^name;   # OUTPUT: «Scalar␤»

And is rw on a parameter requires the presence of a writable Scalar container:

sub f($x is rw) { say $x };
f 42;
CATCH { default { say .^name, ': ', .Str } };
# OUTPUT: «X::Parameter::RW: Parameter '$x' expected a writable container, but got Int value␤»
#COOL METHODS ARRAY
(List) method ACCEPTS

Defined as:

multi method ACCEPTS(List:D: $topic)

If $topic is an Iterable, returns True or False based on whether the contents of the two Iterables match. A Whatever element in the invocant matches anything in the corresponding position of the $topic Iterable. A HyperWhatever matches any number of any elements, including no elements:

say (1, 2, 3)       ~~ (1,  *, 3);  # OUTPUT: «True␤»
say (1, 2, 3)       ~~ (9,  *, 5);  # OUTPUT: «False␤»
say (1, 2, 3)       ~~ (   **, 3);  # OUTPUT: «True␤»
say (1, 2, 3)       ~~ (   ** , 5);  # OUTPUT: «False␤»
say (1, 3)          ~~ (1, ** , 3); # OUTPUT: «True␤»
say (1, 2, 4, 5, 3) ~~ (1, ** , 3); # OUTPUT: «True␤»
say (1, 2, 4, 5, 6) ~~ (1, ** , 5); # OUTPUT: «False␤»
say (1, 2, 4, 5, 6) ~~ (   **   ); # OUTPUT: «True␤»
say ()              ~~ (   **   ); # OUTPUT: «True␤»

In addition, returns False if either the invocant or $topic is a lazy Iterable, unless $topic is the same object as the invocant, in which case True is returned.

If $topic is not an Iterable, returns the invocant if the invocant has no elements or its first element is a Match object (this behaviour powers m:g// smartmatch), or False otherwise.

routine pop

Defined as:

multi sub    pop(Array:D )
multi method pop(Array:D:)

Removes and returns the last item from the array. Fails for an empty array.

Example:

my @foo = <a b>; # a b
@foo.pop;        # b
pop @foo;        # a
pop @foo;
CATCH { default { put .^name, ': ', .Str } };
# OUTPUT: «X::Cannot::Empty: Cannot pop from an empty Array␤»

routine push

Defined as:

multi sub    push(Array:D, ** @values --> Array:D)
multi method push(Array:D: ** @values --> Array:D)

Adds the @values to the end of the array, and returns the modified list. Throws for lazy arrays.

Example:

my @foo = <a b c>;
@foo.push: 'd';
say @foo;                   # OUTPUT: «[a b c d]␤»

Note that push does not attempt to flatten its argument list. If you pass an array or list as the thing to push, it becomes one additional element:

my @a = <a b c>;
my @b = <d e f>;
@a.push: @b;
say @a.elems;               # OUTPUT: «4␤»
say @a[3].join;             # OUTPUT: «def␤»

Only if you supply multiple values as separate arguments to push are multiple values added to the array:

my @a = '1';
my @b = <a b>;
my @c = <E F>;
@a.push: @b, @c;
say @a.elems;                # OUTPUT: «3␤»

See method append for when you want to append multiple values that are stored in a single array.
## Trying the method push
~~~perl
perl6
To exit type 'exit' or '^D'
> my @foo = <a b c>
[a b c]
> @foo.pop
c
> say @foo
[a b]
> pop @foo
b
> say @foo
[a]
> my @a = <abc>
[abc]
> my @b = <def>
[def]
> @a.push: @b
[abc [def]]
> say @a[3]
(Any)
> say @a[3].join
Use of uninitialized value of type Any in string context.
Methods .^name, .perl, .gist, or .say can be used to stringify it to something meaningful.
 in block <unit> at <unknown file> line 1


> say a[3].join
 ===SORRY!=== Error while compiling:
Undeclared routine:
   a used at line 1

> say @a[2]
(Any)
> say @a[2].join
Use of uninitialized value of type Any in string context.
Methods .^name, .perl, .gist, or .say can be used to stringify it to something meaningful.
 in block <unit> at <unknown file> line 1


> say @a.elems
2
> say @a[1]
[def]
> my @c=<f g h>
[f g h]
>@a.push: @c
[abc [def] [f g h]]
> say @a[2]
[f g h]
> say @a[2].join
fgh
> say @a[2].elems
3
> 3

my @a = <abc>
[abc]
> my %h= d, e, f => md, me, mf
 ===SORRY!=== Error while compiling:
Undeclared routines:
   d used at line 1
   md used at line 1. Did you mean 'dd'?
   me used at line 1
   mf used at line 1

> my %h= d, e, f => 'md', 'me', 'mf'
 ===SORRY!=== Error while compiling:
Undeclared routine:
   d used at line 1

> my %h= 'd', 'e', 'f' => 'md', 'me', 'mf'
{d => e, f => md, me => mf}
> @a.push: %h
[abc {d => e, f => md, me => mf}]

>say @a.elems
2
> say @a[1].elems
3
> say @a[1]<d>
e
~~~

# Functions and mutators

It is important to differentiate between functions and mutators.
Functions do not change the state of the object they were called on.
Mutators modify the state of the object.

my @numbers = [7,2,4,9,11,3];

@numbers.push(99);
say @numbers;      #1

say @numbers.sort; #2
say @numbers;      #3

@numbers.=sort;
say @numbers;      #4

Output

[7 2 4 9 11 3 99] #1
(2 3 4 7 9 11 99) #2
[7 2 4 9 11 3 99] #3
[2 3 4 7 9 11 99] #4

Explanation

.push is a mutator; it changes the state of the array (#1)

.sort is a function; it returns a sorted array but doesn’t modify the state of the initial array:

    (#2) shows that it returned a sorted array.

    (#3) shows that the initial array is still unmodified.

In order to enforce a function to act as a mutator, we use .= instead of . (#4) (Line 9 of the script)


# Loops and conditions

Perl 6 has many conditional and looping constructs.
5.1. if

The code runs only if a condition has been met; i.e., an expression evaluates to True.

my $age = 19;

if $age > 18 {
  say 'Welcome'
}

In Perl 6, we can invert the code and the condition.
Even if the code and the condition have been inverted, the condition is always evaluated first.

my $age = 19;

say 'Welcome' if $age > 18;

If the condition is not met, we can specify alternate blocks for execution by using:

    else

    elsif

# run the same code for different values of the variable
my $number-of-seats = 9;

if $number-of-seats <= 5 {
  say 'I am a sedan'
} elsif $number-of-seats <= 7 {
  say 'I am 7 seater'
} else {
  say 'I am a van'
}

5.2. unless

The negated version of an if statement can be written using unless.

The following code:

my $clean-shoes = False;

if not $clean-shoes {
  say 'Clean your shoes'
}

can be written as:

my $clean-shoes = False;

unless $clean-shoes {
  say 'Clean your shoes'
}

Negation in Perl 6 is done using either ! or not.

unless (condition) is used instead of if not (condition).

unless cannot have an else clause.
5.3. with

with behaves like the if statement, but checks if the variable is defined.

my Int $var=1;

with $var {
  say 'Hello'
}

If you run the code without assigning a value to the variable, nothing should happen.

my Int $var;

with $var {
  say 'Hello'
}

without is the negated version of with. You should be able to relate it to unless.

If the first with condition is not met, an alternate path can be specified using orwith.
with and orwith can be compared to if and elsif.


5.4. for

The for loop iterates over multiple values.

my @array = [1,2,3];

for @array -> $array-item {
  say $array-item * 100
}

Notice that we created an iteration variable $array-item and then performed the operation * 100 on each array item.
5.5. given

given is the Perl 6 equivalent of the switch statement in other languages, but much more powerful.

my $var = 42;

given $var {
    when 0..50 { say 'Less than or equal to 50'}
    when Int { say "is an Int" }
    when 42  { say 42 }
    default  { say "huh?" }
}

After a successful match, the matching process will stop.

Alternatively proceed will instruct Perl 6 to continue matching even after a successful match.

my $var = 42;

given $var {
    when 0..50 { say 'Less than or equal to 50';proceed}
    when Int { say "is an Int";proceed}
    when 42  { say 42 }
    default  { say "huh?" }
}

5.6. loop

loop is another way of writing a for loop.

Actually, loop is how for loops are written in C-family programming languages.

Perl 6 belongs to the C-family languages.

loop (my $i = 0; $i < 5; $i++) {
  say "The current number is $i"
}


        	say (‘♔’…‘♙’)».uniname».words»[2]




        	#   KING QUEEN ROOK BISHOP KNIGHT PAWN

          Any class that you create can now have a TWEAK method. This method will be called after all other initializations of a new instance of the class have been done, just before it is being returned by .new. A simple, bit contrived example in which a class A has one attribute, of which the default value is 42, but which should change the value if the default is specified at object creation:

          class A {
              has $.value = 42;
              method TWEAK(:$value = 0) { # default prevents warning
                  # change the attribute if the default value is specified
                  $!value = 666 if $value == $!value;
              }
          }
          # no value specified, it gets the default attribute value
          dd A.new;              # A.new(value => 42)

          # value specified, but it is not the default
          dd A.new(value => 77); # A.new(value => 77)

          # value specified, and it is the default
          dd A.new(value => 42); # A.new(value => 666)


          You can now also create a grapheme by specifying the Unicode name of the grapheme, e.g.:

say "BUTTERFLY".parse-names; # 🦋

or create the Unicode name string at runtime:

my $t = "THUMBS UP SIGN, EMOJI MODIFIER FITZPATRICK TYPE";
print "$t-$_ ".parse-names for 3..6; # 👍🏼👍🏽👍🏾👍🏿

Or collate instead of just sort:

# sort by codepoint value
say <ä a o ö>.sort; # (a o ä ö)
# sort using Unicode Collation Algorithm
say <ä a o ö>.collate; # (a ä o ö)

Or use unicmp instead of cmp:

say "a" cmp "Z"; # More
 say "a" unicmp "Z"; # Less



 By the way, .head now also takes a WhateverCode so you can indicate you want all values except the last N (e.g. .head(*-3) would give you all values except the last three). The same goes for .tail (e.g. .tail(*-3) would give you all values except the first three).

Some additions to the Iterator role make it possible for iterators to support the .skip functionality even better. If an iterator can be more efficient in skipping a value than to actually produce it, it should implement the skip-one method. Derived from this are the skip-at-least and skip-at-least-pull-one methods that can be provided by an iterator.

An example of the usage of .skip to find out the 1000th prime number:

say (^Inf).grep(*.is-prime)[999]; # 7919

Versus:

say (^Inf).grep(*.is-prime).skip(999).head; # 7919

The latter is slightly more CPU efficient, but more importantly much more memory efficient, as it doesn’t need to keep the first 999 prime numbers in memory.

# EXAMPLES
# First 12 even numbers:
say (2, 4 … ∞)[^12];      # OUTPUT: (2 4 6 8 10 12 14 16 18 20 22 24)

# First 10 powers of 2:
say (2, 2², 2³ … ∞)[^10]; # OUTPUT: (2 4 8 16 32 64 128 256 512 1024)

# First 13 Fibonacci numbers:
say (1, 1, *+* … ∞)[^13]; # OUTPUT: (1 1 2 3 5 8 13 21 34 55 89 144 233)



I mentioned earlier that Seqs are one-shot Iterables that can be iterated only once. So what exactly happens when we try to iterate them the second time?

my $seq := gather take 42;

.say for $seq;

.say for $seq;

​

# OUTPUT:

# 42

# This Seq has already been iterated, and its values consumed

# (you might solve this by adding .cache on usages of the Seq, or

# by assigning the Seq into an array)


The Seq is deemed consumed whenever something asks it for its Iterator after another thing grabbed it, like the for loop would. For example, even if in the first for loop above we would've iterated over just 1 item, we wouldn't be able to resume taking more items in the next for loop, as it'd try to ask for the Seq's iterator that was already taken by the first for loop.


As you can imagine, having Seqs always be one-shot would be somewhat of a pain in the butt. A lot of times you can afford to keep the entire sequence around, which is the price for being able to access its values more than once, and that's precisely what the Seq.cachemethod does:

my $seq := gather { take 42; take 70 };

$seq.cache;

​

.say for $seq;

.say for $seq;

​

# OUTPUT:

# 42

# 70

# 42

# 70

As long as you call .cache before you fetch the first item of the Seq, you're good to go iterating over it until the heat death of the Universe (or until its cache noms all of your RAM). However, often you do not even need to call .cache yourself.

Many methods will automatically .cache the Seq for you:

    .Str, .Stringy, .fmt, .gist, .perl methods always .cache
    .AT-POS and .EXISTS-POS methods, or in other words, Positional indexing like $seq[^10], always .cache
    .elems, .Numeric, and .Int will .cache the Seq, unless the underlying Iterator provides a .count-only method (we'll get to those in PART II)
    .Bool will .cache unless the underlying Iterator provides .bool-only or .count-only methods

    sub foo (@pos) { say @pos[1, 3, 5] }

    my $seq := 2, 4 … ∞;
    foo $seq; # OUTPUT: (4 8 12)

    We have a sub that expects a Positional argument and we give it a Seq which isn't Positional, yet it all works out, because the binder .caches our Seq and uses the List the .cache method returns to be the Positional to be used, thanks to it doing the PositionalBindFailover role.

**In Perl 6, Seqs are one-shot Iterables that don't keep their values around, which makes them very useful for iterating over huge, or even infinite, sequences. However, it's perfectly possible to cache Seq values and re-use them, if that is needed. In fact, many of the Seq's methods will automatically cache the Seq for you.**

# Smileys

multi foo (Int:U $x) { 'Y U NO define $x?'         }

multi foo (Int:D $x) { "The square of $x is {$x²}" }

​

my Int $x;

say foo $x;

$x = 42;

say foo $x;

​

# OUTPUT:

# Y U NO define $x?

# The square of 42 is 1764

Smileys are :U, :D, or :_ appended to the type name. The :_ is the default you get when you don't specify a smiley. The :U specifies undefined values only, while :D specifies defined values only.

This can be useful to detect whether a method is called on the class or on the instance by having two multies with :U and :D on the invocant.

# Subsets: Tailor-Made Types

Built-in types are cool and all, but most of the data programmers work with doesn't match them precisely. That's where Perl 6 subsets come into play:

subset Prime of Int where * .is-prime;

my Prime $x = 3;

$x = 11; # works

$x = 4;  # Fails with type mismatch

Using the subset keyword, we created a type called Prime on the fly. It's a subset of Int, so anything that's non-Int doesn't fit the type. We also specify an additional restriction with the where keyword; that restriction being that .is-prime method called on the given value must return a true value.

With that single line of code, we created a special type and can use it as if it were built-in! Not only can we use it to specify the type of variables, sub/method parameters and return values, but we can test arbitrary values against it with the smartmatch operator, just as we can with built-in types:

subset Prime of Int where * .is-prime;

say "It's an Int"  if 'foo' ~~ Int;   # false, it's a Str

say "It's a prime" if 31337 ~~ Prime; # true, it's a prime number

Is your "type" a one-off thing you just want to apply to a single variable? You don't need to declare a separate subset at all! Just use the where keyword after the variable and you're good to go:

multi is-a-prime (Int $ where * .is-prime --> 'Yup' ) {}

multi is-a-prime (Any                    --> 'Nope') {}

​

say is-a-prime 3;     # Yup

say is-a-prime 4;     # Nope

say is-a-prime 'foo'; # Nope

The --> in the signature above is just another way to indicate the return type, or in this case, a concrete returned value. So we have two multies with different signatures. First one takes an Int that is a prime number and the second one takes everything else. With exactly zero code in the bodies of our multies we wrote a subroutine that can tell you whether a number is prime!!

# Subroutines
7.1. Definition

Subroutines (also called subs or functions) are a means of packaging and reusing functionality.

A subroutine definition begins with the keyword sub. After their definition, they can be called by their handle.
Check out the below example:

sub alien-greeting {
 say "Hello earthlings";
}

alien-greeting;

The previous example showcased a subroutine that doesn’t require any input.



The below subroutine accepts a string argument.

sub say-hello (Str $name) {
    say "Hello " ~ $name ~ "!!!!"
}
say-hello "Paul";
say-hello "Paula";



It is possible to define multiple subroutines that have the same name but different signatures. When the subroutine is called, the runtime environment will decide which version to use based on the number and type of supplied arguments. This type of subroutine is defined the same way as normal subs except that we use the multi keyword instead of sub.

multi greet($name) {
    say "Good morning $name";
}
multi greet($name, $title) {
    say "Good morning $title $name";
}

greet "Johnnie";
greet "Laura","Mrs.";



If a subroutine is defined to accept an argument, and we call it without providing it with the required argument, it will fail.

Perl 6 provides us the ability to define subroutines with:

    Optional Parameters

    Default Parameters

Optional parameters are defined by appending ? to the parameter name.

sub say-hello($name?) {
  with $name { say "Hello " ~ $name }
  else { say "Hello Human" }
}
say-hello;
say-hello("Laura");

If the user doesn’t need to supply an argument, a default value can be defined.
This is done by assigning a value to the parameter within the subroutine definition.

sub say-hello($name="Matt") {
  say "Hello " ~ $name;
}
say-hello;
say-hello("Laura");



All the subroutines we’ve seen so far do something — they display some text on the terminal.

Sometimes, though, we execute a subroutine for its return value so we can use it later in the flow of our program.

If a function is allowed to run through it’s block to the end, the last statement or expression will determine the return value.
Implicit return

sub squared ($x) {
  $x ** 2;
}
say "7 squared is equal to " ~ squared(7);

For the sake of clarity, it might be a good idea to explicitly specify what we want returned. This can be done using the return keyword.
Explicit return

sub squared ($x) {
  return $x ** 2;
}
say "7 squared is equal to " ~ squared(7);

Restricting return values

In one of the previous examples, we saw how we can restrict the accepted argument to be of a certain type. The same can be done with return values.

To restrict the return value to a certain type, we either use the returns trait or the arrow notation --> in the signature.
Using the returns trait

sub squared ($x) returns Int {
  return $x ** 2;
}
say "1.2 squared is equal to " ~ squared(1.2);

Using the arrow

sub squared ($x --> Int) {
  return $x ** 2;
}
say "1.2 squared is equal to " ~ squared(1.2);

If we fail to provide a return value that matches the type constraint, an error will be thrown.

Type check failed for return value; expected Int but got Rat (1.44)




Not only can type constraints control the type of the return value; they can also control its definedness.

In the previous examples, we specified that the return value should be an Int.

We could also have specified that the returned Int should be strictly defined or undefined using the following signatures:
-→ Int:D and -→ Int:U

That being said, it is good practice to use those type constraints.
Below is the modified version of the previous example that uses :D to force the returned Int to be defined.

sub squared ($x --> Int:D) {
  return $x ** 2;
}
say "1.2 squared is equal to " ~ squared(1.2);

Chaining

In Perl 6, methods can be chained, so you’re not required to pass the result of one method to another as an argument.

To illustrate: Given an array, you may need to return the unique values of the array, sorted from biggest to smallest.

Here’s a non-chained solution:

my @array = <7 8 9 0 1 2 4 3 5 6 7 8 9>;
my @final-array = reverse(sort(unique(@array)));
say @final-array;

Here, we call unique on @array, pass the result as an argument to sort, and then pass that result to reverse.

In contrast, with chained methods, the above example can be rewritten as:

my @array = <7 8 9 0 1 2 4 3 5 6 7 8 9>;
my @final-array = @array.unique.sort.reverse;
say @final-array;

You can already see that chaining methods is easier on the eye.


Hyper operator

The hyper operator >>. will call a method on all elements of a list and return a list of the results.

my @array = <0 1 2 3 4 5 6 7 8 9 10>;
sub is-even($var) { $var %% 2 };

say @array>>.is-prime;
say @array>>.&is-even;

Using the hyper operator we can call methods already defined in Perl 6, e.g. is-prime that tells us if a number is prime or not.
In addition we can define new subroutines and call them using the hyper operator. In this case we have to prepend & to the name of the method; e.g., &is-even.

This is very practical as it relieves us from writing a for loop to iterate over each value.



Lazy list built using a deduced generator

my $lazylist = (0,2 ... 10);
say $lazylist;

The initial elements are 0 and 2 and the endpoint is 10. No generator was defined, but using the initial elements, Perl 6 will deduce that the generator is (+2)
This lazy list may return (if requested) the following elements (0, 2, 4, 6, 8, 10)
Lazy list built using a defined generator

my $lazylist = (0, { $_ + 3 } ... 12);
say $lazylist;

In this example, we defined explicitly a generator enclosed in { }
This lazy list may return (if requested) the following elements (0, 3, 6, 9, 12)


When using an explicit generator, the endpoint must be one of the values that the generator can return.
If we reproduce the above example with the endpoint being 10 instead of 12, it will not stop. The generator jumps over the endpoint.

Alternatively you can replace 0 …​ 10 with 0 …​^ * > 10
You can read it as: From 0 until the first value greater than 10 (excluding it)

# Classes and objects
class Human {
  has $.name;
  has $.age;
  has $.sex;
  has $.nationality;
}

my $john = Human.new(name => 'John', age => 23, sex => 'M', nationality => 'American');
say $john;

The class keyword is used to define a class.
The has keyword is used to define attributes of a class.
The .new() method is called a constructor. It creates the object as an instance of the class it has been called on.

In the above script, a new variable $john holds a reference to a new instance of "Human" defined by Human.new().
The arguments passed to the .new() method are used to set the attributes of the underlying object.

A class can be given lexical scope using my:

my class Human {

}



Encapsulation is facilitated in Perl 6 with the use of twigils.
Twigils are secondary sigils. They come between the sigil and the attribute name.
Two twigils are used in classes:

    ! is used to explicitly declare that the attribute is private.

    . is used to automatically generate an accessor for the attribute.

By default, all attributes are private but it is a good habit to always use the ! twigil.

Therefore, we should rewrite the above class as:

class Human {
  has $!name;
  has $!age;
  has $!sex;
  has $!nationality;
}

my $john = Human.new(name => 'John', age => 23, sex => 'M', nationality => 'American');
say $john;

Append to the script the following statement: say $john.age;
It will return this error: Method 'age' not found for invocant of class 'Human' because $!age is private and can only be used within the object. Trying to access it outside the object will return an error.

Now replace has $!age with has $.age and observe the result of say $john.age;


Named vs. Positional Parameters

In Perl 6, all classes inherit a default .new() constructor.
It can be used to create objects by providing it with arguments.
The default constructor can only be provided with named arguments.
In our example above, notice that the arguments supplied to .new() are defined by name:

    name ⇒ 'John'

    age ⇒ 23

What if I do not want to supply the name of each attribute each time I want to create an object?
Then I need to create another constructor that accepts positional arguments.

class Human {
  has $.name;
  has $.age;
  has $.sex;
  has $.nationality;
  # new constructor that overrides the default one.
  method new ($name,$age,$sex,$nationality) {
    self.bless(:$name,:$age,:$sex,:$nationality);
  }
}

my $john = Human.new('John',23,'M','American');
say $john;

Using Unicode
Let’s look at how we can output characters using Unicode

say "a";
say "\x0061";
say "\c[LATIN SMALL LETTER A]";

The above 3 lines showcase different ways of building a character:

    Writing the character directly (grapheme)

    Using \x and the code point

    Using \c and the code point name

Now lets output a smiley

say "☺";
say "\x263a";
say "\c[WHITE SMILING FACE]";

Another example combining two code points

say "á";
say "\x00e1";
say "\x0061\x0301";
say "\c[LATIN SMALL LETTER A WITH ACUTE]";

The letter á can be written:

    using its unique code point \x00e1

    or as a combination of the code points of a and acute \x0061\x0301

Some of the methods that can be used:

say "á".NFC;
say "á".NFD;
say "á".uniname;

Output

NFC:0x<00e1>
NFD:0x<0061 0301>
LATIN SMALL LETTER A WITH ACUTE

NFC returns the unique code point.
NFD decomposes the character and return the code point of each part.
uniname returns the code point name.
Unicode letters can be used as identifiers:

my $Δ = 1;
$Δ++;
say $Δ;

Unicode can be used to do math:

my $var = 2 + ⅒;
say $var;














Bibliography:
https://perl6advent.wordpress.com/
https://docs.perl6.org/language/classtut
http://perl6intro.com/
https://docs.perl6.org/type/Str
https://perl6.party/post/Perl-6-Seqs-Drugs-and-Rock-n-Roll
https://perl6.party/post/Perl-6-Seqs-Drugs-and-Rock-n-Roll--Part-2
https://perl6.party/post/Perl-6-Types--Made-for-Humans
