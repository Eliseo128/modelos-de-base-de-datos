
# 🏥 Grupo 1: Sistema de Gestión Hospitalaria

### **Entidades y Atributos**

| Entidad              | Atributos                                                                                                        | Tipo de Campo                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Paciente**         | id_paciente, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, tipo_sangre, fecha_registro | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(10), DATE |
| **Doctor**           | id_doctor, nombre, apellido, especialidad, telefono, email, num_licencia, fecha_contratacion, salario            | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2) |
| **Cita_Medica**      | id_cita, id_paciente, id_doctor, fecha_cita, hora_cita, motivo, estado, observaciones                            | INT, INT, INT, DATE, TIME, TEXT, VARCHAR(50), TEXT                                                         |
| **Diagnostico**      | id_diagnostico, id_cita, descripcion, tratamiento_recomendado, nivel_gravedad, fecha_registro                    | INT, INT, TEXT, TEXT, VARCHAR(50), DATE                                                                    |
| **Factura_Hospital** | id_factura, id_paciente, id_cita, total, estado_pago, metodo_pago, fecha_emision, descuento                      | INT, INT, INT, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE, DECIMAL(5,2)                                 |
| **Sala**             | id_sala, nombre, capacidad, tipo, disponibilidad                                                                 | INT, VARCHAR(100), INT, VARCHAR(50), BOOLEAN                                                               |

### **Relaciones**

* Cita_Medica(id_paciente) → Paciente(id_paciente) *(Muchos a Uno)*
* Cita_Medica(id_doctor) → Doctor(id_doctor) *(Muchos a Uno)*
* Diagnostico(id_cita) → Cita_Medica(id_cita) *(Muchos a Uno)*
* Factura_Hospital(id_cita) → Cita_Medica(id_cita) *(Muchos a Uno)*
* Factura_Hospital(id_paciente) → Paciente(id_paciente) *(Muchos a Uno)*

---

# 💊 Grupo 2: Sistema de Farmacia y Medicamentos

### **Entidades y Atributos**

| Entidad           | Atributos                                                                               | Tipo de Campo                                                           |
| ----------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **Medicamento**   | id_medicamento, nombre, descripcion, precio, stock, fecha_caducidad, id_proveedor, tipo | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, DATE, INT, VARCHAR(50)     |
| **Proveedor**     | id_proveedor, nombre, telefono, email, direccion, pais                                  | INT, VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(50) |
| **Cliente**       | id_cliente, nombre, telefono, direccion, email, fecha_registro                          | INT, VARCHAR(100), VARCHAR(20), VARCHAR(255), VARCHAR(100), DATE        |
| **Venta**         | id_venta, id_cliente, fecha_venta, total, metodo_pago                                   | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50)                              |
| **Detalle_Venta** | id_detalle, id_venta, id_medicamento, cantidad, subtotal                                | INT, INT, INT, INT, DECIMAL(10,2)                                       |
| **Empleado**      | id_empleado, nombre, puesto, telefono, salario, turno                                   | INT, VARCHAR(100), VARCHAR(50), VARCHAR(20), DECIMAL(10,2), VARCHAR(50) |

### **Relaciones**

* Venta(id_cliente) → Cliente(id_cliente)
* Detalle_Venta(id_venta) → Venta(id_venta)
* Detalle_Venta(id_medicamento) → Medicamento(id_medicamento)
* Medicamento(id_proveedor) → Proveedor(id_proveedor)

---

# 🦮 Grupo 3: Sistema de Clínica Veterinaria

### **Entidades y Atributos**

| Entidad         | Atributos                                                                                        | Tipo de Campo                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| **Mascota**     | id_mascota, nombre, especie, raza, edad, id_dueño, peso, sexo                                    | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), INT, INT, DECIMAL(5,2), CHAR(1)         |
| **Dueño**       | id_dueño, nombre, telefono, direccion, email, fecha_registro                                     | INT, VARCHAR(100), VARCHAR(20), VARCHAR(255), VARCHAR(100), DATE                     |
| **Veterinario** | id_veterinario, nombre, especialidad, telefono, email, num_colegiado, turno                      | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), VARCHAR(50) |
| **Consulta**    | id_consulta, id_mascota, id_veterinario, fecha_consulta, motivo, diagnostico, tratamiento, costo | INT, INT, INT, DATE, TEXT, TEXT, TEXT, DECIMAL(10,2)                                 |
| **Vacuna**      | id_vacuna, nombre, tipo, fecha_aplicacion, id_mascota                                            | INT, VARCHAR(100), VARCHAR(50), DATE, INT                                            |

### **Relaciones**

* Mascota(id_dueño) → Dueño(id_dueño)
* Consulta(id_mascota) → Mascota(id_mascota)
* Consulta(id_veterinario) → Veterinario(id_veterinario)
* Vacuna(id_mascota) → Mascota(id_mascota)

---

# 🏨 Grupo 4: Sistema de Reservaciones Hoteleras

### **Entidades y Atributos**

| Entidad        | Atributos                                                                 | Tipo de Campo                                                          |
| -------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Cliente**    | id_cliente, nombre, telefono, email, direccion                            | INT, VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255)             |
| **Habitación** | id_habitacion, numero, tipo, precio_noche, estado                         | INT, VARCHAR(10), VARCHAR(50), DECIMAL(10,2), VARCHAR(20)              |
| **Reserva**    | id_reserva, id_cliente, id_habitacion, fecha_ingreso, fecha_salida, total | INT, INT, INT, DATE, DATE, DECIMAL(10,2)                               |
| **Pago**       | id_pago, id_reserva, monto, metodo_pago, fecha_pago, estado               | INT, INT, DECIMAL(10,2), VARCHAR(50), DATE, VARCHAR(20)                |
| **Empleado**   | id_empleado, nombre, cargo, telefono, email, turno                        | INT, VARCHAR(100), VARCHAR(50), VARCHAR(20), VARCHAR(100), VARCHAR(50) |

### **Relaciones**

* Reserva(id_cliente) → Cliente(id_cliente)
* Reserva(id_habitacion) → Habitación(id_habitacion)
* Pago(id_reserva) → Reserva(id_reserva)

---

# 🎓 Grupo 5: Sistema de Control Escolar

### **Entidades y Atributos**

| Entidad         | Atributos                                                                 | Tipo de Campo                                                                 |
| --------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Alumno**      | id_alumno, nombre, apellido, matricula, fecha_nacimiento, email, telefono | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, VARCHAR(100), VARCHAR(20) |
| **Profesor**    | id_profesor, nombre, especialidad, telefono, email, salario               | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DECIMAL(10,2)     |
| **Materia**     | id_materia, nombre, creditos, semestre                                    | INT, VARCHAR(100), INT, INT                                                   |
| **Grupo**       | id_grupo, id_materia, id_profesor, aula, horario                          | INT, INT, INT, VARCHAR(20), VARCHAR(50)                                       |
| **Inscripción** | id_inscripcion, id_alumno, id_grupo, calificacion_final                   | INT, INT, INT, DECIMAL(4,2)                                                   |

### **Relaciones**

* Grupo(id_profesor) → Profesor(id_profesor)
* Grupo(id_materia) → Materia(id_materia)
* Inscripción(id_grupo) → Grupo(id_grupo)
* Inscripción(id_alumno) → Alumno(id_alumno)

---

# 🍽️ Grupo 6: Sistema de Restaurante

### **Entidades y Atributos**

| Entidad            | Atributos                                                               | Tipo de Campo                                              |
| ------------------ | ----------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Platillo**       | id_platillo, nombre, descripcion, precio, categoria, tiempo_preparacion | INT, VARCHAR(100), TEXT, DECIMAL(10,2), VARCHAR(50), INT   |
| **Cliente**        | id_cliente, nombre, telefono, email                                     | INT, VARCHAR(100), VARCHAR(20), VARCHAR(100)               |
| **Empleado**       | id_empleado, nombre, puesto, turno, salario                             | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), DECIMAL(10,2) |
| **Pedido**         | id_pedido, id_cliente, id_empleado, fecha, hora, estado                 | INT, INT, INT, DATE, TIME, VARCHAR(50)                     |
| **Detalle_Pedido** | id_detalle, id_pedido, id_platillo, cantidad, subtotal                  | INT, INT, INT, INT, DECIMAL(10,2)                          |

### **Relaciones**

* Pedido(id_cliente) → Cliente(id_cliente)
* Pedido(id_empleado) → Empleado(id_empleado)
* Detalle_Pedido(id_pedido) → Pedido(id_pedido)
* Detalle_Pedido(id_platillo) → Platillo(id_platillo)

---

# 🎬 Grupo 7: Sistema de Cine

### **Entidades y Atributos**

