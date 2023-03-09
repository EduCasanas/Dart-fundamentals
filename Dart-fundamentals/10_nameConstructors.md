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
