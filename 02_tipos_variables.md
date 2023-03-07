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
