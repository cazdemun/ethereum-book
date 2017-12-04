# Ethereum

_Nota: A partir de aquí las explicaciones que doy son mayormente mi entendimiento del tema, así que podría estar equivocado._

Ethereum es la red pionera en implementar los contratos inteligentes. 
También usa una criptomoneda, el ether, aunque sus creadores prefieren llamarla criptocombustible. 
Esta redefinición tendrá sentido más adelante.

Existen dos elementos principales en la blockchain de Ethereum: las cuentas y los mensajes. A partir de estos dos conceptos se desprenden los demás que veremos en este capítulo.

## Cuentas

Todas las cuentas en ethereum poseen una dirección y un saldo de ether.
Existen dos tipos de cuentas, las que son propiedad de una persona o entidad, y las cuentas contratos.
Las cuentas contrato poseen, además, un 'almacén', que es simplemente un arreglo donde se almacenan datos, y el código del contrato inteligente.
Este código no es almacenado en ningún lenguaje de alto nivel, sino en bytecode, pero eso se explicará luego.

Los dos tipos de cuenta poseen una cierta dinámica: 
* Los cuentas de usuarios pueden enviar mensajes a otras cuentas de usuarios y a las cuentas contratos.
* Estas cuentas contrato activan automáticamente su código al recibir un mensaje, independientemente de su contenido.
La razón se verá en la siguiente sección, pero este sistema le da bastante importancia al orden de la información en el mensaje.
* Las cuentas contratos pueden enviar mensajes a otras cuentas solo si esa funcionalidad está especificada en el código.
Esto permite, por lo tanto, que múltiples cuentas contrato puedan comunicarse entre sí, aunque hay un límite debido al gas.

Se puede interpretar, entonces, que las cuentas contratos son programas que se activan al recibir un mensaje.
El whitepaper de Ethereum prefiere el término 'agentes autónomos'.
Supongo que es porque la intención final es que estos contratos puedan comunicarse entre sí sin intervención alguna, creando un ecosistema que no necesite de supervisión constante, eso si es programado bien.

El conjunto de todas las cuentas en Ethereum es llamado Estado. 
Este Estado puede cambiar, y debería, y ese es el propósito de los mensajes.

## Mensajes

No es posible hablar de cuentas sin mencionar a los mensajes, pero en esta sección se intentará profundizar más en la estructura de los mensajes.
También llamados transacciones, los mensajes pueden considerarse una función que transforma el último estado registrado en la blockchain.

Por definición de Blockchain (todos los nodos guardan una copia de la estructura de datos), el código de cada contrato es ejecutado en cada máquina de la red.
Si bien parece ineficiente, mi mejor explicación es que ese es el precio a pagar por la inmutabilidad.

_Mencionar el orden del mensaje y como lo interpreta la EVM, o tal vez eso es mejor para la sección de EVM_

## Blockchain

Mencioné en la sección anterior que los mensajes transforman el último estado registrado.
Por lo que veo, cada bloque tiene una copia de un Estado.
Este Estado es el resultado de...
Es probable que una cuenta de usuario con 0 ether sea borrada del Estado, pero las cuentas contratos deberían seguir presentes.

_Los bloques en Ethereum están formados por una lista de cuentas, las cuales son modificados a través de mensajes, o transacciones._
_Por lo que tengo entendido, cada bloque de Ethereum tiene almacenada la totalidad de los contratos, lo cual me genera dudas sobre el espacio, nuevas cuentas y demás._
_Tal vez la duda es porque el tamaño de los bloques en Bitcoin es relativamente fijo, y Bitcoin siempre ha sido una referencia para Blockchain._
_Las transacciones también son almacenadas._

## Gas

He evitado mencionar el gas desde el inicio, y eso es porque quería simplificar el proceso lo más que pudiese.


