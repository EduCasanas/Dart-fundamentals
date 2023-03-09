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
