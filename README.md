# Trivia Arena

**Juego multijugador de trivia en tiempo real sobre una arquitectura de tres capas orientada a eventos, con WebSockets, JWT y seguridad web**

**Materia:** Ingeniería Web 2
**Integrantes:** Juan Cabral · Steven Rusinque Gutierrez
**Fecha:** 20 de septiembre de 2026

> Documento completo en normas APA: ver `Entrega1_IngenieriaWeb2_Cabral_Rusinque.docx` en este repositorio.

---

## Descripción del proyecto

Trivia Arena es un juego multijugador de trivia en tiempo real para la web. Los usuarios se registran, se unen a salas de juego, compiten en rondas de preguntas con tiempo límite y ven un tablero de puntajes actualizado al instante.

**Arquitectura:** tres capas orientada a eventos — el modelo cliente-servidor como base de comunicación, extendido con separación de responsabilidades:

- **Capa de presentación:** React (login, registro, lobby de salas, pantalla de juego).
- **Capa de lógica de negocio:** Node.js/Express — API REST (OpenAPI 3.0/Swagger) + motor del juego con WebSockets (salas, rondas, puntajes en vivo).
- **Capa de datos:** PostgreSQL mediante Sequelize (ORM).

Autenticación y autorización con JWT (hash bcrypt) y controles de seguridad del OWASP Top 10 2023.

## Justificación

1. El dominio del juego es conocido, lo que permite concentrar el esfuerzo en los aspectos arquitectónicos.
2. El tiempo real (salas, rondas sincronizadas, puntaje en vivo) justifica una arquitectura de tres capas orientada a eventos: la lógica del juego emite eventos a los clientes suscritos sin acoplar frontend y base de datos.
3. El manejo de credenciales y sesiones lo convierte en un caso pertinente para JWT y OWASP Top 10.

## Objetivo general

Diseñar y desarrollar un juego multijugador de trivia en tiempo real para la web, sobre una arquitectura de tres capas orientada a eventos, con API REST documentada, comunicación WebSockets, persistencia relacional con ORM, autenticación JWT y controles de seguridad web.

## Objetivos específicos

1. Diseñar la arquitectura de tres capas con modelo orientado a eventos.
2. Implementar la API REST (Node.js/Express) documentada con OpenAPI 3.0 y Swagger.
3. Implementar la capa de eventos del juego (salas, rondas, puntajes) con WebSockets.
4. Modelar la capa de datos en PostgreSQL con Sequelize.
5. Desarrollar la capa de presentación en React consumiendo la API y los eventos, con sesión JWT.
6. Autenticación y autorización con JWT y contraseñas con hash bcrypt.
7. Controles de seguridad OWASP Top 10 2023 (inyección SQL, XSS, CSRF).
8. Pruebas de la API con Postman documentadas.

## Alcance

- **Jugador:** registrarse, iniciar sesión, crear/unirse a una sala, jugar rondas con tiempo límite, historial y estadísticas.
- **Motor del juego:** sincroniza rondas, valida respuestas en el servidor, calcula puntos por precisión y velocidad, y difunde el puntaje en tiempo real.
- **Esta entrega (Entrega 1):** documentación del proyecto (planteamiento, justificación, objetivos, alcance, relación con el curso y plan de trabajo). El código se versionará conforme avance el proceso de desarrollo (SDLC).

## Relación con los contenidos del curso

| Sesión | Aplicación en el proyecto |
|---|---|
| 1 – Full-stack: arquitectura cliente-servidor (Node.js/Express, Django) | Cliente-servidor como base, extendido a arquitectura de tres capas orientada a eventos |
| 2 – APIs REST modernas (OpenAPI 3.0) | API-first: contrato OpenAPI 3.0 documentado con Swagger |
| 3 – Integración backend-frontend | React consume la API REST (fetch/axios) y se suscribe a eventos con WebSockets, con sesión JWT |
| 4 – Persistencia con ORM (Sequelize) | Entidades Usuario, Pregunta, Partida y Puntuación en PostgreSQL con Sequelize |
| 5 – OAuth 2.1 y JWT | Acceso a la API y a los eventos del juego mediante JWT |
| 6 – Seguridad web (OWASP Top 10 2023) | Validación de entrada, consultas parametrizadas, anti-XSS, anti-CSRF, bcrypt |
| 7 – Pruebas y documentación (Postman/Swagger) | Pruebas de endpoints con Postman y documentación en Swagger |
| 8 – Taller integrador backend | El backend del juego como proyecto integrador (API, JWT, pruebas) |

## Metodología

Desarrollo ágil iterativo e incremental, con sprints alineados a las entregas del curso. Git con ramas por funcionalidad e integración mediante pull requests. Enfoque API-first y arquitectura por capas para desarrollar backend y frontend en paralelo.

## Plan de trabajo

1. Definición de la arquitectura de tres capas y del contrato API (OpenAPI 3.0).
2. Capa de datos: modelos Sequelize y migraciones.
3. Capa de lógica de negocio: API REST, JWT y contraseñas seguras.
4. Capa de eventos en tiempo real con WebSockets.
5. Capa de presentación en React.
6. Controles de seguridad (OWASP) y validaciones del servidor.
7. Pruebas con Postman y documentación en Swagger.
8. Integración de las tres capas y pruebas end-to-end multijugador.

## Reparto de responsabilidades

- **Juan Cabral:** arquitectura, capa de datos, lógica de negocio, JWT, seguridad y tiempo real (WebSockets).
- **Steven Rusinque Gutierrez:** contrato OpenAPI, capa de presentación en React, consumo de API y pruebas con Postman/Swagger.

## Referencias

- Fielding, R. T. (2000). *Architectural styles and the design of network-based software architectures* (Tesis doctoral). UC Irvine.
- Fette, I., & Melnikov, A. (2011). *The WebSocket protocol (RFC 6455)*. IETF.
- Fowler, M. (2002). *Patterns of enterprise application architecture*. Addison-Wesley.
- Hardt, D. (2012). *The OAuth 2.0 authorization framework (RFC 6749)*. IETF.
- Jones, M., Bradley, J., & Sakimura, N. (2015). *JSON Web Token (JWT) (RFC 7519)*. IETF.
- OWASP Foundation (2023). *OWASP Top 10*. https://owasp.org/www-project-top-ten/
- Sequelize (2024). *Sequelize documentation*. https://sequelize.org/docs/v6/
- OpenAPI Initiative (2020). *OpenAPI Specification v3.0.3*. https://spec.openapis.org/oas/v3.0.3
- Richardson, L., & Amundsen, M. (2013). *RESTful web APIs*. O'Reilly Media.
