# Solidity

Solidity es el lenguaje de programación más popular para programar contratos inteligentes en Ethereum.
Al parecer sigue un poco los lineamientos de EC6, aunque tiende a desviarse un poco.

Solidity es un lenguaje estático. Eso quiere decir que, al declarar una variable, tiene que declararse su tipo.

Un contrato es un objeto, por lo que es declarado como tal. 
En ese sentido es parecido a Java, aunque este uso sea mucho más intuitivo.
Se puede interpretar al código como la clase y al contrato ya subido al EVM como la instancia del objeto.
Siento que esto es estirar el concepto de OOP. Sobretodo porque, en teoría, solo subirías una vez el contrato a la red.
A menos que se refiera a que, cada vez que la cuenta contrato es activada, se crea una instancia del contrato y se ejecuta.
Esto tendría más sentido.

Los contratos pueden invocarse (llamar desde otro archivo fuente), crearse (declaración estándar) o heredarse.

## Diseño de un contrato

El diseño de un contrato es relativamente sencillo. 

![alt text](./soliditylayout.PNG "Layout")

He aquí un ejemplo con código.

![alt text](./soliditylayout.PNG "Layout")

A continuación una explicación de cada uno de los elementos.

### Versión del compilador

### Nombre del contrato

### Storage

Cuando hablábamos de los elementos de las cuentas contratos, se decía que esta tenía, además de una dirección y un saldo de ether, un contrato y un almacenamiento, o Storage.
Resulta que este Storage puede ser especificado dentro de los contratos inteligentes. 
En este caso, el storage es solo un entero, pero no está límitado a solo un tipo de dato, el Storage puede ser los números y tipos de variables que se desee.
Puede considerarse a estas variables como las que se quiere que perduren más allá de una ejecución.
Usualmente, para que esto suceda en un lenguaje de programación tradicional tenemos que lidiar con el sistema de archivos o con bases de datos.
No aquí, hasta donde tengo entendido.
Las variables declaradas de forma estándar fuera de funciones son automáticamente consideradas State o Storage Variables.
Esta es una forma conveniente pero riesgosa, ya que las variables globales cuestan gas, puesto que están escribiéndose en la blockchain.

*GEth tiene una base datos, LevelDB. Leí que ahí era donde se almacenaban todas las State Variables (Variables de Estado).

### Eventos

### Funciones

#### Constructores

## Importar, heredar y declarar contratos

Múltiples contratos pueden ser declarados en un solo archivo. El último contrato es el que es 'deployed' en la blockchain.

```
pragma solidity ^0.4.20;

contract Account {
    // Represents an account
}

contract CreditAccount is Account {
    // Is type of an account
}
```

La importación de contratos puede ser a través de archivos locales, direcciones HTTP e incluso GitHub.
Pero este grado de libertad depende del compilador.

```
pragma solidity ^0.4.20;

import "./Account.sol";

contract CreditAccount is Account {
    // Is type of an account
}
```