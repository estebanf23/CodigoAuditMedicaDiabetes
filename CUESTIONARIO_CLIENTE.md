# Cuestionario de Relevamiento para Estimación (Auditoría Médica)

Este documento contiene las preguntas clave que debemos realizarle al cliente para transformar la Prueba de Concepto (POC) en una implementación completa y productiva. Las respuestas nos permitirán estimar con precisión el tiempo, los costos y el equipo necesario.

## 1. Arquitectura y Stack Tecnológico
> [!IMPORTANT]
> Definir el stack tecnológico es crítico para saber si podemos reutilizar el código de la POC o si debemos reescribir partes del sistema.

* **Stack Base:** Actualmente la POC está desarrollada con un stack específico. ¿Tienen un stack tecnológico mandatario u homologado en la empresa para Frontend y Backend?
* **Base de Datos:** ¿Qué motor de base de datos relacional o NoSQL (ej. SQL Server, Oracle, PostgreSQL, MongoDB) debemos utilizar para el entorno de producción?
* **Control de Versiones y CI/CD:** ¿Utilizan GitHub, GitLab, Bitbucket o Azure DevOps? ¿Existen flujos de integración y despliegue continuo (CI/CD) ya definidos a los que debamos acoplarnos?

## 2. Inteligencia Artificial (LLM)
> [!NOTE]
> El procesamiento con Inteligencia Artificial es el núcleo del proyecto. Debemos asegurar la privacidad de la información médica.

* **Modelo a Utilizar:** ¿Utilizaríamos la API de FRIDA tal como está implementada actualmente o cuentan con su propio LLM/suscripción empresarial (ej. Azure OpenAI, modelos hosteados on-premise)?
* **Privacidad de Datos:** Al tratarse de datos médicos de diabetes, ¿qué normativas de seguridad (ej. HIPAA, leyes locales) rigen para la anonimización de datos antes de enviarlos al LLM?

## 3. Lógica de Negocio y Motor de Reglas
* **Motor de Reglas:** ¿Se requiere implementar un motor de reglas de negocio propio o de mercado (ej. Drools, IBM ODM, Corticon) para complementar o validar lo que audita la IA?
* **Integración de Reglas:** Si ya cuentan con un motor de reglas, ¿cómo se espera que nos conectemos (API REST, SOAP, Kafka/Mensajería)?

## 4. Infraestructura y Despliegue
* **Entorno Cloud / On-Premise:** ¿Dónde se alojará la aplicación productiva? ¿En una nube pública (AWS, Azure, GCP) o en servidores On-Premise del cliente?
* **Estrategia de Despliegue:** ¿El cliente proveerá los entornos de Desarrollo, QA, Staging y Producción?

## 5. Integración con Sistemas Core
> [!WARNING]
> La integración con sistemas existentes suele ser la fase que más desvíos de tiempo genera si no se releva correctamente.

* **Sistemas de Origen:** ¿De qué sistemas core o de Historia Clínica Electrónica (EHR) obtendremos la información de los pacientes y los pedidos médicos?
* **Autenticación (SSO):** ¿Qué sistema de autenticación manejan para los auditores médicos y usuarios internos (Active Directory, Okta, Auth0, SAML)?

## 6. Roles y Gobernanza
* **Equipo del Cliente:** ¿Qué roles estarán del lado del cliente durante el proyecto? (Especialmente necesitamos confirmación de: *Product Owner, Expertos/Médicos para calibrar las respuestas de la IA, Arquitectos de IT y equipo de Seguridad*).
* **Equipo a Proveer:** En base a la respuesta anterior, podremos definir cuántos desarrolladores, QA, analistas funcionales y especialistas en IA o DevOps necesitamos asignar nosotros.

## 7. Volumetría y Alcance Inicial
* **Volumen de Carga:** ¿Cuál es el volumen mensual de auditorías médicas de diabetes esperado?
* **Usuarios Concurrentes:** ¿Cuántos médicos auditores utilizarán el sistema en simultáneo?

## Estimación Realista (Next Steps)
Una vez respondido este cuestionario, el equipo técnico podrá realizar una **Estimación Realista de Tiempo y Costos (WBS - Work Breakdown Structure)**, dividiendo el proyecto en fases:
1. **Fase de Setup e Integración Base**
2. **Fase de Ajuste del Modelo IA / FRIDA**
3. **Fase de Integración con Motor de Reglas**
4. **Fase de Pruebas UAT (User Acceptance Testing) con Médicos Reales**
5. **Paso a Producción y Estabilización**
