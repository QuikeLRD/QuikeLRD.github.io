---
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

## ¿Qué se hizo?

En colaboración con <a href="https://www.linkedin.com/in/miguel-rendon-marc/" target="_blank" rel="noopener noreferrer">Miguel Abraham</a>, se desarrolló un instrumento virtual en **LabVIEW** orientado a la obtención de parámetros eléctricos y curvas características de transistores BJT y MOSFET. El sistema integra hardware de adquisición de datos (DAQ) y una interfaz gráfica para facilitar la caracterización automatizada y precisa de los dispositivos semiconductores.

## ¿Cómo se hizo?

Se diseñó una arquitectura modular en **LabVIEW**, fundamentada en una máquina de estados orientada a eventos. Esta estructura permitió la implementación de barridos automáticos de señales, el cálculo preciso de parámetros eléctricos y la visualización de curvas características. El sistema gestiona el hardware de adquisición de datos (DAQ), posibilita mediciones simultáneas y exporta los resultados en formatos TDMS para un análisis eficiente y trazabilidad de los datos obtenidos.


El sistema desarrollado permite la medición y visualización automática de parámetros fundamentales de transistores BJT, tales como IC, IB, IE, VBE, VCE, ICSAT y HFE, así como la generación de curvas características I-V, incluyendo IC/VCE, IC/VBE y HFE/IC. Para transistores MOSFET, el instrumento facilita la obtención de parámetros como ID, ID_ON, VDS_ON, VGS, VRD, ICSAT y VRDS_ON. El dispositivo proporciona información precisa y confiable para conocer las caracteristicas y propiedades eléctricas reales de distintos transistores para el diseño de diversos circuitos.

---

> Para una explicación técnica completa y detalles de implementación, consulta la sección documentación.