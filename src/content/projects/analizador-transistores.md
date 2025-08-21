slug: analizador-transistores
title: Analizador de transistores BJT y MOSFET
summary: Instrumento virtual para medición y caracterización de BJT y MOSFET, automatizado en LabVIEW.
keywords:
  - LabVIEW
  - DAQ
  - BJT
  - MOSFET
  - mediciones electrónicas
---

## Descripción General

Este proyecto consiste en el desarrollo de un instrumento virtual programado en **LabVIEW** para caracterizar y medir parámetros fundamentales de transistores BJT y MOSFET. El sistema integra hardware de adquisición de datos (DAQ) y una interfaz gráfica que automatiza barridos, cálculos y visualización de curvas de caracteristicas de los transistores.

## ¿Qué resolví?

- Automatización del proceso de medición (barrido de parámetros, adquisición simultánea de señales).
- Cálculo de métricas como hFE, gm, curvas de transferencia, y generación automática de gráficos.
- Exportación de datos y resultados en formato CSV e imágenes.
- Implementación de estructura modular tipo *state machine* en LabVIEW para robustez y escalabilidad.

## LabVIEW y DAQ

El software se integra con hardware como NI DAQ, permitiendo controlar barridos de voltaje/corriente, sensar señales analógicas, y realizar cálculos en tiempo real. El flujo de trabajo incluye:

- Selección de dispositivo (BJT/MOSFET).
- Configuración de parámetros de barrido.
- Ejecución de medición automática.
- Visualización y exportación de resultados.

## Galería

Las siguientes capturas muestran la interfaz, diagramas y módulos clave del proyecto.

## Rol y tecnologías

> Fui responsable del diseño de la arquitectura, desarrollo completo en LabVIEW, integración de hardware y documentación técnica.  
> Tecnologías principales: LabVIEW, DAQ, electrónica analógica, Astro.

## Resultados

El dispositivo fue capaz de obtener los parametros caracteristicos del transistor, los