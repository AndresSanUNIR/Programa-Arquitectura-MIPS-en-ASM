# Programa-Arquitectura-MIPS-en-ASM
Análisis de Optimización de Pipeline en Arquitectura MIPS Este repositorio contiene el análisis técnico de la ejecución de un algoritmo de procesamiento de vectores ($Y = A \cdot X + B$) en un procesador segmentado.

# Análisis de Optimización de Pipeline en Arquitectura MIPS

Este repositorio contiene el análisis técnico de la ejecución de un algoritmo de procesamiento de vectores ($Y = A \cdot X + B$) en un procesador segmentado.

## 📊 Resumen de Resultados
Se comparó una implementación base frente a una optimizada mediante reordenación de instrucciones para mitigar riesgos de datos.

| Métrica | Implementación Base | Implementación Optimizada | Mejora |
| :--- | :---: | :---: | :---: |
| **Ciclos Totales** | 117 | 101 | **13.7%** |
| **Total de Stalls** | 24 | 16 | **33.3%** |
| **CPI (Cycles Per Inst)** | 1.31 | 1.13 | **13.7%** |

## 🔍 Hallazgos Técnicos
1. **Riesgo Identificado**: Se detectó un *Load-Use Hazard* crítico entre la carga de memoria (`lw`) y la operación aritmética (`mul`).
2. **Solución**: Se aplicó una técnica de reordenación, insertando una instrucción independiente (`addi`) en la burbuja del pipeline.
3. **Impacto**: La eliminación del stall de memoria permitió una ejecución más fluida, acercando el CPI al ideal teórico de 1.0.

## 🛠️ Herramientas Utilizadas
* **Simulador**: MARS (MIPS Assembler and Runtime Simulator).
* **Herramientas de Análisis**: MIPS Pipeline Visualization, Instruction Counter e Instruction Statistics.
