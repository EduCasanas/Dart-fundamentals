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
