# Proyecto PD - GRABADORA Y REPRODUCTOR DE AUDIO

## - Introducción y funcionamiento 
Este proyecto tiene como objetivo principal permitir grabar audio utilizando un micrófono, guardarlo en una tarjeta SD en formato WAV y luego reproducir el audio grabado a través de un altavoz. Además, proporciona una interfaz web simple para controlar estas funciones.

#### Materiales:
- ESP32
- Tarjeta SD
- Microfono
- Altavoz 
- MAX98357A 


### Código y explicación 
```c++

```
Este programa configura un ESP32 para capturar audio de un micrófono, guardarlo en una tarjeta SD y reproducirlo a través de un altavoz, todo controlado mediante una interfaz web. Utiliza buses de comunicación I2S para el audio y SPI para la tarjeta SD, junto con WiFi para la interfaz web.

Se incluyen librerías necesarias para trabajar con audio (Audio.h, AudioFileSourceSD.h, AudioOutputI2S.h, AudioGeneratorWAV.h), la tarjeta SD (SD.h), y WiFi (WiFi.h).

Se declaran las funciones que serán definidas más adelante: setupI2S_RX, setupI2S, setupSD, writeWavHeader, recordAudioToFile, reproducirAudio, handleRecord, handlePlay, handleRecordPlayWithDelay.
#### Definición de pines:
Pines para el I2S (Inter-IC Sound) del micrófono y altavoz.
Pin para el chip select de la tarjeta SD.

#### Configuración de la red WiFi:
Se configuran las credenciales de la red WiFi y se inicia la conexión.

#### Configuración del servidor web:
Se configura un servidor web simple que responde a diferentes rutas ("/", "/record", "/play", "/recordplaydelay") con diferentes funciones.

#### Configuración del I2S para micrófono (RX):
Se configura el I2S en modo recepción para capturar audio desde el micrófono.

#### Inicialización de la tarjeta SD:
Se monta la tarjeta SD para permitir la lectura y escritura de archivos.

#### Grabación de audio en un archivo:
- recordAudioToFile: Captura audio desde el micrófono y lo guarda en la tarjeta SD en formato WAV.
  
#### Configuración del I2S para altavoz (TX):
- setupI2S: Configura el I2S en modo transmisión para enviar audio al altavoz.

#### Reproducción de audio:
 - reproducirAudio: Abre el archivo de audio desde la tarjeta SD y comienza la reproducción a través del altavoz.
   
#### Manejadores de rutas del servidor web:

- handleRecord: Llama a la función de grabación de audio.
- handlePlay: Llama a la función de reproducción de audio.
- handleRecordPlayWithDelay: Graba audio y luego lo reproduce después de un retraso de 2 segundos.

#### Bucle principal:
- loop: Maneja las peticiones del servidor web y verifica si la reproducción de audio está en curso.



