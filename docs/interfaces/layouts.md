# Layouts

Un layout es un contenedor que organiza y gestiona la disposición de los elementos de la interfaz de usuario en una aplicación Android. Los layouts se definen utilizando archivos XML y se encuentran en la carpeta `res/layout` del proyecto.

Existen varios tipos de layouts en Android, cada uno con sus propias características y formas de organizar los elementos. Algunos de los layouts más comunes son:

* **LinearLayout**: Organiza los elementos de manera lineal, ya sea en una dirección vertical u horizontal. Los elementos se colocan uno después del otro.
* **RelativeLayout**: Permite posicionar los elementos en relación a otros elementos o al contenedor padre. Esto proporciona una mayor flexibilidad en la disposición de los elementos.
* **ConstraintLayout**: Es un layout más avanzado que permite crear interfaces complejas mediante restricciones entre los elementos. Es muy útil para crear diseños responsivos y adaptables a diferentes tamaños de pantalla.
* **FrameLayout**: Es un layout simple que permite superponer elementos uno encima del otro. Es útil para crear interfaces donde los elementos se solapan o se muestran de manera temporal.
* **GridLayout**: Organiza los elementos en una cuadrícula, permitiendo definir filas y columnas. Es útil para crear interfaces con una estructura más ordenada y simétrica.
* **TableLayout**: Organiza los elementos en filas y columnas, similar a una tabla. Cada fila puede contener múltiples elementos, y se pueden definir propiedades específicas para cada celda.
* **ScrollView**: Es un contenedor que permite desplazar el contenido cuando este excede el tamaño de la pantalla. Es útil para interfaces con mucho contenido que no cabe en una sola vista.

Vamos a ver algunos de estos layouts en detalle.

## LinearLayout

Un `LinearLayout` organiza los elementos de manera lineal, ya sea en una dirección vertical u horizontal. Los elementos se colocan uno después del otro, y se pueden definir propiedades como el peso (`weight`) para distribuir el espacio entre los elementos de manera proporcional.

Cada elemento dentro de un `LinearLayout` puede tener atributos como `layout_width`, `layout_height`, `layout_weight`, y `gravity` para controlar su tamaño, posición y alineación.

El atributo `weight` permite asignar un peso relativo a cada elemento, de manera que el espacio disponible se distribuya proporcionalmente entre ellos. Por ejemplo, si un elemento tiene un peso de 1 y otro tiene un peso de 2, el segundo elemento ocupará el doble de espacio que el primero.

## RelativeLayout

Un `RelativeLayout` permite posicionar los elementos en relación a otros elementos o al contenedor padre. Esto proporciona una mayor flexibilidad en la disposición de los elementos, ya que se pueden definir reglas de posicionamiento como "alinear a la izquierda de otro elemento" o "alinear al centro del contenedor".

Cada elemento dentro de un `RelativeLayout` puede tener atributos como `layout_alignParentTop`, `layout_below`, `layout_toRightOf`, entre otros, para definir su posición relativa a otros elementos o al contenedor padre.

Un ejemplo de `RelativeLayout` podría ser el siguiente:

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hola, Mundo!"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true" />
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Presionar"
        android:layout_below="@id/textView"
        android:layout_centerHorizontal="true" />
</RelativeLayout>
```

## ConstraintLayout

Un `ConstraintLayout` es un layout más avanzado que permite crear interfaces complejas mediante restricciones entre los elementos. Es muy útil para crear diseños responsivos y adaptables a diferentes tamaños de pantalla.

Cada elemento dentro de un `ConstraintLayout` puede tener atributos como `layout_constraintTop_toTopOf`, `layout_constraintBottom_toBottomOf`, `layout_constraintStart_toStartOf`, entre otros, para definir sus restricciones en relación a otros elementos o al contenedor padre.

Veamos un ejemplo de `ConstraintLayout`:

```xml
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hola, Mundo!"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Presionar"
        app:layout_constraintTop_toBottomOf="@id/textView"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

## GridLayout

Un `GridLayout` organiza los elementos en una cuadrícula, permitiendo definir filas y columnas. Es útil para crear interfaces con una estructura más ordenada y simétrica.

Cada elemento dentro de un `GridLayout` puede tener atributos como `layout_row`, `layout_column`, `layout_rowSpan`, y `layout_columnSpan` para definir su posición y tamaño dentro de la cuadrícula.

Veamos un ejemplo de `GridLayout`:

```xml
<GridLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:rowCount="2"
    android:columnCount="2">
    <TextView
        android:id="@+id/textView1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Elemento 1"
        android:layout_row="0"
        android:layout_column="0" />
    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Elemento 2"
        android:layout_row="0"
        android:layout_column="1" />
    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Elemento 3"
        android:layout_row="1"
        android:layout_column="0" />
    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Elemento 4"
        android:layout_row="1"
        android:layout_column="1" />
</GridLayout>
```