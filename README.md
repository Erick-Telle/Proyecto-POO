
## Descripción
Este proyecto es un sistema completo de gestión para una clínica médica, desarrollado con programación orientada a objetos. Permite manejar pacientes, citas, historias clínicas, facturación y más, con un enfoque en un expediente digital seguro y accesible. El sistema está construido con IntelliJ IDEA y OpenXava para una UI web automática, respaldado por Spring Boot y JPA.

## Características Principales
- **Gestión de Pacientes**: Registro completo con datos personales, seguros médicos y expediente digital.
- **Agendamiento de Citas**: Validación de conflictos, asignación de doctores y salas.
- **Expediente Digital**: Contenedor centralizado de historias clínicas, exámenes, prescripciones y alergias, con generación automática de PDFs y encriptación.
- **Facturación y Pagos**: Cálculo de totales con descuentos por seguros, generación de facturas en PDF.
- **Auditoría y Seguridad**: Logs de accesos, autenticación con roles (admin, doctor, recepcionista, paciente) y MFA opcional.
- **Reportes**: Dashboards y PDFs para citas, facturas y expedientes.

## Tecnologías Utilizadas
- **Lenguaje**: Java 11+.
- **Framework**: OpenXava (para UI CRUD automática), Spring Boot (backend).
- **Persistencia**: JPA/Hibernate con base de datos H2 (desarrollo) o PostgreSQL/MySQL (producción).
- **Herramientas**: IntelliJ IDEA, Maven, Spring Security (autenticación), iText (PDFs), JasperReports (reportes).

## Instalación y Configuración
1. **Clona el Repositorio**:
   ```
   git clone https://github.com/Erick-Telle/Proyecto-POO.git
   ```

2. **Requisitos**:
   - JDK 11+ instalado.
   - IntelliJ IDEA con plugin de OpenXava.
   - Maven para dependencias.

3. **Configura el Proyecto**:
   - Abre en IntelliJ IDEA.
   - Ejecuta `mvn clean install` para descargar dependencias.
   - Configura `application.properties`:
     ```
     spring.datasource.url=jdbc:h2:mem:testdb
     spring.jpa.hibernate.ddl-auto=update
     openxava.application.name=ClinicaApp
     ```
   - Para producción, cambia a PostgreSQL y agrega credenciales.

## Uso
- **Registro de Paciente**: Ve a la pestaña "Paciente" en OpenXava, ingresa datos y guarda. Se genera un expediente digital automáticamente.
- **Agendar Cita**: Selecciona paciente, doctor y sala; valida conflictos.
- **Consulta**: Actualiza historia clínica, prescripciones y exámenes; el expediente se actualiza en PDF.
- **Facturación**: Genera factura con items; aplica seguros.
- **Acceso Seguro**: Inicia sesión con usuario/rol; ve auditoría en "AccesoExpediente".
- **Innovaciones**: Usa "DiagnosticoIA" para sugerencias, o "BlockchainService" para firmar registros.

## Arquitectura
### Entidades Principales (JPA)
- **Paciente**: Centro del sistema, con relaciones 1:N a Cita, HistoriaClinica, etc.
- **Cita**: Vincula Paciente, Doctor, Sala.
- **HistoriaClinica**: Registros médicos.
- **ExpedienteDigital**: Contenedor digital con PDFs encriptados.
- **Factura/ItemFactura**: Cobros con descuentos.
- **Usuario**: Autenticación con roles.
- Otras: Doctor, Medicamento, Examen, SeguroMedico, Alergia, etc. (ver detalles en código).

### Clases Adicionales
- **Repositorios (DAO)**: Interfaces como PacienteRepository para consultas.
- **Servicios**: Lógica como CitaService, ExpedienteService, DiagnosticoIAService.
- **Controladores**: APIs REST para integración (e.g., PacienteController).
- **Utilidades**: ValidacionService, PdfGenerator, EncriptacionService.
- **Excepciones**: Personalizadas como PacienteNoEncontradoException.

### Flujo del Programa
1. Registro de Paciente → Creación de ExpedienteDigital.
2. Agendamiento de Cita → Validación y notificaciones.
3. Consulta → Actualización de HistoriaClinica y Expediente.
4. Procesamiento de Exámenes → Integración a expediente.
5. Facturación → Generación de PDFs.
6. Auditoría Continua → Logs en AccesoExpediente.

### Diagrama ERD 




