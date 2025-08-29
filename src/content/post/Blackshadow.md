---
layout: ../../layouts/post.astro
title: BlackShadow "Desarrollo de un robot minisumo autonomo profesional"
description: En este proyecto se presenta el desarrollo de un robot minisumo.
dateFormatted: Agosto 28, 2025
---

<!-- Lightbox Modal global (solo una vez al inicio) y justificado global -->
<style>
.justificado {
  text-align: justify;
  font-size: 1.05em;
  line-height: 1.8;
}
.lightbox-bg {
  display: none;
  position: fixed;
  z-index: 9000;
  left: 0; top: 0; width: 100vw; height: 100vh;
  background: rgba(0,0,0,0.8);
  justify-content: center;
  align-items: center;
}
.lightbox-bg.active { display: flex; }
.lightbox-img {
  max-width: 90vw;
  max-height: 80vh;
  border-radius: 7px;
  box-shadow: 0 0 25px #000;
}
.lightbox-close {
  position: absolute;
  top: 30px; right: 40px;
  color: #fff;
  font-size: 2em;
  font-weight: bold;
  cursor: pointer;
  background: rgba(0,0,0,0.5);
  border-radius: 50%;
  padding: 0.1em 0.4em;
  transition: background 0.2s;
}
.lightbox-close:hover { background: #e00; }
</style>
<script>
function openLightbox(imgSrc, altText) {
  var modal = document.getElementById('lightbox');
  var img = document.getElementById('lightbox-img');
  img.src = imgSrc;
  img.alt = altText;
  modal.classList.add('active');
}
function closeLightbox(event) {
  if(event) event.stopPropagation();
  document.getElementById('lightbox').classList.remove('active');
}
</script>
<div id="lightbox" class="lightbox-bg" onclick="closeLightbox()">
  <span class="lightbox-close" onclick="closeLightbox(event)">&times;</span>
  <img id="lightbox-img" class="lightbox-img" src="" alt="">
</div>

<div class="justificado">

# **Diagrama esquemático**

<div>
  <img src="/assets/images/posts/blackshadowD/Schematic.png" alt="Diagrama esquemático" 
    style="max-width: 100%; height: auto; cursor: zoom-in;" 
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 1. Diagrama esquemático de la tarjeta de control del minisumo
  </p>
</div>

El diagrama esquemático de la tarjeta de control del minisumo se muestra en la figura 1. Este circuito puede dividirse en cinco etapas principales:

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

Cada una de estas etapas cumple una función específica que contribuye al desempeño óptimo y seguro del minisumo durante la competencia.

## Etapa de Regulación

<div>
  <img src="/assets/images/posts/blackshadowD/Bateria.png" alt="Batería LiPo TATTU 450 mAh 3S" 
    style="max-width: 100%; height: auto; cursor: zoom-in;" 
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 2. Batería LiPo TATTU 450 mAh 3S utilizada en el minisumo
  </p>
</div>

En esta etapa se localiza la entrada para la alimentación del circuito.  
Dado que se requiere una fuente de energía independiente de la red AC, se optó por utilizar una batería LiPo de **3S**, capaz de proporcionar hasta **12.2 V** cuando está completamente cargada. La batería seleccionada fue el modelo **TATTU 450 mAh 3S**, mostrada en la *Figura 2*.  

Una vez definida la batería, se diseñó el circuito de regulación empleando un **regulador LM7805** y dos **diodos 1N4003**. Estos diodos cumplen la función de proteger el sistema contra inversión de polaridad y de salvaguardar al regulador y demás componentes en caso de picos de voltaje.  

Finalmente, esta etapa incorpora dos **capacitores de 100 µF**, cuya función es filtrar el voltaje regulado, eliminando ruidos y pequeñas variaciones.


## Etapa de potencia

## Etapa de potencia

Esta etapa se encarga de recibir señales de control del microcontrolador para decidir el sentido de giro y la velocidad de los motores, proporciona suficiente corriente y voltaje a los motores que el microcontrolador no puede entregar directamente, se seleccionó el [DRV8871](https://www.ti.com/product/DRV8871?utm_source=google&utm_medium=cpc&utm_campaign=asc-null-null-GPN_EN-cpc-pf-google-ww_en_cons&utm_content=DRV8871&ds_k=DRV8871&DCM=yes&gclsrc=aw.ds&gad_source=1&gad_campaignid=14388345080&gbraid=0AAAAAC068F0xJ3rT1tbuoAwJrG_XxBSnj&gclid=Cj0KCQjw_L_FBhDmARIsAItqgt6wGQYhOLwpQqJVhBRKdZShbvXQu-KxwfCC6zK3k0wVsP65_sEquZAaAmG3EALw_wcB#tech-docs) como driver de control de cada motor gracias a su capacidad para manejar hasta 3.6A de corriente y su amplio rango de voltaje el cual va desde 6.5V hasta 45V, de igual forma en el datasheet del componente se nos indica que se debe colocar una resistencia de 15Khz entre su pin ILIM y GND con la finalidad de limitar la corriente. Como recomendación se debe aislar la etapa de potencia de la de control mediante opto acopladores con la finalidad de evitar ruidos e interferencia que se pueda presentar en el futuro.

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

<div>
  <img src="/assets/images/posts/blackshadowD/SensorIR.jpg" alt="Sensor infrarrojo JS40F utilizado en el minisumo"
    style="max-width: 100%; height: auto; cursor: zoom-in;"
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 3. Sensor infrarrojo JS40F utilizado en el minisumo
  </p>
</div>

En esta etapa se encuentran los conectores destinados a la conexión de los diferentes sensores del minisumo. Para la detección del oponente se emplearon sensores de distancia digitales JS40F (figura 3), mientras que para la detección de la línea blanca y evitar que el robot salga del dojo se seleccionaron sensores de línea ML1.

Asimismo, se incorporó un conector de VCC y GND con el propósito de alimentar de forma adecuada cada sensor. Durante la fase de desarrollo, el minisumo utiliza un total de tres sensores infrarrojos JS40F para detección de distancia y dos sensores ML1 para la detección de línea.

# **Diseño del PCB**

<div>
  <img src="/assets/images/posts/blackshadowD/PCB_layout.jpg" alt="Vista general del diseño de PCB" 
    style="max-width: 100%; height: auto; cursor: zoom-in;" 
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 4. Vista general del diseño de PCB
  </p>
</div>

Una vez verificada la funcionalidad del diagrama esquemático, se implementó el diseño en el software EAGLE. Considerando las restricciones de tamaño para competencias de minisumo (10 cm x 10 cm), se decidió utilizar componentes SMD para reducir el área ocupada por la PCB. Como resultado, la tarjeta tiene dimensiones finales de **6 cm x 4 cm**, lo que permite su instalación horizontal dentro del minisumo y deja espacio libre para otros elementos mecánicos.

La placa está diseñada en **dos capas**, lo que facilita el ruteo de señales y la separación adecuada entre líneas de potencia y señales de control, ayudando a minimizar interferencias y ruido eléctrico.  

La PCB se mando a fabricar en JLCPCB con la finalidad de evitar errores de fabricación y obtener un acabo profesional.
En las figuras 3 a 5 se presenta la capa inferior y superior de la PCB.

<div>
  <img src="/assets/images/posts/blackshadowD/BottomLayout.jpg" alt="Capa inferior de la PCB" 
    style="max-width: 100%; height: auto; cursor: zoom-in;" 
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 5. Capa inferior de la PCB
  </p>
</div>

<div>
  <img src="/assets/images/posts/blackshadowD/TopLayout.jpg" alt="Capa superior de la PCB" 
    style="max-width: 100%; height: auto; cursor: zoom-in;" 
    onclick="openLightbox(this.src, this.alt);">
  <p style="text-align: center; font-style: italic; font-size: 1.05em;">
    Figura 6. Capa superior de la PCB
  </p>
</div>

# **Programación del microcontrolador**

# **Programación del microcontrolador**

En el [repositorio](https://github.com/QuikeLRD/BlackShadow) se muestra el código completo del minisumo el cual fue programado mediante el IDE mikroC PRO for PIC debido a que está correctamente optimizado para trabajar con microcontroladores PIC de microchip, facilitando la tarea y reduciendo el tiempo.
</div>