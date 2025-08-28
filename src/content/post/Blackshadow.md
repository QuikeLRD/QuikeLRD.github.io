---
layout: ../../layouts/post.astro
title: BlackShadow "Desarrollo de un robot minisumo autonomo profesional"
description: En este proyecto se presenta el desarrollo de un robot minisumo.
dateFormatted: Agosto 28, 2025
---

# **Diagrama esquemático**

El diagrama esquemático de la tarjeta de control del minisumo se muestra en la figura 1. Este circuito puede dividirse en cinco etapas principales:

1. **Etapa de potencia:**  
   Encargada de controlar los actuadores (motores). Incluye el puente H y los componentes necesarios para garantizar el correcto funcionamiento y la entrega de corriente suficiente a los motores.

2. **Etapa de regulación:**  
   Regula el voltaje de entrada para suministrar una tensión estable de 5V, necesaria para alimentar la lógica y los componentes electrónicos del circuito.

3. **Etapa de control:**  
   Constituida por el microcontrolador, que actúa como el cerebro del sistema. Procesa las señales provenientes de los sensores, gestiona la lógica de operación y controla los motores.

4. **Etapa de sensado:**  
   Integrada por sensores infrarrojos y conectores, permite la lectura de diversos periféricos y la detección del entorno, esencial para la toma de decisiones durante la competencia.

5. **Etapa de interfaz de usuario:**  
   Facilita la comunicación con el operador, mostrando información visual y permitiendo la configuración o indicación de diferentes estados que pueden presentarse a lo largo del combate.

Cada una de estas etapas cumple una función específica que contribuye al desempeño óptimo y seguro del minisumo durante la competencia.

## Etapa de regulación

En esta etapa se localiza la entrada para la alimentación del circuito, dado a que se necesita de una fuente de energía que no requiere conexión directa a AC se optó por usar una bateria lipo de 3s con la capacidad de proporcionar hasta 12.2V cuando estan completamente cargadas, la bateria seleccionada fue TATTU 450 mah 3S, la cual se muestra en la figura 2. Una vez seleccionada la bateria se diseño un circuito para la regulación para ello se utilizo un regulador LM7805 y dos diodos 1N4003 cuya función es proteger al circuito contra la inversión de polaridad de la bateria ademas de proteger al regulador y otros componentes en caso de picos de voltaje. Finalmente en esta etapa se localizan dos capacitores de 100uF cuya función es filtrar el voltaje regulado, eliminando ruidos y pequeñas variacioens, ver figura 3.

## Etapa de potencia

Esta etapa se encarga de recibir señales de control del microcontrolador para decidir el sentido de giro y la velocidad de los motores, proporciona suficiente corriente y voltaje a los motores que el microcontrolador no puede entregar directamente, se selecciono el DRV8871 como driver de control de cada motor gracias a su capacidad para manejar hasta 3.6A de corriente y su amplio rango de voltaje el cual va desde 6.5V hasta 45V, de igual forma en el datasheet del componente se nos indica que se debe colocar una resistencia de 15Khz entre su pin ILIM y GND con la finalidad de limitar la corriente. Como recomendación se debe aislar la etapa de potencia de la de control mediante opto acopladores con la finalidad de evitar ruidos e interferencia que se pueda presentar en el futuro.

## Etapa de control

La etapa de control principal está formada por el microcontrolador **PIC18F26K22**, que es el núcleo lógico del minisumo.  
Sus funciones principales son:

- **Procesar señales de sensores** para interpretar el entorno.
- **Tomar decisiones** (estrategia de combate, evasión, ataque).
- **Controlar los motores** enviando señales a los drivers de potencia.
- **Gestionar entradas y salidas** para interactuar con el usuario (botones, LEDs).
- **Permitir programación y depuración** mediante el pin MCLR y el conector de programación.

## Etapa interfaz de usuario

Esta etapa se comforma por 5 diodos leds con sus respectivas resistencias para regular el voltaje que reciben y evitar dañar algun componente, ademas de un dip switch cuya función es ser un medio de control para cada rutina que pueda tener el minisumo, de los 5 diodos leds colocados, D1 se encarga de activarse en cuanto recibe energía la tarjeta siendo de gran utilidad para la prueba de funcionamiento de la misma.

## Etapa de sensado

En esta etapa se localizan diversos conectores para la utilización de sensores, los sensores utilizados para detectar al oponente fueron JS40F Digital Distance Sensor (figura 4)
mientras que los seleccionados para detectar linea blanca y evitar salirse del dojo son Micro Line Sensor ML1. Ademas se ha colocado un conector de VCC y GND con la finaliad de alimentar cada sensor utilizado, el minisumo al momento del desarrollo emplea 3 sensores IR para distancia y 2 ML1 de detección de linea.

