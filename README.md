# -performance-testing-
# Proyecto QA - Pruebas de Estrés con JMeter sobre Core Bancario

Este repositorio contiene un proyecto de pruebas de rendimiento (estrés y carga) para un sistema bancario core, incluyendo los módulos:

* Caja de Ahorro
* Créditos Hipotecarios
* Plazo Fijo
* Tarjeta de Crédito

Las pruebas se desarrollan utilizando **Apache JMeter**, y se integran con **Jenkins** para su ejecución automatizada. También se contempla la integración con herramientas de gestión como **Jira** o **Azure DevOps**.

---

## 🎯 Objetivos de las pruebas de estrés

1. **Validar concurrencia**: Determinar cuántas solicitudes simultáneas puede manejar cada endpoint sin errores.
2. **Estabilidad bajo carga extrema**: Observar el comportamiento del sistema al superar su capacidad estimada.
3. **Detección de cuellos de botella**: Identificar procesos o endpoints que presentan degradación significativa bajo carga.
4. **Robustez**: Verificar cómo se recupera el sistema luego de eventos de sobrecarga.

---

## 🔍 Ejemplos de límites a simular

Los siguientes escenarios servirán como base para los tests en JMeter:

### Escenario 1: Caja de Ahorro (endpoint: `/cuentas/caja_ahorro/alta`)

* Normal: 100 usuarios concurrentes
* Pico (estrés): 500 usuarios en 10 segundos
* Límite superior simulado: 800 solicitudes simultáneas
* Duración: 5 minutos

### Escenario 2: Créditos Hipotecarios (endpoint: `/creditos/hipotecarios/solicitud`)

* Normal: 30 usuarios
* Pico: 200 usuarios
* Simulación de timeout o cuelgue por validaciones extensas

### Escenario 3: Plazo Fijo (endpoint: `/plazofijo/crear`)

* Normal: 70 usuarios
* Estrés: 300 usuarios en ráfaga
* Evaluación de errores de base de datos

### Escenario 4: Tarjeta de Crédito (endpoint: `/tarjetas/solicitud`)

* Normal: 50 usuarios
* Pico: 250 usuarios
* Límite crítico: 600 solicitudes en menos de 15 segundos

---

## 📁 Estructura del proyecto

```bash
qa-performance-project/
├── jmeter/
│   ├── caja-ahorro-stress.jmx
│   ├── creditos-hipotecarios.jmx
│   ├── plazo-fijo.jmx
│   ├── tarjetas-credito.jmx
│   └── data/
│       └── usuarios.csv
├── reports/
│   └── stress-test-results.html
├── docs/
│   └── instrucciones-ejecucion.md
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Jenkins + Postman + Jira/Azure DevOps (Integración sugerida)

1. **Ejecución en Jenkins**:

   * Usar `Jenkinsfile` para lanzar pruebas desde CLI.
   * Guardar reportes en HTML y exportar métricas.

2. **Integración con Jira**:

   * Asociar los resultados de stress test como evidencia a tareas QA.
   * Plugin: *Jira Integration for Jenkins*.

3. **Integración con Azure DevOps**:

   * Usar tareas en pipelines para invocar JMeter.
   * Publicar artefactos con resultados y logs.

---

## ✅ Requisitos

* Apache JMeter 5.6+
* Java 8+
* Jenkins
* Git

---

## 🔜 Próximos pasos

* [ ] Añadir archivos `.jmx` para cada módulo
* [ ] Cargar datos de prueba en `usuarios.csv`
* [ ] Instrucciones detalladas en `docs/instrucciones-ejecucion.md`
* [ ] Crear pipeline en Jenkins

---

## ✉️ Contacto

*Autor:* \[victor boyeras]
*Email:* \[[victorboyeras@hotmail.com](victorboyeras@hotmail.com)]

---

Este proyecto tiene fines educativos y de entrenamiento para pruebas de rendimiento en sistemas financieros.

---
