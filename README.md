# ScoposDraw
Grbl ScoposDraw

 ScoposDraw está basado en  el Gbrl1.1f.
 
  La versión a fecha Enero 2020 es la 1.1 f y permite usar el spindle como servo, pero no permite usar a la vez el spindle y el servo en un equipo tipo Axidraw, para manejar la potencia del láser o para grabados con Spindle.
  
  Para conseguir ampliar las opciones del ScoposDraw y poder trabajar con el spindle o el láser en control de potencia, al tiempo que usar el Servo para mover el lápiz, y la fresa con el servo, hay que modificar el hardware y el software open-source.
  
   Para poder mover el servo sin perjudicar el uso del spindle, este código usa el pin 3 (Acoplado al Timer 2) como segundo servo del Timer 2.
   
   Por lo tanto, el Pin 11 se programará como sindle_variable como hasta ahora, pero debemos liberar el pin 3 para usarlo como servo.
   
   En config, en vez de  Spindle_as_Servo, existe la variable Y_as_Servo, para indicar que se usará el eje Y como servo y que por lo tanto no existirán 3 ejes.
   
   Si activamos la etiqueta  Y_as_Servo, el zócalo del eje Z pasará a ser usado para el eje Y.
       Por lo que dispondremos de Y_step y Dir_Step para otros usos.
    
   Como para el ScoposDraw, solo se necesitan dos ejes, se usarán los zócalos del X y Z en vez de X e Y. Siendo Z en realidad Y.       Para que funciones el nuevo servo, habrá que crear una nueva opción para darle posición
   
    
    Para ello se ha creado un comando GCode nuevo, el “V”. De manera que V100 ponga el servo a 100
    
    El comando GCode “S” seguirá usándose para controlar la velocidad del spindle o la potencia del láser.
