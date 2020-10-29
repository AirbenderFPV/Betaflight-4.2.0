# Betaflight v4.2.x

<img src="https://raw.githubusercontent.com/wiki/betaflight/betaflight/images/betaflight/bf_logo.png" alt="BetaFlight">

En este repositorio iré actualizando las mejoras de **Betaflight 4.2.x** así como las configuraciones recomendadas.  
El uso de esta información queda bajo la responsabilidad de cada usuario y siendo consciente del quad que tiene.  
Recordad que para usar esta versión de Betaflight es necesario el **Betaflight Configurator version 10.7.0**.  
Nuevas aportaciones de esta versión:  
- Han reprogramado completamente la forma de leer el loop del giroscópico, esto ha provocado un mejor rendimiento y lo hace trabajar a la velocidad nativa del giroscopio, por lo que no lo puedes cambiar, viene por defecto.
- Nuevos modelos de Rates, mas fácil de configurar desde el OSD, con ajustes mas optimizados y rápidos
- Nuevo sistema de compensación por la caída del voltaje de la batería, lo que resulta en un comportamiento más uniforme del acelerador/PID durante todo el tiempo de vuelo.
- Han añadido un nuevo modelo de carrera, el NEF, que esta pensado mas para los tinys, este modo combina el acro para el eje de pith, y horizont en el eje del ROLL.
- Muchas mejoras en el OSD, como poner el logo poner el logo, funciones añadidas para Frsky.
- Podrás bindear receptores Frsky con soporte SPI desde el propio betaflight 4.2 sin entrar por el CLI.
- Ahora es obligatorio calibrar el acelerómetro.
Hay mas mejoras en el betaflight 4.2 he resumido las que son la principales y debes tener en cuenta antes de realizar el cambio. 

Si tienes dudas de como descargarte el configurador o como alcualizar el firmware visita los repositorios:  

[Actualizar firmware 4.2.x] https://github.com/AirbenderFPV/Actualizar-Firmware

[Actualizar/Instalar el Configurador de Betaflight v10.7] https://github.com/AirbenderFPV   

## Menú Betaflight 4.2.x  

### Pantalla de Puertos

En esta pantalla podremos configurar los puertos de nuestro quad.  
Estos puertos normalmente vienen definidos en la placa controladora con la etiqueta TX y acompañada de un numero.  

Por ejemplo:  
El TX3 en la placa controladora sera el puerto Uart3 en Betaflight.  

### Pantalla de Ajustes  

En esta pantalla podremos calibrar, restaurar o hacer una copia de seguridad nuestro quad.



### Pantalla de Configuración  

En esta pantalla podremos configurar el protocolo que controlara nuestros motores y las diferentes funcionalidades de nuestro quad.  
Es una de las pestañas mas importante de la configuración de nuestro quad.  

<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/configuracion.PNG">

_EJemplo: Configuración usada en una controladora MAMBA STM32F722S_

#### Funcionalidades ESC/Motor:
La opción **MOTOR_STOP** controla si los motores girarán o no al armar el quad.  
Si los motores giran al armar el quad y tenemos esta opción deshabilitada seguramente tendremos habilitado el **AIR MODE**.
Por defecto el **Motor Idle Throttle value [percent]** tiene un valor de 4.5, esto es el porcentaje al que giraran los motores al armar.
Por defecto el numero de **Polos del motor** viene como 14. Estos son el numero de imanes que tiene tu campana de motor.
En tinnys a veces este numero se reduce ya que los motores son mas pequeños. Rondan sobre 12.
Lo mejor es asegurarse mirando una campana de nuestros motores.

#### Configuración del sistema y DShot settings:  

El **Acelerómetro** es el sensor que nos ayuda a controlar la inclinazión del quad.  
En caso de volar en **Angle Mode** o **Horizon Mode** necesitas tener activado este sensor. 
Revisa la pantalla de Ajustes para ver como calibrar el quad si usas esos modos.  
Normalmente las controladoras de vuelo no trae equipado un Barómetro ni un Magnetómetro.  
Lo mejor en estos casos es **Desactivar** estos dos sensores.  

