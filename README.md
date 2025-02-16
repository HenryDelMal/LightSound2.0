# LightSound2.0
Python data logger, plotter, and Arduino code for LightSound 2.0 devices

### About LightSound
LightSound is an Arduino-based device that converts light intensity to sound via a light sensor and MIDI board so that blind and visually impaired (BVI) individuals may experience astronomical events like solar eclipses. The original version (LightSound 1.0) was designed and used during the total solar eclipse on August 21, 2017. In preparation for the upcoming North and South American total solar eclipses (2019, 2020, and 2024), LightSound has been redesigned with higher sensitivities and an improved sound library. The project has received funding from IAU100 to build and distribute 20 LightSound 2.0 devices to schools in Chile and Argentina so that BVI students in the path of the 2019 and 2020 solar eclipses may experience the events. 

The LightSound 2.0 devices can run on a 9-volt battery (portable mode) or off of computer power (logging mode). When in portable mode, the switch will turn the device on and off. In order to record data, LightSound must be connected to a computer. In this case, the device runs off of the computer power and will remain on as long as it is plugged in.

To hear the sounds produced by LightSound 2.0, the device must be connected to speakers or headphones via the audio jack.

More information and building instructions for LightSound 2.0 can be found at: http://astrolab.fas.harvard.edu/accessibility.html

### Instructions for logging data
Runs on Python 2.7 or 3.x

