# Cybersecurity Portfolio 

Este repo es donde documento los proyectos que voy construyendo para profundizar en SOC, threat hunting, detection engineering y automatización de seguridad. No son tutoriales copiados ni labs de un curso: cada uno lo armo desde cero, lo rompo, lo arreglo y anoto lo que voy aprendiendo en el proceso.

La idea detrás de esto es simple: quiero que cualquier reclutador o ingeniero que revise este perfil pueda ver no solo que "sé usar" ciertas herramientas, sino que entiendo cómo se conectan entre sí en un entorno real de operaciones de seguridad.

Voy a ir actualizando este README a medida que avanzo. Algunos proyectos van a tardar más que otros — varios dependen de hardware que todavía estoy consiguiendo (RAM, storage para las VMs, etc).

---

## Estado actual

| # | Proyecto | Estado | Enfoque |
|---|----------|--------|---------|
| 1 | [SOC Home Lab Enterprise](#1--soc-home-lab-enterprise) | 🟡 En progreso | SIEM, detección, MITRE ATT&CK |
| 2 | [Threat Hunting Platform](#2-threat-hunting-platform) | ⬜ Pendiente | Sigma/YARA, correlación de IOCs |
| 3 | [SOAR Automation Platform](#3-soar-automation-platform) | ⬜ Pendiente | Respuesta automatizada a incidentes |
| 4 | [AI Security Analyst](#4-ai-security-analyst) | ⬜ Pendiente | LLMs aplicados a triage y reportes |
| 5 | [Cloud SOC (Azure/AWS)](#5-cloud-soc-azureaws) | ⬜ Pendiente | Seguridad en cloud, IAM, logging |
| 6 | [Malware Analysis Sandbox](#6-malware-analysis-sandbox) | ⬜ Pendiente | Análisis dinámico/estático de malware |
| 7 | [Detection Engineering Lab](#7-detection-engineering-lab) | ⬜ Pendiente | Reglas Sigma/YARA/KQL/SPL |
| 8 | [Purple Team Lab](#8-purple-team-lab) | ⬜ Pendiente | Simulación de ataques vs detección |
| 9 | [Phishing Analysis Platform](#9-phishing-analysis-platform) | ⬜ Pendiente | Análisis de correos y URLs maliciosas |
| 10 | [DFIR Platform](#10-dfir-platform) | ⬜ Pendiente | Forense digital y respuesta a incidentes |
| 11 | [Zero Trust Architecture Lab](#11-zero-trust-architecture-lab) | ⬜ Pendiente | MFA, segmentación, PAM |
| 12 | [Executive Security Dashboard](#12-executive-security-dashboard) | ⬜ Pendiente | KPIs, MTTR, risk scoring |

---

## 1. 🛡️ SOC Home Lab Enterprise

**Estado:** En progreso

La base de todo el roadmap. La idea es montar un mini SOC funcional, no una demo de cinco minutos: ingesta de logs reales, detección con reglas propias, y los dashboards que cualquier analista L1/L2 usaría en su día a día.

**Stack:**
- Wazuh
- Elastic Stack (ELK)
- Security Onion
- Sysmon
- Suricata
- Zeek

**Lo que estoy aprendiendo en el camino:**
- Cómo se ve una arquitectura de SIEM de verdad, no solo el "dashboard bonito"
- Ingesta y normalización de logs desde distintas fuentes
- Escribir detecciones mapeadas a MITRE ATT&CK en lugar de alertas genéricas
- Threat hunting manual antes de automatizar nada

> Repo: *(pendiente — lo subo cuando tenga la primera versión estable)*

---

## 2. Threat Hunting Platform

Un sistema propio que recolecta logs, cruza IOCs contra fuentes externas y correlaciona eventos para generar alertas con contexto, no solo "matches" sueltos.

**Stack:** Sigma Rules · YARA · IOC matching · VirusTotal API · KQL / SPL

**Por qué lo hago:** quiero pasar de "ver una alerta" a entender por qué se disparó y si tiene sentido en el contexto del entorno. Es la diferencia entre un analista que sigue un playbook y uno que piensa como atacante.

---

## 3. SOAR Automation Platform

Automatización real de respuesta a incidentes. Ejemplos del tipo de flujo que quiero construir:

- IP maliciosa detectada → bloqueo automático en firewall
- Hash malicioso identificado → aislamiento del endpoint

**Stack:** Shuffle · TheHive · Cortex · Python · PowerShell

El objetivo acá no es solo "automatizar por automatizar", sino reducir el tiempo de respuesta en los pasos repetitivos para que un analista se enfoque en lo que realmente necesita criterio humano.

---

## 4. AI Security Analyst

Este es el más ambicioso del roadmap. La idea es usar modelos de lenguaje para apoyar el trabajo de un SOC: análisis de logs, explicación de incidentes en lenguaje claro, generación de reportes y un primer triage automatizado.

**Stack:** Python · Ollama · OpenAI API · LangChain · Streamlit

No busco reemplazar el criterio de un analista — busco entender hasta dónde un LLM puede acelerar el trabajo sin generar falsos positivos de confianza ("la IA dijo que está bien" no es una conclusión válida en seguridad).

---

## 5. Cloud SOC (Azure/AWS)

Simulación de un entorno cloud vulnerable para practicar detección y respuesta fuera del mundo on-prem.

**Incluye:** Microsoft Sentinel · Defender for Cloud · CloudTrail · GuardDuty · ataques a IAM · análisis de logs cloud

Cloud security tiene una lógica distinta a la de un SOC tradicional — los logs son distintos, los vectores de ataque son distintos, y este proyecto es para no quedarme solo con la teoría.

---

## 6. Malware Analysis Sandbox

Entorno aislado y seguro para analizar muestras de malware sin arriesgar nada fuera del lab.

**Stack:** REMnux · FLARE VM · Cuckoo Sandbox · CAPE Sandbox

Acá también quiero meter algo de automatización para generar reportes y parsers propios en lugar de depender 100% de herramientas ya armadas.

---

## 7. Detection Engineering Lab

Construcción de reglas de detección avanzadas — no las que vienen por defecto en cualquier SIEM, sino las que realmente atrapan comportamiento sospechoso.

**Formatos:** Sigma · YARA · KQL · SPL

**Objetivo de detección:** ransomware, lateral movement, persistence, abuso de PowerShell.

Esta es la habilidad que más se pide hoy en ofertas de SOC L3 / Detection Engineer, y es exactamente donde quiero ser fuerte.

---

## 8. Purple Team Lab

Ataque y defensa en el mismo entorno, para ver el ciclo completo: qué genera logs, cómo se detecta, y cómo se responde.

**Stack:** Atomic Red Team · Caldera · MITRE ATT&CK · Wazuh · Sentinel

La parte valiosa de esto no es "lanzar el ataque" — es ver exactamente qué rastro deja y comparar eso contra lo que mis reglas de detección realmente capturan.

---

## 9. Phishing Analysis Platform

Una plataforma para analizar correos de phishing de punta a punta: headers, URLs, adjuntos, sandbox y reputación.

Es una de las tareas más comunes del día a día de un SOC Analyst, así que quiero tener un proceso propio y documentado para esto, no solo "lo reviso a ojo".

---

## 10. DFIR Platform

Forense digital + respuesta a incidentes: análisis de timeline, análisis de memoria, extracción de IOCs y recolección de artefactos.

**Stack:** Volatility · Autopsy · Velociraptor

---

## 11. Zero Trust Architecture Lab

Diseño de una arquitectura Zero Trust real: MFA, Conditional Access, segmentación de red, PAM y bastion hosts.

Este proyecto está más orientado a Security Engineer / IAM Engineer que a SOC puro, pero es una pieza clave para entender seguridad desde el diseño y no solo desde la detección.

---

## 12. Executive Security Dashboard

Un dashboard tipo enterprise pensado para liderazgo, no para analistas: MTTR, volumen de incidentes, mapeo a MITRE ATT&CK, vulnerabilidades abiertas, KPIs y risk score.

**Stack:** Power BI · Grafana · Kibana

La seguridad también se vende con datos. Saber traducir todo lo técnico de los proyectos anteriores en algo que un CISO o gerente pueda leer en cinco minutos es una habilidad que casi nadie practica y que marca diferencia.

---

## Sobre este repo

Voy a ir subiendo cada proyecto en su propia carpeta/repo con su documentación específica (arquitectura, decisiones técnicas, problemas que me encontré y cómo los resolví). Si algo no está al 100% terminado lo voy a marcar como tal — prefiero ser honesto con el progreso real que inflar el estado de las cosas.

Si encuentras algo que se puede mejorar o tienes feedback, los issues están abiertos.

**Contacto:** [github.com/Andrew11001](https://github.com/Andrew11001)
