# Hablemos de Ethereum (y Blockchain)

> Una blockchain es un libro o registro contable distribuido a través de una red P2P, validada por un mecanismo de consenso y funciones criptográficas, y cuya funcionalidad es expandida con un sistema de contratos inteligentes.

Este es mi mejor intento de traducir la defición de blockchain de la página de Hyperledger. 
Usé esta definición porque Hyperledger es el proyecto que está intentando forjar un estándar en las definiciones de esta tecnología.
Hay que apoyar el esfuerzo.

En sí, blockchain es una estructura de datos combinada con otras tecnologías, como las redes, el consenso, la criptografía y los smart contracts.

Para una defición menos técnica, pero sin caer en analogías, el blockchain es un registro de todos los movimientos de un sistema.
Un ejemplo concreto es el blockchain de Bitcoin, el cual está formado exclusivamente por todas las transacciones de las monedas.
Estas transacciones están conformadas básicamente por la dirección de la persona que envía el dinero, la cantidad que envía y la direccion del destinatario.

Todas las computadores que participan de la red deben tener una copia de la blockchain, por eso se le llama 'distribuido'. 
Una transacción solo ocupa unos cuantos bytes de espacio, por lo que es feasible que pueda almacenarse todo el historial de Bitcoin en cada una de las máquinas de la red.

(Un pequeño paréntesis, Blockchain forma parte de las DLT (Distributed Ledger Technologies), o tecnologías de distribución contables [nombre súper no oficial].
Bitcoin y Ethereum son blockchains, pero Hyperledger* y Corda no lo son, aunque sí son DLT. La clarificación será para otra ocasión.)

Hasta ahí el concepto suena bastante sencillo. 
Una persona realiza una transacción y todos lo apuntan en su copia del registro, la blockchain.

Sin embargo, en la realidad, siempre habrán agentes malintencionados que intenten falsificar información o identidades.
Es aquí donde entran los mecanismos de 


Hasta aquí uno podría tener la idea de que la blockchain es una lista gigantesca de transacciones, y que son almacenadas de esa forma en las computadoras.
Pero la verdad es que las transacciones son agrupadas en bloques, de ahí en nombre de 'block'chain.
Así es posible verificar rápidamente la validez de las transacciones a través de las funciones criptográficas.
Merkle trees, funciones hash y curvas elípticas. 
Blockchain es una conglomeración de estándares matemáticos de criptografía (aprobadas por el gobierno de EEUU*), pero el usuario promedio no tiene que sabe





## Disclaimer

*Cosas que faltan confirmación, todo esto lo estoy escribiendo mayormente de memoria, eventualmente formalizaré todo lo escrito aquí.

Lógica de negocio.






