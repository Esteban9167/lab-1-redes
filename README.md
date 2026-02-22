# Lab #1 – Red – Interconexión
## Navegación hacia disneyplus.com

**Asignatura:** Redes y Comunicación de Datos  
**Integrantes:** Esteban Sequeda Henao
**Fecha:**  21 de febrero 2026  

---

# Lab #1 – Interconexión de Red
## Solución de Navegación para Pepito Pérez y Familia

🎥 **Video de presentación:**  
https://youtu.be/s3rhyPC7yEk

---

# 1. Introducción

El presente laboratorio tiene como objetivo diseñar e implementar una solución de red que permita a Pepito Pérez y su familia acceder al sitio web disneyplus.com desde su hogar utilizando dispositivos cableados e inalámbricos. La solución fue desarrollada en Cisco Packet Tracer, integrando una red doméstica LAN/WLAN con un servidor remoto mediante la simulación de Internet utilizando el objeto Cloud-PT.

---

# 2. Descripción del Problema

Pepito Pérez y su familia necesitan navegar en disneyplus.com desde PC, laptop y smartphone, utilizando red cableada e inalámbrica y demostrando técnicamente que la comunicación es exitosa bajo el modelo OSI y TCP/IP.

---

# 3. Topología Propuesta

Se implementó una topología en estrella extendida.

## Estructura

- Dispositivos finales (PC, Laptop, Smartphone) 
- Switch (LAN)
- Access Point (WLAN)
- Router doméstico
- Cloud-PT (Simulación WAN/Internet)
- Router ISP
- Servidor HTTP + DNS

## Justificación

Facilidad de administración, escalabilidad, aislamiento de fallos y uso común en redes reales, principalmente porque es la que en la vida real y uso cotidiano se suele usar en casa.

---

# 4. Tipos de Red Utilizados

## LAN

Red cableada dentro del hogar, toda la red cableada ethernet, especialmente desde el Router → Switch → PC, esto con la finalidad de probar que las conexiones por cable también funcionaban aunque el problema inicial no nos pedía que utilizáramos PC.

## WLAN

Red inalámbrica mediante Access Point. Aunque se pudo reemplazar por un Home Router que integra ya el switch, el problema requería uso de switch por lo cual se optó por un Access Point y separarlos.

## WAN

Simulada con Cloud-PT para interconectar redes geográficamente separadas.

---

# 5. Dispositivos y Funciones

- Router: Capa 3 y realiza enrutamiento entre redes.
- Switch: Capa 2 e interconecta dispositivos dentro de la LAN.
- Access Point: Permite conexión WiFi bajo estándar IEEE 802.11.
- Servidor: Ejecuta servicios HTTP y DNS.

---

# 6. Servicios Implementados

- DNS: Traduce nombres de dominio a direcciones IP.
- HTTP: Permite acceso al sitio web desde el navegador.

---

# 7. Modelos y Protocolos

## Modelo OSI
Física, Enlace de Datos, Red, Transporte, Sesión, Presentación y Aplicación.

## Modelo TCP/IP
Acceso a Red, Internet, Transporte y Aplicación.

## Protocolos utilizados
IP, TCP, DNS y HTTP.

---

# 8. Validación Técnica

Se realizaron pruebas de conectividad mediante:

- Ping por dirección IP.
- Ping por nombre de dominio.
- Navegación web mediante Web Browser.

Las pruebas confirmaron comunicación exitosa bajo arquitectura TCP/IP.

---

# 9. Problemas y Soluciones Técnicas

## Problema detectado

Los dos routers no se estaban comunicando.

En Router_ISP:

```
Serial0/1/0      unassigned   up   up
Serial0/1/0.1    unassigned   up   up
```

Error: La subinterfaz no tenía IP configurada.

---

## Solución aplicada

### Router_ISP

```bash
enable
configure terminal
interface serial0/1/0
encapsulation frame-relay
no shutdown
exit

interface serial0/1/0.1 point-to-point
ip address 10.0.0.2 255.255.255.252
frame-relay interface-dlci 102
no shutdown
exit
```

### Router1

```bash
interface serial0/1/0
encapsulation frame-relay
no shutdown
exit

interface serial0/1/0.1 point-to-point
ip address 10.0.0.1 255.255.255.252
frame-relay interface-dlci 102
no shutdown
```

Verificación:

```bash
show ip interface brief
show frame-relay map
ping 10.0.0.2
```

---

# 10. Configuración de Puertos Seriales en Cloud-PT

