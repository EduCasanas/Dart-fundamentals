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
Lo anterior ahora con parametros opcionales con nombre en el que especificamos que seran requerridos obligatoriamente.

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero(name: 'Logan', power: 'Regeneracion');

  print(wolverine);
  print(wolverine.name);
  print(wolverine.power);
}

class Hero {
  //atributos
  String name;
  String power;

  Hero({required this.name, required this.power});
}
```

Si queremos que el `poder` sea opcional y ya no requerrido, debemos asignarle un valor por defecto, para que muestre cuando no se envia ningun valor para la variable `power`.

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero(name: 'Logan', power: 'Regeneracion');

  print(wolverine);
  print(wolverine.name);
  print(wolverine.power);
}

class Hero {
  //atributos
  String name;
  String power;

  Hero({required this.name, this.power = 'Sin poder'});
}
```

# Override

Sirve para sobreescribir el comportamiento de una funcion, es decir decirle que debe hacer cierta funcion.

```Dart
void main() {
  //instanciamos el nuevo objeto
  final Hero wolverine = Hero(name: 'Logan', power: 'Regeneracion');

  print(wolverine); //Logan - Regeneracion
  print(wolverine.name); //Logan
  print(wolverine.power); //Regeneracion
}

class Hero {
  //atributos
  String name;
  String power;

  Hero({required this.name, this.power = 'Sin poder'});

  @override
  String toString() {
    return '$name - $power';
  }
}
```
# Name Constructors

```Dart
void main() {
  final Hero ironman = Hero(name: 'Tony Stark', power: 'Money', isAlive: false);

  print(ironman);
  //Tony Stark, Money, is alive: No!
}

class Hero {
  String name;
  String power;
  bool isAlive;

  Hero({required this.name, required this.power, required this.isAlive});

  @override
  String toString() {
    return '$name, $power, is alive: ${isAlive ? 'Yes!' : 'No!'}';
  }
}
```

Es comun que se cree una instancia de una clase que viene de una peticion HTTP,etc.

```Dart
void main() {
  final Map<String, dynamic> rawJson = {
    'name': 'Tony Stark',
    'power': 'Money',
    'isAlive': true
  };

  final Hero ironman =
      Hero(name: 'Tony Stark', power: 'Money', isAlive: rawJson['isAlive']);
  //rawJson al ser de tipo dynamic, hay una posibilidad de que sea nulo, ya
  //sea por error se escribio mal al llamar al rawJson, rawJson['isAlive2'] o se
  //coloco un espacio rawJson['isAlive '], esto va hacer que el valor ya no
  //exista y por ende dara error o se caera la aplicacion.

  print(ironman);
}

class Hero {
  String name;
  String power;
  bool isAlive;

  Hero({required this.name, required this.power, required this.isAlive});

  @override
  String toString() {
    return '$name, $power, is alive: ${isAlive ? 'Yes!' : 'No!'}';
  }
}
```

Para evitar que de errores lo anterior, hacemos lo siguiente: en esta linea `isAlive: rawJson['isAlive2'] ?? false, //aqui evaluamos si es nulo,` y por lo tanto imprime lo siguiente: `Tony Stark, Money, is alive: No!` de esta manera evitamos los valores `nulos`, porque al no encontrar el valor `rawJson['isAlive']` porque colocamos mal `rawJson['isAlive2']` en el `Map rawJson` ya no da `nulo` si no que automaticamente hemos colocado para que asigne `false`.

```Dart
void main() {
  final Map<String, dynamic> rawJson = {
    'name': 'Tony Stark',
    'power': 'Money',
    'isAlive': true
  };

  final Hero ironman = Hero(
    name: 'Tony Stark',
    power: 'Money',
    isAlive: rawJson['isAlive2'] ?? false, //aqui evaluamos si es nulo,
    //colocara false
  );

  print(ironman);
}

class Hero {
  String name;
  String power;
  bool isAlive;

  Hero({required this.name, required this.power, required this.isAlive});

  @override
  String toString() {
    return '$name, $power, is alive: ${isAlive ? 'Yes!' : 'No!'}';
  }
}
```

El bloque anterior es valido, sin embargo hay otra manera creando un `constructor con nombre`, el cual reciba el objeto `Map rawJson` y tenga toda la validacion para crear ese objeto.

