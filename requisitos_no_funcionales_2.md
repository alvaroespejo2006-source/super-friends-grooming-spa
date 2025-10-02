# REQUISITOS FUNCIONALES - APP PERSONALIZACIÓN DE BAÑOS Y ATUENDOS DE MASCOTAS

## RF-001: GESTIÓN DE USUARIOS Y SEGURIDAD

### RF-001.1: Registro y Autenticación
**Descripción:** El usuario debe poder registrarse y autenticarse de forma segura.
- Registro con correo electrónico y contraseña
- Opción de autenticación biométrica (huella/Face ID) si el dispositivo lo permite
- Recuperación de contraseña por correo
**Métrica:** Tiempo medio de registro ≤ 2 minutos  
**Condiciones de Prueba:**  
- Registro en dispositivos iOS y Android  
- Pruebas de login con credenciales válidas e inválidas  
**Criterios de Aceptación:**  
- Usuario recibe confirmación por correo  
- Acceso bloqueado tras 5 intentos fallidos  
- Biometría funciona en dispositivos compatibles

### RF-001.2: Gestión de Perfil de Usuario
**Descripción:** El usuario puede editar sus datos personales y preferencias.
- Edición de nombre, correo y foto de perfil
- Selección de tema y tamaño de fuente en la app
**Métrica:** Cambios reflejados en <2 segundos  
**Condiciones de Prueba:**  
- Edición desde web y móvil  
**Criterios de Aceptación:**  
- Cambios persistentes tras reinicio de sesión  
- Preferencias aplicadas en toda la app

## RF-002: GESTIÓN DE MASCOTAS

### RF-002.1: Registro y Edición de Mascotas
**Descripción:** El usuario puede registrar, editar y eliminar mascotas.
- Campos: nombre, especie, raza, edad, tamaño, peso, alergias, historial de servicios, condiciones médicas
**Métrica:** Registro/edición en <2 minutos  
**Condiciones de Prueba:**  
- Pruebas con diferentes especies y razas  
**Criterios de Aceptación:**  
- Mascotas visibles en el perfil del usuario  
- Cambios persistentes y editables

### RF-002.2: Visualización de Perfil de Mascota
**Descripción:** El usuario visualiza la información y el historial de servicios de cada mascota.
**Métrica:** Visualización inmediata (<1s)  
**Condiciones de Prueba:**  
- Consulta con 1 y con 10 mascotas registradas  
**Criterios de Aceptación:**  
- Historial y detalles correctamente desplegados

## RF-003: PERSONALIZACIÓN DE BAÑOS Y ATUENDOS

### RF-003.1: Selección y Personalización de Servicios de Baño
**Descripción:** El usuario puede elegir entre tipos de baño (medicado, aromático, desparasitante, etc.) y añadir extras.
- Recomendaciones automáticas según perfil y necesidades de la mascota
**Métrica:** Proceso de selección en <2 minutos  
**Condiciones de Prueba:**  
- Selección de distintos tipos y extras  
**Criterios de Aceptación:**  
- Recomendaciones relevantes y visibles  
- Selección guardada en la reserva

### RF-003.2: Selección y Personalización de Atuendos
**Descripción:** El usuario puede elegir atuendos, talla, temporada y accesorios.
- Vista previa de la mascota con el atuendo seleccionado (imagen/simulador)
**Métrica:** Generación de vista previa <3 segundos  
**Condiciones de Prueba:**  
- Pruebas con atuendos de diferentes tallas y estilos  
**Criterios de Aceptación:**  
- Vista previa fiel al atuendo elegido  
- Atuendo guardado en el historial de servicios

## RF-004: CATÁLOGO DE PRODUCTOS Y SERVICIOS

### RF-004.1: Visualización de Catálogo
**Descripción:** El usuario consulta catálogo de productos y servicios en formato tienda online.
- Categorías, imágenes, descripción, precio y disponibilidad
**Métrica:** Carga de catálogo <2 segundos  
**Condiciones de Prueba:**  
- Consulta por categoría y búsqueda por nombre  
**Criterios de Aceptación:**  
- Información clara y actualizada  
- Disponibilidad sincronizada con stock real

### RF-004.2: Valoraciones y Comentarios
**Descripción:** Los usuarios pueden dejar valoraciones y comentarios sobre productos y servicios.
**Métrica:** Publicación de comentarios <2 segundos  
**Condiciones de Prueba:**  
- Pruebas con diferentes tipos de comentarios y valoraciones  
**Criterios de Aceptación:**  
- Comentarios visibles públicamente  
- Moderación activa para contenido inapropiado

## RF-005: GESTIÓN DE CITAS Y RESERVAS

### RF-005.1: Reserva de Servicios
**Descripción:** El usuario agenda citas para servicios seleccionados.
- Selección de fecha y hora disponible
- Modificación y cancelación de cita
- Recordatorios automáticos vía notificación push y correo
**Métrica:** Reserva completada en <2 minutos  
**Condiciones de Prueba:**  
- Pruebas de reserva, modificación y cancelación  
**Criterios de Aceptación:**  
- Confirmación de cita recibida  
- Cambios reflejados en el calendario de la app

### RF-005.2: Gestión de Disponibilidad y Evitación de Duplicidad
**Descripción:** El sistema gestiona disponibilidad en tiempo real para evitar reservas duplicadas.
**Métrica:** Actualización de disponibilidad <1 segundo  
**Condiciones de Prueba:**  
- Reservas simultáneas desde diferentes cuentas  
**Criterios de Aceptación:**  
- No se permite duplicidad de horarios  
- Errores gestionados y comunicados al usuario

## RF-006: SOPORTE Y MANTENIMIENTO POST-LANZAMIENTO

### RF-006.1: Soporte Técnico
**Descripción:** El usuario puede contactar soporte vía chat y correo.
- Respuestas automáticas para preguntas frecuentes
- Escalación a agente humano si es necesario
**Métrica:** Tiempo medio de respuesta <10 minutos (chat)  
**Condiciones de Prueba:**  
- Solicitudes de soporte desde diferentes partes de la app  
**Criterios de Aceptación:**  
- Ticket generado y gestionado correctamente  
- Historial de soporte accesible por el usuario

### RF-006.2: Actualizaciones y Nuevas Funcionalidades
**Descripción:** El sistema permite actualizaciones regulares y despliegue de nuevas funcionalidades.
**Métrica:** Nueva funcionalidad desplegada en <1 semana tras aprobación  
**Condiciones de Prueba:**  
- Simulación de despliegue de actualizaciones  
**Criterios de Aceptación:**  
- Actualización no interrumpe servicios críticos  
- Cambios comunicados previamente al usuario

## RF-007: INTEGRACIÓN Y COMPATIBILIDAD

### RF-007.1: Integración con Sistemas Existentes
**Descripción:** La app se integra con el sistema de facturación y gestión de clientes de la empresa.
**Métrica:** Sincronización de datos <5 minutos  
**Condiciones de Prueba:**  
- Pruebas de envío y recepción de datos a sistemas externos  
**Criterios de Aceptación:**  
- Datos consistentes y sincronizados  
- Integración documentada y verificable

### RF-007.2: Multi-dispositivo y Multi-plataforma
**Descripción:** La app funciona en Android, iOS y versión web.
**Métrica:** Pruebas exitosas en dispositivos compatibles  
**Condiciones de Prueba:**  
- Testing en gama baja, media y alta  
**Criterios de Aceptación:**  
- Experiencia uniforme en todas las plataformas  
- No se presentan errores críticos por incompatibilidad