## Paso 1 — Conectar físicamente

- Router1 Serial0/1/0 → Cloud Serial0
- Router_ISP Serial0/1/0 → Cloud Serial1
- Solo uno debe ser DCE.

## Paso 2 — Crear circuito Frame Relay

En Cloud → Config → Frame Relay:

- From Port: Serial0
- To Port: Serial1
- DLCI: 102
- Add

## Paso 3 — Verificar

```bash
show frame-relay map
```

Debe indicar:

```
status defined, active
```

---

# 11. Referencias (Formato IEEE)

[1] Cisco Systems, *Cisco Packet Tracer User Guide*, Cisco Networking Academy, 2023.  
[2] A. S. Tanenbaum & D. J. Wetherall, *Computer Networks*, 5th ed., Pearson, 2011.  
[3] J. F. Kurose & K. W. Ross, *Computer Networking: A Top-Down Approach*, 7th ed., Pearson, 2017.  
[4] IEEE, *IEEE Standard for Local and Metropolitan Area Networks (IEEE 802.11)*, 2020.  

---

# 12. Videos Consultados (Formato IEEE)

[5] YouTube, “_r3fJi1s6Q4,” YouTube video. Available: https://www.youtube.com/watch?v=_r3fJi1s6Q4  

[6] YouTube, “1LhbvbPcdQE,” YouTube video. Available: https://www.youtube.com/watch?v=1LhbvbPcdQE  

[7] YouTube, “VtY2Ak-fo0c,” YouTube video. Available: https://www.youtube.com/watch?v=VtY2Ak-fo0c  

[8] YouTube, “IQakg45Fe5Q,” YouTube video. Available: https://www.youtube.com/watch?v=IQakg45Fe5Q  

[9] YouTube, “-_UabFPUVSo,” YouTube video. Available: https://www.youtube.com/watch?v=-_UabFPUVSo  

[10] YouTube, “foKHWh3cD80,” YouTube video. Available: https://www.youtube.com/watch?v=foKHWh3cD80  

[11] YouTube, “YdM7yBrtAck,” YouTube video. Available: https://www.youtube.com/watch?v=YdM7yBrtAck  

---

# 13. Declaración de Uso de Inteligencia Artificial

Cuál es el beneficio entre conectar un punto de acceso inalámbrico y un router patee Tracer ?

como hago la colectividad entre reuter para asignar los puertos?

La diferencia y el beneficio de conectar un punto de acceso inalámbrico (Access Point) a un router en Packet Tracerdepende del objetivo de la red.

1️⃣ Router (solo)

Función principal:
• Conectar redes diferentes (ej: LAN ↔ Internet).
• Asignar IP (si tiene DHCP configurado).
• Enrutar tráfico entre subredes.

Limitación:
• No siempre incluye conectividad inalámbrica.
• Los equipos WiFi no pueden conectarse directamente si el router no tiene módulo wireless.

2️⃣ Router + Punto de Acceso (AP)

Beneficio principal:
Permite que dispositivos inalámbricos (laptops, celulares, tablets) se conecten a la red cableada.

Ventajas técnicas:
• Extiende la red cableada a WiFi.
• Permite movilidad de usuarios.
• No crea otra red (si está en modo AP), solo amplía la existente.
• Mejora cobertura si el router está lejos.
• Permite segmentar si se configura con VLAN.

🔎 En Packet Tracer

Si conectas:
Router → Switch → Access Point → Laptop inalámbrica

Obtienes:
• La laptop recibe IP del router (si hay DHCP).
• Puede hacer ping a otros dispositivos.
• Simulación realista de red empresarial.

📌 Diferencia clave

Router: Enruta tráfico, puede asignar IP, conecta redes.  
Access Point: Solo transmite señal WiFi, no asigna IP, conecta dispositivos inalámbricos a la misma red.

🎯 ¿Cuál es el beneficio real?

Agregar un AP:
• Permite conexión inalámbrica sin cambiar la arquitectura.
• Es más económico que comprar un router inalámbrico nuevo.
• Escalable (puedes poner varios AP).
• Ideal para oficinas, colegios, centros comerciales.

---

Para el desarrollo de este laboratorio se utilizó ChatGPT (OpenAI) como apoyo para organización del contenido, redacción técnica y explicación teórica. La información fue validada con material oficial de Cisco Networking Academy con el método de prueba y error.

---

# Entrega Final

Se entregó en la plataforma:

- Link del video
- Link del repositorio
- Actas de reunión

Entrega realizada antes de las 23:00.
