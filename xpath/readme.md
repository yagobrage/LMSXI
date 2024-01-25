EJERCICIO 1
      
    • Nombre del propietario de la agenda.
      	//agenda//propietario//nombre
    •  Teléfono de casa del propietario.
      	//agenda//propietario//telefonos//casa
    •  Nombres y apellidos de los contactos de la agenda.
      	//agenda//contactos//persona//identificadores
    •  Nombre e identificador de cada contacto.
      	//agenda//contactos//persona//@id
    •  Datos del contacto con identificador p02.
      	//agenda//contactos//persona//identificadores//nombre
    •  Identificadores de los contactos que tienen móvil.
      	//agenda//contactos//persona[telefonos/movil]/@id




EJERCICIO 2
1. Nombre del instituto.  
	//ies//nombre
2. Página web del instituto. 
	//ies//web
3. Nombre de los ciclos formativos. 
	//ies//ciclos//nombre
4. Siglas por las que se conocen los ciclos formativos.
	//ies//ciclo//@id
5. Años en los que se publicaron los decretos de título de los ciclos formativos.
	//ies//ciclo//decretoTitulo//@año
6. Ciclos formativos de Grado Medio (se trata de obtener el elemento completo).
	//ies/ciclos/ciclo[grado = 'Medio']
7. Nombre de los ciclos formativos de Grado Superior. 
       //ies//ciclos//ciclo[grado = 'Superior']//nombre
8. Nombre de los ciclos formativos anteriores a 2010.
       //ies/ciclos/ciclo[decretoTitulo/@año < 2010]/nombre
9. Nombre de los ciclos formativos de 2008 o 2010.
	//ies/ciclos/ciclo[decretoTitulo/@año 2008 | 2010]/nombre

















EJERCICIO 3 
1. Extraer todos los elementos <peso> (etiqueta incluida).
	//inventario/producto/peso
2. Extraer las cantidades de todos los elementos <peso> (sin la etiqueta <peso>).
	//inventario/producto/peso/text()
3. Extraer el peso del último elemento.
	//inventario/producto[@codigo='DEZ-138']/peso/text()
4. Extraer las distintas unidades en las que se han almacenado los pesos.
	//inventario/producto/peso/@unidad
5. Extraer el penúltimo codigo.
	//inventario/producto[nombre='Monitor']/@codigo
6. Extraer el peso del elemento cuyo codigo sea AAA-111.
	//inventario/producto[@codigo='AAA-111']/peso
7. Extraer el nombre de los productos que hayan puesto el peso en gramos.
	//inventario/producto[peso[@unidad='g']]/nombre
8. Extraer el codigo de los productos cuyo nombre sea Monitor.
	//inventario/producto[nombre='Monitor']/@codigo



Dia 1 ultimo ejercicio
1 Nombre de los módulos que se imparten en el instituto.
	//ies//modulos//nombre
2. Nombre de los módulos del ciclo ASIR.
	//ies/modulos/modulo[ciclo[text()="ASIR"]]/nombre
3. Nombre de los módulos que se imparten en el segundo curso de cualquier ciclo.
	//ies/modulos/modulo[curso[text()="2"]]/nombre
4. Nombre de los módulos de menos de 5 horas semanales.
  	//ies/modulos/modulo[horasSemanales<5]/nombre
5. Nombre de los módulos que se imparten en el primer curso de ASIR.
         //ies/modulos/modulo[curso[text()="2"]][ciclo[text()="ASIR"]]/nombre
6. Horas semanales de los módulos de más de 3 horas semanales.
        /ies/modulos/modulo[horasSemanales>3]/nombre




Dia 2 ejercicio

1. Nombre de la universidad.
	//universidad/nombre
2. Pais de la universidad.
	//universidad/pais
3. Nombres de las carreras.
	//universidad/carreras/carrera/nombre
4. Años de plan de estudio de las carreras.
	//universidad/carreras/carrera/plan
5. Nombres de todos los alumnos.
	//universidad/alumnos/alumno/nombre
6. Identificadores de todas las carreras.
	//universidad/carreras/carrera/@id
7. Datos de la carrera cuyo id es c01.
	//universidad/carreras/carrera[@id="c01"]
8. Centro en que se estudia de la carrera cuyo id es c02.
	//universidad/carreras/carrera[@id="c02"]/centro
