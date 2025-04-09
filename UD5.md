# Unidad Didáctica 5 - **Test Unitarios con JUnit**  

## 1. Objetivo de la Unidad  
El propósito de esta unidad es introducir a los estudiantes en el concepto de **test unitarios** utilizando **JUnit**, el framework estándar de pruebas para aplicaciones Java. Los test unitarios permiten verificar el correcto funcionamiento de componentes individuales de un programa, asegurando que cada método o clase se comporte como se espera de forma aislada.  

A lo largo de esta unidad, se cubrirán los principios básicos de los test unitarios, la configuración de JUnit, la escritura de pruebas simples y avanzadas, así como la interpretación de resultados y la resolución de errores.  

Al finalizar esta unidad, los estudiantes serán capaces de:  
- Comprender la importancia de los test unitarios en el desarrollo de software.  
- Escribir y ejecutar pruebas utilizando JUnit.  
- Identificar y corregir errores a través de pruebas automatizadas.  
- Aplicar buenas prácticas en la escritura de tests.  

---

## 2. Introducción a los Test Unitarios  

### 2.1. ¿Qué son los Test Unitarios?  
Los test unitarios son pequeños fragmentos de código que prueban de manera aislada el comportamiento de una unidad de software, generalmente métodos o funciones. El objetivo es garantizar que cada componente individual cumpla con los requisitos esperados y se comporte correctamente en diferentes escenarios.  

Los test unitarios ayudan a detectar errores en etapas tempranas del desarrollo, lo que facilita el mantenimiento, reduce el costo de corrección y aumenta la estabilidad del software.  

---

### 2.2. ¿Qué es JUnit?  
JUnit es el framework de test unitarios más utilizado en Java. Permite a los desarrolladores escribir pruebas automatizadas de forma rápida y sencilla. JUnit facilita la validación de resultados esperados, la simulación de escenarios complejos y la automatización de pruebas durante el ciclo de vida del desarrollo.  

JUnit se basa en la **especificación xUnit**, que define la estructura de las pruebas unitarias en diversos lenguajes de programación.  

#### Ventajas de JUnit:  
1. **Automatización de pruebas.**  
2. **Fácil integración con herramientas de desarrollo (Maven, Gradle).**  
3. **Ejecución rápida y retroalimentación inmediata.**  
4. **Facilita la detección de regresiones.**  
5. **Promueve el desarrollo guiado por pruebas (TDD).**  

---

## 3. Configuración del Entorno  

### 3.1. Instalación de JUnit  
Para utilizar JUnit en un proyecto Java, es necesario agregar la dependencia de JUnit al proyecto.  

#### 3.1.1. Configuración con Maven  
```xml
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.9.0</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-engine</artifactId>
        <version>5.9.0</version>
    </dependency>
</dependencies>
```  

#### 3.1.2. Configuración con Gradle  
```groovy
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.0'
}
```  

---

### 3.2. Estructura de un Proyecto con Test Unitarios  
Una buena práctica es separar las pruebas del código fuente. La estructura típica de un proyecto con test unitarios es la siguiente:  

```
src/  
│  
├── main/  
│   └── java/  
│       └── com/example/  
│           └── Calculator.java  
└── test/  
    └── java/  
        └── com/example/  
            └── CalculatorTest.java  
```  

---

## 4. Creación de Test Unitarios con JUnit  

### 4.1. Creación de una Clase de Prueba  
Cada clase de prueba se asocia con una clase específica del código fuente que se desea testear. La convención es nombrar la clase de prueba con el mismo nombre que la clase original, añadiendo el sufijo `Test`.  

**Ejemplo:**  
```java
// Clase original
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```  

```java
// Clase de prueba
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {

    @Test
    public void testAdd() {
        Calculator calculator = new Calculator();
        int result = calculator.add(2, 3);
        assertEquals(5, result, "La suma de 2 + 3 debe ser 5");
    }
}
```  

---

### 4.2. Explicación de la Clase de Prueba  
- **`@Test`**: Anotación que indica que el método es una prueba unitaria.  
- **`assertEquals`**: Comprueba que el resultado obtenido (`result`) es igual al valor esperado (`5`).  
- **Mensaje de error (opcional)**: Proporciona información adicional si la prueba falla.  

---

### 4.3. Otras Anotaciones Comunes  
- **`@BeforeEach`**: Ejecuta un método antes de cada prueba. Útil para inicializar datos.  
- **`@AfterEach`**: Ejecuta un método después de cada prueba.  
- **`@BeforeAll`**: Ejecuta un método antes de todas las pruebas (solo una vez).  
- **`@AfterAll`**: Ejecuta un método después de todas las pruebas (solo una vez).  
- **`@Disabled`**: Desactiva temporalmente una prueba.  

---

## 5. Ejemplo Completo con Múltiples Pruebas  
```java
import org.junit.jupiter.api.*;

import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    Calculator calculator;

    @BeforeEach
    public void setUp() {
        calculator = new Calculator();
    }

    @Test
    public void testAdd() {
        assertEquals(7, calculator.add(3, 4), "La suma de 3 + 4 debe ser 7");
    }

    @Test
    public void testSubtract() {
        assertEquals(2, calculator.subtract(5, 3), "La resta de 5 - 3 debe ser 2");
    }

    @Test
    @Disabled
    public void testDivide() {
        assertEquals(2, calculator.divide(10, 5), "La división de 10 / 5 debe ser 2");
    }
}
```  

---

## 6. Ejecución de las Pruebas  
### 6.1. Desde Línea de Comandos  
Si se está utilizando Maven:  
```bash
mvn test
```  
Si se está utilizando Gradle:  
```bash
gradle test
```  

### 6.2. Desde un IDE  
- En Eclipse o IntelliJ IDEA, haz clic derecho sobre la clase de prueba y selecciona **Run 'CalculatorTest'**.  

---

## 7. Interpretación de Resultados  
- **Verde**: Todas las pruebas pasaron correctamente.  
- **Rojo**: Al menos una prueba ha fallado.  
- **Error de excepción**: La prueba ha lanzado una excepción no manejada.  

---

## 8. Buenas Prácticas en Test Unitarios  
1. **Escribir pruebas para cada método público.**  
2. **Asegurarse de probar tanto casos normales como extremos.**  
3. **Evitar dependencias externas en pruebas unitarias (mocking si es necesario).**  
4. **Las pruebas deben ser rápidas y repetibles.**  
5. **Mantener las pruebas organizadas y bien documentadas.**