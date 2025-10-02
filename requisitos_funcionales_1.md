#  REQUISITOS FUNCIONALES - SISTEMA DE PELUQUERÍA Y AGENDAMIENTO PARA MASCOTAS

## **RF-001: GESTIÓN DE USUARIOS**

### RF-001.1: Registro de Usuario
**Descripción:** El sistema debe permitir el registro de nuevos usuarios mediante correo electrónico, teléfono y contraseña, validando la unicidad de los datos.
**Actor:** Usuario nuevo
**Precondiciones:** Usuario no registrado previamente
**Flujo Principal:**
1. Usuario accede a la página de registro
2. Sistema solicita correo, teléfono y contraseña
3. Usuario proporciona la información requerida
4. Sistema valida formato y unicidad de datos (bloquea correos duplicados)
5. Sistema envía confirmación por correo electrónico
6. Usuario confirma registro a través del enlace enviado
7. Sistema crea la cuenta y redirige al inicio de sesión

**Criterios de Aceptación:**
- Bloqueo de registros con correos duplicados
- Envío de confirmación por email
- Registro exitoso redirige al inicio de sesión

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "El sistema bloquea correos duplicados y envía confirmación por email"

---

### RF-001.2: Inicio y Cierre de Sesión
**Descripción:** El sistema debe permitir a los usuarios iniciar y cerrar sesión, gestionando correctamente la sesión activa.
**Actor:** Usuario registrado
**Precondiciones:** Usuario con cuenta creada y confirmada
**Flujo Principal:**
1. Usuario accede al formulario de inicio de sesión
2. Usuario ingresa correo/teléfono y contraseña
3. Sistema valida credenciales
4. Usuario accede al sistema si las credenciales son correctas
5. Usuario puede cerrar sesión desde cualquier pantalla
6. Sistema elimina la sesión activa y redirige al inicio

**Criterios de Aceptación:**
- Inicio de sesión solo con credenciales válidas
- Mensajes claros ante credenciales incorrectas
- Cierre de sesión elimina sesión activa y redirige

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Probé login con credenciales correctas e incorrectas... elimina la sesión activa y redirige al inicio"

---

## **RF-002: AGENDAMIENTO Y SERVICIOS DE PELUQUERÍA**

### RF-002.1: Agenda de Citas para Servicios
**Descripción:** El sistema debe permitir agendar citas para cortes de pelo de perros en fechas y horas disponibles.
**Actor:** Usuario registrado
**Precondiciones:** Usuario autenticado
**Flujo Principal:**
1. Usuario accede a la sección de agendamiento
2. Sistema muestra calendario con horarios disponibles
3. Usuario selecciona fecha y hora libre
4. Sistema bloquea horarios ocupados y pasados
5. Usuario confirma cita
6. Sistema registra la cita y envía confirmación por email

**Criterios de Aceptación:**
- Solo horarios libres y válidos pueden seleccionarse
- Citas agendadas generan confirmación automática

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "El calendario solo permite seleccionar horarios libres y bloquea los ocupados o pasados"

---

### RF-002.2: Selección de Servicios y Accesorios
**Descripción:** El sistema debe permitir seleccionar el tipo de corte de pelo y agregar accesorios al servicio.
**Actor:** Usuario registrado
**Precondiciones:** Usuario agendando cita
**Flujo Principal:**
1. Usuario selecciona tipo de corte: básico, estético, de raza
2. Sistema muestra opciones de accesorios: moños, lazos
3. Usuario agrega accesorios al servicio
4. Sistema actualiza el total de la cita con costos extras

**Criterios de Aceptación:**
- Opciones de corte y accesorios desplegadas correctamente
- Costo extra reflejado en el total de la cita

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Los accesorios se pueden agregar, y el costo extra se refleja en el total de la cita"

---

### RF-002.3: Visualización Previa de Servicios
**Descripción:** El sistema debe mostrar imágenes de cortes y accesorios antes de confirmar la cita.
**Actor:** Usuario registrado
**Precondiciones:** Usuario seleccionando servicios/accesorios
**Flujo Principal:**
1. Usuario consulta imágenes de cortes y accesorios disponibles
2. Sistema muestra imágenes en buena resolución
3. Usuario confirma selección

**Criterios de Aceptación:**
- Imágenes en alta calidad, sin distorsión
- Visualización correcta en varios navegadores y dispositivos

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Cada opción muestra imágenes en buena resolución... no se pixelan en pantallas grandes"

---

### RF-002.4: Modificación y Cancelación de Citas
**Descripción:** El sistema debe permitir modificar o cancelar citas previamente agendadas hasta 24 horas antes.
**Actor:** Usuario registrado
**Precondiciones:** Cita agendada por el usuario
**Flujo Principal:**
1. Usuario accede a sus citas agendadas
2. Usuario selecciona cita a modificar o cancelar
3. Sistema verifica si la acción es dentro del plazo permitido
4. Usuario modifica detalles o cancela cita
5. Sistema actualiza el estado y envía notificación

**Criterios de Aceptación:**
- Modificación/cancelación solo disponible hasta 24 horas antes
- Notificación automática de cambios

