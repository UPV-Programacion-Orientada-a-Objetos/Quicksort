# Método de Ordenamiento Quicksort.
Es un algoritmpo de ordenamiento basado en la técnica de divide y vencerás, que permite, en promedio, ordenar n elementos en un tiempo proporcional
de n log n

## Descripción del algoritmo
El algoritmo trabaja de la siguiente forma:

* Elegir un elemento del conjunto de elementos a ordenar, al que llamaremos pivote.
* Resituar los demás elementos de la lista a cada lado del pivote, de manera que a un lado queden todos los menores que él, y al otro los mayores. 
* Los elementos iguales al pivote pueden ser colocados tanto a su derecha como a su izquierda, dependiendo de la implementación deseada. 
* En este momento, el pivote ocupa exactamente el lugar que le corresponderá en la lista ordenada.
* La lista queda separada en dos sublistas, una formada por los elementos a la izquierda del pivote, y otra por los elementos a su derecha.
* Repetir este proceso de forma recursiva para cada sublista mientras éstas contengan más de un elemento. 
* Una vez terminado este proceso todos los elementos estarán ordenados.

![Quicksort](Quicksort.png "Quicksort.png")


Como se puede suponer, la eficiencia del algoritmo depende de la posición en la que termine el pivote elegido.
En el mejor caso, el pivote termina en el centro de la lista, dividiéndola en dos sublistas de igual tamaño. 
En el peor caso, el pivote termina en un extremo de la lista. El orden de complejidad del algoritmo es mayor.

### Código de ejemplo
```public class Quicksort {
    public static void quickSort(int[] vector, int izquierda, int derecha) {
        int pivote = vector[izquierda]; //se toma el inicio del vector como pivote
        int i = izquierda; //
        int j = derecha;
        int auxIntercambio;
        /*Se va recorriendo el vector para organizar los numeros 
        menores o iguales al pivote a la derecha y los mayores a la izquierda*/
        while (i < j) {//Se ejecuta mientras los indices no sean el mismo
            while (vector[i] <= pivote && i < j) {
                i++;
            }
            while (vector[j] > pivote) {
                j--;
            }
            if (i < j) {
                auxIntercambio = vector[i];
                vector[i] = vector[j];
                vector[j] = auxIntercambio;
            }
        }
        /*Se cambia la ubicacion del pivote y el valor que del vector en la posicion j, 
        dado que en este punto dicho valor ya no es mayor al pivote*/
        vector[izquierda] = vector[j];
        vector[j] = pivote;
        /*System.out.println("\n\nArreglo en las vueltas");
        for (int n : vector) {
            System.out.print(n + " ");
        }*/
        
        if (izquierda < j - 1) {
            quickSort(vector, izquierda, j - 1);
        }
        if (j + 1 < derecha) {
            quickSort(vector, j + 1, derecha);
        }
        
    }

    public static void main(String[] args) {
        int[] numeros = new int[10];
        Random rnd = new Random();
        
        //Se muestra el vector desordenado 
        System.out.println("Vector desordenado");
        for (int i = 0; i < numeros.length; i++) {
            numeros[i] = rnd.nextInt(50);
            System.out.print(numeros[i] + " ");
        }
        
        //Se ordena el vector
        Quicksort.quickSort(numeros, 0, numeros.length - 1);
        
        //Se muestra el vector ordenado
        System.out.println("\nVector Ordenado");
        for (int n : numeros) {
            System.out.print(n + " ");
        }

    }
}
```

