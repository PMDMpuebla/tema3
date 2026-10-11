# Otros componentes

En esta sección se describen otros componentes que podemos utilizar en nuestras aplicaciones; algunas son:

* **AlertDialog**: Un componente que permite mostrar un cuadro de diálogo con un mensaje y opciones para que el usuario interactúe. Se puede personalizar el título, el mensaje, los botones y las acciones asociadas a cada botón.
* **Toast**: Un componente que muestra un mensaje breve en la pantalla durante un tiempo determinado. Es útil para mostrar notificaciones rápidas o confirmaciones de acciones realizadas por el usuario.
* **Snackbar**: Similar al Toast, pero con más opciones de personalización y la posibilidad de incluir acciones. Se muestra en la parte inferior de la pantalla y puede contener un mensaje y un botón para realizar una acción.

## Toast

Un `Toast` es un componente que muestra un mensaje breve en la pantalla durante un tiempo determinado. Es útil para mostrar notificaciones rápidas o confirmaciones de acciones realizadas por el usuario. A diferencia de los diálogos, los `Toast` no requieren interacción del usuario y desaparecen automáticamente después de un tiempo.

Un ejemplo de cómo mostrar un `Toast` en una actividad es el siguiente:

```kotlin
val toast = Toast.makeText(this, "Este es un mensaje de Toast", Toast.LENGTH_SHORT)
toast.show()
```

En este caso se muestra un `Toast` con el mensaje "Este es un mensaje de Toast" durante un tiempo corto. También se puede personalizar la duración del `Toast` utilizando `Toast.LENGTH_LONG` para mostrarlo durante un tiempo más largo.

## AlertDialog

Un `AlertDialog` es un componente que permite mostrar un cuadro de diálogo con un mensaje y opciones para que el usuario interactúe. Se puede personalizar el título, el mensaje, los botones y las acciones asociadas a cada botón.

Hay diferentes formas de crear un `AlertDialog`, pero una de las más comunes es utilizar la clase `AlertDialog.Builder`. A continuación, se muestra un ejemplo de cómo crear un `AlertDialog` con un título, un mensaje y dos botones:

```kotlin
val builder = AlertDialog.Builder(this)
builder.setTitle("Título del diálogo")
builder.setMessage("Este es el mensaje del diálogo.")
builder.setPositiveButton("Aceptar") { dialog, which ->
    // Acción a realizar cuando se hace clic en el botón Aceptar
    Toast.makeText(this, "Botón Aceptar clickeado", Toast.LENGTH_SHORT).show()
}
builder.setNegativeButton("Cancelar") { dialog, which ->
    // Acción a realizar cuando se hace clic en el botón Cancelar
    Toast.makeText(this, "Botón Cancelar clickeado", Toast.LENGTH_SHORT).show()
}
val dialog = builder.create()
dialog.show()
```

Como vemos en este caso se pueden establecer diferentes acciones para cada botón del `AlertDialog`. En este ejemplo, se muestra un `Toast` con un mensaje informativo cuando se hace clic en cada uno de los botones.

## Snackbar

Un `Snackbar` es un componente similar al `Toast`, pero con más opciones de personalización y la posibilidad de incluir acciones. Se muestra en la parte inferior de la pantalla y puede contener un mensaje y un botón para realizar una acción. Un ejemplo de cómo mostrar un `Snackbar` con un mensaje y un botón es el siguiente:

```kotlin
val snackbar = Snackbar.make(findViewById(R.id.rootLayout), "Este es un mensaje de Snackbar", Snackbar.LENGTH_LONG)
snackbar.setAction("Deshacer") {
    // Acción a realizar cuando se hace clic en el botón Deshacer
    Toast.makeText(this, "Acción Deshacer clickeada", Toast.LENGTH_SHORT).show()
}
snackbar.show()
```

En este caso, se muestra un `Snackbar` con el mensaje "Este es un mensaje de Snackbar" y un botón "Deshacer". Cuando se hace clic en el botón, se muestra un `Toast` con un mensaje informativo.