**Prioridad:** SHOULD (Importante)
**Fuente:** Entrevista QA - "Puede modificar o cancelar hasta 24 horas antes. Probé reprogramar y funcionó bien"

---

## **RF-003: PANEL DE ADMINISTRACIÓN**

### RF-003.1: Vista de Citas para Administrador
**Descripción:** El sistema debe mostrar todas las citas agendadas en un panel de control para el administrador/peluquero.
**Actor:** Administrador/Peluquero
**Precondiciones:** Usuario con permisos administrativos
**Flujo Principal:**
1. Administrador accede al panel de control
2. Sistema muestra lista de citas programadas con detalles: cliente, tipo de corte, accesorios, estado de pago
3. Administrador gestiona estado de las citas

**Criterios de Aceptación:**
- Panel muestra todas las citas con información relevante
- Estado de pago visible en cada cita

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "El panel muestra todas las citas con detalles de cliente, tipo de corte, accesorios y estado de pago"

---

## **RF-004: PAGOS Y FACTURACIÓN**

### RF-004.1: Procesamiento de Pagos en Línea
**Descripción:** El sistema debe integrar una pasarela de pagos para procesar y validar pagos en línea.
**Actor:** Usuario registrado
**Precondiciones:** Usuario con cita agendada
**Flujo Principal:**
1. Usuario inicia pago de servicio
2. Sistema redirige a pasarela de pago
3. Usuario ingresa datos de tarjeta o método de pago
4. Sistema procesa pago y valida fondos
5. Sistema informa resultado (aprobado/rechazado) y motivos si corresponde
6. Sistema actualiza estado de pago de la cita

**Criterios de Aceptación:**
- Integración con pasarela válida
- Mensajes claros ante pagos rechazados
- Pagos exitosos actualizan estado de la cita

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Probé tarjetas válidas, rechazadas... El sistema responde con mensajes claros"

---

## **RF-005: USABILIDAD Y ACCESIBILIDAD**

### RF-005.1: Rendimiento y Disponibilidad
**Descripción:** El sistema debe cargar la página principal en menos de 3 segundos y mantener una disponibilidad mensual superior al 99%.
**Actor:** Usuario registrado
**Precondiciones:** Sistema operativo
**Flujo Principal:**
1. Usuario accede al sitio o aplicación
2. Sistema carga la página principal en menos de 3 segundos
3. Sistema mantiene disponibilidad superior al 99% mensual

**Criterios de Aceptación:**
- Tiempos de carga medidos y auditados
- Reportes de disponibilidad mensual

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Carga de ~2.5 segundos... disponibilidad del 99.3%"

---

### RF-005.2: Accesibilidad y Multiplataforma
**Descripción:** El sistema debe ser accesible desde dispositivos móviles y tablets, con interfaz adaptable y textos fáciles de entender.
**Actor:** Usuario registrado
**Precondiciones:** Usuario accediendo desde cualquier dispositivo
**Flujo Principal:**
1. Usuario accede desde móvil, tablet o escritorio
2. Sistema adapta interfaz y visualización
3. Textos y botones son claros, legibles y accesibles

**Criterios de Aceptación:**
- Diseño responsive y multiplataforma
- Fuentes y botones aptos para todo tipo de usuarios

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Probé en móviles y tablets... interfaz intuitiva, etiquetas claras y botones grandes"

---

## **RF-006: SEGURIDAD Y PROTECCIÓN DE DATOS**

### RF-006.1: Seguridad de la Plataforma
**Descripción:** El sistema debe proteger los datos personales y de pago de los usuarios mediante cifrado y buenas prácticas de seguridad.
**Actor:** Usuario registrado
**Precondiciones:** Usuario con datos personales registrados
**Flujo Principal:**
1. Usuario ingresa datos personales y/o de pago
2. Sistema cifra los datos sensibles
3. Sistema opera bajo protocolo HTTPS
4. Sistema aplica controles OWASP

**Criterios de Aceptación:**
- Cifrado de datos sensibles
- Uso de HTTPS en toda la plataforma
- Cumplimiento de buenas prácticas OWASP

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "Usa HTTPS, cifrado de datos sensibles y cumple buenas prácticas OWASP"

---

### RF-006.2: Cumplimiento Normativo y Multilenguaje
**Descripción:** El sistema debe cumplir con normativas de protección de datos (ejemplo: GDPR) y permitir acceso en al menos dos idiomas (español e inglés).
**Actor:** Usuario internacional
**Precondiciones:** Usuario accediendo a la plataforma
**Flujo Principal:**
1. Usuario accede a la plataforma y selecciona idioma
2. Sistema presenta contenido en idioma seleccionado
3. Sistema solicita consentimiento para tratamiento de datos personales
4. Sistema maneja cookies y políticas de privacidad

**Criterios de Aceptación:**
- Contenido completamente traducido
- Consentimiento explícito de datos personales
- Políticas de privacidad y cookies disponibles

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista QA - "El sitio permite acceso en español e inglés... cumple con normativas de protección de datos (GDPR)"

---
