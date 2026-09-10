1.1 Los cuatro defectos. Para cada uno: qué está mal, en qué archivo y en qué líneas se
manifiesta, y qué consecuencia tiene. Un defecto no es "falta una línea": es qué garantía se
pierde por no tenerla.

**RPTA:** 

- Defecto 1: El job "publicar" se puede ejecutar inclusive cuando "validar" ha fallado porque no se indica que
  "publicar" depende de "validar". Esto genera que se puedan publicar paquetes no válidos, generando errores o
  aumentando la Tasa de fallo en cambios.

- Defecto 2: En el job "publicar", cada publicación reemplaza el paquete anterior, es decir, se pierde la trazabilidad
  entre versiones para un usuario que desee usar otras versiones del artefacto.

- Defecto 3: El workflow no espera al reporte de SonarQube. Es decir, si SonarQube encuentra alguna falla o no se cumple
  con algún requisito, el job continuará igualmente con la publicación.

- Defecto 4: Se instalan dependencias 2 veces y en instancias diferentes, lo cual hace que descargar e instalar 2 veces
  las librerías de Python (aumenta la duración del workflow)


1.2 El defecto que explica la duración. De los cuatro, cuál explica el tiempo que
registraron en docs/linea-base.md. Sustenten con el número que midieron.

**RPTA:** 

1.3 El vínculo con su caso. Cuál de los cuatro defectos ataca la restricción del caso
transversal de su grupo. Citen un dato del value stream map que levantaron en la Sesión 1.

**RPTA:**

1.4 La métrica DORA. Qué métrica DORA esperan mover con la intervención y por qué.
Solo dos son alcanzables sin despliegue: identifiquen cuáles y elijan una.

**RPTA:** *Lead Time para cambios*: Esta métrica 

1.5 El proxy. Qué número concreto van a medir para sustentar que la métrica se movió.
Decláralo antes de intervenir.

**RPTA:**
