---
layout: ../../layouts/post.astro
title: BlackShadow "Desarrollo de un robot minisumo autonomo profesional"
description: En este proyecto se presenta el desarrollo de un robot minisumo.
dateFormatted: Agosto 28, 2025
---

# **Diagrama esquemático**

<div style="text-align: justify; font-size: 1.05em; line-height: 1.8;">
El diagrama esquemático de la tarjeta de control del minisumo se muestra en la figura 1. Este circuito puede dividirse en cinco etapas principales:
<br><br>
<ol>
  <li>
    <b>Etapa de potencia:</b><br>
    Encargada de controlar los actuadores (motores). Incluye el puente H y los componentes necesarios para garantizar el correcto funcionamiento y la entrega de corriente suficiente a los motores.
  </li>
  <li>
    <b>Etapa de regulación:</b><br>
    Regula el voltaje de entrada para suministrar una tensión estable de 5V, necesaria para alimentar la lógica y los componentes electrónicos del circuito.
  </li>
  <li>
    <b>Etapa de control:</b><br>
    Constituida por el microcontrolador, que actúa como el cerebro del sistema. Procesa las señales provenientes de los sensores, gestiona la lógica de operación y controla los motores.
  </li>
  <li>
    <b>Etapa de sensado:</b><br>
    Integrada por sensores infrarrojos y conectores, permite la lectura de diversos periféricos y la detección del entorno, esencial para la toma de decisiones durante la competencia.
  </li>
  <li>
    <b>Etapa de interfaz de usuario:</b><br>
    Facilita la comunicación con el operador, mostrando información visual y permitiendo la configuración o indicación de diferentes estados que pueden presentarse a lo largo del combate.
  </li>
</ol>
<br>
Cada una de estas etapas cumple una función específica que contribuye al desempeño óptimo y seguro del minisumo durante la competencia.
</div>

## Etapa de Regulación

En esta etapa se localiza la entrada para la alimentación del circuito.  
Dado que se requiere una fuente de energía independiente de la red AC, se optó por utilizar una batería LiPo de **3S**, capaz de proporcionar hasta **12.2 V** cuando está completamente cargada. La batería seleccionada fue el modelo **TATTU 450 mAh 3S**, mostrada en la *Figura 2*.  

Una vez definida la batería, se diseñó el circuito de regulación empleando un **regulador LM7805** y dos **diodos 1N4003**. Estos diodos cumplen la función de proteger el sistema contra inversión de polaridad y de salvaguardar al regulador y demás componentes en caso de picos de voltaje.  

Finalmente, esta etapa incorpora dos **capacitores de 100 µF**, cuya función es filtrar el voltaje regulado, eliminando ruidos y pequeñas variaciones. Véase la *Figura 3*.  


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

Esta etapa está conformada por cinco diodos LED con sus respectivas resistencias, las cuales regulan el voltaje recibido para evitar daños en los componentes. Además, incorpora un DIP switch que funciona como medio de control para seleccionar las distintas rutinas que pueda ejecutar el minisumo.

De los cinco diodos LED, el D1 se enciende en cuanto la tarjeta recibe alimentación, lo que resulta de gran utilidad como indicador de encendido y para la verificación inicial del correcto funcionamiento del sistema.

## Etapa de sensado

En esta etapa se encuentran los conectores destinados a la conexión de los diferentes sensores del minisumo. Para la detección del oponente se emplearon sensores de distancia digitales JS40F, mientras que para la detección de la línea blanca y evitar que el robot salga del dojo se seleccionaron sensores de línea ML1.

Asimismo, se incorporó un conector de VCC y GND con el propósito de alimentar de forma adecuada cada sensor. Durante la fase de desarrollo, el minisumo utiliza un total de tres sensores infrarrojos JS40F para detección de distancia y dos sensores ML1 para la detección de línea.