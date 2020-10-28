# Betaflight-4.2.x

En este repositorio iré actualizando las mejoras de **Betaflight 4.2.x** así como las configuraciones recomendadas.  
El uso de esta información queda bajo la responsabilidad de cada usuario y siendo consciente del quad que tiene.  
Recordad que para usar esta versión de Betaflight es necesario el **Betaflight Configurator version 10.7**.  
Si tienes dudas de como descargarte el configurador o como alcualizar el firmware visita mis repositorios:  

- Actualizar firmware 4.2.x en Betaflight  

- Actualizar Configurador de Betaflight  

## Menú Betaflight 4.2.x  
### Pantalla de Ajustes  

### Pantalla de Configuración  

#### DShot settings:  

- Con el filtro rpm habilitado   
dshot300 -> 4k max pidloop  
dshot600 -> 8k max pidloop  

- Usando el bidirectional y con el filtro rpm habilitados:     

dshot150 -> 2k max pidloop  
dshot300 -> 4k max pidloop (Recomendable para controladoras F4)    
dshot600 -> 8k max pidloop (Recomendable para controladoras F7)   

- Sin usar el bidirectional y con el filtro rpm habilitados:    

dshot150 -> 4k max pidloop   
dshot300 -> 8k max pidlopp    
dshot600 -> up to 16k max pidloop (8k es el maximo que se puede configurar en la versión 4.2)  

#### Actualizar Firmware ESC o 4in1:

Es muy recomendable actualizar el firmware de nuestros ESC o placa 4in1.


### Pantalla de Energía y Batería

### Pantalla de Modo de Seguridad

### Pantalla de Ajustar PID

#### PID
#### TASAS
#### FILTROS


#### Ajustes rapidos recomendados en Betaflight 4.2.x

Estos comandos son sugerencias sobre cómo se pueden ajustar algunas de las configuraciones menos comunes para adaptarse a un cierto tipo de vuelo. Son valores que Betaflight nos da como orientativos para los diferentes tipos de vuelo. No ajustaran perfecto nuestro quad, ya que no incluyen ajustes de PID o valores de filtro, pero nos ayudaran a tener un control mas adaptado a nuestras necesidades.

Para usar estos comandos tendremos que copiarlos y pegarlos en el CLI, una vez pegados le damos a enter.
Para guardarlos tenemos que ejecutar el comando Save.

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

Notas oficiales de la versión
https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes

Joshua Bardwell
https://www.youtube.com/watch?v=rhfOVJMxY7E

QuadMx Drones
https://www.youtube.com/watch?v=tCgN-EwdSQ8