El código del contrato está escrito en un lenguaje completo.
Para los que este término les resulta extraño, un lenguaje completo es un lenguaje de programación normal.
La razón de lo que parece ser una redefinición innecesaria es porque Bitcoin posee un lenguaje incompleto, esto es, no permite recursividades.
Esto impide que se pueda abusar del sistema y mandar instrucciones que nunca terminen.

Tal vez, como me pasó a mí, desde que se mencionó que Ethereum poseía un lenguaje completo, i.e. que permitía recursividades, surgió una duda persistente:
¿Y cómo evitan que un mensaje cree una recursividad infinita y colapse la red?

Es ahí donde entra el concepto de gas, y el por qué el ether es considerado un criptocombustible.

## EVM

Las computadoras funcionan leyendo código máquina y ejecutándolo en sus circuitos.
~~Ahora, si entendí bien, los programas (o clientes) que implementan  la red Ethereum tiene su propio 'código máquina', que es básicamente su lenguaje de programación.~~
Ahora, si entendí bien, la red Ethereum tiene especificado su propio 'código máquina', que es básicamente su lenguaje de programación.
Intuyo que se le llama 'virtual machine' porque esta especificación está básicamente simulando un computadora.
Incluso tiene implementado un stack, memoria y almacenamiento.

El código máquina de Ethereum, o bytecode, es necesario porque elimina las ambiguedades de los lenguajes de alto nivel, ya que son, en esencia, simples instrucciones como PUSH1 o CALLDATALOAD:

https://github.com/ethereum/wiki/wiki/Ethereum-Development-Tutorial

Además, el tamaño de un contrato en bytecode es pequeño en comparación a lenguajes de alto nivel. Sin mencionar el parseo o análisis del código, muchísimo más directo y eficiente.

Pero los lenguajes de alto nivel siguen siendo necesarios, y es ahí donde entra solidity.

## Solidity

Cuando escribí que el bytecode era necesario porque eliminaba las ambiguedades, en realidad solo lo estaba suponiendo.
Un lenguaje máquina, al ser de bajo nivel, es perfecto para crear un sistema robusto, o al menos así es como yo lo entiendo.

Sin embargo, para el desarrollo de contratos inteligentes es necesario un lenguaje más práctico, 
y si bien hubieron varias propuestas basadas en otros lenguajes, Solidity es actualmente el más popular, y el único soportado oficialmente, creo.
La razón puede ser por su parecido con JavaScript, y el hecho de que las aplicaciones descentralizadas están teniendo su auge en la web, por lo que se siente más natural.

Al ser un lenguaje de alto nivel, este necesita ser compilado al bytecode de la EVM, por lo que se usa... no sé.

No sé donde poner esto pero, cada vez que subes un contrato inteligente, estás creando una cuenta contrato.

## Clientes

__Importante: No confundir el cliente con la billetera (o wallet).__

En el mundo del software hay una clara línea entre abstracción e implementación.
Me gusta visualizarlo como que la abstracción es lo que se escribe en la pizarra y la implementación es el código que intenta replicar lo que está en dicha pizarra.
Alguien tiene que programar todo lo especificado en las secciones anteriores, y es ahí donde nace el concepto de clientes.

Si bien en el siguiente capítulo se adentrará en más detalle, es válido mencionar los diferentes intentos de implementación, ya sean los oficiales y los de terceros.

### Implementaciones oficiales

¿Por qué existen distintas implementaciones oficiales? 
Porque están escritas en diferentes lenguajes.
Si entendí bien, estas implementaciones tienen que programar, entre otras cosas, el lenguaje máquina de la EVM, por lo que uno puede imaginarse el trabajo que se requiere.

* GEth (Go)
* Eth (C++)
* Pyethapp (Python)

### Implementaciones de terceros

_Nota: Estas implementaciones son, por razones obvias, no oficiales. Utilizar bajo su propio riesgo._

## Posibles tópicos a añadirse en este capítulo:

* Dapps

Wallets y Native Dapps

Web Dapps

* ¿Metamask?
* Consenso: Proof of Work vs Proof of Stake