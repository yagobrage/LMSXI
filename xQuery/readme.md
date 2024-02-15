Escribe las consultas XQuery que permitan obtener la siguiente información:
1. Título y editorial de todos los libros.
* Los datos de cada libro deben estar dentro de un elemento <libro>.
* El título y la editorial de cada libro deben estar separados por un guión medio (-).

<libros>
{
  for $libro in //libro
  return
    <libro>
      <titulo>{data($libro/titulo)}</titulo>
      <editorial>{data($libro/editorial)}</editorial>
    </libro>
}
</libros>


2. El título de todos los libros de menos de 400 páginas.
* Se debe obtener únicamente los datos, sin etiquetas.

for $libro in //libro[paginas < 400]
return data($libro/titulo)


3. La cantidad de libros de más de 400 páginas.

count(//libro[paginas > 400])


4. Una lista HTML con el título de los libros de la editorial O'Reilly Media ordenados por título.
<ul>
{
  for $libro in //libro[editorial = 'O''Reilly Media']
  order by $libro/titulo
  return
    <li>{data($libro/titulo)}</li>
}
</ul>


5. Título y editorial de los libros de 2018 y 2019.
* Los datos de cada libro deben estar dentro de un elemento <libro>.
* El título y la editorial deben ir dentro de los elementos <titulo> y <editorial> respectivamente.

<libros>
{
  for $libro in //libro[(@publicacion = 2018) or (@publicacion = 2019)]
  return
    <libro>
      <titulo>{data($libro/titulo)}</titulo>
      <editorial>{data($libro/editorial)}</editorial>
    </libro>
}
</libros>

6. Título y editorial de los libros con más de un autor.
* Los datos de cada libro deben estar dentro de un elemento <libro>.
* El título y la editorial deben ir dentro de los elementos <titulo> y <editorial> respectivamente.
 <libros>
{
  for $libro in //libro[count(autor) > 1]
  return
    <libro>
      <titulo>{data($libro/titulo)}</titulo>
      <editorial>{data($libro/editorial)}</editorial>
    </libro>
}
</libros>


7. Título y año de publicación de los libros que tienen versión electrónica.
* Los datos de cada libro deben estar dentro de un elemento <libro>.
* El título y el año de publicación deben ir dentro de los elementos <titulo> y <fecha-publicacion> respectivamente.

<libros>
{
  for $libro in //libro[edicionElectronica]
  return
    <libro>
      <titulo>{data($libro/titulo)}</titulo>
      <fecha-publicacion>{data($libro/@publicacion)}</fecha-publicacion>
    </libro>
}
</libros>

8. Título de los libros que no tienen versión electrónica.
* Se debe obtener únicamente los datos, sin etiquetas.

for $libro in //libro[not(edicionElectronica)]
return data($libro/titulo)














Escribe las consultas XQuery que permitan obtener la siguiente información:
1. Una lista que contiene, para cada receta, el elemento <titulo> de la receta y un elemento <calorias> que contenga el número de calorías.

for $receta in //receta
return <receta>
         <titulo>{$receta/titulo/text()}</titulo>
         <calorias>{$receta/nutricion/@caloria}</calorias>
       </receta>

2. Una lista similar a la primera, ordenada según las calorías.
for $receta in //receta
order by $receta/nutricion/@caloria
return <receta>
         <titulo>{$receta/titulo/text()}</titulo>
         <calorias>{$receta/nutricion/@caloria}</calorias>
       </receta>


3. Una lista similar a la primera, ordenada alfabéticamente según el título.
for $receta in //receta
order by $receta/titulo/text()
return <receta>
         <titulo>{$receta/titulo/text()}</titulo>
         <calorias>{$receta/nutricion/@caloria}</calorias>
       </receta>


4. Una lista similar a la primera, ordenada según el contenido de grasa.

for $receta in //receta
order by $receta/nutricion/@grasa
return <receta>
         <titulo>{$receta/titulo/text()}</titulo>
         <calorias>{$receta/nutricion/@caloria}</calorias>
       </receta>

5. Una lista similar a la primera, con el título como atributo y las calorías como contenido.
for $receta in //receta
return <receta titulo="{$receta/titulo/text()}">
         {$receta/nutricion/@caloria}
       </receta>


6. Una lista que contenga para cada receta, el título como atributo y cada uno de los ingredientes de nivel superior (sin añadir los ingredientes que están dentro de otros ingredientes).
for $receta in //receta
return <receta titulo="{$receta/titulo/text()}">
         {for $ingrediente in $receta/ingrediente
          return <ingrediente nombre="{$ingrediente/@nombre}" cantidad="{$ingrediente/@cantidad}" unidad="{$ingrediente/@unidad}"/>}
       </receta>


7. Una lista con cada una de las recetas que contengan el ingrediente harina. Poner el título de la receta como atributo del elemento receta.
for $receta in //receta[descendant::ingrediente/@nombre = 'harina']
return <receta titulo="{$receta/titulo/text()}"/>


8. Una lista de todas aquellas recetas que tengan un ingrediente llamado relleno y este contenga en su interior más de 5 elementos ingrediente. 
* La lista resultante estará formada por elementos receta que contienen un atributo titulo con el valor del elemento titulo de la receta. 
* Además, dentro de cada elemento receta habrá elementos ingrediente con el nombre de cada uno de los ingredientes.

for $receta in //receta[ingrediente[@nombre = 'relleno' and count(ingrediente) > 5]]
return <receta titulo="{$receta/titulo/text()}">
         {for $ingrediente in $receta/ingrediente[@nombre = 'relleno']
          return <ingrediente nombre="{$ingrediente/ingrediente/@nombre}" cantidad="{$ingrediente/ingrediente/@cantidad}" unidad="{$ingrediente/ingrediente/@unidad}"/>}
       </receta>


















Escribe las consultas XQuery que permitan obtener la siguiente información:
1. cada uno de los nombres de las categorias con la etiqueta "categoria".

for $categoria in distinct-values(//categoria)
return <categoria>{$categoria}</categoria>


2. los titulos de los tutoriales con el número de visitas entre paréntesis, ambos dentro de la misma etiqueta "lostutoriales".
<lostutoriales>
{
  for $tutorial in //tutorial
  return <titulo>{$tutorial/titulo} ({data($tutorial/visitas)})</titulo>
}
</lostutoriales>


3. los nombres de los tutoriales con menos de 2000 visitas
for $tutorial in //tutorial
where $tutorial/visitas < 2000
return $tutorial/titulo/text()


4. los nombres de los tutoriales de XML con más de 30.000 visitas

for $tutorial in //tutorial[categoria = 'XML' and visitas > 30000]
return $tutorial/titulo/text()

5. el número total de visitas

sum(//visitas)


6. los nombres de las categorías distintas, cada una en una etiqueta <categoriadistintas>
<categoriastrdistintas>
{
  for $categoria in distinct-values(//categoria)
  return <categoriadistintas>{$categoria}</categoriadistintas>
}
</categoriastrdistintas>


7. nombres y apellidos de los autores eliminando los repetidos y acompañar cada nombre con todos sus tutoriales, ordenados alfabeticametne por nombre de autor; cada autor en una etiqueta <autor> que contendrá una etiqueta <nombreyapellidos> y una etiqueta <titulo>.
<autores>
{
  for $autor in distinct-values(//autor/nombre)
  let $tutoriales := //tutorial[autor/nombre = $autor]
  order by $autor
  return <autor>
           <nombreyapellidos>{$autor} {distinct-values($tutoriales/autor/apellidos)}</nombreyapellidos>
           {for $titulo in $tutoriales/titulo order by $titulo return <titulo>{$titulo}</titulo>}
         </autor>
}
</autores>


8. la media de vistas de los tutoriales, dentro de una etiqueta <media>.
<media>
{
  avg(//visitas)
}
</media>


9. cuantos tutoriales de XML hay, dentro de una etiqueta <totaltutoriales>.
<totaltutoriales>
{
  count(//tutorial[categoria = 'XML'])
}
</totaltutoriales>


10. el nombre del tutorial y su categoría, ordenado por el nombre de cada categoría
string-join(
  for $categoria in distinct-values(//categoria) order by $categoria
  return (
    $categoria,
    for $tutorial in //tutorial[categoria = $categoria] order by $tutorial/titulo
    return concat($tutorial/titulo, ' - ', $tutorial/categoria)
  ),
  '\n'
)


11. todos los datos de cada tutorial excepto las visitas.
for $tutorial in //tutorial
return <tutorial>
         {for $node in $tutorial/* except $tutorial/visitas
          return $node}
       </tutorial>


12. En una tabla de HTML de dos columnas, el título de los tutoriales y los nombres de los autores.

<html>
  <body>
    <table border="1" cellpadding="8">
      <tr>
        <th>Título del Tutorial</th>
        <th>Nombres de los Autores</th>
      </tr>
      {
        for $tutorial in //tutorial
        return
          <tr>
            <td>{$tutorial/titulo}</td>
            <td>{string-join(distinct-values($tutorial/autor/nombre), ', ')}</td>
          </tr>
      }
    </table>
  </body>
</html>
