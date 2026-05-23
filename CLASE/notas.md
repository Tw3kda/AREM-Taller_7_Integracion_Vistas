# Taller 7 – Integración de Vistas Arquitectónicas
## Caso de Estudio: FarmApp

---

# Integrantes
- Santiago Navarro Cuy
- David Santiago Medina
- Juan Diego Escobar
- Jacobo Andres Pacheco

---

# Objetivo del Taller

Integrar todas las vistas arquitectónicas desarrolladas durante el curso para analizar cómo interactúan entre sí las capas de negocio, información, aplicaciones, infraestructura y seguridad dentro de la plataforma FarmApp.

---

# Descripción del Caso

FarmApp es una cadena nacional de farmacias que cuenta con una plataforma de e-commerce integrada a sus puntos físicos de venta. Los clientes pueden realizar compras de medicamentos mediante una aplicación móvil o plataforma web, consultar disponibilidad de productos, acceder a promociones personalizadas y realizar pagos electrónicos.

La organización sincroniza múltiples sistemas internos como:

- Sistema POS
- CRM
- Inventario
- Logística de entregas
- Pasarela de pagos

El objetivo de la integración arquitectónica es garantizar una experiencia consistente, segura y escalable para clientes y empleados.

---

# Vistas Arquitectónicas Integradas

## 1. Vista de Negocio

La vista de negocio representa los procesos principales que soportan la operación de FarmApp.

### Procesos principales
- Compra de medicamentos
- Validación de prescripciones
- Gestión de inventario
- Procesamiento de pagos
- Despacho y entrega
- Programas de fidelización

### Objetivo
Permitir una operación eficiente entre los canales físicos y digitales.

---

## 2. Vista de Información

La vista de información describe las entidades y datos críticos del sistema.

### Entidades principales
- Cliente
- Producto
- Pedido
- Inventario
- Pago
- Descuento
- Prescripción

### Objetivo
Garantizar consistencia y disponibilidad de la información entre todos los sistemas.

---

## 3. Vista de Aplicaciones

La vista de aplicaciones representa las plataformas y sistemas que automatizan los procesos de negocio.

### Aplicaciones utilizadas
- App móvil
- Plataforma e-commerce
- Sistema POS
- CRM
- Sistema logístico
- Pasarela de pagos

### Objetivo
Permitir integración y automatización de los procesos operativos y comerciales.

---

## 4. Vista de Infraestructura

La vista de infraestructura define los recursos tecnológicos que soportan la plataforma.

### Componentes principales
- Servidores regionales
- Nube híbrida
- Base de datos replicada
- Balanceadores de carga
- Redes seguras

### Objetivo
Garantizar disponibilidad, rendimiento y escalabilidad del sistema.

---

## 5. Vista de Seguridad

La vista de seguridad protege los datos, aplicaciones e infraestructura.

### Controles implementados
- Control de acceso por roles
- Cifrado de datos personales
- Autenticación multifactor
- Monitoreo de fraude
- Auditoría de transacciones

### Objetivo
Proteger la información sensible y asegurar la continuidad del servicio.

---

# Relación entre las Capas Arquitectónicas

Las vistas arquitectónicas se encuentran conectadas entre sí de manera jerárquica y funcional.

## Relación Negocio → Aplicaciones
Los procesos de negocio utilizan aplicaciones para automatizar operaciones como compras, pagos y gestión de clientes.

Ejemplo:
- El proceso de compra utiliza la App móvil y la plataforma e-commerce.
- El proceso de despacho utiliza el sistema logístico.

---

## Relación Aplicaciones → Información
Las aplicaciones consultan y actualizan información constantemente.

Ejemplo:
- El CRM accede a datos de clientes.
- El sistema POS actualiza el inventario.
- La plataforma e-commerce registra pedidos y pagos.

---

## Relación Información → Infraestructura
Toda la información se almacena y procesa en la infraestructura tecnológica.

Ejemplo:
- Bases de datos replicadas almacenan pedidos e inventario.
- Los servidores regionales procesan las solicitudes de usuarios.

---

## Relación Seguridad → Todas las Capas
La seguridad actúa de forma transversal en toda la arquitectura.

Ejemplo:
- El cifrado protege datos personales.
- Los controles de acceso restringen permisos según roles.
- El monitoreo detecta fraudes en pagos electrónicos.

---

# Flujo General del Sistema

## Escenario: Compra de un medicamento

1. El cliente ingresa a la app o sitio web.
2. Selecciona productos y genera un pedido.
3. El sistema consulta el inventario disponible.
4. Se procesa el pago electrónico.
5. El CRM actualiza el historial del cliente.
6. El sistema logístico coordina el despacho.
7. Los mecanismos de seguridad monitorean toda la transacción.

---

# Beneficios de la Integración Arquitectónica

- Integración entre tiendas físicas y e-commerce
- Mejor experiencia para el cliente
- Actualización en tiempo real del inventario
- Mayor seguridad en pagos y datos personales
- Escalabilidad para soportar crecimiento futuro
- Automatización de procesos internos

---

# Conclusiones

La integración de las vistas arquitectónicas permite comprender cómo todos los componentes tecnológicos y de negocio de FarmApp trabajan de forma coordinada.

Cada capa cumple una función específica:

- La vista de negocio define los procesos.
- Las aplicaciones automatizan operaciones.
- La información centraliza los datos.
- La infraestructura soporta la operación.
- La seguridad protege todo el ecosistema.

Gracias a esta integración, FarmApp puede ofrecer un servicio moderno, seguro, eficiente y escalable para sus clientes y empleados.

---
