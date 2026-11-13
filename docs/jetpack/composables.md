# Composables

Como hemos visto en la anterior sección, Jetpack Compose se basa en un enfoque declarativo para construir interfaces de usuario. Los componentes de UI en Compose se representan mediante funciones anotadas con `@Composable`, que permiten describir la apariencia y el comportamiento de la interfaz de manera modular y reutilizable.

Los composables son funciones que generan elementos de la interfaz de usuario y pueden ser combinadas para crear interfaces más complejas. Estas funciones pueden recibir parámetros, lo que permite personalizar su comportamiento y apariencia según las necesidades de la aplicación.

Existen diferentes tipos de composables, como:

- **Composables de UI**: Son los componentes básicos que representan elementos visuales, como botones, textos, imágenes y contenedores. Estos composables se utilizan para construir la estructura de la interfaz de usuario.
- **Composables de estado**: Permiten gestionar el estado de la aplicación y actualizar la UI de manera reactiva. Estos composables utilizan `State` y `MutableState` para almacenar y observar cambios en los datos.
- **Composables de navegación**: Facilitan la navegación entre diferentes pantallas de la aplicación. Estos composables permiten definir rutas y manejar la transición entre vistas de manera sencilla.
- **Composables de efectos**: Permiten ejecutar acciones secundarias o efectos colaterales en respuesta a cambios en el estado o eventos de la aplicación. Estos composables se utilizan para realizar tareas como llamadas a APIs, actualizaciones de la base de datos o animaciones.

Vamos a ver algunos de los composables más comunes y cómo se utilizan en Jetpack Compose:

- **Text**: Muestra un texto en la interfaz de usuario. Se puede personalizar el estilo, tamaño y color del texto mediante parámetros.

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name!")
}
```

- **Button**: Representa un botón interactivo que puede recibir eventos de clic. Se puede personalizar el contenido y el estilo del botón.

```kotlin
@Composable
fun MyButton(onClick: () -> Unit) {
    Button(onClick = onClick) {
        Text("Click me!")
    }
}
```

- **Column**: Organiza los elementos de la interfaz de usuario en una disposición vertical.

```kotlin
@Composable
fun MyColumn() {
    Column {
        Text("Item 1")
        Text("Item 2")
        Text("Item 3")
    }
}
```

- **Row**: Organiza los elementos de la interfaz de usuario en una disposición horizontal.

```kotlin
@Composable
fun MyRow() {
    Row {
        Text("Item A")
        Text("Item B")
        Text("Item C")
    }
}
```

- **Card**: Representa un contenedor con estilo de tarjeta que puede contener otros composables. Se puede personalizar el contenido, el estilo y la forma de la tarjeta.

```kotlin
@Composable
fun MyCard() {
    Card(elevation = 4.dp) {
        Column {
            Text("Card Title")
            Text("Card Content")
        }
    }
}
```

- **Image**: Muestra una imagen en la interfaz de usuario. Se puede personalizar el tamaño, la forma y el contenido de la imagen.

```kotlin
@Composable
fun MyImage() {
    Image(painter = painterResource(id = R.drawable.my_image), // Carga la imagen desde los recursos
        contentDescription = "My Image")
}
```

