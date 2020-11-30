## Brayan Mauricio Vega Ortega - B47519
## IE0405 - Modelos Probabilísticos de Señales y Sistemas
### Proyecto 4

Para la solución de este proyecto se divide en tres partes de acuerdo a lo solicitado.
La primera parte se compone de una simulación del sistema de comunicación utilizando una modulación QPSK, para enviar y recibir una imagen determinada. Como primer paso se implementan las funciones que fueron definidas en las secciones anteriores de este proyecto y fueron estas:
 1. fuente_info(imagen), encargada de "leer" la imagen y retorna un vector de pixeles para el caso de una imagen en formato JPG
 2. rgb_a_bit(vector_pixel), convierte los pixeles de base decimal (de 0 a 255) a binaria (de 00000000 a 11111111)
 3. modulador(bits_Rx, FS, MPP), se utiliza la función que simula el esquema de       
    modulación BPSK como base, pero se realizan los ajustes necesarios para la implementación de la modulación QPSK:
    - En el apartado #2 Construyendo un periodo de la señal portadora, se agrega un if para seleccionar el caso donde si x == 1 seleccione una de las dos                    portadoras que corresponden para la modulación por QPSK.
 4. canal_ruidoso(senal_Tx, Pm, SNR): Simula un canala ruidoso con AWGN para senal_Tx.
 5. demodulador(senal_Rx, carrier, MPP): Demodula a senal_Rx (señal recibida) y determina los bits recibidos usando el criterio de demodulación por detección de energía.
 6. bits_a_rgb(bits_Rx, dims): Reconstruye los bits recibidos en bits_Rx en una imagen.
    
Posteriormente, se sigue con la definición de parametros a emplear, tal como se muestra en el código, e implementar la medición de tiempo que dilata la simulación, en la línea de código donde se comenta #3 Modular la cadena de bits usando el esquema QPSK, se establecen las dos cadenas que utiliza la modulación QPSK, además de definir a la potencia promedio de la señal modulada como la suma de la potencia Pm1 de la primera portadora y Pm2 de la segunda portadora. Lo mismo se realiza para el caso de la variable senal_Tx, que se compone de la suma de la señal de las dos secuencias, lo mismo se realiza con las variables portadora y moduladora. Después, se realiza el llamado de las funciones antes mencionadas. Además de realizar el cálculo y mostrar el tiempo que duró la simulación, así como el número de errores de la simulación. En las últimas secciones de esta primera parte se muestra el código empleado para que se muestren la figura usada como referencia y la obtenida al final de la simulación, además de mostrar el comportamiento de las variables moduladora, senal_Tx, senal_Rx y senal_demodulada.

Dentro de la segunda sección del proyecto se llevan a cabo las puebas de estacionaridad y ergodicidad a la señal modulada denotada senal_Tx. Se inicia con la creación del vector de tiempo, denotado t_muestreo, se asigna el rango de valor para A1 y A2, que va de -1 a 1 contenido en A, se hacen las formas de ondas posible, ligada a las 4 funciones del tiempo x(t). Empleando un buble que recorra A, definiendo los posibles comportamiento de las funciones en x1 y x2, para luego ser almacendas en la matriz x_t. Determinando el promedio de las 4 funciones para cada instante representado por t y obtener el resultado teórico del valor esperado, ambos son representados mediante una gráfica.

Analizando al gráfica generada para esta segunda sección, podemos determinar que en la señal modulada senal_Tx presenta ergodicidad, esto debido a que el promedio mostrado para las funciones comparte el mismo valor que el teórico esperado.

Para la tercera y última sección, se requiere determinar la densidad espectral de potenciia para la señal modulada llamada senal_Tx. Para ello se emplea scipy importando especificamente fft que representa la transformada de Fourier, tomando la señal modulada y aplicando la transformadad de Fourier. Determinando la cantidad de elementos que componen la señal modulada, para se empleado en obtener el número de símbolos presentes. El tiempo de la simulación para este caso se obtiene mediante la multipliación del número de símbolos por el periodo de la portadora. Todo este proceso se ve representado en la grafica que se muestra al simular el código utilizado.