```Dart
void main() {
  final Map<String, dynamic> rawJson = {
    'name': 'Tony Stark',
    'power': 'Money',
    'isAlive': true
  };

  final Hero ironman = Hero.fromJson(rawJson);

  print(ironman);
  //Tony Stark, Money, is alive: Yes!
}

class Hero {
  String name;
  String power;
  bool isAlive;

  Hero({required this.name, required this.power, required this.isAlive});

  Hero.fromJson(Map<String, dynamic> json)
      : name = json['name'] ?? 'No name found',
        power = json['power'] ?? 'No power found',
        isAlive = json['isAlive'] ?? 'No isAlive found';

  @override
  String toString() {
    return '$name, $power, is alive: ${isAlive ? 'Yes!' : 'No!'}';
  }
}
```

>Cuando se lea de un json, hay que acostumbrarse a hacer las validaciones para manejar los `nulos`.

# Getters and Setters

```Dart
void main() {
  final mySquare = Square(side: 10);
  
    
  mySquare.side = -5; //llamando al setter
  //Setting new value: -5.0
  //Unhandled exception:
  //value must be >0

  print('Area: ${mySquare.area}'); //llamando al getter
}

class Square {
  //variable privada
  double _side;

  Square({required double side}) : _side = side;

  //Getter
  double get area {
    return _side * _side;
  }

  //Setter
  set side(double value) {
    print('Setting new value: $value');
    if (value < 0) throw 'value must be >0';
    _side = value;
  }

  double calculateArea() {
    return _side * _side;
  }
}
```

Como vimos los `Setters` me permiten de cierta forma controlar como quiero establecer los valores, es decir si no cumplen ciertas condiciones no los establezco y lanzo un error. Pero si agrego `-10` ya no lanza el error.

```Dart
final mySquare = Square(side: -10);
```
# Aserciones

Agregamos el siguiente codigo `assert` para tratar que no se ingrese el `final mySquare = Square(side: -10);` como un numero negativo.

```Dart
Square({required double side})
      : assert(side >= 0),
        _side = side;
```

Intentamos probar el siguiente codigo en `visual studio code` pero no lanza el `assert` y calcula el area sin ningun problema, pero cuando ejecutamos el mismo codigo en `Dart Pad` si arroja el error: `Uncaught Error: Assertion failed`.

```Dart
void main() {
  final mySquare = Square(side: -10);

  //mySquare.side = -5;

  print('Area: ${mySquare.area}');
}

class Square {
  //variable privada
  double _side;

  //constructor
  Square({required double side})
      : assert(side >= 0),
        _side = side;

  //Getter
  double get area {
    return _side * _side;
  }

  //Setter
  set side(double value) {
    print('Setting new value: $value');
    if (value < 0) throw 'value must be >0';
    _side = value;
  }

  double calculateArea() {
    return _side * _side;
  }
}
```

El `assert` que colocamos estaria bien si solo fuera poco codigo, pero en la realidad, siempre se colocaran mas `asserts` y para eso hay que especificar exactamente la clase de error, porque podrian saltar varios `asserts` y no saber cual de ellos es.

Agregamos esto:

```Dart
      : assert(side >= 0, 'side must be >= 0'),
```

Nos queda asi:

```Dart
void main() {
  final mySquare = Square(side: -10);

  //mySquare.side = -5;

  print('Area: ${mySquare.area}');
}

class Square {
  //variable privada
  double _side;

  //constructor
  Square({required double side})
      : assert(side >= 0, 'side must be >= 0'),
        _side = side;

  //Getter
  double get area {
    return _side * _side;
  }

  //Setter
  set side(double value) {
    print('Setting new value: $value');
    if (value < 0) throw 'value must be >0';
    _side = value;
  }

  double calculateArea() {
    return _side * _side;
  }
}
```

Ahora lanza el `assert` asi: `Uncaught Error: Assertion failed: "side must be >= 0"`, de esta manera es mas especifico el tipo de error que tenemos en el codigo.

# Clases abstractas y Enums

Las `clases abstractas` se puede ver como un molde que va a ayudar a crear otros moldes. Estas no pueden instanciar nuevos objetos. Los `enums` sirven para delimitar el tipo de opciones disponibles.

```Dart
void main() {}

//cuando quiere delimitar el tipo de opciones
enum PlantType { nuclear, wind, water } //ojo los enums no terminan con ;

//clase abstracta
abstract class EnergyPlant {
  double energyLeft;
  String type; //nuclear, wind, water

  //constructor
  EnergyPlant({required this.energyLeft, required this.type});

  //metodo
  void consumeEnergy(double amount);
}
```

