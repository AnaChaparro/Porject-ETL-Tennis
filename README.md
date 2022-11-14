
# Project ETL Tennis 🎾

https://github.com/AnaChaparro/Porject-ETL-Tennis/blob/main/im%C3%A1genes/moises-alex-WqI-PbYugn4-unsplash.jpg

Se trata de un proyecto de ETL que se va a basar en el tennis profesional masculino, centrándose en los torneos jugados durante la temporada de 2021. Los pasos seguidos para la obtención, transformación y carga en una base de datos son los expesados a continuación.

## 1. Extracción de datos.

El proceso de extracción se ha basado en dos métodos, el primero se ha obtenido un archivo csv descargádolo directamente desde la web de kaggle. El archivo contiene información sobre todos los torneos profesionales jugados desde 2018 hasta febrero de 2022. El otro método utilizado ha sido el scraping, usando la herramienta de Selenium, se han obtenido tres tablas, dos de ellas de la página web de la ATP estadísticas y otra de la página web de la ESPN.

Por estos dos métodos obtenemos finalmente la tabla de torneos, la tabla de efectividad al saque, efectividad al resto y la tabla del ranking ATP, todo ello del año 2021.

## 2. Transformación de los datos.

Una vez se han obtenido estos csv, se exportan a cuatro Data Frame para ser limpiados.

En primer lugar se unifican datos y se elimina algún valor nulos que pueda aparecer en las tablas. Se establecen las variables a estudiar y que columnas debemos conservar de cada tabla.

El número de jugadores de las tablas se reduce a 84 en las tablas de saque, resto y ranking, y en función de esos jugadores comunes en las tres tablas nos quedaremos con los torneos de 2021 en los que hayan intervenido éstos, bien sea quedando como ganadores o perdedores.


Una vez verificamos que los datos son sólidos y se decide concatenar las tablas de saque, resto y ranking, las cuales tienen el elemento jugador en común para poder establcer una base de datos en la que las tablas de jugadores y torneos puedan relacionarse de manera correcta.

## 3. Carga en una base de datos.

Una vez tenemos los dos archivos limpios, se procede a la carga en una base de datos utilizando SQL. Se relacionan las tablas de manera que en la tabla de jugadores la PK serán los mismos, conviertiéndose y relacionándose con la tabla de torneos a través de winner y loser de cada partido.

El diagrama EER quedaría de la siguiente forma:


## 4. Comprobación de la solidez de la base datos.

Una vez se ha construido la base de datos, se pueden realizar diversos estudios en función de los parámetros definidos en cada tabla. 

Mediante la BD creada se pueden realizar querys para el estudio de diferentes parámetros. En este caso se ha obtenido información sobre la relación que tienen las efectividades en resto y saque con los partidos ganados, el promedio de aces (saques directos) que se realizan en partidos ganados y perdidos de los torneos con categoría Grand Slam, donde se verifica que no es un determinante a la hora de ganar o perder un partido, es decir la correlación en baja, y verificar que tanto el porcentaje de torneos que se juegan la mayor parte son en pista dura, frente una proporción menos en tierra batida y hierba, teniendo en cuenta los partidos jugados en cada tipo de pista por los tres mejores jugadores del ranking ATP.




