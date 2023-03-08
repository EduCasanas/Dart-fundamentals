# Dart-fundamentals

## Introduccion

Siempre se recomienda que toda variable o funcion se especifique su tipo de dato, en este caso la funcion principal que ejecuta nuestro programa se llama `main`, la palabra `void` indica que es una funcion que no retorna nada, es decir indicamos a Dart que no espere ningun valor de la funcion.

## Variable tipo `var`

Tipo de variable que va a ser inferido.

```Dart
void main() {
  var myName = 'Edu'; 
  //runtimeType imprime el tipo de dato de myName
  print(myName.runtimeType);//String
  print(myName);
}
```

Como vimos myName se volvio tipo `String` por lo tanto si queremos modificar su tipo ya NO se puede. Pero si podemos modificar su valor por otro del mismo tipo String.

```Dart
void main() {
  var myName = 'Edu';
  print(myName);
  myName = 123;//da error, un tipo int no puede ser asignado a un tipo String. Si en lugar de 123, colocamos '123' ya no daria error porque reconoce como un String.
  print(name);
}
```

## Variable tipo `final`

```Dart
void main() {
  final myName = 'Edu';
  print(myName);
}   
```

Si ahora intento cambiar el valor por uno del mismo tipo, me da error:

```Dart
void main() {
  final myName = 'Edu';
  print(myName);
  myName = 'jorge';//error myName solo puede asignarse una vez
  print(myName);
}
```

## Variable tipo `late final`

Asignacion tardia

```Dart
void main() {
  late final myName;
  myName = 'jorge';
  print(myName);
}
```

>Es util cuando en ese momento no se dispone del dato, pero se sabe que luego se asignara su valor.

## Variable tipo `const`

```Dart
void main() {
  const myName = 'edu';
  print(myName);
}
```

`const` sirve para crear una constante en tiempo de construccion. Si yo se que la variable nunca va a cambiar de valor asigno como constante. Esto ayuda a la velocidad de dart y flutter.

`final` se asigna en tiempo de ejecucion, lo utilizo cuando en un determinado tiempo yo necesito calcular el valor de la variable usaria `final` en lugar de `const`.

## Interpolacion

Cuando se quiere solamente leer la variable dentro de un string:

```Dart
  print('Hola $myName');
```  

Cuando se requierre hacer algun calculo, o aplicar una funcion:

```Dart
  print('Hola ${myName.toUpperCase()}');
  print('Hola ${1 + 1}');
```
# Tipos de variables

Se recomienda usar `final`, al menos que la variable se vaya a cambiar
despues, alli si se usaria `String pokemon = 'Ditto';`

```Dart
void main() {
  final String pokemon = 'Ditto';
  final int hp = 100;
  final bool isAlive = true;
  final List<String> abilities = ['impostor'];
  final sprites = <String>['ditto/front.png', 'ditto/back.png'];

//permite imprimir multilineas
  print("""
$pokemon
$hp
$isAlive
$abilities
$sprites
""");
}
```

Formas de escribir las listas:

```Dart
final abilities = ['impostor'];
final abilities = <String>['impostor'];
final List<String> abilities = ['impostor'];

```
# Tipo de variable `dynamic`

Dynamic se recomienda usarlo poco, es decir en casos especificos ya que dynamic puede ser cualquier tipo de variable incluso nula.

>`dynamic` por defecto acepta nulos y no es necesario colocarle el signo ?

```Dart
dynamic errorMessage = 'Hola';
//pese a que se asigna un String como valor, la variable se mantiene del tipo dynamic y no cambia a String.
errorMessage = true;
errorMessage = [1,2,3,4,5,6];//lista
errorMessage = {1,2,3,4,5,6};//set de datos
errorMessage = ()=> true;//funcion que regresa un booleano
errorMessage = null;
```

>Hay que ser cuidadosos con el uso de dynamic ya que pierde cualquier restriccion, incluido el null safety, por ejemplo si hacemos lo siguiente Dart deberia arrojar error.

```Dart
errorMessage = null;
errorMessage +=1;
```
# Maps

Los `maps` se componen de `clave` y `valor` y se colocan con llaves {}

```Dart
void main() {
  final pokemon = {
    'name' : 'Ditto',
    'hp' : 100,
  };
}
```

Es comun encontrar un `map` asi:

```Dart
final Map<String, dynamic> pokemon{
    'clave' : 'valor'
}
```

>donde <String, dynamic> `String` es el tipo de variable de la clave y `dynamic` es el tipo de variable del valor.

Pero tambien hay otros tipos de `maps` con clave `entero` y valor `string`.

