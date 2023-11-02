**Transformaciones**:
1. **`map`**: Aplica una función a cada elemento del RDD y crea un nuevo RDD con los resultados. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   result_rdd = rdd.map(lambda x: x * 2)
   ```

2. **`filter`**: Crea un nuevo RDD que contiene solo los elementos que satisfacen una condición dada. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   result_rdd = rdd.filter(lambda x: x % 2 == 0)
   ```

3. **`reduceByKey`**: Realiza una reducción por clave en un RDD de pares clave-valor. Por ejemplo:
   ```python
   rdd = sc.parallelize([(1, 2), (2, 3), (1, 4)])
   result_rdd = rdd.reduceByKey(lambda x, y: x + y)
   ```

4. **`flatMap`**: Similar a `map`, pero puede generar múltiples valores de salida para cada entrada. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3])
   result_rdd = rdd.flatMap(lambda x: (x, x * 2))
   ```

5. **`distinct`**: Elimina duplicados de un RDD y retorna un nuevo RDD con elementos únicos. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 2, 3, 3, 4, 4, 5])
   unique_rdd = rdd.distinct()
   ```

6. **`sortBy`**: Ordena los elementos del RDD en función de una clave dada. Por ejemplo, para ordenar en orden ascendente:
   ```python
   rdd = sc.parallelize([3, 1, 4, 2, 5])
   sorted_rdd = rdd.sortBy(lambda x: x)
   ```

7. **`groupByKey`**: Agrupa elementos por clave en un RDD de pares clave-valor y retorna un RDD de claves y listas de valores. Por ejemplo:
   ```python
   rdd = sc.parallelize([(1, 'A'), (2, 'B'), (1, 'C')])
   grouped_rdd = rdd.groupByKey()
   ```

8. **`union`**: Combina dos RDD en uno solo. Por ejemplo, para combinar dos RDD con los mismos tipos de elementos:
   ```python
   rdd1 = sc.parallelize([1, 2, 3])
   rdd2 = sc.parallelize([4, 5, 6])
   combined_rdd = rdd1.union(rdd2)
   ```


**Acciones**:
1. **`count`**: Retorna el número de elementos en el RDD. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   count = rdd.count()
   ```

2. **`collect`**: Retorna todos los elementos del RDD como una lista en el programa principal. Útil para recuperar los resultados a nivel local. Ten en cuenta que si el RDD es grande, esto puede consumir mucha memoria en el programa principal.
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   collected_data = rdd.collect()
   ```

3. **`reduce`**: Realiza una operación de reducción en el RDD. Por ejemplo, puedes usar `reduce` para calcular la suma de elementos en el RDD.
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   sum = rdd.reduce(lambda x, y: x + y)
   ```

4. **`first`**: Retorna el primer elemento del RDD.
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   first_element = rdd.first()
   ```

5. **`take`**: Retorna los primeros N elementos del RDD como una lista. Útil cuando no necesitas todo el RDD. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   first_three_elements = rdd.take(3)
   ```

6. **`foreach`**: Ejecuta una función en cada elemento del RDD. Puede ser útil para realizar operaciones personalizadas en los elementos. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   rdd.foreach(lambda x: print(x))
   ```

7. **`countByValue`**: Cuenta la cantidad de veces que aparece cada valor único en el RDD. Retorna un diccionario con los valores y sus frecuencias. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 2, 3, 3, 4, 4, 5])
   value_counts = rdd.countByValue()
   ```

8. **`saveAsTextFile`**: Guarda el contenido del RDD en un archivo de texto en el sistema de archivos. Por ejemplo:
   ```python
   rdd = sc.parallelize([1, 2, 3, 4, 5])
   rdd.saveAsTextFile("/ruta/del/archivo")
   ```

Estos ejemplos ilustran una variedad de transformaciones y acciones en Spark que te permiten realizar operaciones de filtrado, ordenamiento, agrupación, conteo, almacenamiento y más en clústeres de Spark. Puedes combinar estas operaciones para realizar análisis de datos más complejos en un entorno distribuido.