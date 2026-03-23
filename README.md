# 🌐 Redes para Desarrolladores: Routers, Switches y Hubs

---

## 🧩 1. ¿Qué es cada dispositivo?

| Concepto | Definición simple | Nivel técnico (breve) | Ejemplo real |
| :--- | :--- | :--- | :--- |
| **Router** | Conecta tu red con internet | Usa direcciones IP para enviar datos entre redes | Tu router WiFi en casa |
| **Switch** | Conecta dispositivos dentro de una misma red | Usa direcciones MAC para enviar datos al dispositivo correcto | Red de una oficina |
| **Hub** | Repite la información a todos los dispositivos | Hace broadcast sin filtrar datos | Tecnología antigua (casi no se usa) |

---

## ⚙️ 2. ¿Cómo funciona realmente?

### 📡 Router
* **Recibe** paquetes y mira la IP destino.
* **Decide** por dónde enviarlos (ruta).
* **Conecta** redes distintas (ej: tu casa ↔ internet).

### 🔀 Switch
* **Aprende** las direcciones MAC de los dispositivos conectados.
* **Envía** datos solo al dispositivo correcto.
* **Evita** tráfico innecesario.

### 📢 Hub
* **Envía** todo a todos (broadcast).
* **No distingue** destinatarios.
* **Genera congestionamiento** (tráfico innecesario) → Por eso está obsoleto.

---

## 💻 3. Conexión con desarrollo

### 🌐 Router y una API
Cuando haces un `fetch("https://api.miapp.com")`:
1. El router envía tu petición hacia internet.
2. Encuentra la IP del servidor.
3. Devuelve la respuesta a tu computador.

### 🏢 Switch en backend / Data Center
* Permite que los servidores se comuniquen rápido.
* **Ejemplo:** Comunicación ultra-rápida entre el Servidor Backend ↔ Base de datos.
* Reduce tráfico y mejora el rendimiento general.

### ⚠️ Problemas de red que afectan tu app
* ⏳ **Alta latencia:** Todo responde lento.
* ❌ **Pérdida de paquetes:** Errores intermitentes o peticiones que se quedan "congeladas".
* 🔍 **DNS mal configurado:** El sistema no encuentra la URL de la API.
* 🔌 **Router caído:** No hay conexión hacia el exterior.
* 🔥 **Switch saturado:** Respuestas lentas en la infraestructura interna.

---

## 🌍 4. Caso práctico: *"La app no funciona"*

* **¿Es culpa del Router?**
  * Sí, si no hay acceso a internet en absoluto.
  * *Ejemplo:* Nadie puede entrar a la web desde fuera.
* **¿Es culpa del Switch?**
  * Sí, si falla la comunicación interna.
  * *Ejemplo:* El backend no puede hablar con la base de datos aunque ambos estén encendidos.
* **¿Es la Red o es mi Código?**
  * **Red:** Errores de conexión (`timeout`, `connection refused`).
  * **Código:** Errores `500` (Internal Server Error), bugs lógicos, datos corruptos.
  * 💡 *Tip de supervivencia:* Prueba con comandos como `ping`, `curl` o intenta abrir la URL de la API directamente en el navegador.

---

## 🧪 5. Analogía clave

> 📦 **Router** = La oficina de correos que envía cartas entre distintas ciudades.  
> 📬 **Switch** = El recepcionista del edificio que entrega el paquete exactamente al departamento correcto.  
> 📢 **Hub** = Alguien que entra al edificio gritando el mensaje para que lo escuchen todos los pisos.

---

## 🧠 BONUS: Arquitectura moderna y Cloud

### ⚖️ Load Balancer (Balanceador de carga)
* Reparte el tráfico entrante entre varios servidores para evitar que uno solo se sature.
* Mejora la disponibilidad (si un servidor muere, redirige al otro).

### ☁️ Cloud (AWS, Azure, Google Cloud)
Todo este hardware físico existe en la nube, pero de forma virtualizada:
* **Router** ➔ Gateways (Internet Gateways, NAT Gateways).
* **Switch** ➔ Redes internas privadas o VPC (Virtual Private Cloud).
* **Load Balancer** ➔ Servicios gestionados (como AWS ALB).