```Dart
final pokemons = {
    1 : 'ABC',
    2 : 'XYZ',
    3 : '123',
    150 : 'AGJH'
};
```

Aqui vemos un `map` que contiene otros tipos de variables e incluso un `map` dentro de otro `map`.

```Dart
void main() {
  final pokemon = {
    'name' : 'Ditto',
    'hp' : 100,
    'isAlive' : true,
    'abilities' : <String>['impostor'],
    'sprites' : {
        1 : 'ditto/front.png',
        2 : 'ditto/back.png'
    }
  };
}
```

>podemos agregar el `map` tambien de la siguiente forma, pero la forma que se establecio arriba, permite que dart infiera el tipo, ya vimos que dart es bueno infiriendo los tipos de `clave` y `valor`.

```Dart
'sprites' : Map<int, String>{
        1 : 'ditto/front.png',
        2 : 'ditto/back.png'
    }
```

Para imprimir el valor de la variable name que esta dentro del `map`, hariamos lo siguiente:

```Dart
print(pokemon);//esto imprime todo el map
print('Name: ${pokemon['name']}');//esto imprime: Name: Ditto
```

Ahora si queremos acceder a los valores del `map sprites` lo haremos de la siguiente manera:

```Dart
print('Back: ${pokemon['sprites'][2]}');
print('Front: ${pokemon['sprites'][1]}');
```
# Listas, iterables y sets

## Listas

Las `listas` se representan con [ ]

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  print('List original $numbers');
}
```

## Metodos de las listas e iterables

**Longitud de una lista: `length`**

```Dart
print('List original ${numbers.length}');//13
```

**Indice de una lista: `first`**

```Dart
print('Index 0: ${numbers[0]}');//Index 0: 1
//tambien se puede obtener el primer elemento de la lista asi:
print('Index 0: ${numbers.first}');
```

**Ultimo elemento de la lista: `last`**

```Dart
print('Index 0: ${numbers.last}');
```

**Invertir listado: `reversed`**

```Dart
print('Reversed: ${numbers.reversed}');
//Lista original: [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10]
//Reversed: (10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1)
```

>Tomar en cuenta que ahora cambio la lista original paso de tener `[ ]` a `( )`, ahora el listado paso a ser un `iterable`.

Si ahora se quiere recuperar la lista con los [ ].

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final reversedNumbers = numbers.reversed;
  //(10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1)
  print('List: ${reversedNumbers.toList()}');
  //[10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1]
}
```

## Sets

Los `sets` se colocan entre llaves { }

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final reversedNumbers = numbers.reversed;
  print('List: ${reversedNumbers.toList()}');
  //[10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1]
  print('Set: ${reversedNumbers.toSet()}');
  //Set: {10, 9, 8, 7, 6, 5, 4, 3, 2, 1}
}
```

>Notar que los `sets` son un conjunto de elementos unicos, como podemos ver el listado original contenia elementos repetidos,ahora en el `set` solo aparecen valores unicos sin repetirse.

Si quisiera quitar elementos repetidos de una lista, manteniendo su tipo de variable Lista, haria lo siguiente:

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  print('List original no repetion: ${numbers.toSet().toList()}');
  //List original no repetion: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
```

## Mas metodos de los Iterables `where`

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final numbersGreaterThan5 = numbers.where((int num) {
    return num > 5;
  });
  print('>5 iterable: $numbersGreaterThan5');
  //>5 iterable: (6, 7, 8, 9, 9, 10)
}
```

>Lo anterior me dio un iterable, pero tiene elementos repetidos, ahora lo quiero sin esos elementos repetidos, aplico un `set`.

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final numbersGreaterThan5 = numbers.where((int num) {
    return num > 5;
  });
  print('>5 iterable: $numbersGreaterThan5');
  //>5 iterable: (6, 7, 8, 9, 9, 10)
  print('>5 set: ${numbersGreaterThan5.toSet()}');
  //>5 set: {6, 7, 8, 9, 10}
}
```
# Funciones

Creamos la funcion `greetEveryone` que luego es llamada en la funcion principal `main`.

```Dart
void main() {
  greetEveryone();
  //esta funcion no imprime nada, solo se ejecuta
}

greetEveryone() {
  return 'Hello everyone';
}
```

>Siempre es recomendable especificar el tipo de funcion y en general todas las variables.

```Dart
void main() {
  print(greetEveryone());
  //Hello everyone
}

String greetEveryone() {
  return 'Hello everyone';
}
```

## Lambda Functions o funciones de flecha

```Dart
void main() {
  print(greetEveryone());
  //Hello everyone
}

String greetEveryone()=>'Hello everyone';
```