Las frequencias del sersor Giro y del PID son importantisimas para volar.  
Estas estan condicionadas a el tipo de controladora de vuelo tengamos, una F7 irá mejor que una F4.  
Si tienes poca experiencia es mejor dejar los ajustes por defecto.  
Consulta en las especificaciones de tus ESCs o 4in1 que DSHOT tiene antes de aplicar cualquier corrección.  
Se puede habilitar el bidirectional con el switch **DShot Bidirectional**.  
También hay que consultar en las especificaciones de tus ESCs o 4in1 si lo soporta.  

- Con el filtro rpm habilitado   
dshot300 -> 4k max pidloop (Recomendable para controladoras F4)  
dshot600 -> 8k max pidloop (Recomendable para controladoras F7)   

- Usando el bidirectional y con el filtro rpm habilitados:     

dshot150 -> 2k max pidloop   
dshot300 -> 4k max pidloop (Recomendable para controladoras F4)     
dshot600 -> 8k max pidloop (Recomendable para controladoras F7)    

- Sin usar el bidirectional y con el filtro rpm habilitados:    

dshot150 -> 4k max pidloop (Recomendable para controladoras F4)   
dshot300 -> 8k max pidlopp (Recomendable para controladoras F7)  
dshot600 -> up to 16k max pidloop (8k es el maximo que se puede configurar en la versión 4.2)  

Para la actualización de firmware de los ESC o 4in1 visita:

[Repertorio ESC and 4in1] https://github.com/AirbenderFPV

#### Armado y Aliniación de Placa y Sensores:

Si tenemos el Acelerómetro activado, habilitaremos la selección del Ángulo de armado máximo.  
Personalmente recomiendo el valor **180º** para poder armar el quad bajo cualquier inclinación.  

En cuanto a la aliniación de la placa, si la montamos de forma que la flecha dibujada en la controladora de vuelo apunte hacia delante, todos los valores tienen que ser cero.


<img src="https://raw.githubusercontent.com/AirbenderFPV/Betaflight-4.2.0/main/images/configuracion.PNG">

#### Receptor: 

En este subapartado podemos configurar como será la comunicación

### Pantalla de Energía y Batería

Esta pantalla nos ayuda con la gestión de el voltage y la corriente de nuestro quad.  

- Valores por defecto, no editar   
El voltaje mínimo de celda nunca debe bajar de 3.3v.  
Si bajamos el voltaje de una celda por debajo de 3.3v podemos dañar la Lipo.   
El voltaje de aviso por defecto se configura en 3.5v.  
Este voltaje es el que determina en el OSD cuando aparece el aviso de _LOW VOLTAGE_    

Para ajustes y calibraciones del sensor de voltaje, de corriente y mucha mas información visita:  

[Repertorio Baterias] https://github.com/AirbenderFPV/Baterias

### Pantalla de Modo de Seguridad

### Pantalla de Ajustar PID

#### PID  
Esta pestaña nos ayuda a calibrar el PID de nuestro quad, si tienes poca experiencia es mejor dejar los ajustes por defecto.

#### TASAS  
Esta pestaña nos ayuda a calibrar los "rates" o tasas de nuestro quad, en otras palabras la sensibilidad de nuestros sticks.   
Podemos editar el perfil de cada palanca editando los valores para respuestas mas ajustadas a nuestra forma de volar.  
Si tienes poca experiencia es mejor dejar los ajustes por defecto.  

#### FILTROS  
Esta pestaña nos ayuda a filtrar las señales de nuestro quad, si tienes poca experiencia es mejor dejar los ajustes por defecto.   

#### Ajustes rapidos recomendados en Betaflight 4.2.x

Estos comandos son sugerencias sobre cómo se pueden ajustar algunas de las configuraciones menos comunes para adaptarse a un cierto tipo de vuelo. Son valores que Betaflight nos da como orientativos para los diferentes tipos de vuelo. No ajustaran perfecto nuestro quad, ya que no incluyen ajustes de PID o valores de filtro, pero nos ayudaran a tener un control mas adaptado a nuestras necesidades.

Para usar estos comandos tendremos que copiarlos y pegarlos en el CLI, una vez pegados le damos a enter.  
Para guardarlos tenemos que ejecutar el comando _Save_.

- ProRace (Requiere una buena controladora y motores en buen estado, revisar en los primeros vuelos que los motores no se calienten)

