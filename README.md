Proyecto Análisis Cuentas Por Cobrar en Power BI
Procedimientos a Realizar Paso a Paso
1. El archivo fuente es de Excel, llamado Cuentas por Cobrar.
2. Cargo la fuente de datos para el este caso es un Excel la tabla DATA a Power BI.
3. Importo la imagen de fondo, para usar como fondo del Daschoard
4. Creo la tabla Calendario (CalendarAuto) y la vincularlo con el campo de la tabla DATA
al Crear la tabla Calendario ya se esta creando un Modelo de datos, la tabla data pueden haber fecha repetidas
pero como tengo mi tabla calendario ,esta me permite decir que la fecha es unica 
8. creo las siguientes  columnas calculadas y  medidas : 

   Columnas Calculadas en la tabla DATA.![Power Query](https://github.com/user-attachments/assets/dfc61272-a1a4-4916-a512-2f9870222968)

   
Tipo Saldo = IF(Data[Fecha Vencimiento] <= TODAY(); "Saldo Vencido"; "Por Vencer") 
Dias Transcurridos = DATEDIFF(Data[Fecha Factura]; Data[Fecha Vencimiento]; DAY) 
Rango Dias = IF(Data[Dias Transcurridos]<=14; "0-14";
                IF(Data[Dias Transcurridos]<=30; "15-30";
                IF(Data[Dias Transcurridos]<=60; "31-60";
                IF(Data[Dias Transcurridos]<=90; "61-90";
                IF(Data[Dias Transcurridos]<=120; "91-120"; "+120"))))) 

Orden = IF(Data[Dias Transcurridos]<=14; 1;
            IF(Data[Dias Transcurridos]<=30; 2;
            IF(Data[Dias Transcurridos]<=60; 3;
            IF(Data[Dias Transcurridos]<=90; 4;
            IF(Data[Dias Transcurridos]<=120; 5; 6))))) 

      MEDIDAS : 
Núm.Fact.Por.Vencer = CALCULATE([Núm.Facturas]; Data[Tipo Saldo] = "Por Vencer") 
Núm.Fact.Vencidas = CALCULATE([Núm.Facturas]; Data[Tipo Saldo] = "Saldo Vencido") 
Núm.Facturas = COUNTROWS(Data)

![Cuentas x Pagar ](https://github.com/user-attachments/assets/f6b413ba-3287-4360-aabe-78597e3c0c30)
![Datajpg](https://github.com/user-attachments/assets/2d1c69b2-7aca-4592-b811-e41b23475a84)

Con Powery Puedo realizar las trasnformaciones como las siguientes :  
borrar datos Nulos 
agregar columnas condicionales 
Reemplazar valores (por ejemplo, cambiar “N/A” por 0) 
Dividir columnas por delimitadores o posiciones fijas
Combinar columnas en una sola (concatenación)
Quitar espacios en blanco (inicio, final o ambos)
 es Impactante lo secillo que hace esto Power Query , en un excel tomaria tiempo a demas que necesitas de muchas funciones

![Power Query](https://github.com/user-attachments/assets/ac8f7fc4-32a6-4f06-b496-3c02a4a5f70b)
