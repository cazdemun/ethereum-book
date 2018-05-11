# Capítulo 3: Clientes

## ¿Dónde está el código?

Básicamente, hemos resumido el whitepaper de Ethereum en el capítulo anterior. Pero haremos un pequeño recordatorio.

Como vimos, no solo con Ethereum, sino con Blockchain en general, una red de registros distribuidos debe ocuparse de las siguiente cosas:

* Blockchain (como estructura de datos), aquí están incluidas las cuentas y mensajes
* Lenguage de programación para Contratos Inteligentes y el EVM
* Funciones criptográficas
* Protocolos de consenso
* Redes p2p

La pregunta del millón es... ¿y quién programa todo esto?

Bueno, definitivamente no nosotros. Al programa que implementa todas las especificaciones descritas en el capítulo anterior se le llama _cliente_, y, mientras este programa pueda __hacer todo lo que se supone que debe hacer__, el lenguaje no importa. Es por esto que __existen muchas implementaciones del cliente de Ethereum__, ya sea oficiales o de terceros. El riesgo de las implementaciones de terceros es evidente, por eso en este capítulo solo hablaremos sobre las implementaciones oficiales:

* Geth, escrita en Go
* Eth, escrita en C++
* Pyethapp, escrita en Python

La implementación más popular, de lejos, es Geth. En este capítulo nos centraremos en cómo cómo Geth maneja todos los aspectos de la red Ethereum a través de su CLI, o Command Line Interface. Esto, para los que no conozcan, quiere decir que el cliente solo puede ser manejado a través de líneas de comandos, no hay ventanas ni interfaces gráficas.

¿Primitivo? Tal vez, en el CLI ni siquiera se usa el mouse. Pero cuando te acostumbras, luego de un tiempo, te das cuenta que estás en control total del programa, un sentimiento que ninguna GUI es capaz de ofrecerte, a menos que la construyas tú mismo.

Por cierto, si todavía tienes problemas para diferenciar entre implementación y especificación, míralo de esta forma: Necesito un programa que sume dos números enteros. Puedes escribir este programa de mil formas distintas y en mil lenguajes distintos, pero mientras haga lo especificado, cuenta como implementación.

# Referencias:

