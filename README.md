
# ACTIVIDAD-U1-F01.-AN-LISIS-DE-UN-SISTEMA-REAL
# Universidad Autónoma de Nuevo León
## Facultad de Ingeniería Mecánica y Eléctrica
**Carrera:** Ingeniero en Tecnología de Software (ITS)

**Actividad:** Análisis de un Sistema Real 
**Alumno:** Angel Adrián Velez Contreras
**Matrícula:** 2145646

---

## 01. Sistema Seleccionado: Aplicación Bancaria

**Identificación Conceptual:**
* **Presentación:** Interfaz móvil (iOS y Android) donde el usuario consulta su saldo, ingresa credenciales y autoriza movimientos.
* **Lógica de negocio:** Motor que valida fondos suficientes, aprueba préstamos según el historial, aplica comisiones y verifica la autenticación (tokens/contraseñas).
* **Datos:** Bases de datos relacionales que almacenan la información de los clientes, cuentas, historial de transacciones y estados de las tarjetas.

---

## 02. Catálogo de Reglas de Negocio

| ID | Descripción | Condición | Acción | Prioridad |
| :--- | :--- | :--- | :--- | :--- |
| **RN-01** | Límite de transferencias | Si el monto a transferir supera $10,000 MXN diarios. | Solicitar autenticación biométrica o token. | Alta |
| **RN-02** | Fondos insuficientes | Si el monto + comisión es mayor al saldo. | Denegar la transacción. | Crítica |
| **RN-03** | Bloqueo de seguridad | Si se ingresa la contraseña mal 3 veces. | Bloquear el acceso a la cuenta. | Crítica |
| **RN-04** | Nuevo dispositivo | Si se inicia sesión desde un dispositivo nuevo. | Enviar código de verificación. | Alta |
| **RN-05** | Saldo mínimo | Si el saldo de cheques cae por debajo de $1,000. | Cobrar comisión de $50 MXN. | Media |
| **RN-06** | Aprobación de préstamo | Si hay historial limpio y nómina activa. | Pre-aprobar préstamo automáticamente. | Media |
| **RN-07** | Uso internacional | Si la tarjeta se usa fuera del país sin aviso. | Congelar transacción preventivamente. | Alta |
| **RN-08** | Pago de TDC | Si no se realiza el pago mínimo al corte. | Aplicar tasa de interés moratoria. | Alta |
| **RN-09** | Inactividad | Si la app está inactiva por 5 minutos. | Cerrar la sesión automáticamente. | Alta |
| **RN-10** | Reembolsos | Si se cancela una compra con débito. | Acreditar el monto en máximo 72 hrs. | Baja |

---

## 03. Modelado UML (Diagrama de Clases)

*El diagrama cuenta con 5 entidades principales y define 3 invariantes del dominio (Edad >= 18, Saldo >= 0, Monto de transacción > 0).*


<img width="622" height="665" alt="diagrama_uml" src="https://github.com/user-attachments/assets/3f815ca0-5cc7-418b-a01b-6acb8e565007" />

---

## 04. Proceso BPMN (Transferencia Bancaria)

*Flujo principal de una transferencia interbancaria utilizando swimlanes (Cliente y Sistema Core) y compuertas lógicas de validación.*


<img width="3425" height="8192" alt="diagrama_bpmn" src="https://github.com/user-attachments/assets/2e8867bc-f286-43b7-9e98-1a0da4ce7f7e" />
