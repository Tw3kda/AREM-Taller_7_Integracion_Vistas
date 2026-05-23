# Taller 7: Integración de Vistas de Arquitectura (Escenario TO-BE)
# Integrantes
- Santiago Navarro Cuy
- David Santiago Medina
- Juan Diego Escobar
- Jacobo Andres Pacheco

##  Objetivo del Taller
Integrar todas las vistas arquitectónicas desarrolladas a lo largo del curso (Negocio, Aplicaciones, Información, Infraestructura y Seguridad) en una narrativa visual coherente. El propósito es analizar cómo interactúan entre sí las capas tecnológicas y cómo se alinean verticalmente para soportar y automatizar los objetivos estratégicos y financieros del cliente real.

---

##  1. Narrativa de las Vistas Arquitectónicas Integradas

### A. Vista de Negocio
Representa la transformación de la operación del cliente. Los procesos manuales, vulnerables y aislados en archivos de cálculo son reemplazados por flujos automatizados y centralizados:
* **Registrar Transacción / Gasto:** Captura controlada de flujos de salida de dinero.
* **Cálculo Automático de Balances:** Algoritmos en tiempo real que eliminan el cruce manual de datos.
* **Generación de Reportes Financieros:** Disponibilidad inmediata de estados contables para la toma de decisiones.

### B. Vista de Aplicaciones (Enfoque C4 - Nivel 2: Contenedores)
Define las fronteras del software y las responsabilidades de los componentes ejecutables:
* **Frontend (Aplicación Web):** Interfaz moderna desarrollada en *React / Next.js* que consume servicios mediante APIs y restringe las acciones del usuario a formularios validados.
* **Backend (API REST):** Cerebro lógico en *Node.js / Python FastAPI* que centraliza las reglas contables e interactúa directamente con los datos de forma segura.

### C. Vista de Información
Abstrae el modelo de datos para garantizar la integridad, consistencia y persistencia de la información financiera:
* **Entidades Críticas:** `Usuario / Rol`, `Transacción / Gasto` y `Cuenta / Balance`. Se elimina el almacenamiento en archivos planos `.xlsx` propensos a corrupción por sobreescritura.

### D. Vista de Infraestructura
Define el entorno físico/cloud que sirve de soporte tecnológico para el despliegue del sistema:
* **Servidor Cloud (VPS):** Aloja los contenedores del entorno de ejecución de las aplicaciones.
* **Base de Datos Relacional (PostgreSQL):** Motor de base de datos que asegura transacciones ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad).

### E. Vista de Seguridad (Eje Transversal)
No es un componente aislado, sino una capa que inyecta controles de mitigación de riesgos a lo largo de toda la arquitectura:
* Autenticación Multifactor (MFA) y tokens JWT para el acceso.
* Control de Acceso Basado en Roles (RBAC).
* Cifrado de datos en tránsito a través de protocolos TLS/HTTPS.
* Auditoría inmutable de logs para rastrear cualquier modificación en las transacciones.

---

## 2. Diagrama de Integración Multicapa (Mermaid)

A continuación se presenta el mapa arquitectónico jerárquico (*Top-Down*). El flujo continuo resaltado en color verde representa la trazabilidad completa del caso de uso crítico: **"Registrar un nuevo gasto y generar el balance financiero automático"**.

<img width="4290" height="3216" alt="Tablero-Integrado-cliente" src="https://github.com/user-attachments/assets/dc72f9df-8025-4731-a586-748e23ae49c3" />


##  3. Relación entre las Capas Arquitectónicas

Las vistas de la arquitectura propuesta para el estado futuro (**To-Be**) no operan de forma aislada; se encuentran conectadas e integradas de manera jerárquica y funcional bajo un enfoque de trazabilidad vertical (*Top-Down*) y transversal:

### A. Relación Negocio ➔ Aplicaciones (Soporte Operativo)
Los procesos de la capa de negocio definen el *qué* hace la organización, mientras que la capa de aplicaciones determina el *cómo* se automatizan dichas necesidades mediante software.
* **Ejemplo en el sistema:** El proceso de negocio *Registrar Transacción / Gasto* se encuentra soportado y automatizado directamente por el contenedor **Aplicación Web (Frontend)**, el cual captura e interactúa con el usuario mediante formularios validados. Por otro lado, el proceso de *Cálculo Automático de Balances* es ejecutado de manera transparente por los algoritmos lógicos implementados en la **API Backend**.

### B. Relación Aplicaciones ➔ Información (Manipulación de Datos)
Las aplicaciones actúan como los motores de procesamiento y control que consultan, estructuran, transforman y actualizan los modelos lógicos de datos del negocio.
* **Ejemplo en el sistema:** La **API Backend** recibe las peticiones estructuradas desde el Frontend en formato JSON. Posteriormente, procesa esta información aplicando las reglas contables del negocio para instanciar y validar la **Entidad: Transacción / Gasto** y recalcular los estados correspondientes en la **Entidad: Cuenta / Balance**.

### C. Relación Información ➔ Infraestructura (Persistencia Real)
Toda abstracción lógica de datos, entidades y relaciones conceptuales requiere de un sustento físico que garantice su almacenamiento, disponibilidad y propiedades de transaccionalidad.
* **Ejemplo en el sistema:** Los modelos lógicos representados por las entidades de *Transacción* y *Balance* se materializan físicamente como tablas estructuradas e índices dentro del motor de **Base de Datos PostgreSQL**. Este motor, junto con la ejecución lógica de la API, se despliega y procesa de forma segura dentro del **Servidor Cloud (VPS)** contratado por el cliente.

