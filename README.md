# Lab #1 – Red – Interconexión
## Navegación hacia disneyplus.com

**Asignatura:** Redes y Comunicación de Datos  
**Integrantes:** ___________________________  
**Fecha:** _________________________________  

---

# 1. Introducción

El presente laboratorio tiene como objetivo diseñar e implementar una topología de red que permita a Pepito Pérez y su familia navegar en el sitio web `disneyplus.com` desde su hogar, utilizando dispositivos cableados e inalámbricos.

La solución fue desarrollada y validada mediante **Cisco Packet Tracer**, simulando la red LAN/WLAN doméstica, la conexión WAN y el servidor remoto.

---

# 2. Objetivo General

Diseñar, implementar y validar una red LAN/WLAN conectada a una WAN simulada, demostrando la comunicación exitosa bajo los modelos **OSI** y **TCP/IP**.

---

# 3. Marco Teórico

## 3.1 Tipos de Red

- **LAN (Local Area Network):** Red que conecta dispositivos dentro del hogar.
- **WLAN (Wireless LAN):** Red inalámbrica utilizada por dispositivos móviles.
- **WAN (Wide Area Network):** Red que conecta la red doméstica con Internet.

---

## 3.2 Topologías de Red

Se analizaron las siguientes topologías:

- Bus  
- Anillo  
- Malla  
- Estrella  

Se seleccionó la **topología estrella**, ya que:

- Facilita la administración.
- Permite escalabilidad.
- Aísla fallos.
- Es la más utilizada en redes domésticas.

---

## 3.3 Modelos de Comunicación

### Modelo OSI

1. Física  
2. Enlace de Datos  
3. Red  
4. Transporte  
5. Sesión  
6. Presentación  
7. Aplicación  

### Modelo TCP/IP

1. Acceso a Red  
2. Internet  
3. Transporte  
4. Aplicación  

---

## 3.4 Protocolos Utilizados

- **DHCP:** Asignación automática de direcciones IP.
- **DNS:** Traducción de nombres de dominio a direcciones IP.
- **HTTP:** Transferencia de páginas web.
- **TCP:** Protocolo de transporte orientado a conexión.
- **IP:** Direccionamiento lógico de paquetes.
- **ICMP:** Protocolo utilizado para pruebas de conectividad (ping).

---

# 4. Diseño de la Topología

## 4.1 Componentes Utilizados

- Router doméstico
- Switch
- PC cableada
- Smartphone (WLAN)
- Cloud-PT (simulación de Internet)
- Servidor Web (Disney+)

---

## 4.2 Direccionamiento IP

Red LAN: `192.168.1.0/24`  
Gateway: `192.168.1.1`  
Servidor remoto: `200.10.10.2`  

Asignación dinámica mediante DHCP.

---

## 4.3 Diagrama de Red

*(Insertar aquí captura exportada desde Cisco Packet Tracer)*

---

# 5. Implementación en Cisco Packet Tracer

### Paso 1: Configuración del Router
- Asignación de IP al gateway.
- Activación del servicio DHCP.

### Paso 2: Configuración del DNS
- Registro del dominio `disneyplus.com` apuntando a la IP del servidor.

### Paso 3: Configuración del Servidor Web
- Activación del servicio HTTP.

### Paso 4: Conexión a la Cloud (WAN)
- Enlace entre router doméstico y red externa.

---

# 6. Validación de la Comunicación

## 6.1 Prueba con Ping

```bash
ping 192.168.1.1
ping 200.10.10.2
```

Resultado: Respuesta exitosa (Reply).

---

## 6.2 Prueba con Navegador Web

```
http://disneyplus.com
```

Resultado: Carga exitosa de la página web.

---

## 6.3 Validación en Modo Simulación

Se observó:

- Encapsulamiento del paquete.
- Paso por switch.
- Enrutamiento en el router.
- Tránsito por la Cloud.
- Respuesta del servidor.

---

# 7. Resultados

La red permitió comunicación exitosa entre los dispositivos locales y el servidor remoto.

Se validó:

- Conectividad IP (ICMP).
- Resolución de nombres (DNS).
- Navegación web (HTTP sobre TCP).

---

# 8. Dificultades Encontradas

- Configuración incorrecta del gateway.
- Errores iniciales en DNS.
- Problemas de direccionamiento IP.

---

# 9. Conclusiones

- La topología estrella es adecuada para redes domésticas.
- DHCP y DNS son fundamentales para la navegación web.
- El modelo OSI permite comprender el flujo de datos.
- Packet Tracer valida el funcionamiento realista de la red.

---

# 10. Referencias (Formato IEEE)

[1] Cisco Networking Academy, *Introduction to Networks v7.0*, Cisco Press, 2020.  
[2] A. S. Tanenbaum y D. Wetherall, *Computer Networks*, 5th ed., Pearson, 2011.  
[3] IETF, “RFC 791 – Internet Protocol,” 1981.  
[4] IETF, “RFC 793 – Transmission Control Protocol,” 1981.  

---

# 11. Declaración de Uso de Inteligencia Artificial (Si aplica)

**IA utilizada:** ___________________________  

**Preguntas realizadas:**  
- _________________________________________  

**Validación realizada por el equipo:**  
- _________________________________________  

**Aplicación en la topología:**  
- _________________________________________  