set iterm_relax_cutoff = 30  
set rc_smoothing_auto_smoothness = 5  
set ff_interpolate_sp = ON  
set ff_smooth_factor = 0  
set ff_spike_limit = 60  
set ff_boost = 20  
set feedforward_transition = 0  
set yaw_lowpass_hz = 100  
set throttle_boost = 7  
set throttle_boost_cutoff = 25  
set dyn_lpf_dterm_curve_expo = 7  
set gyro_rpm_notch_q = 600  


- Race y Fast Freestyle (Tolera controladoras de gama media, quad de respuesta rapida)

set iterm_relax_cutoff = 20  
set rc_smoothing_auto_smoothness = 7  
set ff_interpolate_sp = AVERAGED_2  
set ff_smooth_factor = 20  
set ff_spike_limit = 70  
set ff_boost = 15  
set feedforward_transition = 0  
set yaw_lowpass_hz = 100  
set throttle_boost = 7  
set throttle_boost_cutoff = 25  
set dyn_lpf_dterm_curve_expo = 7  
set gyro_rpm_notch_q = 700  

- HD (Ideal para hacer grabaciones en HD con nuestra camara de acción)

set iterm_relax_cutoff = 10  
set rc_smoothing_auto_smoothness = 20  
set ff_interpolate_sp = AVERAGED_3  
set ff_smooth_factor = 40  
set ff_spike_limit = 55  
set ff_boost = 0  
set feedforward_transition = 40  
set yaw_lowpass_hz = 70  
set throttle_boost = 5  
set throttle_boost_cutoff = 10  
set dyn_lpf_dterm_curve_expo = 7  
set gyro_rpm_notch_q = 800  

- Cinematic (Ideal para cinehoops y hoops)

set iterm_relax_cutoff = 5  
set rc_smoothing_auto_smoothness = 40  
set ff_interpolate_sp = AVERAGED_4  
set ff_smooth_factor = 50  
set ff_spike_limit = 50  
set ff_boost = 0  
set feedforward_transition = 70  
set yaw_lowpass_hz = 50  
set throttle_boost = 2  
set throttle_boost_cutoff = 10  
set dyn_lpf_dterm_curve_expo = 8  
set gyro_rpm_notch_q = 900  
set iterm_windup = 75  


- Valores por defecto ( Valor zero sisgnifica 'apagado')  
Estos son los valores por defecto por si queremos volver atrás en alguna de estas configuraciones

set iterm_relax_cutoff = 15  
set rc_smoothing_auto_smoothness = 10  
set ff_interpolate_sp = AVERAGED_2  
set ff_smooth_factor = 37	  
set ff_spike_limit = 60  
set ff_boost = 15  
set feedforward_transition = 0  
set yaw_lowpass_hz = 0  
set throttle_boost = 5  
set throttle_boost_cutoff = 15  
set dyn_lpf_dterm_curve_expo = 5  
set gyro_rpm_notch_q = 500  
set iterm_windup = 100  

- Configuración extra para los usuarios de 4in1  
Recomendable si usas un 4in1 usar estos ajustes independientemente del modo de vuelo seleccionado anteriormente

set dyn_lpf_dterm_curve_expo = 6  
set vbat_sag_compensation = 100  
set vbat_pid_gain = OFF  
set rc_smoothing_type = FILTER  
set rc_smoothing_input_hz = 0  
set rc_smoothing_derivative_hz = 0  
set rc_smoothing_input_type = BIQUAD  
set rc_smoothing_derivative_type = PT1  
set rc_smoothing_auto_smoothness = 10  

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

Esta pantalla nos permite introducir comandos para programar o extraer valores de la controladora de vuelo de nuestro drone  
Para guardarlos tenemos que ejecutar el comando **Save**.

Podemos listar nuestros ajustes cambiados respecto a los valores por defecto con el comando **diff_all**


#### Fuentes de información

[Notas oficiales de la versión] https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes  

[Joshua Bardwell] https://www.youtube.com/watch?v=rhfOVJMxY7E  

[QuadMx Drones] https://www.youtube.com/watch?v=tCgN-EwdSQ8   
 
[Midronedecarreras] https://www.midronedecarreras.com/betaflight/#Descarga_el_Configurador_BLHeli_suite_32  

[Airbender_FPV] https://www.instagram.com/airbender_fpv/

