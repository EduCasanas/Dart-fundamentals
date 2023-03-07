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
