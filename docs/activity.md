# Activities

En Android, una Activity representa una sola pantalla con una interfaz de usuario. Es uno de los componentes fundamentales de una aplicación Android y permite a los usuarios interactuar con la aplicación.

Cada Activity tiene un ciclo de vida bien definido, que consiste en varios estados y métodos que se llaman en diferentes momentos. Estos métodos permiten a los desarrolladores gestionar el comportamiento de la Activity en respuesta a eventos del sistema y del usuario.

Esta actividad puede ser iniciada por el sistema o por otra Activity, y puede ser destruida cuando ya no es necesaria. Es importante comprender el ciclo de vida de una Activity para garantizar un manejo adecuado de los recursos y una experiencia de usuario fluida.

Existen diferentes tipos de Activities, como las Activities principales, que son el punto de entrada de la aplicación, y las Activities secundarias, que se utilizan para mostrar información adicional o realizar tareas específicas.

Durante este tema, exploraremos cómo crear y gestionar Activities en Android, así como cómo manejar su ciclo de vida para garantizar un comportamiento adecuado de la aplicación. También aprenderemos a pasar datos entre Activities y a utilizar Intents para iniciar nuevas Activities.

## Creación de un Activity

Vamos a crear un Activity en Android utilizando Kotlin. Para ello, seguiremos los siguientes pasos:

1. Crear una nueva clase que extienda de `AppCompatActivity`.
2. Sobrescribir el método `onCreate()` para inicializar la Activity y establecer su contenido de la interfaz de usuario.
3. Definir el layout de la Activity en un archivo XML o utilizando Jetpack Compose.
4. Registrar la Activity en el archivo `AndroidManifest.xml` para que el sistema pueda reconocerla y lanzarla cuando sea necesario.

Veamos en detalle cada uno de estos pasos y cómo implementarlos en nuestro proyecto Android.

### AppCompatActivity

`AppCompatActivity` es una clase de la biblioteca de compatibilidad de Android que proporciona funcionalidades adicionales y soporte para características más recientes de Android. Al extender `AppCompatActivity`, nuestra Activity obtiene acceso a las funciones de ActionBar, temas personalizados y otras características que mejoran la experiencia del usuario.

Es importante realiarlo tanto en el lenguaje de programación Kotlin como en Java, ya que es la base para crear Activities modernas y compatibles con diferentes versiones de Android.