>Si existieran mas metodos comunes a otras clases, se los puede definir en la clase abstracta, pero no se deben `implementar`, con implementacion se refiere a que no se deben realizar calculos aun, solo definir los metodos como lo hicimos con `consumeEnergy`, ya que estos metodos seran sobreescritos con un `@override` en la clase que queremos implementar la clase abstracta.

# Extends y Enums

El `extends` hace que una clase herede de otra clase `Padre` todos los atributos, metodos,etc. El `enum` permite delimitar las opciones que queremos que sean usadas.

```Dart
void main() {
  final windPlant = WindPlant(initialEnergy: 9);

  print('wind: ${chargePhone(windPlant)}');
  //Unhandled exception:
  //Exception: Not enough energy
}

double chargePhone(EnergyPlant plant) {
  if (plant.energyLeft < 10) {
    throw Exception('Not enough energy');
  }
  return plant.energyLeft - 10;
}

//cuando quiere delimitar el tipo de opciones
enum PlantType { nuclear, wind, water } //ojo los enums no terminan con ;

//clase abstracta
abstract class EnergyPlant {
  double energyLeft;
  PlantType type; //nuclear, wind, water

  //constructor
  EnergyPlant({required this.energyLeft, required this.type});

  //metodo
  void consumeEnergy(double amount);
}

//extends o heredar de otra clase
class WindPlant extends EnergyPlant {
  //constructor
  WindPlant({required double initialEnergy})
      : super(energyLeft: initialEnergy, type: PlantType.wind);

  //el @override sobreescribe el metodo que esta en la clase abstracta
  @override
  void consumeEnergy(double amount) {
    energyLeft -= amount;
  }
}
```

Implementamos esta funcion `chargePhone` que cuando se instancia el objeto `final windPlant = WindPlant(initialEnergy: 9);` lanza la exepcion. La idea de la creacion de la funcion `chargePhone` es que aplique el principio de `inversion de dependencias`, es decir puedo crear otro tipo de planta y la funcion  `chargePhone` no se va a ver afectada.

```Dart
double chargePhone(EnergyPlant plant) {
  if (plant.energyLeft < 10) {
    throw Exception('Not enough energy');
  }
  return plant.energyLeft - 10;
}
```
# Implements

El `implements` nos ayuda explicitamente a colocar cada uno de los `overrides`.
El `extendes` y `implements` sirven para la herencia, pero en el `implements` lo uso cuando quiero implementar algun metodo especifico mientras que en la herencia, hereda todo lo que la clase padre tiene, y no siempre voy a querer heredar todo, porque habran metodos que no quiero utilizar.

```Dart
void main() {
  final windPlant = WindPlant(initialEnergy: 100);
  final nuclearPlant = NuclearPlant(energyLeft: 1000);

  print('wind: ${chargePhone(windPlant)}');
  print('nuclear: ${chargePhone(nuclearPlant)}');
}

double chargePhone(EnergyPlant plant) {
  if (plant.energyLeft < 10) {
    throw Exception('Not enough energy');
  }
  return plant.energyLeft - 10;
}

enum PlantType { nuclear, wind, water }

abstract class EnergyPlant {
  double energyLeft;
  final PlantType type; //nuclear, wind, water

  EnergyPlant({required this.energyLeft, required this.type});

  void consumeEnergy(double amount);
}

class WindPlant extends EnergyPlant {
  WindPlant({required double initialEnergy})
      : super(energyLeft: initialEnergy, type: PlantType.wind);

  @override
  void consumeEnergy(double amount) {
    energyLeft -= amount;
  }
}

class NuclearPlant implements EnergyPlant {
  @override
  double energyLeft;

  @override
  final PlantType type = PlantType.nuclear;

  NuclearPlant({required this.energyLeft});

  @override
  void consumeEnergy(double amount) {
    energyLeft -= amount * 0.5;
  }
}
```

# Mixins

Los `mixins` se escriben con la palabra reservada `with` y sirven para darle una mayor especialidad a la clase, por ejemplo: `class Murcielago extends Mamifero with Volador, Caminante {}` aqui la clase Murcielago hereda de la clase Mamifero pero con el `mixin` especializamos al murcielago para que pueda volar y caminar.

