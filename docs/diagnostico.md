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

- Es el defecto 4, la descarga e instalación doble de librerías. Según los datos, realizar este paso toma entre 9 y 10 segundos.

1.3 El vínculo con su caso. Cuál de los cuatro defectos ataca la restricción del caso
transversal de su grupo. Citen un dato del value stream map que levantaron en la Sesión 1.

**RPTA:**

- Afectaría a la duración del Process Time. En el caso de Financiera los Andes, afectaría al tiempo de la Integración continua, que en el caso dura 35 minutos, pero con más librerías y más paquetes de Python, podría durar mucho más.

1.4 La métrica DORA. Qué métrica DORA esperan mover con la intervención y por qué.
Solo dos son alcanzables sin despliegue: identifiquen cuáles y elijan una.

**RPTA:** *Lead Time para cambios*: Esta métrica mide el tiempo desde el commit hasta producción. Se espera mejorar porque
se reduciría el doble tiempo para obtener la "Validación" en el pipeline.

1.5 El proxy. Qué número concreto van a medir para sustentar que la métrica se movió.
Decláralo antes de intervenir.

**RPTA:** Se medirá el tiempo de duración del workflow, esperando pasar de ~55s a ~45s.

4.1 Medición posterior. El valor del proxy después de la intervención, junto al de la línea
base. Qué cambió y en qué proporción.

**RPTA:** Nuevo valor: 1m y 10s. Linea base: ~55 s. Lo principal fue que se agregaron steps y algunas validaciones adicionales, lo cual pudo aumentar el tiempo.

4.2 Justificación de la versión. Qué versión declararon y qué commits del historial la
sustentan.

**RPTA:** Version 1.5.5. Se contaron los feat y los fix luego del ultimo feat (el pipeline). Se incluye el fix de los cambios de este laboratorio

4.3 Lo que no se resolvió. El pipeline sigue teniendo limitaciones. Nombren una y
expliquen qué haría falta para resolverla.

**RPTA:** Cálculo manual de las versiones. Se necesitaría un estándar de commits e implementar una herramienta (o pipeline) que actualice automáticamente la versión según la cantidad de
fixes o features.

4.4 Declaración de uso de IA generativa, conforme al sílabo

**RPTA:** Se uso Gemini 3.1 Pro para ayudar en la detección de los Defectos 3 y 4. También, se usó el LLM para la programación en el pipeline. Finalmente se uso el LLM para dar asistencia en una limitación final del pipeline (4.3).
