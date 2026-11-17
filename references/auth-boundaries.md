# Autenticación antes del efecto protegido

Esta guía añade un control explícito de arquitectura y cobertura. La existencia de una comprobación dentro de un handler no demuestra que todas las entradas del sistema estén protegidas.

## Referencias

Consultadas el 2026-11-06:

- [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html): permisos en cada solicitud, denegación por defecto, controles ubicados correctamente y pruebas de integración. Recomienda mecanismos configurables de forma transversal, en lugar de depender de comprobaciones manuales en cada método.
- [OWASP REST Security](https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html): control de acceso por endpoint no público y validación de las credenciales presentadas. Si usa JWT, comprobar integridad y claims requeridos por su perfil; decodificar no equivale a verificar.

Consultar la documentación oficial del framework y versión encontrados para establecer el orden real de ejecución. No imponer la API de un framework a otro.

## Recorrido verificable

Para cada entrada protegida afectada, registrar:

| Método y ruta | Política pública/privada | Registro y montaje | Autenticación compartida | Autorización | Primer efecto protegido | Evidencia |
| --- | --- | --- | --- | --- | --- | --- |
| Ruta concreta del proyecto | Requisito o configuración | Archivo y línea | Archivo, línea y orden | Rol, recurso o tenant | Lectura, escritura, envío o tarea | Inspección y test real, o pendiente |

Seguir el arranque, los prefijos, routers anidados y aliases relevantes. Un middleware declarado pero no montado no protege; tampoco uno registrado después de una ruta que ya devuelve respuesta. Revisar los métodos HTTP realmente expuestos. No asumir que la protección del frontend, del proxy o del endpoint principal se hereda a otro acceso.

La identidad debe originarse en una credencial validada por un componente confiable. Si viene de un gateway, comprobar que el backend no pueda recibir la misma cabecera de un cliente no confiable por otro camino. No es necesario exigir que la autorización de cada objeto viva en middleware: puede requerir datos de negocio, pero debe ejecutarse antes del efecto protegido.

## Cómo clasificar

- **Defecto comprobado:** una ruta privada omite autenticación, acepta identidad no verificada, omite permisos o ejecuta operaciones antes del rechazo. Mostrar el camino concreto, efecto y severidad justificada.
- **Problema de arquitectura:** controles manuales repetidos dentro de handlers, sin aplicación transversal ni prueba de cobertura. Informarlo aunque no se haya demostrado un bypass, y distinguirlo de una vulnerabilidad reproducida. Proponer middleware o mecanismo equivalente con excepciones públicas explícitas.
- **Control equivalente verificado:** guard, filtro o dependencia compartida que se ejecuta antes de la lógica protegida, está conectada a las rutas y tiene política de cobertura. No generar un falso positivo por el nombre del archivo.
- **No verificable:** el router, arranque o componente de identidad no está disponible. Describir el hueco; no afirmar que la aplicación está protegida porque una función aislada rechaza algunos usuarios.

## Pruebas de regresión

Entrar por el cliente de prueba real del framework, un dispatcher equivalente o el transporte que expone la operación. No llamar solo a la función de negocio con una identidad prearmada para validar autenticación.

Cubrir ruta y alias privados con ausencia de credencial, credencial inválida y expirada/revocada si el mecanismo lo contempla. Cubrir usuario autenticado sin permiso y una operación permitida. Confirmar las excepciones públicas y la política de rutas nuevas o no declaradas.

Observar el cuerpo de respuesta, el estado y los efectos: una prueba que espera `401` puede pasar aunque ya se haya enviado un correo, leído un secreto o modificado la base. Instrumentar servicios posteriores o usar datos aislados para comprobar que no se ejecutaron; no sustituir el autenticador que se intenta probar. Los dobles de email o colas sirven para observar efectos, no para simular una autenticación exitosa.

Estas pruebas no certifican toda la aplicación. Registrar rutas efectivamente cubiertas y las pendientes, con su razón.
