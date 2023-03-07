# Tipos de variables

Se recomienda usar final, al menos que la variable se vaya a cambiar
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

## Tipo de variable `dynamic`

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

>Hay que ser cuidadosos con el uso de dynamic ya que pierde cualquier restriccion, incluido el null safety, por ejemplo si hacemos lo siguiente Dart no arroja error.

```Dart
errorMessage = null;
errorMessage +=1;
```