| Entidad      | Atributos                                                    | Tipo de Campo                                                 |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------- |
| **Pelicula** | id_pelicula, titulo, duracion, clasificacion, genero, idioma | INT, VARCHAR(100), INT, VARCHAR(10), VARCHAR(50), VARCHAR(50) |
| **Sala**     | id_sala, numero, capacidad, tipo                             | INT, INT, INT, VARCHAR(50)                                    |
| **Función**  | id_funcion, id_pelicula, id_sala, fecha, hora                | INT, INT, INT, DATE, TIME                                     |
| **Boleto**   | id_boleto, id_funcion, asiento, precio, estado               | INT, INT, VARCHAR(10), DECIMAL(10,2), VARCHAR(20)             |
| **Empleado** | id_empleado, nombre, puesto, turno                           | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50)                   |

### **Relaciones**

* Función(id_pelicula) → Pelicula(id_pelicula)
* Función(id_sala) → Sala(id_sala)
* Boleto(id_funcion) → Función(id_funcion)

---

# 🧾 Grupo 8: Sistema de Contabilidad Empresarial

### **Entidades y Atributos**

| Entidad        | Atributos                                                               | Tipo de Campo                                              |
| -------------- | ----------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Empleado**   | id_empleado, nombre, cargo, salario, departamento                       | INT, VARCHAR(100), VARCHAR(50), DECIMAL(10,2), VARCHAR(50) |
| **Cliente**    | id_cliente, nombre, email, telefono                                     | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20)               |
| **Factura**    | id_factura, id_cliente, fecha_emision, monto_total, estado, metodo_pago | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50)    |
| **Gasto**      | id_gasto, descripcion, monto, fecha, categoria                          | INT, TEXT, DECIMAL(10,2), DATE, VARCHAR(50)                |
| **Movimiento** | id_mov, tipo, fecha, monto, descripcion                                 | INT, VARCHAR(50), DATE, DECIMAL(10,2), TEXT                |

### **Relaciones**

* Factura(id_cliente) → Cliente(id_cliente)

---

# 🧠 Grupo 9: Sistema de Psicología Clínica

### **Entidades y Atributos**

| Entidad       | Atributos                                                               | Tipo de Campo                                                           |
| ------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **Paciente**  | id_paciente, nombre, edad, genero, telefono, email                      | INT, VARCHAR(100), INT, CHAR(1), VARCHAR(20), VARCHAR(100)              |
| **Psicologo** | id_psicologo, nombre, especialidad, telefono, email, cedula             | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50) |
| **Sesión**    | id_sesion, id_paciente, id_psicologo, fecha, hora, motivo, notas, costo | INT, INT, INT, DATE, TIME, TEXT, TEXT, DECIMAL(10,2)                    |
| **Factura**   | id_factura, id_paciente, id_sesion, total, estado_pago, fecha_emision   | INT, INT, INT, DECIMAL(10,2), VARCHAR(50), DATE                         |

### **Relaciones**

* Sesión(id_paciente) → Paciente(id_paciente)
* Sesión(id_psicologo) → Psicologo(id_psicologo)
* Factura(id_sesion) → Sesión(id_sesion)

---

# 🔬 Grupo 10: Sistema de Laboratorio Clínico

### **Entidades y Atributos**

| Entidad      | Atributos                                                                              | Tipo de Campo                                                |
| ------------ | -------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Paciente** | id_paciente, nombre, edad, genero, telefono, email                                     | INT, VARCHAR(100), INT, CHAR(1), VARCHAR(20), VARCHAR(100)   |
| **Prueba**   | id_prueba, nombre, tipo, costo, tiempo_resultado                                       | INT, VARCHAR(100), VARCHAR(50), DECIMAL(10,2), INT           |
| **Muestra**  | id_muestra, id_paciente, id_prueba, fecha_toma, tipo_muestra, resultado, observaciones | INT, INT, INT, DATE, VARCHAR(50), TEXT, TEXT                 |
| **Técnico**  | id_tecnico, nombre, turno, telefono, email                                             | INT, VARCHAR(100), VARCHAR(50), VARCHAR(20), VARCHAR(100)    |
| **Factura**  | id_factura, id_paciente, id_muestra, total, estado_pago, metodo_pago, fecha_emision    | INT, INT, INT, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE |

### **Relaciones**

* Muestra(id_paciente) → Paciente(id_paciente)
* Muestra(id_prueba) → Prueba(id_prueba)
* Factura(id_muestra) → Muestra(id_muestra)

---