9. Nombre de las carreras que tengan subdirector.
	//universidad/carreras/carrera[subdirector]/nombre
10. Nombre de los alumnos que estén haciendo proyecto.
        //universidad/alumnos/alumno/estudios[proyecto]/../nombre
11. Códigos de las carreras en las que hay algún alumno matriculado.
	//universidad/alumnos/alumno/estudios/carrera/@codigo
12. Apellidos y nombre de los alumnos con beca.
	//universidad/alumnos/alumno[@beca="si"]/apellido1 | //universidad/alumnos/alumno[@beca="si"]/apellido2 | //universidad/alumnos/alumno[@beca="si"]/nombre
13. Nombre de las asignaturas de la titulación c04.
	//universidad/asignaturas/asignatura[@titulacion="c04"]/nombre
14. Nombre de las asignaturas de segundo trimestre.
	//universidad/asignaturas/asignatura[trimestre[text()="2"]]/nombre
15. Nombre de las asignaturas que no tienen 4 créditos teóricos.
	//universidad/asignaturas/asignatura[creditos_teoricos!=4]/nombre
16. Código de la carrera que estudia el último alumno.
	//universidad/alumnos/alumno[@id="e04"]/estudios/carrera/@codigo
17. Código de las asignaturas que estudian mujeres.
	//universidad/alumnos/alumno[sexo[text()="Mujer"]]/estudios/asignaturas/asignatura/@codigo
18. Nombre de los alumnos que están matriculados en la asignatura a02.
	//universidad/alumnos/alumno[estudios/asignaturas/asignatura[@codigo="a02"]]/nombre
19. Códigos de las carreras que estudian los alumnos matriculados en alguna asignatura.
	//universidad/alumnos/alumno[estudios/asignaturas/asignatura]/estudios/carrera/@codigo
20. Apellidos de todos los hombres.
	//universidad/alumnos/alumno[sexo[text()="Hombre"]]/apellido1 | //universidad/alumnos/alumno[sexo[text()="Hombre"]]/apellido2
21. Nombre de la carrera que estudia Víctor Manuel.
        //universidad/alumnos/alumno[nombre[text()="Víctor Manuel"]]/estudios/carrera/nombre (no funciona)
22. Nombre de las asignaturas que estudia Luisa.
  	//universidad/alumnos/alumno[nombre[text()="Luisa"]]/estudios/asignaturas/asignatura/nombre
23. Primer apellido de los alumnos matriculados en Ingeniería del Software.
	//universidad/alumnos/alumno[estudios/asignaturas/asignatura[nombre="Ingeniería del Software"]]/apellido1
24. Nombre de las carreras que estudian los alumnos matriculados en la asignatura Tecnología de los Alimentos.
	//universidad/alumnos/alumno[estudios/asignaturas/asignatura[nombre="Tecnología de los Alimentos"]]/estudios/carrera/nombre
25. Nombre de los alumnos matriculados en carreras que no tienen subdirector.
	//universidad/alumnos/alumno[not(estudios/carrera[subdirector])]/nombre
26. Nombre de las alumnos matriculados en asignaturas con 0 créditos prácticos y que estudien la carrera de I.T. Informática.
	//universidad/alumnos/alumno[estudios/carrera[nombre="I.T. Informática"] and estudios/asignaturas/asignatura[creditos_practicos=0]]/nombre
27. Nombre de los alumnos que estudian carreras cuyos planes son anteriores a 2002.
	//universidad/alumnos/alumno[estudios/carrera[plan < 2002]]/nombre

Primer ejercicio dia 2
1. Extraer la cantidad depositada en el fondo con cuenta asociada 20-A.
	//listado/fondo[cuentaasociada[text()="20-A"]]/datos/cantidaddepositada

2. Extraer un listado sin etiquetas de todas las monedas usadas por los distintos fondos.
	//listado/fondo/datos/moneda/text()

3. Extraer el DNI de las cuentas que usen dólares como moneda de base.
        //listado/cuenta[saldoactual/@moneda = "euros"]/titular/@dni

4. Extraer toda la información de los fondos que usen Euros por un valor inferior a 2500.
	//listado/fondo[datos/moneda = "Euros" and datos/cantidaddepositada < 2500]
