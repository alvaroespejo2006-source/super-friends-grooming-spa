#  REQUISITOS NO FUNCIONALES - SISTEMA DE PELUQUERÍA Y AGENDAMIENTO PARA MASCOTAS

## **RNF-001: RENDIMIENTO Y CAPACIDAD**

### RNF-001.1: Tiempo de Respuesta de Interfaz
**Descripción:** El sistema debe garantizar que las páginas principales y operaciones críticas se carguen rápidamente.
**Métrica Específica:** 
- Carga de página principal: ≤ 3 segundos
- Operaciones de login, registro y pago: ≤ 2 segundos
- Navegación estándar: ≤ 1.5 segundos

**Medición:** Tiempo desde acción del usuario hasta renderizado completo.
**Condiciones de Prueba:** 
- Red estándar móvil 4G (≥10 Mbps)
- Horarios pico (6-8 PM)
- Base de datos con mínimo 5,000 registros

**Criterios de Aceptación:**
- 95% de las operaciones cumplen el tiempo objetivo
- Loading states para operaciones >2 segundos

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Carga de ~2.5 segundos en promedio, dentro del objetivo"

---

### RNF-001.2: Capacidad de Usuarios Concurrentes
**Descripción:** El sistema debe soportar al menos 500 usuarios concurrentes sin degradación significativa.
**Métrica Específica:**
- Usuarios concurrentes objetivo: 500
- Usuarios concurrentes máximo probado: 600

**Medición:** Pruebas de carga con herramientas como JMeter.
**Condiciones de Prueba:**
- Simulación de operaciones reales durante 2 horas
- Mix de agendamiento, pagos, consultas

**Criterios de Aceptación:**
- Sin caídas ni lentitud significativa bajo carga máxima
- Auto-scaling recomendado para crecimiento futuro

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Soporta hasta 600 usuarios concurrentes sin caída"

---

## **RNF-002: SEGURIDAD Y PROTECCIÓN DE DATOS**

### RNF-002.1: Encriptación de Datos
**Descripción:** Toda la información sensible debe estar protegida mediante cifrado y protocolos seguros.
**Métrica Específica:**
- Datos en tránsito: HTTPS (TLS 1.2+)
- Datos sensibles: Hash seguro para contraseñas (SHA-256 con salt)

**Medición:** Auditorías de seguridad y pruebas de penetración
**Condiciones de Prueba:**
- Escaneo de vulnerabilidades mensual
- Verificación de cifrado en formularios críticos

**Criterios de Aceptación:**
- No almacenar contraseñas en texto plano
- Cumplimiento de buenas prácticas OWASP

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Usa HTTPS, cifrado de datos sensibles y cumple buenas prácticas OWASP"

---

### RNF-002.2: Autenticación y Control de Acceso
**Descripción:** El sistema debe implementar mecanismos robustos de autenticación y protección contra accesos no autorizados.
**Métrica Específica:**
- Bloqueo automático tras 5 intentos fallidos
- Expiración de sesión tras 30 minutos de inactividad

**Medición:** Logs de seguridad y métricas de intentos de acceso
**Condiciones de Prueba:**
- Simulación de intentos de acceso no autorizado
- Pruebas de bypass de autenticación

**Criterios de Aceptación:**
- Mensajes claros ante login fallido o sesión expirada
- Notificación por correo ante accesos sospechosos

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Probé login con credenciales correctas e incorrectas..."

---

## **RNF-003: DISPONIBILIDAD Y CONFIABILIDAD**

### RNF-003.1: Disponibilidad del Sistema
**Descripción:** La plataforma debe estar operativa de manera continua, con mínima interrupción.
**Métrica Específica:**
- Disponibilidad mensual objetivo: ≥99%
- Mantenimientos programados: máximo 2 horas mensuales

**Medición:** Monitoreo continuo con herramientas como UptimeRobot.
**Condiciones de Prueba:**
- Simulación de fallos de infraestructura
- Pruebas de recuperación post-caída

**Criterios de Aceptación:**
- Infraestructura redundante recomendada para alta disponibilidad
- Página de estado público para comunicar incidencias

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Disponibilidad del 99.3% mensual"

---

## **RNF-004: USABILIDAD Y EXPERIENCIA DE USUARIO**

### RNF-004.1: Facilidad de Uso y Accesibilidad
**Descripción:** La plataforma debe ser intuitiva y accesible para todo tipo de usuarios.
**Métrica Específica:**
- Tasa de éxito en tareas básicas: ≥90%
- Cumplimiento WCAG 2.1 nivel AA

**Medición:** Tests de usabilidad y auditoría de accesibilidad
**Condiciones de Prueba:**
- Pruebas con usuarios reales y herramientas automáticas
- Testing en distintos dispositivos y navegadores

**Criterios de Aceptación:**
- Textos claros, botones grandes y legibles
- Navegación por teclado y lectores de pantalla soportados

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Interfaz intuitiva, etiquetas claras y botones grandes, aptos para todo tipo de usuarios"

---

### RNF-004.2: Compatibilidad Multiplataforma e Idiomas
**Descripción:** El sistema debe funcionar correctamente en dispositivos móviles, tablets y debe permitir el acceso en al menos dos idiomas.
**Métrica Específica:**
- Soporte para iOS 12+, Android 8+, Chrome/Firefox/Safari/Edge (últimas 3 versiones)
- Traducción completa a español e inglés

**Medición:** Testing automatizado cross-device y revisión de traducciones
**Condiciones de Prueba:**
- Pruebas en farm de dispositivos reales
- Verificación de cambio de idioma en todo el contenido

**Criterios de Aceptación:**
- Interfaz responsive y sin errores de visualización
- Traducción de correos y notificaciones

**Prioridad:** SHOULD (Importante)
**Fuente:** Entrevista QA - "Probé en móviles y tablets... el contenido se traduce correctamente, incluyendo correos de confirmación"

---

## **RNF-005: CUMPLIMIENTO LEGAL Y AUDITORÍA**

### RNF-005.1: Protección de Datos Personales y Consentimiento
**Descripción:** El sistema debe cumplir con normativas de protección de datos (ej. GDPR) y gestionar consentimiento explícito.
**Métrica Específica:**
- Consentimiento explícito antes del registro
- Política de privacidad accesible en todo momento

**Medición:** Auditorías de privacidad y revisiones legales
**Condiciones de Prueba:**
- Verificación de flujos de aceptación de política
- Pruebas de eliminación de datos a solicitud

**Criterios de Aceptación:**
- Registro de consentimientos con timestamp
- Mecanismos para ejercer derechos ARCO

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "El sistema tiene políticas de privacidad, opción de aceptar cookies y maneja consentimiento explícito de datos personales"

---

### RNF-005.2: Auditoría y Trazabilidad de Seguridad
**Descripción:** El sistema debe registrar todas las actividades críticas para auditoría y detección de problemas.
**Métrica Específica:**
- 100% de transacciones loggeadas
- Retención de logs: mínimo 2 años

**Medición:** Auditorías internas y verificación de logs
**Condiciones de Prueba:**
- Simulación de actividades sospechosas
- Pruebas de integridad de logs

**Criterios de Aceptación:**
- Logs inmutables y exportables para auditoría
- Alertas automáticas por patrones anómalos de acceso

**Prioridad:** SHOULD (Importante)
**Fuente:** Buenas prácticas de sistemas web y entrevista QA

---
