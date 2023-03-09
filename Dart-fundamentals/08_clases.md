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
