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