### D. Relación Seguridad ➔ Todas las Capas (Gobernanza Transversal)
La seguridad no constituye un nivel jerárquico inferior ni un componente aislado al final del flujo, sino que actúa como una capa de mitigación de riesgos e inyección de políticas que envuelve y protege a todo el ecosistema arquitectónico.
* **Intersección con la capa de Aplicaciones:** El control de acceso **Autenticación MFA & JWT** blinda las sesiones de la *Aplicación Web*, mientras que el modelo **RBAC (Control de Acceso Basado en Roles)** restringe los endpoints de la *API Backend* según los privilegios del usuario (Contador, Administrador, etc.).
* **Intersección con la capa de Información:** El principio de **Auditoría Inmutable de Logs** vigila constantemente cualquier inserción, edición o cambio de estado sobre las entidades de *Transacción*, evitando fraudes o alteraciones maliciosas en la contabilidad.
* **Intersección con la capa de Infraestructura:** El protocolo de **Cifrado de Conexiones TLS/HTTPS** garantiza que todo paquete de datos que viaje desde el cliente hacia el *Servidor Cloud* o la *Base de Datos* sea ilegible para atacantes externos (mitigando ataques de tipo *Man-in-the-Middle*).



##  4. Realizar una reflexión crítica sobre la coherencia de la arquitectura.

El análisis integrado de las cinco vistas del estado futuro (**To-Be**) demuestra una alta **coherencia arquitectónica**, fundamentada en la resolución directa de las vulnerabilidades operativas del cliente mediante principios sólidos de ingeniería de software:

* **Eliminación de Conflictos de Concurrencia e Integridad de Datos:** El principal dolor del cliente en el estado *As-Is* era la volatilidad de la información financiera alojada en hojas de cálculo de Google Drive (riesgo de sobreescrituras accidentales, pérdida de fórmulas y falta de históricos). Al centralizar la persistencia en una Base de Datos Relacional (PostgreSQL) combinada con el aislamiento transaccional de una API backend, se garantiza que múltiples usuarios operen concurrentemente sin comprometer la integridad contable.
* **Alineación Vertical Estricta (Top-Down):** Existe una correspondencia unívoca y limpia entre las necesidades del negocio y las capacidades del software. Los procesos de la capa de Negocio se mapean directamente como responsabilidades de código en el Backend. A su vez, el desacoplamiento tecnológico adoptado (Frontend independiente del Backend) permite que modificaciones en la capa de Infraestructura o escalamientos de hardware se realicen de manera invisible para el usuario final.
* **Seguridad como Eje Transversal e Integral:** A diferencia de los esquemas tradicionales donde la seguridad se añade de forma reactiva al final del desarrollo, esta arquitectura inyecta controles en cada interacción. La protección de identidad en la interfaz (MFA/JWT), la restricción de privilegios en la lógica de negocio (RBAC), el cifrado en los canales de la nube (HTTPS/TLS) y la vigilancia inmutable (Auditoría de logs) transforman al sistema en un ecosistema gobernable y resiliente frente a fraudes internos o fallos operativos.

---

## 5. Investigar ejemplos reales de documentación de vistas en empresas similares.

Para validar y respaldar las decisiones tomadas en este diseño arquitectónico, se analizó cómo organizaciones globales de la industria fintech, de banca digital y de software financiero estructuran, unifican y documentan sus vistas de sistemas:

### Caso 1: Nubank (Banca Digital y Gestión Financiera)
* **Enfoque de Documentación de Vistas:** Nubank fundamenta la documentación y el diseño de sus sistemas de gestión, contabilidad y balances contables utilizando los niveles de abstracción del **Modelo C4**. La compañía prioriza la legibilidad técnica mediante arquitecturas orientadas a servicios independientes (escritos en Clojure).
* **Lección Aplicada a Nuestro Diseño:** La separación tajante entre la lógica de procesamiento y el almacenamiento físico (como se propuso al dividir la API Backend de la Base de Datos PostgreSQL) emula el diseño de Nubank. Esto asegura que la base de datos funcione como un libro contable inmutable, facilitando auditorías financieras y garantizando consistencia absoluta en los balances históricos.

### Caso 2: Stripe (Infraestructura de Procesamiento Financiero y Pagos)
* **Enfoque de Documentación de Vistas:** Stripe documenta la interacción de sus plataformas mapeando de forma exhaustiva diagramas de contenedores (C2) y flujos dinámicos enfocados de forma estricta en la seguridad de los datos. Toda su documentación técnica y de arquitectura hace explícita la inyección transversal de políticas de seguridad, tales como el control de accesos basado en alcances (*scopes*) y el cifrado de datos tanto en tránsito como en reposo.
* **Lección Aplicada a Nuestro Diseño:** La implementación de una API REST protegida por tokens que valida roles de usuario (RBAC) y escribe logs de auditoría automáticos sigue el estándar de diseño documentado por Stripe. Esto garantiza el blindaje de la capa de Información frente a modificaciones no autorizadas por parte de actores externos o internos.

---
