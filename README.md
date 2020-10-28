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

De lo contrario, nos interesa filtrar la señal para evitar el ruido que podamos tener en la señal
Para un freestyle lo recomendable seria hacer un filtrado de la senyal
set ff_interpolate_sp = Average_2

Si hacemos una mezcla entre un freestyle y un cinematic con nuestra camara de acción
set ff_interpolate_sp = Average_3

Para Hoops y Cinematicos tendriamos que usar un filtrado mas alto para suavizar los movimientos
set ff_interpolate_sp = Average_4
 

### Título Pantalla de Receptor

### Título Pantalla de Modos

### Título Pantalla de Correcciones

### Título Pantalla de Servos

### Título Pantalla de Motores

### Título Pantalla de OSD

### Título Pantalla de Transmisor de Video

### Título Pantalla de Sensores

### Título Pantalla de Registro Conectado

### Título Pantalla de Caja Negra

### Título Pantalla de CLI



Fuentes de información

Notas oficiales de la versión
https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes

Joshua Bardwell
https://www.youtube.com/watch?v=rhfOVJMxY7E

QuadMx Drones
https://www.youtube.com/watch?v=tCgN-EwdSQ8



