# Interfaces Clásicas (XML)

En Android, las interfaces clásicas se definen utilizando archivos XML. Estos archivos describen la estructura y el comportamiento de los elementos de la interfaz de usuario.

Estos archivos XML se encuentran en la carpeta `res/layout` del proyecto y se utilizan para definir la apariencia y el comportamiento de las vistas de la aplicación.

Es importante seguir las convenciones de nomenclatura y organización de los archivos XML para mantener un código limpio y fácil de mantener.

Vamos a ver un ejemplo de cómo se define una interfaz clásica en XML:

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">
    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hola, Mundo!" />
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Presionar" />
</LinearLayout>
```

En este ejemplo, podemos ver varias vistas definidas dentro de un `LinearLayout`. Cada vista tiene atributos que definen su tamaño, posición y comportamiento. Por ejemplo, el `TextView` muestra un texto y el `Button` permite al usuario interactuar con la aplicación.

Podemos diferenciar 2 apartados en este ejemplo:

* **Layout**: Define la estructura de la interfaz, en este caso un `LinearLayout` que organiza sus elementos de manera vertical.
* **Widgets**: Son los elementos de la interfaz, como `TextView` y `Button`, que permiten al usuario interactuar con la aplicación.

Cada uno de estos apartados tiene sus propios atributos y propiedades que se pueden configurar para personalizar la apariencia y el comportamiento de la interfaz.

## Propiedades Comunes

Habrá que tener en cuenta algunas propiedades comunes que se utilizan en los elementos de la interfaz:

* `android:layout_width` y `android:layout_height`: Definen el ancho y alto de la vista. Pueden tomar valores como `match_parent`, `wrap_content` o un valor específico en dp.
* `android:layout_margin`: Define el margen de la vista. Puede ser un valor específico en dp.
* `android:layout_padding`: Define el relleno de la vista. Puede ser un valor específico en dp.
* `android:gravity`: Define la alineación del contenido dentro de la vista.
* `android:orientation`: Define la orientación de un contenedor, como `LinearLayout`, que puede ser `vertical` u `horizontal`.
* `android:id`: Define un identificador único para la vista, que se puede utilizar para referenciarla en el código Java o Kotlin.

Más adelante, veremos cómo se pueden utilizar estas propiedades para crear interfaces más complejas y personalizadas.

## Uso de los Layouts y Widgets en Kotlin

Es importante mencionar que para poder utilizar los layouts y widgets definidos en XML, es necesario referenciarlos en el código Kotlin de la aplicación. Esto se hace utilizando el método `findViewById`, que permite obtener una referencia a la vista definida en el archivo XML.

Sin embargo, se debe utilizar la función `setContentView` para establecer el layout que se va a utilizar en la actividad. Por ejemplo:

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val textView: TextView = findViewById(R.id.textView)
        val button: Button = findViewById(R.id.button)
        button.setOnClickListener {
            textView.text = "¡Botón presionado!"
        }
    }
}
```

En este ejemplo, se establece el layout `activity_main` como la interfaz de la actividad. Luego, se obtienen referencias a las vistas `TextView` y `Button` utilizando sus identificadores definidos en el archivo XML. Finalmente, se establece un listener para el botón que cambia el texto del `TextView` cuando se presiona.

!!! info
    A partir de Android Studio 4.1, se puede utilizar la función `ViewBinding` para evitar el uso de `findViewById`, lo que simplifica el código y mejora la seguridad de tipos. Esto lo veremos en detalle en la sección de Jetpack Compose, donde se utilizan técnicas más modernas para manejar las interfaces de usuario en Android.