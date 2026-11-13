# Ejemplo App Compose

Vamos a crear una aplicación sencilla utilizando Jetpack Compose. Esta aplicación mostrará una lista de elementos y permitirá al usuario interactuar con ellos.

Comenzaremos creando un proyecto de Android en Android Studio y seleccionando la opción de Jetpack Compose. Una vez creado el proyecto, podemos empezar a construir nuestra interfaz de usuario utilizando composables.

### Estructura del proyecto

Vamos a crear la arquitectura básica de nuestra aplicación siguiendo el patrón MVVM (Model-View-ViewModel). La estructura del proyecto será la siguiente:

```
app/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/ejemploappcompose/
│   │   │       ├── model/
│   │   │       │   └── Item.kt
│   │   │       ├── view/
│   │   │       │   └── MainActivity.kt
│   │   │       └── viewmodel/
│   │   │           └── ItemViewModel.kt
```

Como vemos, se utilizará un paquete `model` para las clases de datos, un paquete `view` para las actividades y composables, y un paquete `viewmodel` para los ViewModels que gestionarán el estado de la aplicación.

Esta distinción es importante a la hora de organizar el código y mantener una separación clara entre la lógica de negocio y la presentación, lo que facilita el mantenimiento y la escalabilidad del proyecto.

### Creación del modelo de datos

En el paquete `model`, crearemos una clase de datos llamada `Item` que representará cada elemento de la lista. Esta clase tendrá un identificador único y un nombre.

```kotlin
data class Item(val id: Int, val name: String)
```

En este caso se usa una data class para representar un elemento de la lista, lo que nos permite aprovechar las funcionalidades automáticas que ofrece Kotlin, como la generación de métodos `toString()`, `equals()` y `hashCode()`, así como la desestructuración de objetos.

Este modelo de datos se utilizará como base para la lista de elementos que se mostrará en la interfaz de usuario, y permitirá a los desarrolladores trabajar con datos de manera más sencilla y estructurada.

### Creación del ViewModel

El ViewModel se encargará de gestionar el estado de la lista de elementos y proporcionar los datos a la interfaz de usuario. Crearemos una clase llamada `ItemViewModel` en el paquete `viewmodel`.

```kotlin
class ItemViewModel : ViewModel() {
    private val _items = MutableStateFlow<List<Item>>(emptyList())
    val items: StateFlow<List<Item>> = _items.asStateFlow()

    fun loadItems() {
        // Simulamos la carga de datos
        _items.value = List(20) { index -> Item(index, "Item #$index") }
    }

    fun addItem(name: String) {
        val newItem = Item(_items.value.size, name)
        _items.value = _items.value + newItem
    }
}
```

Habrás podido ver que se utiliza `MutableStateFlow` para almacenar la lista de elementos y exponerla como un `StateFlow` inmutable. Esto permite que la interfaz de usuario observe los cambios en la lista y se actualice automáticamente cuando se agregan nuevos elementos.

El uso de `StateFlow` es una práctica recomendada en aplicaciones modernas de Android, ya que proporciona un flujo de datos reactivo y facilita la gestión del estado de la aplicación. Esto va a hacer que una vez se cambie el estado de la lista, cualquier componente que dependa de ella se vuelva a componer automáticamente, reflejando los cambios en la interfaz de usuario sin necesidad de intervención manual.

### Creación de la interfaz de usuario

Vamos con la parte visual de la aplicación. En el paquete `view`, crearemos la actividad principal `MainActivity` y definiremos los composables que compondrán la interfaz de usuario.

```kotlin
class MainActivity : ComponentActivity() {
    private val itemViewModel: ItemViewModel by viewModels()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MyApp(itemViewModel)
        }
    }
}
```

Vemos como hemos creado una instancia del `ItemViewModel` utilizando la delegación `by viewModels()`, lo que nos permite acceder al ViewModel de manera sencilla y mantener su ciclo de vida vinculado a la actividad. Habrás observado que la clase `MainActivity` extiende de `ComponentActivity`, lo que nos permite utilizar Jetpack Compose para definir la interfaz de usuario de manera declarativa.

La función `setContent` se utiliza para establecer el contenido de la actividad, y dentro de ella llamamos a nuestro composable `MyApp`, pasando el `itemViewModel` como parámetro. Esto nos permite que la interfaz de usuario tenga acceso al estado y los datos gestionados por el ViewModel.

Vamos a ver el composable `MyApp` que definirá la estructura principal de la interfaz de usuario:

```kotlinkotlin
@Composable
fun MyApp(itemViewModel: ItemViewModel) {
    val items by itemViewModel.items.collectAsState()
    Remember { itemViewModel.loadItems() }
    Column {
        LazyColumn {
            items(items) { item ->
                Text(item.name)
            }
        }
        Button(onClick = { itemViewModel.addItem("New Item") }) {
            Text("Add Item")
        }
    }
}
```

Veamos por partes este ejemplo:

- **Uso de `collectAsState()`**: Se utiliza para observar los cambios en el `StateFlow` de la lista de elementos. Cada vez que la lista cambia, el composable se vuelve a componer automáticamente, reflejando los cambios en la interfaz de usuario.
- **Uso de `Column`**: Se utiliza para organizar los elementos de la interfaz de usuario en una disposición vertical. Dentro de la columna, se encuentra un `LazyColumn` que muestra la lista de elementos y un botón para agregar nuevos elementos.
- **Uso de `LazyColumn`**: Se utiliza para mostrar la lista de elementos de manera eficiente, renderizando solo los elementos visibles en la pantalla. Esto mejora el rendimiento en listas largas. En este caso se cargan los elementos de la lista utilizando el método `items()` que recibe la lista de elementos y un lambda que define cómo se debe mostrar cada elemento.
- **Uso de `Button`**: Se utiliza para permitir al usuario agregar nuevos elementos a la lista. Al hacer clic en el botón, se llama al método `addItem()` del ViewModel, que agrega un nuevo elemento a la lista y provoca que la interfaz de usuario se actualice automáticamente.