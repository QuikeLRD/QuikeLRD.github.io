---
slug: simulacion-automovil
title: Sistema de simulación de un automóvil basado en FPGA
summary: En este proyecto se presenta el desarrollo de un sistema de simulación automotriz que integra diversas funcionalidades modernas, utilizando una tarjeta FPGA como núcleo de control.
---

## ¿Qué se hizo?

A lo largo del proyecto trabajé en equipo con [Jesús Adrián](https://www.linkedin.com/in/jes%C3%BAs-adri%C3%A1n-mondragon-ledesma-b683701a2/) con el objetivo de desarrollar un sistema de simulación automotriz sobre FPGA que integrara funciones modernas de un vehículo real, como encendido y apagado, luces interiores y exteriores, sensores de seguridad (cinturón y punto ciego), faros automáticos mediante LDR, limpiaparabrisas sensibles a humedad, indicadores en LEDs y buzzer de alerta, así como sensores ultrasónicos para maniobras de reversa.

## ¿Cómo se hizo?

Para llevar a cabo el proyecto se utilizó una tarjeta FPGA Cyclone IV programada en VHDL mediante el software Quartus. El desarrollo se realizó bajo un enfoque modular, dividiendo cada función del automóvil en bloques independientes (encendido, luces, sensores de punto ciego, luces intermitentes, faros, etc).
El procedimiento incluyó: instalación y configuración del entorno de diseño, definición de entradas y salidas por módulo, programación en VHDL, simulaciones mediante testbench digital, síntesis del diseño y posterior implementación en hardware. Se emplearon sensores como LDR e IR, un ADC0804 para convertir señales analógicas a digitales, y diversos LEDs y buzzers. Finalmente, se verificó el funcionamiento real mediante pruebas físicas y comparación con las simulaciones, utilizando LEDs indicadores y herramientas de medición básicas.

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


> El código completo se encuentra en el repositorio al inicio de esta página.