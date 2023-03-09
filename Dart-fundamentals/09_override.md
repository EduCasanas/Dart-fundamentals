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
