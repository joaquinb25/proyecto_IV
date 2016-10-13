##**Ejercicios tema 1: Introducción a la infraestructura virtual: concepto y soporte físico**

###Joaquin Ballesteros Ortega

####**EJERCICIO 1**

**Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años**

Voy a realizar los calculos sobre: 

![im1](https://github.com/joaquinb25/proyecto_IV/blob/hito1/imagenes1/1.png)

http://www.macnificos.com/comprar-qnap-tvs-871t-i7-16g-thunderbolt-2-mac-pc/sistemas-nas-disco-almacenamiento?gclid=Cj0KEQjwvve_BRDmg9Kt9ufO15EBEiQAKoc6qncgxuf0BIakMbv6i2Q5LOmh3VTGKflxwoOoF9uw5nQaAtBS8P8HAQ

Veamos ahora su amortizacion a los 4 años, para ello, debemos amortizar cada año un 25%:

3.019,99€ × 0,25 = 754,99€ por año.

Amortización a los 7 años: 

Primer año : 3.019,99€ × 0,25 = 754,99€
Segundo año : 3.019,99€ × 0,25 = 754,99€
Tercer y cuarto año : 3.019,99€ * 0.15 = 452,99€
Quinto año : 3.019,99€ * 0.10 = 301,99€
Sexto y séptimo año : 3.019,99€ * 0.05 = 150,995€


####**EJERCICIO 2**

**Usando las tablas de precios de servicios de alojamiento en Internet y de 
proveedores de servicios en la nube, Comparar el coste durante un año de un 
ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo 
de procesador en los dos vendedores) y con el resto de las características 
similares (tamaño de disco duro equivalente a transferencia de disco duro)
 en el caso de que la infraestructura comprada se usa sólo el 1% o el 10% del
 tiempo**

Servidor dedicado: 

![im2](https://github.com/joaquinb25/proyecto_IV/blob/hito1/imagenes1/xl8%20foto.png)



Servidor cloud:


![im3](https://github.com/joaquinb25/proyecto_IV/blob/hito1/imagenes1/cloud%20img.png)


Uso de 1%:

-Servidor dedicado: 119,99 euros/mes * 12 meses = 1439,88 euros/año. 
-Servidor cloud: 150 €/mes * 12 meses * 0.01 = 18 euros/mes.

Uso de 10%:

-Servidor dedicado: 119,99 euros/mes * 12 meses = 1439,88 euros/año.
 -Servidor cloud: 208,80 €/mes * 12 meses * 0.10 = 180 euros/mes.


####**EJERCICIO 3**

**¿Qué tipo de virtualización usarías en cada caso?** 


Para poder disponer de diferentes sistemas operativos usaría una virtualización plena que permite ejecutar cada sistema operativo en su máquina virtual correspondiente.

Si quisiera usar una aplicación en un sistema operativo diferente, usaría una virtualización de aplicaciones como WINE.

Para los programas escritos en Python donde se requieren diferentes 
versiones de librerías, usaría una virtualización de entorno de desarollo.


####**EJERCICIO 4**

**Comprobar si el procesador o procesadores instalados tienen estos flags. 
¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden?**

Mediante el comando egrep '^flags.*(vmx|svm)' /proc/cpuinfo comprobamos que el flag vmx está activado:

root@joaquinballesteros:/home/joaquinballesteros# egrep '^flags.*(vmx|svm)' /proc/cpuinfo

flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 
clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm 
constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf 
eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid
 sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb
 tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts

Flag vmx activado, por tanto es posible la virtualización.

Con el comando cat /proc/cpuinfo vemos el modelo de procesador de mi pc:

Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz


####**EJERCICIO 5**

**1.Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok. **
**2.Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios.**

1.1

Primero instalamos el paquete cpu-checker: *sudo apt-get install cpu-checker* y despues introducimos el comando *kvm-ok* y la respuesta es:

root@joaquinballesteros:/home/joaquinballesteros# kvm-ok INFO: /dev/kvm exists KVM acceleration can be used 

Por tanto puedo usar la aceleración por hardware del procesador.

1.2

Tengo instalado virtualbox y vagrant.
