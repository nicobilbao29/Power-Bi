Proyecto Bi  Cuentas por Cobrar en Power BI

🔄 Procedimientos a Realizar Paso a Paso

Cargar la fuente de datos
Se utiliza como fuente un archivo de Excel llamado "Cuentas por Cobrar", específicamente la tabla llamada DATA, la cual se carga en Power BI.

Importar imagen de fondo
Se importa una imagen para usarla como fondo del Dashboard, mejorando la presentación visual del informe.

Crear la tabla de calendario (CalendarAuto)
Se crea una tabla calendario usando la función CALENDARAUTO() y se establece una relación con el campo de fecha en la tabla DATA.

Esto permite establecer un modelo de datos más robusto, ya que aunque la tabla DATA pueda tener fechas repetidas, la tabla calendario proporciona fechas únicas para análisis.

Crear columnas calculadas y medidas
Se crean nuevas columnas calculadas dentro de la tabla DATA, además de medidas DAX que permitirán realizar análisis específicos sobre las cuentas por cobrar.

   ![Cuentas x Pagar ](https://github.com/user-attachments/assets/f6b413ba-3287-4360-aabe-78597e3c0c30)
 

   
Tipo Saldo = IF(Data[Fecha Vencimiento] <= TODAY(); "Saldo Vencido"; "Por Vencer") 
Dias Transcurridos = DATEDIFF(Data[Fecha Factura]; Data[Fecha Vencimiento]; DAY) 


      MEDIDAS : 
Núm.Fact.Por.Vencer = CALCULATE([Núm.Facturas]; Data[Tipo Saldo] = "Por Vencer") 
Núm.Fact.Vencidas = CALCULATE([Núm.Facturas]; Data[Tipo Saldo] = "Saldo Vencido") 
Núm.Facturas = COUNTROWS(Data)

Data cargada en Power bi 

![Datajpg](https://github.com/user-attachments/assets/2d1c69b2-7aca-4592-b811-e41b23475a84)



![Power Query](https://github.com/user-attachments/assets/ac8f7fc4-32a6-4f06-b496-3c02a4a5f70b)
Con Powery Puedo realizar las trasnformaciones como las siguientes :  
borrar datos Nulos 
agregar columnas condicionales 
Reemplazar valores (por ejemplo, cambiar “N/A” por 0) 
Dividir columnas por delimitadores o posiciones fijas
Combinar columnas en una sola (concatenación)
Quitar espacios en blanco (inicio, final o ambos)
 es Impactante lo secillo que hace esto Power Query , en un excel tomaria tiempo a demas que necesitas de muchas funciones
