# Touch Lamp — Lámpara Vintage con Sensor Táctil

![PCB Top View](https://raw.githubusercontent.com/picli3/touch-lamp/main/docs/top_view.png)

PCB con 3 LEDs que simulan ser filamento incandescente, diseñada para integrarse en una **lámpara vintage**. El control táctil está basado en el circuito integrado **SGL8022W**, que permite encendido/apagado y regulación de intensidad luminosa (dimmer) con solo tocar el electrodo sensor.

## Características

- **Control táctil** basado en SGL8022W (SOP-8)
- **3 LEDs** dispuestos para simular un filamento incandescente vintage
- **Regulación de intensidad** — toques repetidos cambian el brillo (ciclo: apagado → bajo → medio → alto → apagado)
- **Alimentación:** 5 VCC
- **Formato compacto** ideal para montaje dentro de lámparas decorativas
- Diseñado en **KiCad 10.0**

## Componentes Principales

| Ref | Componente | Descripción | Footprint |
|-----|-----------|-------------|-----------|
| U1 | **SGL8022W** | IC touch sensor para regulación de brillo LED | SOP-8 |
| Q1 | NPN transistor | Driver de salida para LEDs | SOT-23-3 |
| D1-D3 | LED 0603 | LEDs simulando filamento incandescente | 0603 LED |
| C1 | 100 nF | Capacitor de desacople | 0603 |
| C2 | 10 µF | Capacitor de filtro de alimentación | 0805 |
| C3 | 10 nF | Capacitor de oscilación del SGL8022W | 0603 |
| R1 | 4.7 kΩ | Resistencia de polarización | 0603 |
| R2 | 1 kΩ | Resistencia de base del transistor | 0603 |
| R3 | 5.1 Ω | Resistencia limitadora de corriente de LEDs | 0603 |
| R4, R5 | 5.1 kΩ | Resistencias de configuración de modo | 0603 |

## Cómo Funciona

1. **Sensor táctil:** El SGL8022W detecta la capacitancia del cuerpo humano a través de un electrodo conectado al pin TI (Touch Input, pin 5).
2. **Procesamiento:** El chip interpreta los toques y controla la salida PWM en el pin SO (pin 7).
3. **Driver de salida:** La señal PWM pasa por un transistor NPN (Q1) que maneja los 3 LEDs en paralelo.
4. **Modos de operación:** Configurables mediante los pines OPT1/OPT2 y los jumpers JP1/JP2 en la PCB.

### Ciclo de operación por defecto

| Toque | Estado |
|-------|--------|
| 1er toque | Encendido — brillo bajo |
| 2do toque | Brillo medio |
| 3er toque | Brillo alto |
| 4to toque | Apagado |

## Archivos del Proyecto

| Archivo | Descripción |
|---------|-------------|
| `lampara_bintge.kicad_sch` | Esquemático en KiCad |
| `lampara_bintge.kicad_pcb` | Diseño de PCB en KiCad |
| `lampara_bintge.kicad_pro` | Proyecto KiCad |
| `lampara_bintge.kicad_prl` | Archivo de diseño de placa |

## BOM (Bill of Materials)

El archivo `BOM.csv` incluido en los releases contiene la lista completa de materiales con referencias, valores, footprints y descripciones.

## Licencia

Este proyecto se comparte con fines educativos y de hobby. Si lo usas o modificas, agradeceremos la atribución.