```kotlin
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

Habrás podido observar que en el ejemplo anterior, hemos sobrescrito el método `onCreate()` para inicializar la Activity y establecer su contenido de la interfaz de usuario utilizando un layout definido en XML.

Este método es especial ya que forma parte de los métodos del ciclo de vida de una Activity y se llama cuando la Activity se crea por primera vez. Es el lugar adecuado para realizar la inicialización de la interfaz de usuario y configurar cualquier recurso necesario para la Activity.

## Ciclo de vida de un Activity

Uno de los aspectos más importantes a comprender al trabajar con Activities en Android es su ciclo de vida. El ciclo de vida de una Activity describe los diferentes estados por los que pasa una Activity desde su creación hasta su destrucción.

Un Activity puede estar en uno de los siguientes estados:

1. **Creada (Created)**: La Activity ha sido creada, pero aún no es visible para el usuario.
2. **Iniciada (Started)**: La Activity es visible para el usuario, pero aún no está en primer plano.
3. **Reanudada (Resumed)**: La Activity está en primer plano y el usuario puede interactuar con ella.
4. **Pausada (Paused)**: La Activity está parcialmente visible, pero otra Activity está en primer plano y el usuario no puede interactuar con ella.
5. **Detenida (Stopped)**: La Activity ya no es visible para el usuario y está en segundo plano.
6. **Destruida (Destroyed)**: La Activity ha sido destruida y liberada de memoria.
7. **Reiniciada (Restarted)**: La Activity ha sido reiniciada después de haber sido detenida.

<figure>
    <img src="https://developer.android.com/images/activity_lifecycle.png" alt="Ciclo de vida de un Activity" />
    <figcaption>Ciclo de vida de un Activity en Android</figcaption>
</figure>

### Métodos del ciclo de vida

Habrás podido ver que cada estado del ciclo de vida de un Activity está asociado con métodos específicos que se llaman automáticamente por el sistema en diferentes momentos. Estos métodos permiten a los desarrolladores gestionar el comportamiento de la Activity y realizar acciones adecuadas en respuesta a eventos del sistema y del usuario.

Cada método del ciclo de vida tiene un propósito específico y se utiliza para realizar tareas como inicializar recursos, guardar el estado de la Activity, liberar recursos o actualizar la interfaz de usuario.

Es importante saber utilizar estos métodos de manera adecuada para garantizar un manejo eficiente de los recursos y una experiencia de usuario fluida. A continuación, se describen los métodos más importantes del ciclo de vida de un Activity:

1. **onCreate()**: Se llama cuando la Activity se crea por primera vez. Es el lugar adecuado para inicializar la interfaz de usuario y configurar cualquier recurso necesario para la Activity.
2. **onStart()**: Se llama cuando la Activity se vuelve visible para el usuario. Aquí se pueden realizar tareas relacionadas con la preparación de la interfaz de usuario y la actualización de datos.
3. **onPause()**: Se llama cuando la Activity se pausa. Aquí se pueden realizar tareas relacionadas con guardar el estado de la interfaz antes de pausar.
4. **onRestart()/onResume()**: Se llama cuando la Activity se reinicia después de haber sido pausada. Aquí se pueden realizar tareas relacionadas con la reanudación de la interfaz y la actualización de datos.
5. **onStop()**: Se llama cuando la Activity se detiene. Aquí se pueden realizar tareas relacionadas con liberar recursos y guardar el estado de la Activity.
6. **onDestroy()**: Se llama cuando la Activity es destruida. Aquí se pueden realizar tareas relacionadas con liberar todos los recursos y finalizar la Activity.

## Definir el layout de un Activity

Es importante definir el layout de un Activity para determinar cómo se verá la interfaz de usuario. En Android, existen dos enfoques principales para definir el layout: utilizando archivos XML o utilizando Jetpack Compose:

* **XML Layouts**: Los layouts XML son archivos que describen la estructura y apariencia de la interfaz de usuario utilizando un lenguaje de marcado. Estos archivos se colocan en la carpeta `res/layout` del proyecto y se pueden referenciar desde el código de la Activity para establecer el contenido de la interfaz.
* **Jetpack Compose**: Jetpack Compose es un enfoque moderno para crear interfaces de usuario en Android utilizando un lenguaje declarativo basado en Kotlin. Con Compose, se pueden definir los elementos de la interfaz directamente en el código de la Activity, lo que permite una mayor flexibilidad y facilidad de uso.

Ahora nos centraremos en cómo definir el layout de forma clásica utilizando XML, y posteriormente exploraremos cómo hacerlo con Jetpack Compose.

Para establecer el layout de un Activity utilizando XML, se utiliza el método `setContentView()` dentro del método `onCreate()`. Este método recibe como parámetro el identificador del layout que se desea utilizar, que se encuentra en la carpeta `res/layout` del proyecto.

## Registrar un Activity en el AndroidManifest.xml

Para que el sistema pueda reconocer y lanzar un Activity, es necesario registrarlo en el archivo `AndroidManifest.xml`. Este archivo se encuentra en la raíz del proyecto y contiene información sobre la aplicación, incluyendo los componentes que la conforman.

Para registrar un Activity, se debe agregar una entrada dentro de la etiqueta `<application>` en el archivo `AndroidManifest.xml`. La entrada debe incluir el nombre completo de la clase del Activity y, opcionalmente, otros atributos como el tema o la orientación de la pantalla.

Además, es importante definir un Activity principal que actúe como punto de entrada de la aplicación. Este Activity se marca con el atributo `android.intent.action.MAIN` y se asocia con la categoría `android.intent.category.LAUNCHER`, lo que indica que es el Activity que se lanzará cuando el usuario inicie la aplicación desde el lanzador de aplicaciones.

Veamos estos atributos en un ejemplo de registro de un Activity en el archivo `AndroidManifest.xml`:

```xml
<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/Theme.MyApplication">
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>
```

En este ejemplo, hemos registrado un Activity llamado `MainActivity` como el Activity principal de la aplicación. Esto significa que cuando el usuario inicie la aplicación desde el lanzador de aplicaciones, se abrirá automáticamente el `MainActivity`.

Es importante tener en cuenta el intent-filter, que define la acción y la categoría del Activity. La acción `android.intent.action.MAIN` indica que este Activity es el punto de entrada de la aplicación, mientras que la categoría `android.intent.category.LAUNCHER` indica que este Activity se mostrará en el lanzador de aplicaciones.

!!! info
    En Android un Intent es un objeto que permite la comunicación entre diferentes componentes de la aplicación, como Activities, Services y Broadcast Receivers. Los Intents se utilizan para iniciar nuevas Activities, enviar datos entre ellas y realizar otras acciones dentro de la aplicación.

Puedes usar un Intent no solo para abrir tus propias Activities, sino también para abrir Activities de otras aplicaciones instaladas en el dispositivo. Por ejemplo, puedes usar un Intent para abrir la cámara, el navegador web o cualquier otra aplicación que tenga un Activity registrado para manejar la acción correspondiente.

Ejemplo de apertura de la camara utilizando un Intent:

```kotlin
val intent = Intent(MediaStore.ACTION_IMAGE_CAPTURE)
startActivity(intent)
```