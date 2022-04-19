<div align="center">
  <img src="https://i.imgur.com/u16cAve.png" alt="Size Limit CLI" width="500" height="150">
</div>
<p align="center">
  <img align="center" height="70" width="80" src="https://i.imgur.com/Z3VxCiV.png">
  <img align="center" height="70" width="80" src="https://i.imgur.com/kAXpnpj.png">
  <img align="center" height="70" width="200" src="https://i.imgur.com/yfq67rA.png">
</p>

# products-front-automation

Proyecto de automatización web de los productos de Kushki, en el que se visualizara los escenarios de cada producto
dentro de la carpeta Features (ejemplo: Final, Internal).

## Empecemos 🚀

### Requisitos 📋

- jdk 8
- maven 3.6

En caso de no tenerlo instalado, acceder al siguiente
enlace [Configuración Jdk y Maven](https://docs.google.com/presentation/d/1djXZa7noP5GnV-x8D_xvwB0qH3X4elQHiKx6rdJOnkQ/edit#slide=id.g10c319f3c46_2_0)

### Estructura del Proyecto 📂

```
src
├── main
│   ├── java
│       └── com.kushki
│           └── Page                Page para cada tipo de producto
│           └── Step                Contiene los steps definitions del Feature
│           └── Util                Utilitarios
├── test
│   ├── java
│   ├── resources
│       └── Features                Contiene los feature de los productos 
```

### Configuración de Ambientes 🛠️

Esto nos permitirá poder ejecutar los escenarios en ambientes especificos en el archivo `serenity.conf`

```js
environments {
  default {
    webdriver.base.url = "https://uat-console.kushkipagos.com"
  }
  dev {
    webdriver.base.url = "https://qa-console.kushkipagos.com/auth"
  }
  staging {
    webdriver.base.url = "https://dev-console.kushkipagos.com/staging"
  }
  prod {
    webdriver.base.url = "https://uat-console.kushkipagos.com"
  }
}
```

### Configuración de Properties ⚙

<p align="left">
  <img src="https://i.imgur.com/3UpIeTL.png" alt="Size Limit CLI" width="600" height="400">
</p>

Para poder cambiar algun parámetro ir al archivo `serenity.properties`

* **serenity.proyect.name**: nombre del proyecto de automatización
* **serenity.logging**: log de de ejecución
* **webdriver.driver**: tipo de navegador
* **webdriver.autodownload**: descarga automatica del webdriver
* **serenity.browser.maximized**: browser maximizado
* **chrome.switches**: modalidad headless
* **serenity.take.screenshots**: toma de captura de evidencia
* **webdriver.wait.for.timeout**: tiempo explicito
* **webdriver.timeouts.implicitlywait**: tiempo implicito

### Ejecución de Escenarios 📝

Para realizar la ejecución de los features, se deberá identificar los **@tags** de los features junto al ambiente que se
desea probar y ejecutar el siguiente comando:

***
En caso se desee ejecutar algún escenario de un feature en particular se deberia indicar el tag de dicho escenario

```
mvn clean verify "-Dcucumber.filter.tags=@Otp" -Denvironment=uat
```

***
En caso se deseen ejecutar todos los escenarios al mismo tiempo

```
mvn clean verify
```

***

El reporte de serenity es generado en el directorio `target/site/serenity/index.html`
