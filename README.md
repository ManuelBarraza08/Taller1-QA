Taller 1 QA - Evaluación Unidad N°II

Objetivos del Proyecto

El objetivo principal de este proyecto es implementar y documentar un flujo básico de Integración Continua (CI), incorporando buenas prácticas de pruebas automatizadas. Se incluyen pruebas unitarias atómicas con JUnit, diseño de escenarios bajo el enfoque BDD (Behavior-Driven Development) utilizando Cucumber y Gherkin, y simulaciones de pruebas de rendimiento utilizando k6.

Estructura del Proyecto

El proyecto sigue la arquitectura y el patrón estándar de Maven para asegurar una alta cohesión y bajo acoplamiento, separando el código fuente de los tests:

src/main/java/: Contiene el código fuente y la lógica de la aplicación (ej. Calculadora.java).

src/test/java/: Contiene las pruebas unitarias atómicas y la configuración de las pruebas.

src/test/resources/: Aloja los archivos de comportamiento .feature escritos en lenguaje Gherkin.

.github/workflows/: Contiene la configuración del pipeline automatizado (ci.yml).

load_test.js: Script de configuración para las pruebas de rendimiento con k6.

Comandos Utilizados

A continuación, se detallan los comandos principales ejecutados en PowerShell durante el desarrollo del taller:

Control de versiones (Git y GitHub):

git init: Inicializa el repositorio local.

git add .: Prepara todos los archivos modificados para el commit.

git commit -m "mensaje": Guarda los cambios localmente con un mensaje descriptivo.

git push -u origin main: Sube los cambios al repositorio remoto en GitHub.

git pull origin main --allow-unrelated-histories: Sincroniza y fusiona los archivos del repositorio remoto con el local.

Ejecución de Pruebas (Maven):

mvn clean test: Limpia el directorio de construcción temporal (target/) y ejecuta todas las pruebas automatizadas (Unitarias y BDD).

Pruebas de Rendimiento (k6):

k6 run load_test.js: Ejecuta el script de prueba de carga simulando la concurrencia de múltiples usuarios virtuales.

Estructura y Explicación del Pipeline (GitHub Actions)

El pipeline de Integración Continua está definido en el archivo .github/workflows/ci.yml y automatiza la validación del código.

Trigger (Eventos): Está configurado para ejecutarse automáticamente en cada evento push o pull_request que se realice sobre la rama main.

Entorno: Utiliza un entorno virtual basado en la última versión de Ubuntu (ubuntu-latest).

Pasos del flujo (Steps):

Checkout: Clona el código del repositorio en la máquina virtual.

Configuración de Java: Instala y configura el entorno Java JDK 21 (Temurin), asegurando que coincida con la versión declarada en el pom.xml.

Ejecución de Tests: Ejecuta el comando de Maven para compilar el código y correr la suite completa de pruebas. Si alguna prueba falla, el pipeline se detiene y marca un error (cruz roja), evitando que código defectuoso pase a producción.