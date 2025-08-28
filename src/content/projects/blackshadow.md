---
slug: blackshadow
title: Desarrollo de un minisumo autonomo profesional para competencia
summary: El proyecto consistió en el desarrollo de un robot minisumo autónomo, capaz de participar en competencias de sumo robótico. El sistema integra sensores para la detección de rivales y límites del área de combate, junto con una lógica de control eficiente que permite ejecutar maniobras ofensivas y defensivas en tiempo real.
---

## ¿Qué se hizo?



## ¿Comó se hizo?

Para llevar a cabo el proyecto se utilizó una tarjeta FPGA Cyclone IV programada en VHDL mediante el software Quartus. El desarrollo se realizó bajo un enfoque modular, dividiendo cada función del automóvil en bloques independientes (encendido, luces, sensores de punto ciego, luces intermitentes, faros, etc).
El procedimiento incluyó: instalación y configuración del entorno de diseño, definición de entradas y salidas por módulo, programación en VHDL, simulaciones mediante testbench digital, síntesis del diseño y posterior implementación en hardware. Se emplearon sensores como LDR e IR, un ADC0804 para convertir señales analógicas a digitales, y diversos  LEDs y buzzers. Finalmente, se verificó el funcionamiento real mediante pruebas físicas y comparación con las simulaciones, utilizando LEDs indicadores y herramientas de medición básicas.

## Resultados obtenidos

El sistema diseñado cumplió con los objetivos de emular funcionalidades clave de un automóvil real dentro de una maqueta digital. Los niveles de iluminación detectados por el LDR se visualizaron correctamente en LEDs gracias al ADC0804, lo que permitió representar en tiempo real las condiciones del entorno. Se logró integrar con éxito los módulos de seguridad (cinturón y punto ciego), las luces automáticas e intermitentes, y el encendido del vehículo.
Durante las pruebas se identificaron inconsistencias en la respuesta de los LEDs, atribuidas a fluctuaciones en la señal de entrada y a la falta de calibración del divisor de voltaje. No obstante, el diseño resultó válido y funcional, demostrando la viabilidad del enfoque modular en FPGA. Como áreas de mejora, se recomienda realizar calibraciones más precisas, simulaciones más detalladas y optimizar las conexiones para garantizar mayor estabilidad.


## Video explicativo
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/HNhlBs4aUqM"
  title="Video explicativo"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
></iframe>
---

> El codigo completo se encuentra en el repositorio al inicio de esta página.