>OJO: las funciones flecha NO permiten elaborar mas cosas entre llaves, como a continuacion:

```Dart
String greetEveryone()=>{
  return 'Hello everyone';
};
```

## Funcion que recibe 2 parametros

```Dart
void main() {
  print('Suma: ${addTwoNumbers(10, 20)}');
  //Suma: 30
  print('Suma: ${addTwoNumbers2(20, 20)}');
  //Suma: 40
}

//funcion que recibe 2 argumentos
int addTwoNumbers(int a, int b) {
  return a + b;
}

//el mismo calculo anterior usando funcion flecha
int addTwoNumbers2(int a, int b) => a + b;
```

## Funciones con parametros opcionales

```Dart
void main() {
  print('Suma: ${addTwoNumbersOptional(20, 20)}');
}

int addTwoNumbersOptional(int a, [int? b]) {
  b ??= 0; //esto significa que si b tiene valor que lo deje, pero
  //si no tiene que asigne como 0.
  return a + b;
}
```

>Esto `b = b ?? 0;` es lo mismo que escribir asi `b ??= 0;` y esto `b = b + 1;` es lo mismo a esto `b++;`.

Lo anterior tambien podemos definir los parametros opcionales asi:

```Dart
void main() {
  print('Suma: ${addTwoNumbersOptional(20, 20)}');
}
//asi es mas recomendable utilizar ya que es mas legible
int addTwoNumbersOptional(int a, [int b = 0]) {
  return a + b;
}
```
# Parametros posicionales

>`Parametros posicionales` quiere decir que yo al pasarle a la funcion parametros, estos seran asignados conforme su posicion, por ejemplo, si yo le paso (20,10), dart asignara 20 a la primera variable a, y el otro valor de 10 a la variable b.

```Dart
void main() {
  print('Suma: ${addTwoNumbersOptional(20, 20)}');
}

int addTwoNumbersOptional(int a, [int b = 0]) {
  return a + b;
}
```

## Parametros NO posicionales

Es decir le puedo pasar los valores especificos a cada variable sin importar la posicion.
Las variables opcionales NO posicionales se colocan entre llaves { }, esto me arroja un `error` en las variables ya que Dart dice que pueden ser nulas, la solucion para permitir que sean nulas seria colocar el signo de pregunta `String? name`, pero no quiero trabajar con variables nulas.

```Dart
String greetPearson({String name, String message}) {
  return 'Hola, edu';
}
```

Por ello se hace lo siguiente:
1.-En la variable `message` se agrega un mensaje `'Hola'` este valor es usado por defecto en caso de no recibir ningun valor.
2.-`required` hace que esa variable a pesar de estar dentro de las llaves de opcionales, pida obligatoriamente el valor de `name`.

```Dart
void main() {
  print(greetPearson(name: 'Jorge'));
  //Hola, Jorge
}

String greetPearson({required String name, String message = 'Hola'}) {
  return '$message, $name';
}
```

Como vimos anteriormente, solo le pasamos el valor requerrido `name` y no dio ningun error, ahora le pasaremos el parametro opcional `message`:

```Dart
void main() {
  print(greetPearson(name: 'Jorge', message: 'Hi,'));
  //Hi, Jorge
}

String greetPearson({required String name, String message = 'Hola,'}) {
  return '$message $name';
}
```
# Clases

Hemos creado la clase, los atributos, el constructor, la instancia pero nos da un error en esta linea `Hero(String pName, String pPower) {`, dice que la variable `name` debe ser inizializada.

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero('Logan', 'Regeneracion');

  print(wolverine);
}

class Hero {
  //atributos
  String name;
  String power;

  //constructor
  Hero(String pName, String pPower) {
    name = pName; //this.name = pName | this se suele omitir
    power = pPower; //this.power = pPower | this se suele omitir
  }
}
```

Para solucionarlo, hacemos lo siguiente:

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero('Logan', 'Regeneracion');

  print(wolverine);
  //Instance of 'Hero'
  print(wolverine);
  //Logan
  print(wolverine);
  //Regeneracion
}

class Hero {
  //atributos
  String name;
  String power;

  //de esta forma al momento de hacer la instancia, tambien va a asignar
  //las variables name y power.
  Hero(String pName, String pPower)
      : name = pName,
        power = pPower;
}
```

Habra casos en que se debe hacer el constructor como arriba y habra otros casos que en la mayoria se lo hace asi:

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero('Logan', 'Regeneracion');

  print(wolverine);
  print(wolverine.name);
  print(wolverine.power);
}

class Hero {
  //atributos
  String name;
  String power;

  Hero(this.name, this.power);
}
```
