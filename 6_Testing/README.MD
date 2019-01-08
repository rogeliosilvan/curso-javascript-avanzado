# Testing

## Prueba unitaria 

Una prueba unitaria se centra en una única unidad de código, por regla general en un módulo u objeto. Esto nos proporciona una prueba sencilla, rápida de escribir y ejecutar. La idea es tener muchas pruebas unitarias. Estas son útiles cuando se tiene que realizar algún cambio en el código, con lo cual nos aseguramos que después de haberlo modificado seguirá funcionando como esperamos. Siempre habrá un test que cubra el código modificado y fallará en caso de romperlo con el cambio.

Una prueba unitaria no debe tener dependencias, es decir, no debe utilizar ningún framework de aplicación ni código externo. Se debe probar al componente de forma aislada a todos los demás. Algunos piensan que una prueba automatizada es únicamente una prueba unitaria y esto no es así, pues existen diferentes tipos de pruebas automatizadas y cada una tiene un objetivo distinto.
Los tres tipos más comunes de pruebas automatizadas son:
1. Pruebas unitarias: Se prueba una única pieza de código, como un objeto o una función, siempre aislándolas del resto.
2. Pruebas de integración: Estas pruebas se corren una vez aprobadas las pruebas unitarias, con el fin de probar un conjunto de partes de software para ver su funcionamiento.
3. Pruebas funcionales o de aceptación: Son pruebas automáticas del conjunto de la aplicación. Herramientas como Appium (móvil), Selenium web (web), entre muchos otros nos facilitan la ejecución automática de las pruebas.

Lo que hay que tener claro es que si estamos escribiendo una prueba unitaria y nos parece complicada es muy probable que no estemos haciendo una prueba unitaria. Las pruebas que más complicadas nos pueden parecer son las pruebas funcionales y de integración, ya que estas son más complejas y lentas (y también son más complicadas de mantener que las unitarias).

## TDD (Test Driven Development)

La programación TDD (Test Driven Development) es una técnica de diseño e implementación de software incluida dentro de la metodología XP (Extreme Programming). Esta técnica nos permite obtener una cobertura de pruebas muy alta, aunque es importante destacar que este índice no indica que tengamos una buena calidad de tests. Por lo tanto, no debe ser un valor en el que fijarse únicamente. El proceso TDD podemos reducirlo a los siguientes pasos:

1. Escribimos una prueba que recoja nuestros requisitos.
2. Ejecutamos la prueba. Esta debe fallar, en caso contrario es que no estamos desarrollándola bien, por lo tanto no es válida.
3. Se escribe la mínima cantidad de código necesaria para que el test pase.
4. Se vuelve a ejecutar la prueba, esta debe correr exitosamente.
5. Se recomienda refactorizar el código escrito, ya que cualquier cambio que hagamos vamos a estar seguros que nuestro código va funcionar si los tests son favorables.
6. Repetimos el punto uno para el siguiente requisito.

La TDD nos aportar una cobertura de código entre un 90% y 100%, lo que indica que añadir nuevas funcionalidades va ser fácil, ya que nos da una alta confianza sobre nuestro código. Igualmente, TDD se puede compaginar con pruebas unitarias sin problema (incluso es recomendable hacerlo). Es cierto que esta metodología tiene una curva de aprendizaje algo lenta al principio, porque cambia nuestra forma de plantearnos el desarrollo, pero una vez arrancados este proceso es ágil y rápido.
También puede parecer que es un gasto de recursos, ya que el tiempo que estás aprendiendo TDD no estás produciendo, pero no es así. No se trata de una inversión a corto plazo, sino a largo plazo de cara al mantenimiento del código una vez estemos alojados en producción. En proyectos en los que no se tienen buenos tests puede ser un dolor de cabeza añadir nuevas funcionalidades o actualizaciones de las mismas. En este sentido, pueden llegar casos en los que plantearse echar abajo todo el código y empezar de nuevo, debido a la gran deuda técnica que se arrastra con un código insostenible.

## Herramientas para JS:

* [Jasmine](https://jasmine.github.io)
* [AVA](https://github.com/avajs/ava)
* [Mocha](https://mochajs.org)

## Testing e2e

El testing e2e (end-to-end) es una metodología para testear el flujo de nuestra aplicación de principio
a fin como lo haría un usuario. Se utiliza para asegurar que nuestra aplicación entera funciona
por lo que deberia probarse en un entorno real. Al hacer pruebas como un usuario final probaremos
todas las partes de nuestra aplicación como la base de datos, el frontend, el backend y dependencias
que tengamos.

Suelen ser tests complicados de desarrollar y dificiles de mantener con el tiempo ya que si nos cambia un poco
el frontal de nuestra aplicación y los selectores que usamos no son los correctos tenemos que volver a cambiar el test.

## Herramientas para tests e2e:

* [TestCafe](https://devexpress.github.io/testcafe/)
* [Cypress](https://www.cypress.io)
* [Selenium](https://www.seleniumhq.org)

## Ejercicios:

Tenemos una base de datos de jugadores de la eurocopa de 2016. Queremos hacer una clase que implemente un
pequeño gestor de base de datos. Podremos hacer las siguientes operaciones:

* Find:
  - Recibirá como parametro un objeto y como segundo parametro el nombre de un equipo.
   Se puede buscar por nombre y por position:
  ```
    MyClass.find({name: "David de Gea"}, "spain")
  ```
  - En caso de no existir devulve null

* FindAll:
  - Igual que el anterior pero buscará todos los jugadores con los que pueda coincidir el nombre o la posicion.
  - En caso de no existir devuelve un array vacio.

* GetPlayersByTeam:
  - Recibe como parametro el nombre de un equipo y te devuelve los datos de sus jugadores.
  - En caso de no existir devuelve null

* GetTeams
  - No recibe nada como parametro y devuelve una lista con el nombre de todos los equipos.


**Se debe utilizar TDD para el desarrollo de la clase**

**Como obtener la información:**

La información está en GitHub. Concretamente aquí: 
https://github.com/jokecamp/FootballData/tree/master/UEFA_European_Championship/Euro%202016/players_json

Para obtener el json de un equipo hay que obtener el raw haciendole una petición usando [Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Utilizando_Fetch)

Os dejo un listado de los equipos para que lo incluyais en la aplicación:

```
const teams = ["albania",
"austria",
"belgium",
"croatia",
"czech",
"england",
"france",
"german",
"hungary",
"iceland",
"ireland",
"italy",
"northern-ireland",
"poland",
"portugal",
"romania",
"russia",
"slovakia",
"spain",
"sweden",
"swiss",
"turkey",
"ukraine",
"wales"]
```
La url a la que hay que realizar la petición sería así:

```
https://raw.githubusercontent.com/jokecamp/FootballData/master/UEFA_European_Championship/Euro%202016/players_json/${team}-players.json
```

