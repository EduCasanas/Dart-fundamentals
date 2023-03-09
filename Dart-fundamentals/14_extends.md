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
