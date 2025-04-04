# Examen_de_Redes
https://github.com/MrShadowDani/Examen_de_Redes.git

Parte Teoríca
1. El Mural de las Siete Capas
Este mural representa el modelo OSI, cuyas siete capas definen las funciones y procesos que se siguen para enviar datos desde un origen hasta un destino. Cada capa aporta su parte de la comunicación, desde la capa física (transmisión de bits por el medio) hasta la capa de aplicación (servicios y protocolos cercanos al usuario). El paso por todas ellas asegura que el mensaje sea empaquetado, enviado y recibido de forma correcta y estandarizada.

2. Los Dos Pergaminos del Mensajero
El “Mensajero Confiable” equivale a TCP (Transmission Control Protocol), que establece una conexión, intercambia saludos (el “handshake de tres pasos”) y confirma la llegada de los datos, reintentando si algo falla. El “Mensajero Veloz” corresponde a UDP (User Datagram Protocol), que envía los mensajes sin establecer conexión previa ni confirmar recepción. TCP ofrece fiabilidad y control de flujo, pero con mayor sobrecarga; UDP es más rápido y simple, aunque puede perder paquetes.

3. El Enigma de las Subredes
Para dividir 192.168.50.0 en 4 subredes, se requiere “pedir prestados” dos bits de la porción de host. La máscara resultante es 255.255.255.192 (o /26). Cada subred tiene 62 direcciones utilizables (4 subredes × 64 direcciones totales en cada una, restando 2 para la dirección de red y broadcast en cada subred).

4. La Encrucijada de las Rutas
El tótem simboliza una tabla de enrutamiento, que indica a qué destino enviar los paquetes. Las flechas “talladas en piedra” representan entradas de enrutamiento estático (no cambian automáticamente), mientras que las flechas “móviles” aluden a enrutamiento dinámico, el cual adapta las rutas si hay fallas o cambios en la red. En un router moderno, la tabla de enrutamiento define la “salida” o interfaz por la que se debe reenviar cada paquete, según la dirección de destino.

5. El Guardián de la Máscara Única
La leyenda describe la técnica de NAT (Network Address Translation), donde un único dispositivo (por ejemplo, un router) “enmascara” las direcciones privadas de varios hosts y muestra solamente su propia dirección pública al exterior. Esto protege la identidad interna y ahorra direcciones IPv4. Dos beneficios principales son mayor seguridad (pues los equipos internos no son visibles desde fuera) y uso eficiente de las direcciones IP públicas.

Parte Practica

Ejercicio 1: La Ruta Perdida entre Dos Reinos
Este ejercicio consiste en conectar dos redes locales (simbolizadas por “dos ciudades”) a través de un enlace punto a punto. Para ello:
• Se crean dos routers, cada uno con su propia red local y un switch al que se conectan los PCs.
• Se configura un enlace directo (serial o Ethernet) entre ambos routers.
• Se asignan direcciones IP distintas a cada subred, y se usa una subred adicional para enlazar los routers.
• Se añaden rutas estáticas o una ruta por defecto en cada router de forma que los paquetes puedan pasar de una ciudad a la otra.
• El objetivo es comprobar la comunicación cruzada (PCs de Ciudad A haciendo ping a los de Ciudad B y viceversa).

Ejercicio 2: La Ciudad de las Redes Aisladas
Aquí se implementa un entorno de VLANs (redes virtuales) y enrutamiento inter-VLAN (router-on-a-stick). La historia lo describe como “una gran metrópolis” dividida en facciones, pero técnicamente es:
• Un switch configurado con varias VLAN
• PCs asociados a cada VLAN para que, dentro de la misma VLAN, se comuniquen entre sí directamente.
• Un router conectado en un único enlace “trunk” al switch y con subinterfaces (Fa0/0.10, Fa0/0.20, etc.) para el enrutamiento entre VLANs.
• El objetivo es verificar que los PCs en VLAN diferentes pueden comunicarse a través del router y que los de la misma VLAN lo hacen sin intervención del router.
