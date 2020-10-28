# Betaflight-4.2.0
Configuración recomendada

En este repositorio iré actualizando las mejoras de Betaflight 4.2.0 así como las configuraciones recomendadas.

### Pantalla de inicio

### Pantalla de Ajustes

### Pantalla de Configuración

### Pantalla de Energía y Batería

### Pantalla de Modo de Seguridad

### Pantalla de Ajustar PID

#### PID
#### TASAS
#### FILTROS


- Configurar el interpolador de señal:

Para carreras y con una emisora de alta prestación podemos habilitar este modo
set ff_interpolate_sp = ON 

De lo contrario, nos interesa filtrar la señal para evitar el ruido que podamos tener en la señal;
Para un freestyle lo recomendable seria hacer un filtrado de la senyal;
set ff_interpolate_sp = Average_2

Si hacemos una mezcla entre un freestyle y un cinematic con nuestra camara de acción
set ff_interpolate_sp = Average_3

Para Hoops y Cinematicos tendriamos que usar un filtrado mas alto para suavizar los movimientos
set ff_interpolate_sp = Average_4
 

### Pantalla de Receptor

### Pantalla de Modos

### Pantalla de Correcciones

### Pantalla de Servos

### Pantalla de Motores

### Pantalla de OSD

### Pantalla de Transmisor de Video

### Pantalla de Sensores

### Pantalla de Registro Conectado

### Pantalla de Caja Negra

### Pantalla de CLI



#### Fuentes de información

Notas oficiales de la versión
https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes

Joshua Bardwell
https://www.youtube.com/watch?v=rhfOVJMxY7E

QuadMx Drones
https://www.youtube.com/watch?v=tCgN-EwdSQ8



