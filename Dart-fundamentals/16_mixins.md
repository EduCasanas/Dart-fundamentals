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
