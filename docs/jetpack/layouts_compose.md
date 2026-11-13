# Layouts Compose

En Jetpack Compose, los layouts son componentes que se utilizan para organizar y distribuir los elementos de la interfaz de usuario en la pantalla. Los layouts permiten crear estructuras de UI flexibles y responsivas, adaptándose a diferentes tamaños de pantalla y orientaciones.

Algunos de los layouts más comunes en Jetpack Compose son:

- **Column**: Organiza los elementos de la interfaz de usuario en una disposición vertical. Los elementos se apilan uno encima del otro.

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

- **Row**: Organiza los elementos de la interfaz de usuario en una disposición horizontal. Los elementos se colocan uno al lado del otro.

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

- **Box**: Permite superponer elementos de la interfaz de usuario. Los elementos se colocan uno encima del otro, y se pueden alinear y posicionar según sea necesario.

```kotlin
@Composable
fun MyBox() {
    Box {
        Text("Item 1")
        Text("Item 2", modifier = Modifier.align(Alignment.Center))
    }
}
```

- **ConstraintLayout**: Permite crear layouts más complejos utilizando restricciones entre los elementos.

```kotlin
@Composable
fun MyConstraintLayout() {
    ConstraintLayout {
        val (text1, text2) = createRefs()
        Text("Item 1", Modifier.constrainAs(text1) {
            top.linkTo(parent.top)
            start.linkTo(parent.start)
        })
        Text("Item 2", Modifier.constrainAs(text2) {
            top.linkTo(text1.bottom)
            start.linkTo(parent.start)
        })
    }
}
```
- **LazyColumn**: Permite crear listas de elementos que se cargan de manera perezosa, es decir, solo se renderizan los elementos visibles en la pantalla, lo que mejora el rendimiento en listas largas.

```kotlin
@Composable
fun MyLazyColumn() {
    LazyColumn {
        items(100) { index ->
            Text("Item #$index")
        }
    }
}
```

- **LazyRow**: Similar a LazyColumn, pero organiza los elementos en una disposición horizontal.

```kotlin
@Composable
fun MyLazyRow() {
    LazyRow {
        items(100) { index ->
            Text("Item #$index")
        }
    }
}
```

Estos layouts proporcionan una base sólida para construir interfaces de usuario en Jetpack Compose, permitiendo a los desarrolladores crear aplicaciones con diseños flexibles y adaptables a diferentes dispositivos y tamaños de pantalla.

Es importante que a la hora de diseñar la interfaz de usuario, los desarrolladores consideren la jerarquía y la organización de los elementos, así como el uso adecuado de los layouts para lograr una experiencia de usuario coherente y agradable.