```Dart
abstract class Animal {}

abstract class Mamifero extends Animal {}

abstract class Ave extends Animal {}

abstract class Pez extends Animal {}

abstract class Volador {
  void volar() => print('Estoy volando');
}

abstract class Caminante {
  void caminar() => print('Estoy caminando');
}

abstract class Nadador {
  void nadar() => print('Estoy nadando');
}

class Delfin extends Mamifero with Nadador {}

class Murcielago extends Mamifero with Volador, Caminante {}

class Gato extends Mamifero with Caminante {}

class Paloma extends Ave with Volador, Caminante {}

class Pato extends Ave with Caminante, Volador, Nadador {}

class Tiburon extends Pez with Nadador {}

class PezVolador extends Pez with Nadador, Volador {}

void main() {
  final flipper = Delfin();
  flipper.nadar();

  final batman = Murcielago();
  batman.caminar();
  batman.volar();

  final namor = Pato();
  namor.caminar();
  namor.nadar();
  namor.volar();
}
```
# Futures

El `Future` es una promesa de que se recibira un valor, la promesa puede fallar, y hay que manejar la excepcion.

```Dart
void main() {
  print('Inicio del programa');

  httpGet('https://educa.com/cursos').then((value) {
    print(value);
  }).catchError((err) {
    print('Error: $err');
  });

  print('Fin del programa');
}

Future<String> httpGet(String url) {
  return Future.delayed(const Duration(seconds: 1), () {
    throw 'Error en la peticion http';

    //return 'Respuesta de la peticion http';
  });
}
```
# Async-await try-catch

`Async-await` se usan en conjunto con los `Futures`, y sirve para especificar a `Dart` que tiene que esperar la promesa de respuesta primero antes de continuar ejecutando el resto de codigo. A diferencia de solo usar el `Future` en el que el codigo se ejecutaba linea por linea sin restriccion alguna mientras tanto esperaba la promesa de respuesta.

```Dart
void main() async {
  print('Inicio del programa');

  try {
    final value = await httpGet('https://educa.com/cursos');
    print(value);
  } catch (err) {
    print('Tenemos un error: $err');
  }

  print('Fin del programa');
}

Future<String> httpGet(String url) async {
  await Future.delayed(const Duration(seconds: 2));

  throw 'Error en la peticion';

  //return 'Tenemos un valor de la peticion';
}
```
# Try, on, catch, finally

```Dart
void main() async {
  print('Inicio del programa');

  try {
    final value = await httpGet('https://educa.com/cursos');
    print('Exito: $value');
  } on Exception catch (err) {
    print('Tenemos una excepcion: $err');
  } catch (err) {
    print('OOPs! algo terrible paso: $err');
  } finally {
    print('Fin del try and catch');
  }

  print('Fin del programa');
}

Future<String> httpGet(String url) async {
  await Future.delayed(const Duration(seconds: 3));

  throw Exception('No hay parametros en el URL');

  //throw 'Error en la peticion';
  //para un error no controlado imprimta OOPs!..

  //return 'Tenemos un valor de la peticion';
  //cuando todo sale bien, imprimira Exito: Tenemos un valor...
}
```
# Streams

Los `streams` son como un flujo de datos que van a estar pasando, si ejecutamos el codigo de abajo, no pasara nada, porque los `streams` necesita de `listeners`.`print('desde periodic $value');` deberia haber impreso esto en consola pero no paso nada. Haciendo una analogia, es como estar en un auditorio a punto de dar una charla pero si no va nadie para que empezar la charla.

```Dart
void main() {
  emitNumbers();
}

Stream<int> emitNumbers() {
  return Stream.periodic(Duration(seconds: 1), (value) {
    print('desde periodic $value');
    return value;
  });
}
```

Ahora agregamos el `listen()` y ademas agregamos el `take()`, el `take` le dice al `stream` ejecuta 5 veces y luego cierra el `stream`.

```Dart
void main() {
  emitNumbers().listen((value) {
    print('Stream value: $value');
  });
}

Stream<int> emitNumbers() {
  return Stream.periodic(Duration(seconds: 1), (value) {
    //print('desde periodic $value');
    return value;
  }).take(5);
}
```

El codigo de arriba imprimira esto:

```md
Stream value: 0
Stream value: 1
Stream value: 2
Stream value: 3
Stream value: 4
```
# Async*

```Dart
void main() {
  emitNumbers().listen((int value) {
    print('Stream: $value');
  });
}

Stream<int> emitNumbers() async* {
  final valuesToEmit = [1, 2, 3, 4, 5];

  for (int i in valuesToEmit) {
    await Future.delayed(const Duration(seconds: 3));
    yield i;
  }
}
```
