# Controles (widgets)

Los controles (también conocidos como widgets) son elementos visuales que permiten a los usuarios interactuar con la aplicación. Son la base de la interfaz de usuario en Android.

Mientras que los Layouts definen la estructura y organización de la interfaz, los controles son los elementos que permiten al usuario realizar acciones, como ingresar texto, seleccionar opciones, o activar funciones.

Hay diferentes tipos de controles en Android, cada uno con su propia funcionalidad y propósito. Algunos de los controles más comunes incluyen:

* **TextView**: Muestra texto en la pantalla. Es un control de solo lectura y no permite la interacción del usuario.
* **EditText**: Permite al usuario ingresar texto. Es un control interactivo que puede aceptar diferentes tipos de entrada, como texto, números, o contraseñas.
* **Button**: Permite al usuario realizar una acción al hacer clic en él. Puede tener diferentes estilos y comportamientos, como botones de texto, botones de imagen, o botones con iconos.
* **CheckBox**: Permite al usuario seleccionar una o varias opciones de un conjunto. Es un control de selección múltiple que puede estar marcado o desmarcado.
* **RadioButton**: Permite al usuario seleccionar una opción de un conjunto. Es un control de selección única, y generalmente se agrupa en un `RadioGroup` para asegurar que solo una opción esté seleccionada a la vez.
* **Switch**: Permite al usuario activar o desactivar una opción. Es un control de selección binaria que puede representar estados como "encendido" o "apagado".
* **Spinner**: Permite al usuario seleccionar una opción de una lista desplegable.
* **SeekBar**: Permite al usuario seleccionar un valor dentro de un rango mediante un control deslizante.
* **ProgressBar**: Muestra el progreso de una operación en curso. Puede ser indeterminado (sin un valor específico) o determinado (con un valor que indica el progreso).
* **ImageView**: Muestra imágenes en la pantalla. Puede mostrar imágenes desde recursos locales o desde la web.

Cada uno de estos controles tiene sus propios atributos y propiedades que se pueden configurar para personalizar su apariencia y comportamiento. En las siguientes secciones, veremos algunos de estos controles en detalle y cómo se pueden utilizar en una aplicación Android.

Veamos algunos de estos controles en detalle.

## TextView

Un `TextView` es un control que permite mostrar texto en la pantalla. Es un control de solo lectura y no permite la interacción del usuario.

Este control es muy versátil y se puede utilizar para mostrar títulos, descripciones, mensajes de error, o cualquier otro tipo de texto en la interfaz de usuario.

Algunas de sus propiedades más comunes incluyen:

* `android:text`: Define el texto que se mostrará en el control.
* `android:textSize`: Define el tamaño del texto.
* `android:textColor`: Define el color del texto.

## EditText

Un `EditText` es un control que permite al usuario ingresar texto. Es un control interactivo que puede aceptar diferentes tipos de entrada, como texto, números, o contraseñas.

Algunas de sus propiedades más comunes incluyen:

* `android:hint`: Define un texto de sugerencia que se muestra cuando el control está vacío.
* `android:inputType`: Define el tipo de entrada que se espera, como texto, número, correo electrónico, etc.
* `android:maxLength`: Define la longitud máxima del texto que se puede ingresar en el control.

## Button

Un `Button` es un control que permite al usuario realizar una acción al hacer clic en él. Puede tener diferentes estilos y comportamientos, como botones de texto, botones de imagen, o botones con iconos.

Algunas de sus propiedades más comunes incluyen:

* `android:text`: Define el texto que se mostrará en el botón.
* `android:onClick`: Define el método que se ejecutará cuando el usuario haga clic en el botón; aunque este método se define en el código Java o Kotlin de la aplicación.
* `android:background`: Define el fondo del botón, que puede ser un color, una imagen, o un drawable personalizado.

Este elemento es fundamental para la interacción del usuario con la aplicación, ya que permite ejecutar acciones específicas al ser presionado.

## Spinner

Un `Spinner` es un control que permite al usuario seleccionar una opción de una lista desplegable. Es útil cuando se desea ofrecer varias opciones al usuario sin ocupar demasiado espacio en la interfaz.

Este control se puede configurar con un adaptador que proporciona los datos que se mostrarán en la lista desplegable. Al seleccionar una opción, el `Spinner` muestra el valor seleccionado y permite al usuario cambiar su elección.

Algunas de sus propiedades más comunes incluyen:

* `android:entries`: Define un array de opciones que se mostrarán en el `Spinner`.
* `android:prompt`: Define un texto que se mostrará como título de la lista desplegable cuando el usuario haga clic en el `Spinner`.

También se puede personalizar la apariencia del `Spinner` mediante estilos y temas, así como manejar eventos de selección para realizar acciones específicas cuando el usuario elige una opción.

Además, se puede establecer un adaptador personalizado para mostrar elementos más complejos en la lista desplegable, como imágenes junto con texto, utilizando un `ArrayAdapter` o un `BaseAdapter`. Veremos en las siguientes secciones el uso de Adapters y Listeners para manejar la interacción con los controles de manera más avanzada.

## ImageView

Un `ImageView` es un control que permite mostrar imágenes en la pantalla. Puede mostrar imágenes desde recursos locales o desde la web.

Este control es muy útil para mostrar logotipos, iconos, fotos, o cualquier otro tipo de imagen en la interfaz de usuario.

Algunas de sus propiedades más comunes incluyen:

* `android:src`: Define la fuente de la imagen que se mostrará en el control.
* `android:scaleType`: Define cómo se ajustará la imagen dentro del control, como `centerCrop`, `fitCenter`, `fitXY`, entre otros.
* `android:contentDescription`: Define una descripción de la imagen para mejorar la accesibilidad, especialmente para usuarios con discapacidades visuales.

Este control también se puede utilizar junto con bibliotecas de carga de imágenes, como Glide o Picasso, para cargar imágenes desde la web de manera eficiente y con soporte para caché y manejo de errores.

## Otros Controles

Además de los controles mencionados anteriormente, existen muchos otros controles en Android que permiten crear interfaces de usuario más complejas y funcionales.

Puedes ver algunos de estos controles en la documentación oficial de Android: [Controles de la interfaz de usuario](https://developer.android.com/guide/topics/ui/controls).