Package requirements: `datetime`, `sys`, and [`pySerial`](https://pyserial.readthedocs.io/en/latest/pyserial.html#installation)
1. Ensure that the serial logger program (LightSound2_data_logger.py) is located in the folder where you will save your data
2. Connect the LightSound 2.0 to the computer with a micro-USB B cord (must be able to transfer data)
3. Determine the appropriate serial port of the LightSound 2.0
    - Windows: type `mode` into command line, port should have the form `COM*`
    - Mac: type `ls /dev/tty.*` into terminal, port should have the form `/dev/tty.usbmodem*` or `/dev/tty.usbserial*` 
    - Linux: type `ls/dev/tty*` into terminal, port should have the form `/dev/ttyUSB*` or `/dev/ttyACM*`
4. In the terminal (Mac/Linux) or command line (Windows), navigate to data folder and type: `python LightSound2_data_logger.py port 9600 timezone file_prefix`
    - `port` is the full port name determined in Step 3 (i.e. including `/dev/tty*` for Mac or Linux)
    - `9600` is the baud rate for reading the LightSound 2.0 data
    - `timezone` is the timezone of observations (e.g. CST, EST, ART, CLT, etc.)
    - `file_prefix` is the prefix of the name of the data files (the script saves the data with the correct extension)
5. The brightness values that are being recorded by the LightSound will be visible in the terminal.
6. To stop data logging, press `Ctrl + C` in terminal/command line. The script will automatically save the raw data (\*\_raw.log) as a .csv (\*\_data.csv) file for later use.

### Instructions for plotting data
Runs on Python 2.7 or 3.x

Package requirements: `datetime`, `matplotlib`, `numpy`, `sys`
1. Ensure that the serial logger program (LightSound2_data_plotter.py) is located in the folder where you will save your data
2. In the terminal (Mac/Linux) or command line (Windows), navigate to data folder and type: `python LightSound2_data_plotter.py filename plot_lines savename.png`
    - `filename` is the full name of the data file (should end with \_raw.log or \_data.csv)
    - `plot_lines` determines whether the plot will include whether the gain and integration times
        - To plot the lux (intensity) values only, replace `plot_lines` with `0`
        - To plot the lux, gain, and integration times, replace `plot_lines` with `1`
    - `savename` is the prefix of the image name the plot will save to; use none if you do not want to save the image (extension typically is .png)

-----

# LightSound2.0
Python data logger, plotter y código para Arduino de dispositivos LightSound 2.0

### Acerca de LightSound

LightSound es un dispositivo basado en Arduino que convierte la intensidad de la luz en sonido a través de un sensor de luz y una placa MIDI para que las personas ciegas y con discapacidades visuales (BVI) puedan experimentar eventos astronómicos como los eclipses solares. La versión original (LightSound 1.0) se diseñó y usó durante el eclipse total de Sol el 21 de agosto de 2017, en los Estados Unidos. En preparación para los próximos eclipses solares totales en Norteamérica y Sudamérica (2019, 2020 y 2024), LightSound se ha rediseñado con mayor sensibilidad y una biblioteca de sonido mejorada. El proyecto ha recibido fondos de IAU100 para construir y distribuir 20 dispositivos LightSound 2.0 a escuelas en Chile y Argentina para que los estudiantes BVI que se encuentren en el camino de los eclipses solares de 2019 y 2020 puedan experimentar los eventos. 

El LightSound trabaja con una batería de 9 voltios si se lo usa en su modo portátil. El interruptor del dispositivo lo apaga unicamente si se usa esa batería. 

Para escuchar la transformación de luz en sonido, es necesario que el LightSound esté conectado a un dispositivo externo: auriculares o parlantes.

 Para registro y analisis de datos, el LightSound debe estar conectado a la PC, en este caso no necesita batería y el interruptor no tiene acción sobre el dispositivo, por eso, conectado a la PC el dispositivo estará trabajando permanentemente.

Se puede encontrar más información e instrucciones de construcción para LightSound 2.0 en: http://astrolab.fas.harvard.edu/accessibility.html


### Instrucciones para el registro de datos
El script corre en Python 2.7 o 3.x

Paquetes python requeridos: `datetime`, `sys` y [`pySerial`](https://pyserial.readthedocs.io/en/latest/pyserial.html#installation)

1. Asegúrese de que el programa registrador serie (LightSound2_data_logger.py) esté ubicado en la carpeta donde guardará sus datos.
2. Conecte el LightSound 2.0 a la computadora con un cable micro-USB B (debe poder transferir datos).
3. Determine el puerto serie utilizado por el LightSound 2.0. Según su sistema operativo:
    - En Windows: escriba `mode` en la línea de commandos del símbolo de sistema, el puerto debe tener el formato `COM*`
    - En Mac: escriba `ls /dev/tty.*` en la terminal, el puerto debe tener el formato `/dev/tty.usbmodem*` o `/dev/tty.usbserial*`
    - En Linux: escriba `ls /dev/tty*` en la terminal, el puerto debe tener el formato `/dev/ttyUSB*` o `/dev/ttyACM*` (considerando * como 0, 1, o 2)
4. En la terminal (Mac/Linux) o en la línea de comandos (Windows), navegue hasta la carpeta de datos y escriba: `python LightSound2_data_logger.py port 9600 timezone file_prefix`
    - `port` es el nombre del puerto determinado en el Paso 3, debe escribir completo `/dev/ttyACM*`
    - `9600` es la velocidad en baudios para leer los datos de LightSound 2.0
    - `timezone` (ona horaria) es la zona horaria de las observaciones (por ejemplo, CST, EST, ART, CLT, etc.). ART significa Hora en Argentina. CLT, hora en Chile.
    - `file_prefix` es el prefijo para el nombre de los archivos de datos, considerar que el script coloca automaticamente la extensión
5. Se verán en la terminal los valores que está registrando el LightSound
6. Para detener e registro de datos, presionar Ctrl + C en la terminal/linea de comandos. El script salvará automáticamente los datos crudos (\*\_raw.log) como un archivo .csv (\*\_data.csv) para su uso posterior.

### Instrucciones para graficar los datos
Corre en Python 2.7 o 3.x

Paquetes Python requeridos: `datetime`, `matplotlib`, `numpy`, `sys`

1. Asegúrese de que el programa de registro en serie (LightSound2_data_plotter.py) esté ubicado en la carpeta donde guardará sus datos.
2. En la terminal (Mac/Linux) o en la línea de comandos (Windows), navegue hasta la carpeta de datos y escriba: `python LightSound2_data_plotter.py filename plot_lines savename.png`
    - `filename` es el nombre completo del archivo de datos (debe terminar con \_raw.log o \_data.csv) 
    - `filename` (nombre-archivo) es el prefijo del nombre del archivo de registro para los datos (la extensión debe ser la misma que la utilizada para el registro de datos)
    - `plot_lines` determina si la gráfica incluirá  ganancia o tiempo de integración
        - Para  graficar solo los valores de lux (intensidad), reemplace `plot_lines` con `0`
        - Para  graficar los tiempos de lux, ganancia e integración, reemplace `plot_lines` con `1`
    - `savename` es el prefijo del nombre del archivo en que se guardará el gráfico; no use ninguno si no desea guardar la imagen (la extensión es típicamente .png)
