# Métodos de Ordenamiento

En informática, un algoritmo de clasificación es un algoritmo que ordena los elementos de una lista. Los órdenes más utilizados son el orden numérico y el orden lexicográfico, ya sea ascendente o descendente. La clasificación eficiente es importante para optimizar la eficiencia de otros algoritmos (como los algoritmos de búsqueda y combinación) que requieren que los datos de entrada estén en listas ordenadas. La clasificación también suele ser útil para canonicalizar datos y producir resultados legibles por humanos.

Formalmente, la salida de cualquier algoritmo de clasificación debe cumplir dos condiciones:

1. La salida está en orden monótono (cada elemento no es menor ni mayor que el elemento anterior, según el orden requerido).
2. La salida es una permutación (una reordenación, pero conservando todos los elementos originales) de la entrada.

Para una eficiencia óptima, los datos de entrada deben almacenarse en una estructura de datos que permita el acceso aleatorio en lugar de una que solo permita el acceso secuencial.

## Bubble sort

El bubble sort, a veces denominado sinking sort, es un algoritmo de clasificación simple que recorre repetidamente la lista de entrada elemento por elemento, comparando el elemento actual con el siguiente e intercambiando sus valores si es necesario. Estos pases por la lista se repiten hasta que no es necesario realizar intercambios durante un pase, lo que significa que la lista queda completamente ordenada. El algoritmo, que es una clasificación por comparación, recibe su nombre por la forma en que los elementos más grandes "burbujan" hasta la parte superior de la lista.

Este algoritmo simple funciona mal en el mundo real y se utiliza principalmente como herramienta educativa. Las bibliotecas de clasificación integradas en lenguajes de programación populares como Python y Java utilizan algoritmos más eficientes, como quicksort, timsort o merge sort. Sin embargo, si se permite el procesamiento paralelo, el bubble sort se realiza en tiempo O(n), lo que la hace considerablemente más rápida que las implementaciones paralelas de clasificación por inserción o selección que no se paralelizan con tanta eficacia.

### Implementación en código.

```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        bubbleSort(arr);
        System.out.println("Array ordenado con Bubble Sort:");
        printArray(arr);
    }

    static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - i - 1; j++)
                if (arr[j] > arr[j + 1]) {
                    // swap temp and arr[i]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
    }

    static void printArray(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```

## Insertion sort

El insertion sort es un algoritmo de clasificación simple que construye la matriz (o lista) ordenada final, un elemento a la vez, mediante comparaciones. Es mucho menos eficiente en listas grandes que algoritmos más avanzados como quicksort, heapsort, o merge sort. Sin embargo, el insertion sort ofrece varias ventajas:

1. Implementación simple: Jon Bentley muestra una versión C/C++ de tres líneas que tiene cinco líneas cuando está optimizada.
2. Eficiente para conjuntos de datos (bastante) pequeños, muy parecido a otros algoritmos de clasificación cuadráticos (es decir, O(n2))
3. Más eficiente en la práctica que la mayoría de los otros algoritmos cuadráticos simples, como selection sort o bubble sort.
4. Adaptativo, es decir, eficiente para conjuntos de datos que ya están sustancialmente ordenados: la complejidad temporal es O(kn) cuando cada elemento en la entrada no está a más de k lugares de su posición ordenada
5. Estable; es decir, no cambia el orden relativo de los elementos con claves iguales
6. En su lugar; es decir, sólo requiere una cantidad constante O(1) de espacio de memoria adicional
7. En línea; es decir, puede ordenar una lista a medida que la recibe

Cuando las personas clasifican manualmente las cartas en una mano de bridge, la mayoría usa un método similar al insertion sort.

### Implementación en código.

```java
public class InsertionSort {
    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6};
        insertionSort(arr);
        System.out.println("Array ordenado con Insertion Sort:");
        printArray(arr);
    }

    static void insertionSort(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }

    static void printArray(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```

## Selection sort

En informática, el selection sort es un algoritmo de clasificación por comparación in situ. Tiene una complejidad temporal O(n2), lo que lo hace ineficiente en listas grandes y, en general, funciona peor que el tipo de inserción similar. El selection sort destaca por su simplicidad y tiene ventajas de rendimiento sobre algoritmos más complicados en determinadas situaciones, especialmente cuando la memoria auxiliar es limitada.

El algoritmo divide la lista de entrada en dos partes: una sublista ordenada de elementos que se construye de izquierda a derecha al principio (izquierda) de la lista y una sublista de los elementos restantes sin clasificar que ocupan el resto de la lista. Inicialmente, la sublista ordenada está vacía y la sublista sin clasificar es la lista de entrada completa. El algoritmo procede encontrando el elemento más pequeño (o más grande, dependiendo del orden de clasificación) en la sublista sin clasificar, intercambiándolo con el elemento sin clasificar más a la izquierda (poniéndolo en orden) y moviendo los límites de la sublista un elemento hacia la derecha. .

La eficiencia temporal del selection sort es cuadrática, por lo que existen varias técnicas de clasificación que tienen una mejor complejidad temporal que el selection sort.

### Implementación en código.
```java
public class SelectionSort {
    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        selectionSort(arr);
        System.out.println("Array ordenado con Selection Sort:");
        printArray(arr);
    }

    static void selectionSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++)
                if (arr[j] < arr[minIndex])
                    minIndex = j;
            int temp = arr[minIndex];
            arr[minIndex] = arr[i];
            arr[i] = temp;
        }
    }

    static void printArray(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```
