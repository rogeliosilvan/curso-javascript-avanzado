# HTML5 API

## Local Storage

### Recursos

* [Local Storage](https://developer.mozilla.org/es/docs/Web/API/Window/localStorage)
* [Aplicacions offline en un mundo online](https://youtu.be/aoLAFNO5dkk)

### API

* setItem(): Añadir una clave y valor al local storage
```
const person = {
    name: "Obaseki Nosa",
    location: "Lagos",
}
window.localStorage.setItem('user', JSON.stringify(person));
``` 
* getItem(): Obtener un valor a través de su clave
```
window.localStorage.getItem('user');
JSON.parse(window.localStorage.getItem('user'));
```
* removeItem(): borrar un item a través de su clave
```
window.localStorage.clear();
```
* clear(): Borrar todo el local storage
```
window.localStorage.clear()
```

## Selectors

* querySelector(): selecciona un elemento del DOM a través de un selector CSS
```
document.querySelector('#myId .myClass')
```
* querySelectorAll(): selecciona todos los elemento del DOM a través de un selector CSS
```
document.querySelectorAll('#myId .myClass')
```

## Geolocation

API que te permite saber la latitud y longitud de alguien. Es necesario que se acepte el permiso para trabajar con ella.
```
function getLocation() {
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition);
    } else {
        console.log("Geolocation is not supported by this browser.");
    }
}
function showPosition(position) {
    console.log(position.coords.latitude, position.coords.longitude)
}
```

## Offline

Detectar si alguien esta online u offline es facil gracias a la propiedad onLine.
Si usamos navigator.onLine 
```
window.navigator.onLine //return true or false
```

## Notifications

Se pueden mostrar notificaciones en el navegador. Lo único que necesitamos son permisos para mostrarlas:

* Notification.requestPermission:
```
Notification.requestPermission().then(function(result) {
  console.log(result);
});
```
* new Notification():
```
new Notification("Holiwis :D");
```

### Ejercicio

1. Muestra en el DOM las coordenadas de tu posicion.
2. Si las coordenadas ya las tienes guaradas en el local storage y son las mismas no sobreescribirlas
3. Mostrar las coordenadas en una notificación.
