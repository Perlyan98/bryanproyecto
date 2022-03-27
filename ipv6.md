# Prefijos de subred 
>Notación de los prefijos


- Esta notación está descrita en la RFC 4291 "IP Version 6 Addressing Architecture".
- Un prefijo es un conjunto de bits (en la zona de mayor peso) en una dirección IPv6, que se utiliza para identificar subredes o el tipo de dirección.
- El nombre exacto que reciben estos bits es “prefijo de enrutado global”.
- La notación de prefijo es muy similar a la forma en que se escriben las direcciones IPv4 en notación CIDR (Classless Interdomain Routing), indicando detrás de la dirección IP el número de bits que determinan el ID de la red (192.168.0.10/24 equivale a una máscara 255.255.255.0)

> En IPv6 tenemos, Dirección IPv6 / Longitud del prefijo

- El campo “Longitud del prefijo” especifica cuantos bits de la parte izquierda de la dirección forman el prefijo.

- Gracias al prefijo, los routers saben como dirigir los paquetes que les llegan hacia su destino correcto en una subred determinada.

- Un ejemplo, en la siguiente dirección IPv6, puesto que cada carácter hexadecimal consta de 4 bits, el prefijo es la parte marcada en azul (10 caracteres hexadecimales):

> 2E78:DA53:1200::/40

La notación abreviada (sustitución de ceros con un doble “:”) se puede aplicar también a la representación del prefijo, siguiendo las reglas ya explicadas.

# Clasificacion de direcciones ipv6
> Existen tres tipos de direcciones IPv6:

- Unicast: las direcciones IPv6 unicast identifican de forma exclusiva una interfaz en un dispositivo con IPv6 habilitado. Como se muestra en la ilustración, las direcciones IPv6 de origen deben ser direcciones unicast.

- Multicast: las direcciones IPv6 multicast se utilizan para enviar un único paquete IPv6 a varios destinos.

- Anycast: las direcciones IPv6 anycast son direcciones IPv6 unicast que se pueden asignar a varios dispositivos. Los paquetes enviados a una dirección anycast se enrutan al dispositivo más cercano que tenga esa dirección. En este curso, no se analizan las direcciones anycast.

>A diferencia de IPv4, IPv6 no tiene una dirección de broadcast. Sin embargo, existe una dirección IPv6 multicast de todos los nodos que brinda básicamente el mismo resultado.

![imagen](https://interpolados.files.wordpress.com/2017/03/134.png)

# Reglas de estructura 

Cuando se habla en IPv4 sobre direccionamiento, en un instante pensamos en direcciones privadas y direcciones pública, pero en el caso de IPv6, debemos pensar en direcciones Global Unicast, las cuales se asemejan a las direcciones públicas de IPv4.

Estas direcciones Global Unicast están definidas con la dirección y prefijo 2000::/3, lo que indica que los tres primeros bits del primer cuarteto de esta dirección no pueden variar (0010), entonces, estas direcciones pueden empezar con el valor numérico 2000 y 3000.

La gracia de definir estas direcciones unicast globales, es que se jerarquiza la asignación de direcciones, permitiendo subdividirla para ser entregada a los RIRs (Regional Internet Registries), y estos asignarlas a los ISPs.

Por lo tanto, la estrategia de asignación de direcciones IPv6 es la siguiente:

Las direcciones públicas se agrupan numéricamente por regiones.
Dentro de cada región, se subdividen para ser asignadas a los ISPs.
Cada ISP de cada región, vuelve a subdividir para asignar a los clientes.
Las dos entidades encargadas del proceso de asignación de direcciones son la ICANN y la IANA.

> En total son 5 RIR, los cuales son:

- AFRINIC
- APNIC
- ARIN
- LACNIC
- RIPE NCC

Ahora ya sabemos que las direcciones Global Unicast empiezan con el prefijo 2000::/3, pero la estructura de la dirección en sí, esta definida por la RFC 3587.
Esta RFC especifica que los primeros tres bits ya mencionados más los siguientes 45 representan el prefijo de routing global. De los cuales, la IANA puede asignar un prefijo 12 al 23 a los RIRs, estos asignan un prefijo 32 a los ISP, los cuales asignan un /48 a los clientes, y las redes LAN usan una barra 64.

![iamgen](https://www.w0lff4ng.org/assets/img/fundamentos-de-ipv6-parte-2/ipv6.png)



# Direcciones especiales

Versión 6 ha sido un poco compleja estructura de dirección IP que en IPv4. IPv6 ha reservado algunas direcciones y dirección notaciones de propósitos especiales. Consulte la tabla que aparece a continuación:

![imagen](https://www.tutorialspoint.com/es/ipv6/images/special_address_table.jpg)

- Como se muestra en la tabla, la dirección 0:0:0:0:0:0:0:0/128 no especifica nada y se dice que es indeterminado. Después simplificar, todos los 0s son compactados a ::/128.

- En IPv4, la dirección 0.0.0.0 con máscara 0.0.0.0 representa la ruta por defecto. El mismo concepto se aplica también a IPv6, la dirección 0:0:0:0:0:0:0:0 máscara con todos los 0s representa la ruta por defecto. IPv6 Después de aplicar regla, esta dirección se comprime a ::/0.

- Las direcciones de loopback en IPv4 son representados por 127.0.0.1 a 127.255.255.255. Pero en el IPv6, sólo 0:0:0:0:0:0:0:1/128 representa la dirección de bucle. Una vez dirección de retorno de bucle, que se puede representar como ::1/128.

>## Reservados Dirección de multidifusión para los protocolos de enrutamiento
![imagen](https://www.tutorialspoint.com/es/ipv6/images/reserved_multicast_routing_address.jpg)

- El cuadro anterior muestra la reserva las direcciones de multidifusión de protocolo de enrutamiento interior.

- Las direcciones están reservadas por el mismo reglamento de IPv4.


>## Reservados Dirección de multidifusión para los Routers/Nodo

![imagen](https://www.tutorialspoint.com/es/ipv6/images/reserved_multicast_routers_nodes_address.jpg)

- Estas direcciones a los routers y hosts para hablar con los routers disponibles y de los hosts en un segmento sin ser configurado con una dirección Ipv6. Los hosts utilizan EUI-64 base configuración automática para configurar automáticamente una dirección IPv6 y, a continuación, hablar a los hosts/routers del segmento por medio de estas direcciones.