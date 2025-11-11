Aquí tienes 20 grupos diferentes de sistemas de administración, cada uno con sus tablas, atributos, tipos de campos y relaciones, presentados en formato de tabla y sin generar código.

---

**Grupo 1: Sistema de Administración de una Librería**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Libro** | id_libro, titulo, isbn, fecha_publicacion, num_paginas, id_autor, id_editorial, precio, stock | INT, VARCHAR(255), VARCHAR(13), DATE, INT, INT, INT, DECIMAL(10,2), INT |
| **Autor** | id_autor, nombre, apellido, nacionalidad, fecha_nacimiento, biografia, email | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, TEXT, VARCHAR(100) |
| **Editorial** | id_editorial, nombre, direccion, telefono, email, pais, sitio_web | INT, VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(50), VARCHAR(255) |
| **Cliente** | id_cliente, nombre, apellido, direccion, telefono, email, fecha_registro, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(20) |
| **Empleado** | id_empleado, nombre, apellido, dni, fecha_contratacion, cargo, salario, telefono | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, VARCHAR(50), DECIMAL(10,2), VARCHAR(20) |
| **Venta** | id_venta, fecha_venta, id_cliente, id_empleado, total_venta, metodo_pago, descuento_aplicado | INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2) |
| **Detalle_Venta** | id_detalle, id_venta, id_libro, cantidad, precio_unitario, subtotal, iva_aplicado | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2) |

**Relaciones:**
*   Libro (id_autor) -> Autor (id_autor) (Muchos a Uno)
*   Libro (id_editorial) -> Editorial (id_editorial) (Muchos a Uno)
*   Venta (id_cliente) -> Cliente (id_cliente) (Muchos a Uno)
*   Venta (id_empleado) -> Empleado (id_empleado) (Muchos a Uno)
*   Detalle_Venta (id_venta) -> Venta (id_venta) (Muchos a Uno)
*   Detalle_Venta (id_libro) -> Libro (id_libro) (Muchos a Uno)

---

**Grupo 2: Sistema de Gestión de un Hospital**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Paciente** | id_paciente, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, num_seguro_social | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(20) |
| **Medico** | id_medico, nombre, apellido, especialidad, telefono, email, licencia_medica, salario, fecha_contratacion | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DECIMAL(10,2), DATE |
| **Cita** | id_cita, id_paciente, id_medico, fecha_cita, hora_cita, motivo, estado_cita, comentarios | INT, INT, INT, DATE, TIME, TEXT, VARCHAR(50), TEXT |
| **Historial_Medico** | id_historial, id_paciente, fecha_registro, diagnostico, tratamiento, medicamentos, notas, id_medico_tratante | INT, INT, DATETIME, TEXT, TEXT, TEXT, TEXT, INT |
| **Habitacion** | id_habitacion, numero_habitacion, tipo_habitacion, estado_habitacion, costo_diario, capacidad, descripcion | INT, VARCHAR(10), VARCHAR(50), VARCHAR(50), DECIMAL(10,2), INT, TEXT |
| **Internacion** | id_internacion, id_paciente, id_habitacion, fecha_ingreso, fecha_salida, diagnostico_ingreso, costo_total, observaciones | INT, INT, INT, DATETIME, DATETIME, TEXT, DECIMAL(10,2), TEXT |
| **Factura** | id_factura, id_paciente, fecha_emision, total_factura, estado_pago, fecha_vencimiento, id_internacion, id_cita | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), DATE, INT, INT |

**Relaciones:**
*   Cita (id_paciente) -> Paciente (id_paciente) (Muchos a Uno)
*   Cita (id_medico) -> Medico (id_medico) (Muchos a Uno)
*   Historial_Medico (id_paciente) -> Paciente (id_paciente) (Muchos a Uno)
*   Historial_Medico (id_medico_tratante) -> Medico (id_medico) (Muchos a Uno)
*   Internacion (id_paciente) -> Paciente (id_paciente) (Muchos a Uno)
*   Internacion (id_habitacion) -> Habitacion (id_habitacion) (Muchos a Uno)
*   Factura (id_paciente) -> Paciente (id_paciente) (Muchos a Uno)
*   Factura (id_internacion) -> Internacion (id_internacion) (Uno a Uno o Muchos a Uno)
*   Factura (id_cita) -> Cita (id_cita) (Uno a Uno o Muchos a Uno)

---

**Grupo 3: Sistema de Gestión de un Restaurante**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Plato** | id_plato, nombre_plato, descripcion, precio, categoria, tiempo_preparacion, ingredientes, disponible | INT, VARCHAR(100), TEXT, DECIMAL(10,2), VARCHAR(50), INT, TEXT, BOOLEAN |
| **Mesa** | id_mesa, numero_mesa, capacidad, estado_mesa, ubicacion, es_reservable, observaciones | INT, INT, INT, VARCHAR(50), VARCHAR(100), BOOLEAN, TEXT |
| **Empleado_Restaurante** | id_empleado, nombre, apellido, cargo, salario, fecha_contratacion, telefono, email, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DECIMAL(10,2), DATE, VARCHAR(20), VARCHAR(100), VARCHAR(20) |
| **Pedido** | id_pedido, fecha_pedido, id_mesa, id_empleado, estado_pedido, total_pedido, tipo_pedido, hora_pedido | INT, DATETIME, INT, INT, VARCHAR(50), DECIMAL(10,2), VARCHAR(50), TIME |
| **Detalle_Pedido** | id_detalle_pedido, id_pedido, id_plato, cantidad, precio_unitario, notas_plato, subtotal, descuento_item | INT, INT, INT, INT, DECIMAL(10,2), TEXT, DECIMAL(10,2), DECIMAL(5,2) |
| **Cliente_Restaurante** | id_cliente, nombre, apellido, telefono, email, fecha_registro, preferencias_alimentarias, puntos_fidelidad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, TEXT, INT |
| **Reserva** | id_reserva, id_cliente, id_mesa, fecha_reserva, hora_reserva, num_personas, estado_reserva, comentarios | INT, INT, INT, DATE, TIME, INT, VARCHAR(50), TEXT |

**Relaciones:**
*   Pedido (id_mesa) -> Mesa (id_mesa) (Muchos a Uno)
*   Pedido (id_empleado) -> Empleado_Restaurante (id_empleado) (Muchos a Uno)
*   Detalle_Pedido (id_pedido) -> Pedido (id_pedido) (Muchos a Uno)
*   Detalle_Pedido (id_plato) -> Plato (id_plato) (Muchos a Uno)
*   Reserva (id_cliente) -> Cliente_Restaurante (id_cliente) (Muchos a Uno)
*   Reserva (id_mesa) -> Mesa (id_mesa) (Muchos a Uno)

---

**Grupo 4: Sistema de Inventario y Ventas para una Tienda de Ropa**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Producto** | id_producto, nombre_producto, descripcion, precio, stock, id_categoria, id_marca, talla, color, material | INT, VARCHAR(255), TEXT, DECIMAL(10,2), INT, INT, INT, VARCHAR(10), VARCHAR(20), VARCHAR(50) |
| **Categoria** | id_categoria, nombre_categoria, descripcion_categoria, fecha_creacion, ultima_actualizacion, es_activa | INT, VARCHAR(100), TEXT, DATETIME, DATETIME, BOOLEAN |
| **Marca** | id_marca, nombre_marca, pais_origen, sitio_web, telefono_contacto, fecha_registro | INT, VARCHAR(100), VARCHAR(50), VARCHAR(255), VARCHAR(20), DATE |
| **Venta_Ropa** | id_venta, fecha_venta, id_cliente, id_empleado, total_venta, metodo_pago, descuento_total, estado_venta | INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2), VARCHAR(50) |
| **Detalle_Venta_Ropa** | id_detalle, id_venta, id_producto, cantidad, precio_unitario, subtotal, iva_aplicado, id_talla_vendida | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), VARCHAR(10) |
| **Cliente_Ropa** | id_cliente, nombre, apellido, direccion, telefono, email, fecha_registro, puntos_fidelidad, preferencias_estilo | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, INT, TEXT |
| **Empleado_Tienda** | id_empleado, nombre, apellido, cargo, dni, fecha_contratacion, salario, telefono, email | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(20), VARCHAR(100) |

**Relaciones:**
*   Producto (id_categoria) -> Categoria (id_categoria) (Muchos a Uno)
*   Producto (id_marca) -> Marca (id_marca) (Muchos a Uno)
*   Venta_Ropa (id_cliente) -> Cliente_Ropa (id_cliente) (Muchos a Uno)
*   Venta_Ropa (id_empleado) -> Empleado_Tienda (id_empleado) (Muchos a Uno)
*   Detalle_Venta_Ropa (id_venta) -> Venta_Ropa (id_venta) (Muchos a Uno)
*   Detalle_Venta_Ropa (id_producto) -> Producto (id_producto) (Muchos a Uno)

---

**Grupo 5: Sistema de Gestión de Proyectos**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Proyecto** | id_proyecto, nombre_proyecto, descripcion, fecha_inicio, fecha_fin_estimada, estado_proyecto, presupuesto, id_gerente | INT, VARCHAR(255), TEXT, DATE, DATE, VARCHAR(50), DECIMAL(15,2), INT |
| **Tarea** | id_tarea, nombre_tarea, descripcion, fecha_inicio, fecha_fin_estimada, estado_tarea, prioridad, id_proyecto, id_asignado | INT, VARCHAR(255), TEXT, DATE, DATE, VARCHAR(50), VARCHAR(20), INT, INT |
| **Empleado_Proyecto** | id_empleado, nombre, apellido, email, telefono, cargo, fecha_contratacion, salario, habilidades | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), DATE, DECIMAL(10,2), TEXT |
| **Asignacion_Tarea** | id_asignacion, id_tarea, id_empleado, fecha_asignacion, fecha_entrega, progreso, comentarios | INT, INT, INT, DATETIME, DATE, INT, TEXT |
| **Hito** | id_hito, nombre_hito, fecha_estimada, fecha_completado, descripcion, id_proyecto, estado_hito, responsable | INT, VARCHAR(255), DATE, DATE, TEXT, INT, VARCHAR(50), INT |
| **Documento** | id_documento, nombre_documento, tipo_documento, fecha_subida, url_documento, id_proyecto, id_autor_documento, version | INT, VARCHAR(255), VARCHAR(50), DATETIME, VARCHAR(255), INT, INT, VARCHAR(10) |
| **Comentario** | id_comentario, id_tarea, id_empleado, fecha_comentario, texto_comentario, id_documento_adjunto | INT, INT, INT, DATETIME, TEXT, INT |

**Relaciones:**
*   Proyecto (id_gerente) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Tarea (id_proyecto) -> Proyecto (id_proyecto) (Muchos a Uno)
*   Tarea (id_asignado) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Asignacion_Tarea (id_tarea) -> Tarea (id_tarea) (Muchos a Uno)
*   Asignacion_Tarea (id_empleado) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Hito (id_proyecto) -> Proyecto (id_proyecto) (Muchos a Uno)
*   Hito (responsable) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Documento (id_proyecto) -> Proyecto (id_proyecto) (Muchos a Uno)
*   Documento (id_autor_documento) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Comentario (id_tarea) -> Tarea (id_tarea) (Muchos a Uno)
*   Comentario (id_empleado) -> Empleado_Proyecto (id_empleado) (Muchos a Uno)
*   Comentario (id_documento_adjunto) -> Documento (id_documento) (Muchos a Uno)

---

**Grupo 6: Sistema de Gestión Escolar**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Estudiante** | id_estudiante, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, num_matricula, fecha_inscripcion | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(20), DATE |
| **Profesor** | id_profesor, nombre, apellido, email, telefono, especialidad, fecha_contratacion, salario, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, DECIMAL(10,2), VARCHAR(20) |
| **Curso** | id_curso, nombre_curso, descripcion, creditos, id_profesor, horario, aula, nivel_educativo, costo_curso | INT, VARCHAR(100), TEXT, INT, INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), DECIMAL(10,2) |
| **Inscripcion** | id_inscripcion, id_estudiante, id_curso, fecha_inscripcion, estado_inscripcion, nota_final, fecha_modificacion | INT, INT, INT, DATE, VARCHAR(50), DECIMAL(4,2), DATETIME |
| **Asistencia** | id_asistencia, id_estudiante, id_curso, fecha_clase, presente, justificacion, comentarios | INT, INT, INT, DATE, BOOLEAN, TEXT, TEXT |
| **Materia** | id_materia, nombre_materia, descripcion, nivel_academico, es_obligatoria, horas_semanales | INT, VARCHAR(100), TEXT, VARCHAR(50), BOOLEAN, INT |
| **Calificacion** | id_calificacion, id_inscripcion, tipo_evaluacion, fecha_evaluacion, puntaje, ponderacion, comentarios | INT, INT, VARCHAR(50), DATE, DECIMAL(5,2), DECIMAL(3,2), TEXT |

**Relaciones:**
*   Inscripcion (id_estudiante) -> Estudiante (id_estudiante) (Muchos a Uno)
*   Inscripcion (id_curso) -> Curso (id_curso) (Muchos a Uno)
*   Curso (id_profesor) -> Profesor (id_profesor) (Muchos a Uno)
*   Asistencia (id_estudiante) -> Estudiante (id_estudiante) (Muchos a Uno)
*   Asistencia (id_curso) -> Curso (id_curso) (Muchos a Uno)
*   Calificacion (id_inscripcion) -> Inscripcion (id_inscripcion) (Muchos a Uno)

---

**Grupo 7: Sistema de Gestión de Gimnasio**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Socio** | id_socio, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, fecha_registro, tipo_membresia, fecha_vencimiento_membresia | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50), DATE |
| **Membresia** | id_membresia, tipo_membresia, descripcion, costo, duracion_meses, beneficios, num_sesiones_incluidas, es_activa | INT, VARCHAR(50), TEXT, DECIMAL(10,2), INT, TEXT, INT, BOOLEAN |
| **Entrenador** | id_entrenador, nombre, apellido, especialidad, telefono, email, fecha_contratacion, salario, certificado | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, DECIMAL(10,2), VARCHAR(100) |
| **Clase** | id_clase, nombre_clase, descripcion, horario, duracion_minutos, id_entrenador, cupo_maximo, costo_clase, nivel_dificultad | INT, VARCHAR(100), TEXT, VARCHAR(100), INT, INT, INT, DECIMAL(10,2), VARCHAR(50) |
| **Reserva_Clase** | id_reserva, id_socio, id_clase, fecha_reserva, estado_reserva, fecha_cancelacion, comentarios | INT, INT, INT, DATETIME, VARCHAR(50), DATETIME, TEXT |
| **Pago** | id_pago, id_socio, fecha_pago, monto, metodo_pago, concepto, id_membresia_pagada, estado_pago | INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(50), VARCHAR(100), INT, VARCHAR(50) |
| **Rutina_Personalizada** | id_rutina, id_socio, id_entrenador, fecha_creacion, objetivo, descripcion_ejercicios, frecuencia, duracion_semanas | INT, INT, INT, DATE, VARCHAR(100), TEXT, VARCHAR(50), INT |

**Relaciones:**
*   Socio (tipo_membresia) -> Membresia (tipo_membresia) (Muchos a Uno)
*   Clase (id_entrenador) -> Entrenador (id_entrenador) (Muchos a Uno)
*   Reserva_Clase (id_socio) -> Socio (id_socio) (Muchos a Uno)
*   Reserva_Clase (id_clase) -> Clase (id_clase) (Muchos a Uno)
*   Pago (id_socio) -> Socio (id_socio) (Muchos a Uno)
*   Pago (id_membresia_pagada) -> Membresia (id_membresia) (Muchos a Uno)
*   Rutina_Personalizada (id_socio) -> Socio (id_socio) (Muchos a Uno)
*   Rutina_Personalizada (id_entrenador) -> Entrenador (id_entrenador) (Muchos a Uno)

---

**Grupo 8: Sistema de Gestión de Hotel**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Huesped** | id_huesped, nombre, apellido, fecha_nacimiento, nacionalidad, direccion, telefono, email, dni_pasaporte, fecha_registro | INT, VARCHAR(100), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE |
| **Habitacion_Hotel** | id_habitacion, numero_habitacion, tipo_habitacion, capacidad, precio_noche, estado_habitacion, caracteristicas, piso | INT, VARCHAR(10), VARCHAR(50), INT, DECIMAL(10,2), VARCHAR(50), TEXT, INT |
| **Reserva_Hotel** | id_reserva, id_huesped, fecha_entrada, fecha_salida, numero_adultos, numero_ninos, estado_reserva, total_reserva, fecha_reserva | INT, INT, DATE, DATE, INT, INT, VARCHAR(50), DECIMAL(10,2), DATETIME |
| **Detalle_Reserva** | id_detalle_reserva, id_reserva, id_habitacion, precio_noche_reservado, cantidad_noches, subtotal, servicios_adicionales | INT, INT, INT, DECIMAL(10,2), INT, DECIMAL(10,2), TEXT |
| **Empleado_Hotel** | id_empleado, nombre, apellido, cargo, fecha_contratacion, salario, telefono, email, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2), VARCHAR(20), VARCHAR(100), VARCHAR(20) |
| **Servicio_Adicional** | id_servicio, nombre_servicio, descripcion, costo_unitario, disponible, categoria, duracion | INT, VARCHAR(100), TEXT, DECIMAL(10,2), BOOLEAN, VARCHAR(50), VARCHAR(50) |
| **Factura_Hotel** | id_factura, id_reserva, fecha_emision, total_factura, estado_pago, metodo_pago, id_huesped_pago, fecha_vencimiento | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), INT, DATE |

**Relaciones:**
*   Reserva_Hotel (id_huesped) -> Huesped (id_huesped) (Muchos a Uno)
*   Detalle_Reserva (id_reserva) -> Reserva_Hotel (id_reserva) (Muchos a Uno)
*   Detalle_Reserva (id_habitacion) -> Habitacion_Hotel (id_habitacion) (Muchos a Uno)
*   Factura_Hotel (id_reserva) -> Reserva_Hotel (id_reserva) (Uno a Uno o Muchos a Uno)
*   Factura_Hotel (id_huesped_pago) -> Huesped (id_huesped) (Muchos a Uno)

---

**Grupo 9: Sistema de Gestión de Inmobiliaria**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Propiedad** | id_propiedad, direccion, tipo_propiedad, num_habitaciones, num_banos, superficie_m2, precio_venta, precio_alquiler, estado_propiedad, fecha_publicacion, descripcion | INT, VARCHAR(255), VARCHAR(50), INT, INT, DECIMAL(10,2), DECIMAL(15,2), DECIMAL(15,2), VARCHAR(50), DATE, TEXT |
| **Propietario** | id_propietario, nombre, apellido, telefono, email, direccion_propietario, fecha_registro, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), DATE, VARCHAR(20) |
| **Cliente_Inmobiliaria** | id_cliente, nombre, apellido, telefono, email, preferencias_propiedad, presupuesto_maximo, fecha_registro, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), TEXT, DECIMAL(15,2), DATE, VARCHAR(20) |
| **Agente_Inmobiliario** | id_agente, nombre, apellido, telefono, email, licencia_agente, fecha_contratacion, salario, comision_porcentaje | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2), DECIMAL(5,2) |
| **Visita_Propiedad** | id_visita, id_propiedad, id_cliente, id_agente, fecha_visita, hora_visita, comentarios_cliente, calificacion_propiedad | INT, INT, INT, INT, DATE, TIME, TEXT, INT |
| **Contrato_Venta** | id_contrato_venta, id_propiedad, id_propietario, id_cliente, id_agente, fecha_contrato, precio_final, fecha_cierre, estado_contrato, comision_agente | INT, INT, INT, INT, INT, DATE, DECIMAL(15,2), DATE, VARCHAR(50), DECIMAL(10,2) |
| **Contrato_Alquiler** | id_contrato_alquiler, id_propiedad, id_propietario, id_cliente, id_agente, fecha_inicio, fecha_fin, monto_alquiler_mensual, estado_contrato, deposito_garantia | INT, INT, INT, INT, INT, DATE, DATE, DECIMAL(10,2), VARCHAR(50), DECIMAL(10,2) |

**Relaciones:**
*   Propiedad (id_propietario) -> Propietario (id_propietario) (Muchos a Uno)
*   Visita_Propiedad (id_propiedad) -> Propiedad (id_propiedad) (Muchos a Uno)
*   Visita_Propiedad (id_cliente) -> Cliente_Inmobiliaria (id_cliente) (Muchos a Uno)
*   Visita_Propiedad (id_agente) -> Agente_Inmobiliario (id_agente) (Muchos a Uno)
*   Contrato_Venta (id_propiedad) -> Propiedad (id_propiedad) (Uno a Uno)
*   Contrato_Venta (id_propietario) -> Propietario (id_propietario) (Muchos a Uno)
*   Contrato_Venta (id_cliente) -> Cliente_Inmobiliaria (id_cliente) (Muchos a Uno)
*   Contrato_Venta (id_agente) -> Agente_Inmobiliario (id_agente) (Muchos a Uno)
*   Contrato_Alquiler (id_propiedad) -> Propiedad (id_propiedad) (Uno a Uno)
*   Contrato_Alquiler (id_propietario) -> Propietario (id_propietario) (Muchos a Uno)
*   Contrato_Alquiler (id_cliente) -> Cliente_Inmobiliaria (id_cliente) (Muchos a Uno)
*   Contrato_Alquiler (id_agente) -> Agente_Inmobiliario (id_agente) (Muchos a Uno)

---

**Grupo 10: Sistema de Gestión de Flota de Vehículos**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Vehiculo** | id_vehiculo, marca, modelo, ano_fabricacion, tipo_vehiculo, matricula, num_chasis, fecha_adquisicion, id_conductor_asignado, estado_vehiculo, kilometraje_actual | INT, VARCHAR(50), VARCHAR(50), INT, VARCHAR(50), VARCHAR(20), VARCHAR(50), DATE, INT, VARCHAR(50), INT |
| **Conductor** | id_conductor, nombre, apellido, dni, licencia_conducir, fecha_contratacion, telefono, email, fecha_nacimiento, estado_empleado | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), DATE, VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50) |
| **Mantenimiento** | id_mantenimiento, id_vehiculo, fecha_mantenimiento, tipo_mantenimiento, costo_mantenimiento, descripcion_trabajo, proximo_mantenimiento, taller_mecanico | INT, INT, DATE, VARCHAR(100), DECIMAL(10,2), TEXT, DATE, VARCHAR(100) |
| **Ruta** | id_ruta, nombre_ruta, origen, destino, distancia_km, tiempo_estimado_horas, descripcion_ruta, peajes_incluidos | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), DECIMAL(10,2), DECIMAL(5,2), TEXT, BOOLEAN |
| **Viaje** | id_viaje, id_vehiculo, id_conductor, id_ruta, fecha_inicio_viaje, fecha_fin_viaje, kilometraje_inicio, kilometraje_fin, combustible_gastado, comentarios | INT, INT, INT, INT, DATETIME, DATETIME, INT, INT, DECIMAL(10,2), TEXT |
| **Gasolina** | id_recarga, id_vehiculo, fecha_recarga, cantidad_litros, precio_litro, total_gasto, tipo_combustible, estacion_servicio, kilometraje_recarga | INT, INT, DATETIME, DECIMAL(8,2), DECIMAL(5,2), DECIMAL(10,2), VARCHAR(50), VARCHAR(100), INT |
| **Seguro** | id_seguro, id_vehiculo, numero_poliza, fecha_inicio_poliza, fecha_fin_poliza, compania_seguros, tipo_cobertura, costo_anual, fecha_pago_renovacion | INT, INT, VARCHAR(50), DATE, DATE, VARCHAR(100), VARCHAR(100), DECIMAL(10,2), DATE |

**Relaciones:**
*   Vehiculo (id_conductor_asignado) -> Conductor (id_conductor) (Muchos a Uno)
*   Mantenimiento (id_vehiculo) -> Vehiculo (id_vehiculo) (Muchos a Uno)
*   Viaje (id_vehiculo) -> Vehiculo (id_vehiculo) (Muchos a Uno)
*   Viaje (id_conductor) -> Conductor (id_conductor) (Muchos a Uno)
*   Viaje (id_ruta) -> Ruta (id_ruta) (Muchos a Uno)
*   Gasolina (id_vehiculo) -> Vehiculo (id_vehiculo) (Muchos a Uno)
*   Seguro (id_vehiculo) -> Vehiculo (id_vehiculo) (Muchos a Uno)

---

**Grupo 11: Sistema de Gestión de Recursos Humanos**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Empleado_RRHH** | id_empleado, nombre, apellido, dni, fecha_nacimiento, genero, direccion, telefono, email, fecha_contratacion, cargo, salario, departamento, estado_empleado | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(100), DECIMAL(10,2), VARCHAR(100), VARCHAR(50) |
| **Departamento** | id_departamento, nombre_departamento, descripcion, id_gerente_departamento, fecha_creacion, num_empleados | INT, VARCHAR(100), TEXT, INT, DATE, INT |
| **Puesto** | id_puesto, nombre_puesto, descripcion_puesto, salario_minimo, salario_maximo, nivel_jerarquico, habilidades_requeridas | INT, VARCHAR(100), TEXT, DECIMAL(10,2), DECIMAL(10,2), VARCHAR(50), TEXT |
| **Ausencia** | id_ausencia, id_empleado, tipo_ausencia, fecha_inicio, fecha_fin, estado_aprobacion, motivo_ausencia, comentarios | INT, INT, VARCHAR(50), DATE, DATE, VARCHAR(50), TEXT, TEXT |
| **Evaluacion_Desempeno** | id_evaluacion, id_empleado, fecha_evaluacion, calificacion, comentarios_evaluador, objetivos_establecidos, fecha_proxima_evaluacion, id_evaluador | INT, INT, DATE, DECIMAL(4,2), TEXT, TEXT, DATE, INT |
| **Capacitacion** | id_capacitacion, nombre_capacitacion, descripcion, fecha_inicio, fecha_fin, proveedor, costo, duracion_horas, es_obligatoria | INT, VARCHAR(255), TEXT, DATE, DATE, VARCHAR(100), DECIMAL(10,2), INT, BOOLEAN |
| **Participacion_Capacitacion** | id_participacion, id_empleado, id_capacitacion, fecha_inscripcion, estado_participacion, calificacion_obtenida, fecha_finalizacion | INT, INT, INT, DATE, VARCHAR(50), DECIMAL(4,2), DATE |

**Relaciones:**
*   Empleado_RRHH (departamento) -> Departamento (nombre_departamento) (Muchos a Uno) - (considerando nombre como clave)
*   Empleado_RRHH (cargo) -> Puesto (nombre_puesto) (Muchos a Uno) - (considerando nombre como clave)
*   Departamento (id_gerente_departamento) -> Empleado_RRHH (id_empleado) (Muchos a Uno)
*   Ausencia (id_empleado) -> Empleado_RRHH (id_empleado) (Muchos a Uno)
*   Evaluacion_Desempeno (id_empleado) -> Empleado_RRHH (id_empleado) (Muchos a Uno)
*   Evaluacion_Desempeno (id_evaluador) -> Empleado_RRHH (id_empleado) (Muchos a Uno)
*   Participacion_Capacitacion (id_empleado) -> Empleado_RRHH (id_empleado) (Muchos a Uno)
*   Participacion_Capacitacion (id_capacitacion) -> Capacitacion (id_capacitacion) (Muchos a Uno)

---

**Grupo 12: Sistema de Gestión de Eventos**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Evento** | id_evento, nombre_evento, descripcion, fecha_inicio, fecha_fin, ubicacion, tipo_evento, capacidad_maxima, costo_entrada, organizador, estado_evento | INT, VARCHAR(255), TEXT, DATETIME, DATETIME, VARCHAR(255), VARCHAR(50), INT, DECIMAL(10,2), VARCHAR(100), VARCHAR(50) |
| **Participante** | id_participante, nombre, apellido, email, telefono, fecha_registro, tipo_participante, empresa, pais | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATETIME, VARCHAR(50), VARCHAR(100), VARCHAR(50) |
| **Ticket** | id_ticket, id_evento, id_participante, fecha_compra, precio_pagado, tipo_ticket, estado_ticket, metodo_pago, codigo_qr | INT, INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), VARCHAR(50), VARCHAR(255) |
| **Agenda_Evento** | id_sesion, id_evento, nombre_sesion, descripcion_sesion, hora_inicio, hora_fin, orador, sala, tema | INT, INT, VARCHAR(255), TEXT, TIME, TIME, VARCHAR(100), VARCHAR(50), VARCHAR(100) |
| **Patrocinador** | id_patrocinador, nombre_patrocinador, nivel_patrocinio, contacto_persona, email_contacto, telefono_contacto, sitio_web, monto_patrocinio | INT, VARCHAR(100), VARCHAR(50), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(255), DECIMAL(10,2) |
| **Evento_Patrocinador** | id_evento_patrocinador, id_evento, id_patrocinador, fecha_inicio_acuerdo, fecha_fin_acuerdo, monto_acordado, tipo_beneficio | INT, INT, INT, DATE, DATE, DECIMAL(10,2), TEXT |
| **Feedback_Evento** | id_feedback, id_evento, id_participante, fecha_feedback, calificacion_general, comentarios_adicionales, sugerencias, calificacion_oradores | INT, INT, INT, DATETIME, INT, TEXT, TEXT, DECIMAL(4,2) |

**Relaciones:**
*   Ticket (id_evento) -> Evento (id_evento) (Muchos a Uno)
*   Ticket (id_participante) -> Participante (id_participante) (Muchos a Uno)
*   Agenda_Evento (id_evento) -> Evento (id_evento) (Muchos a Uno)
*   Evento_Patrocinador (id_evento) -> Evento (id_evento) (Muchos a Uno)
*   Evento_Patrocinador (id_patrocinador) -> Patrocinador (id_patrocinador) (Muchos a Uno)
*   Feedback_Evento (id_evento) -> Evento (id_evento) (Muchos a Uno)
*   Feedback_Evento (id_participante) -> Participante (id_participante) (Muchos a Uno)

---

**Grupo 13: Sistema de Gestión de Supermercado**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Producto_Super** | id_producto, nombre_producto, descripcion, precio_unitario, stock, id_categoria, id_proveedor, fecha_vencimiento, codigo_barras, peso_gramos, tipo_empaque | INT, VARCHAR(255), TEXT, DECIMAL(10,2), INT, INT, INT, DATE, VARCHAR(50), INT, VARCHAR(50) |
| **Categoria_Super** | id_categoria, nombre_categoria, descripcion_categoria, pasillo, fecha_creacion, es_perecedero | INT, VARCHAR(100), TEXT, VARCHAR(50), DATETIME, BOOLEAN |
| **Proveedor** | id_proveedor, nombre_proveedor, contacto_persona, telefono, email, direccion_proveedor, ruc | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20) |
| **Venta_Super** | id_venta, fecha_venta, id_cajero, id_cliente, total_venta, metodo_pago, descuento_aplicado, estado_venta, numero_ticket | INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2), VARCHAR(50), VARCHAR(50) |
| **Detalle_Venta_Super** | id_detalle, id_venta, id_producto, cantidad, precio_unitario_venta, subtotal, iva_aplicado, descuento_item | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), DECIMAL(5,2) |
| **Cajero** | id_cajero, nombre, apellido, dni, fecha_contratacion, salario, turno, telefono, email | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(20), VARCHAR(100) |
| **Cliente_Super** | id_cliente, nombre, apellido, telefono, email, fecha_registro, puntos_fidelidad, direccion_cliente, fecha_nacimiento | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, INT, VARCHAR(255), DATE |

**Relaciones:**
*   Producto_Super (id_categoria) -> Categoria_Super (id_categoria) (Muchos a Uno)
*   Producto_Super (id_proveedor) -> Proveedor (id_proveedor) (Muchos a Uno)
*   Venta_Super (id_cajero) -> Cajero (id_cajero) (Muchos a Uno)
*   Venta_Super (id_cliente) -> Cliente_Super (id_cliente) (Muchos a Uno)
*   Detalle_Venta_Super (id_venta) -> Venta_Super (id_venta) (Muchos a Uno)
*   Detalle_Venta_Super (id_producto) -> Producto_Super (id_producto) (Muchos a Uno)

---

**Grupo 14: Sistema de Gestión de Biblioteca Pública**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Libro_Biblioteca** | id_libro, titulo, autor, isbn, editorial, anio_publicacion, genero, disponibilidad, num_ejemplares, fecha_adquisicion, estanteria | INT, VARCHAR(255), VARCHAR(255), VARCHAR(13), VARCHAR(100), INT, VARCHAR(50), BOOLEAN, INT, DATE, VARCHAR(50) |
| **Socio** | id_socio, nombre, apellido, direccion, telefono, email, fecha_registro, fecha_vencimiento_membresia, dni, tipo_socio | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, DATE, VARCHAR(20), VARCHAR(50) |
| **Prestamo** | id_prestamo, id_libro, id_socio, fecha_prestamo, fecha_devolucion_esperada, fecha_devolucion_real, estado_prestamo, multa_generada, id_bibliotecario | INT, INT, INT, DATETIME, DATE, DATETIME, VARCHAR(50), DECIMAL(10,2), INT |
| **Autor_Biblioteca** | id_autor, nombre_autor, apellido_autor, nacionalidad, fecha_nacimiento, biografia, libros_destacados, fecha_fallecimiento | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, TEXT, TEXT, DATE |
| **Editorial_Biblioteca** | id_editorial, nombre_editorial, pais_origen, direccion, telefono, email, sitio_web, fecha_fundacion | INT, VARCHAR(100), VARCHAR(50), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(255), DATE |
| **Bibliotecario** | id_bibliotecario, nombre, apellido, dni, fecha_contratacion, cargo, telefono, email, turno | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, VARCHAR(50), VARCHAR(20), VARCHAR(100), VARCHAR(50) |
| **Multa** | id_multa, id_prestamo, monto_multa, fecha_generacion, fecha_pago, estado_pago, motivo_multa, id_socio_multado | INT, INT, DECIMAL(10,2), DATETIME, DATETIME, VARCHAR(50), TEXT, INT |

**Relaciones:**
*   Libro_Biblioteca (id_autor) -> Autor_Biblioteca (id_autor) (Muchos a Uno) - (Si se tiene en cuenta un solo autor por libro)
*   Libro_Biblioteca (editorial) -> Editorial_Biblioteca (nombre_editorial) (Muchos a Uno) - (considerando nombre como clave)
*   Prestamo (id_libro) -> Libro_Biblioteca (id_libro) (Muchos a Uno)
*   Prestamo (id_socio) -> Socio (id_socio) (Muchos a Uno)
*   Prestamo (id_bibliotecario) -> Bibliotecario (id_bibliotecario) (Muchos a Uno)
*   Multa (id_prestamo) -> Prestamo (id_prestamo) (Muchos a Uno)
*   Multa (id_socio_multado) -> Socio (id_socio) (Muchos a Uno)

---

**Grupo 15: Sistema de Gestión de Clínicas Veterinarias**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Mascota** | id_mascota, nombre_mascota, especie, raza, fecha_nacimiento, genero, peso_kg, id_propietario, chip_identificacion, color, esterilizado | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), DATE, CHAR(1), DECIMAL(5,2), INT, VARCHAR(50), VARCHAR(50), BOOLEAN |
| **Propietario** | id_propietario, nombre, apellido, direccion, telefono, email, fecha_registro, dni, ocupacion | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(20), VARCHAR(100) |
| **Veterinario** | id_veterinario, nombre, apellido, especialidad, telefono, email, licencia_veterinaria, fecha_contratacion, salario | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2) |
| **Consulta** | id_consulta, id_mascota, id_veterinario, fecha_consulta, motivo_consulta, diagnostico, tratamiento, peso_mascota_consulta, observaciones | INT, INT, INT, DATETIME, TEXT, TEXT, TEXT, DECIMAL(5,2), TEXT |
| **Vacuna** | id_vacuna, nombre_vacuna, descripcion, laboratorio, fecha_vencimiento_lote, tipo_enfermedad | INT, VARCHAR(100), TEXT, VARCHAR(100), DATE, VARCHAR(100) |
| **Historial_Vacunacion** | id_historial_vac, id_mascota, id_vacuna, fecha_aplicacion, fecha_proxima_dosis, id_veterinario_aplico, numero_lote, comentarios | INT, INT, INT, DATE, DATE, INT, VARCHAR(50), TEXT |
| **Factura_Veterinaria** | id_factura, id_propietario, fecha_emision, total_factura, estado_pago, metodo_pago, id_consulta_asociada, fecha_vencimiento | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), INT, DATE |

**Relaciones:**
*   Mascota (id_propietario) -> Propietario (id_propietario) (Muchos a Uno)
*   Consulta (id_mascota) -> Mascota (id_mascota) (Muchos a Uno)
*   Consulta (id_veterinario) -> Veterinario (id_veterinario) (Muchos a Uno)
*   Historial_Vacunacion (id_mascota) -> Mascota (id_mascota) (Muchos a Uno)
*   Historial_Vacunacion (id_vacuna) -> Vacuna (id_vacuna) (Muchos a Uno)
*   Historial_Vacunacion (id_veterinario_aplico) -> Veterinario (id_veterinario) (Muchos a Uno)
*   Factura_Veterinaria (id_propietario) -> Propietario (id_propietario) (Muchos a Uno)
*   Factura_Veterinaria (id_consulta_asociada) -> Consulta (id_consulta) (Muchos a Uno)

---

**Grupo 16: Sistema de Gestión de Taller Mecánico**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Vehiculo_Taller** | id_vehiculo, marca, modelo, ano, matricula, num_chasis, id_cliente, kilometraje_entrada, color, fecha_recepcion, estado_general | INT, VARCHAR(50), VARCHAR(50), INT, VARCHAR(20), VARCHAR(50), INT, INT, VARCHAR(20), DATETIME, TEXT |
| **Cliente_Taller** | id_cliente, nombre, apellido, telefono, email, direccion_cliente, dni, fecha_registro, preferencia_contacto | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), DATE, VARCHAR(50) |
| **Mecanico** | id_mecanico, nombre, apellido, especialidad, telefono, email, fecha_contratacion, salario, certificado | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, DECIMAL(10,2), VARCHAR(100) |
| **Orden_Reparacion** | id_orden, id_vehiculo, fecha_recepcion, fecha_salida_estimada, estado_orden, diagnostico_inicial, costo_estimado, id_mecanico_asignado, observaciones | INT, INT, DATETIME, DATE, VARCHAR(50), TEXT, DECIMAL(10,2), INT, TEXT |
| **Repuesto** | id_repuesto, nombre_repuesto, descripcion, precio_unitario, stock, id_proveedor_repuesto, num_pieza_fabricante, compatibilidad_vehiculos | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, INT, VARCHAR(50), TEXT |
| **Detalle_Reparacion** | id_detalle_rep, id_orden, id_repuesto, cantidad_repuesto, precio_repuesto_unitario, mano_obra_horas, costo_mano_obra_hora, subtotal_item | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(5,2), DECIMAL(10,2), DECIMAL(10,2) |
| **Factura_Taller** | id_factura, id_orden, fecha_emision, total_factura, estado_pago, metodo_pago, fecha_vencimiento, id_cliente_factura, iva_aplicado | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE, INT, DECIMAL(5,2) |

**Relaciones:**
*   Vehiculo_Taller (id_cliente) -> Cliente_Taller (id_cliente) (Muchos a Uno)
*   Orden_Reparacion (id_vehiculo) -> Vehiculo_Taller (id_vehiculo) (Muchos a Uno)
*   Orden_Reparacion (id_mecanico_asignado) -> Mecanico (id_mecanico) (Muchos a Uno)
*   Detalle_Reparacion (id_orden) -> Orden_Reparacion (id_orden) (Muchos a Uno)
*   Detalle_Reparacion (id_repuesto) -> Repuesto (id_repuesto) (Muchos a Uno)
*   Factura_Taller (id_orden) -> Orden_Reparacion (id_orden) (Muchos a Uno)
*   Factura_Taller (id_cliente_factura) -> Cliente_Taller (id_cliente) (Muchos a Uno)

---

**Grupo 17: Sistema de Gestión de Bodega/Almacén**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Producto_Almacen** | id_producto, nombre_producto, descripcion, codigo_sku, stock_actual, ubicacion_almacen, id_categoria, id_proveedor, peso_kg, volumen_m3, fecha_ultimo_movimiento | INT, VARCHAR(255), TEXT, VARCHAR(50), INT, VARCHAR(100), INT, INT, DECIMAL(10,2), DECIMAL(10,2), DATETIME |
| **Categoria_Almacen** | id_categoria, nombre_categoria, descripcion_categoria, temperatura_ideal, tipo_almacenamiento, es_peligroso | INT, VARCHAR(100), TEXT, VARCHAR(50), VARCHAR(50), BOOLEAN |
| **Proveedor_Almacen** | id_proveedor, nombre_proveedor, contacto_persona, telefono, email, direccion_proveedor, ruc, pais_origen | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(50) |
| **Entrada_Producto** | id_entrada, id_producto, cantidad_entrada, fecha_entrada, id_proveedor, num_factura_compra, costo_unitario, id_empleado_recepcion, observaciones | INT, INT, INT, DATETIME, INT, VARCHAR(50), DECIMAL(10,2), INT, TEXT |
| **Salida_Producto** | id_salida, id_producto, cantidad_salida, fecha_salida, destino, id_cliente_salida, num_pedido_salida, id_empleado_despacho, motivo_salida | INT, INT, INT, DATETIME, VARCHAR(100), INT, VARCHAR(50), INT, TEXT |
| **Empleado_Almacen** | id_empleado, nombre, apellido, dni, fecha_contratacion, cargo, turno, telefono, email, licencia_manejo_montacargas | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, VARCHAR(50), VARCHAR(50), VARCHAR(20), VARCHAR(100), BOOLEAN |
| **Inventario_Fisico** | id_inventario, fecha_inventario, id_producto, stock_sistema, stock_fisico, diferencia, id_empleado_realizo, comentarios, ultima_actualizacion | INT, DATE, INT, INT, INT, INT, INT, TEXT, DATETIME |

**Relaciones:**
*   Producto_Almacen (id_categoria) -> Categoria_Almacen (id_categoria) (Muchos a Uno)
*   Producto_Almacen (id_proveedor) -> Proveedor_Almacen (id_proveedor) (Muchos a Uno)
*   Entrada_Producto (id_producto) -> Producto_Almacen (id_producto) (Muchos a Uno)
*   Entrada_Producto (id_proveedor) -> Proveedor_Almacen (id_proveedor) (Muchos a Uno)
*   Entrada_Producto (id_empleado_recepcion) -> Empleado_Almacen (id_empleado) (Muchos a Uno)
*   Salida_Producto (id_producto) -> Producto_Almacen (id_producto) (Muchos a Uno)
*   Salida_Producto (id_empleado_despacho) -> Empleado_Almacen (id_empleado) (Muchos a Uno)
*   Inventario_Fisico (id_producto) -> Producto_Almacen (id_producto) (Muchos a Uno)
*   Inventario_Fisico (id_empleado_realizo) -> Empleado_Almacen (id_empleado) (Muchos a Uno)

---

**Grupo 18: Sistema de Gestión de Clientes (CRM)**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Cliente_CRM** | id_cliente, nombre, apellido, empresa, email, telefono, direccion, fecha_registro, industria, sector, estado_cliente, fuente_lead, notas_cliente | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(100), VARCHAR(20), VARCHAR(255), DATETIME, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(50), TEXT |
| **Contacto_CRM** | id_contacto, id_cliente, nombre_contacto, apellido_contacto, email_contacto, telefono_contacto, cargo_contacto, fecha_nacimiento, rol | INT, INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50) |
| **Oportunidad_Venta** | id_oportunidad, id_cliente, nombre_oportunidad, descripcion, valor_estimado, etapa_venta, fecha_cierre_estimada, id_comercial_responsable, probabilidad_cierre, fecha_creacion | INT, INT, VARCHAR(255), TEXT, DECIMAL(15,2), VARCHAR(50), DATE, INT, DECIMAL(3,2), DATETIME |
| **Actividad_CRM** | id_actividad, id_oportunidad, id_contacto, tipo_actividad, fecha_actividad, hora_actividad, descripcion_actividad, estado_actividad, id_empleado_realizo | INT, INT, INT, VARCHAR(50), DATE, TIME, TEXT, VARCHAR(50), INT |
| **Empleado_Comercial** | id_empleado, nombre, apellido, email, telefono, cargo_comercial, fecha_contratacion, salario, cuota_ventas | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, DECIMAL(10,2), DECIMAL(10,2) |
| **Producto_Servicio_CRM** | id_item, nombre_item, descripcion, precio_lista, tipo_item, es_recurrente, fecha_lanzamiento, categoria_item | INT, VARCHAR(255), TEXT, DECIMAL(10,2), VARCHAR(50), BOOLEAN, DATE, VARCHAR(100) |
| **Detalle_Oportunidad** | id_detalle, id_oportunidad, id_item, cantidad, precio_unitario_acordado, subtotal_item, descuento_aplicado, fecha_agregado | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), DATETIME |

**Relaciones:**
*   Contacto_CRM (id_cliente) -> Cliente_CRM (id_cliente) (Muchos a Uno)
*   Oportunidad_Venta (id_cliente) -> Cliente_CRM (id_cliente) (Muchos a Uno)
*   Oportunidad_Venta (id_comercial_responsable) -> Empleado_Comercial (id_empleado) (Muchos a Uno)
*   Actividad_CRM (id_oportunidad) -> Oportunidad_Venta (id_oportunidad) (Muchos a Uno)
*   Actividad_CRM (id_contacto) -> Contacto_CRM (id_contacto) (Muchos a Uno)
*   Actividad_CRM (id_empleado_realizo) -> Empleado_Comercial (id_empleado) (Muchos a Uno)
*   Detalle_Oportunidad (id_oportunidad) -> Oportunidad_Venta (id_oportunidad) (Muchos a Uno)
*   Detalle_Oportunidad (id_item) -> Producto_Servicio_CRM (id_item) (Muchos a Uno)

---

**Grupo 19: Sistema de Gestión de Farmacia**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Medicamento** | id_medicamento, nombre_medicamento, descripcion, precio_venta, stock, id_proveedor, fecha_vencimiento, codigo_barra, principio_activo, forma_farmaceutica, requiere_receta | INT, VARCHAR(255), TEXT, DECIMAL(10,2), INT, INT, DATE, VARCHAR(50), VARCHAR(255), VARCHAR(100), BOOLEAN |
| **Proveedor_Farmacia** | id_proveedor, nombre_proveedor, contacto_persona, telefono, email, direccion_proveedor, ruc, fecha_registro | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), DATE |
| **Cliente_Farmacia** | id_cliente, nombre, apellido, telefono, email, direccion, fecha_registro, num_seguro_medico, fecha_nacimiento, preferencias | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), DATE, VARCHAR(50), DATE, TEXT |
| **Venta_Farmacia** | id_venta, fecha_venta, id_farmaceutico, id_cliente, total_venta, metodo_pago, descuento_total, numero_factura, estado_venta | INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2), VARCHAR(50), VARCHAR(50) |
| **Detalle_Venta_Farmacia** | id_detalle, id_venta, id_medicamento, cantidad, precio_unitario_venta, subtotal, iva_aplicado, id_receta_asociada | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), INT |
| **Farmaceutico** | id_farmaceutico, nombre, apellido, dni, fecha_contratacion, salario, licencia_colegiado, turno, telefono, email | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), VARCHAR(20), VARCHAR(100) |
| **Receta_Medica** | id_receta, id_cliente, id_medico_receto, fecha_emision, fecha_vencimiento, diagnostico, medicamento_recetado_texto, dosis_indicada, estado_receta | INT, INT, INT, DATE, DATE, TEXT, TEXT, TEXT, VARCHAR(50) |

**Relaciones:**
*   Medicamento (id_proveedor) -> Proveedor_Farmacia (id_proveedor) (Muchos a Uno)
*   Venta_Farmacia (id_farmaceutico) -> Farmaceutico (id_farmaceutico) (Muchos a Uno)
*   Venta_Farmacia (id_cliente) -> Cliente_Farmacia (id_cliente) (Muchos a Uno)
*   Detalle_Venta_Farmacia (id_venta) -> Venta_Farmacia (id_venta) (Muchos a Uno)
*   Detalle_Venta_Farmacia (id_medicamento) -> Medicamento (id_medicamento) (Muchos a Uno)
*   Detalle_Venta_Farmacia (id_receta_asociada) -> Receta_Medica (id_receta) (Muchos a Uno)
*   Receta_Medica (id_cliente) -> Cliente_Farmacia (id_cliente) (Muchos a Uno)
*   Receta_Medica (id_medico_receto) -> Veterinario (id_veterinario) o Medico (id_medico) (Muchos a Uno) - (Dependiendo de si se gestionan médicos externos o se asume un médico en la misma farmacia)

---

**Grupo 20: Sistema de Gestión de Consultora de Marketing Digital**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Cliente_Consultora** | id_cliente, nombre_empresa, contacto_principal, email_contacto, telefono_contacto, direccion_empresa, sector, fecha_inicio_contrato, estado_contrato, presupuesto_mensual | INT, VARCHAR(255), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(255), VARCHAR(100), DATE, VARCHAR(50), DECIMAL(10,2) |
| **Servicio_Marketing** | id_servicio, nombre_servicio, descripcion, costo_estandar, duracion_estimada_meses, es_recurrente, categoria_servicio, herramientas_utilizadas | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, BOOLEAN, VARCHAR(50), TEXT |
| **Proyecto_Marketing** | id_proyecto, id_cliente, nombre_proyecto, descripcion, fecha_inicio, fecha_fin_estimada, estado_proyecto, presupuesto_proyecto, id_gerente_proyecto, objetivos | INT, INT, VARCHAR(255), TEXT, DATE, DATE, VARCHAR(50), DECIMAL(10,2), INT, TEXT |
| **Empleado_Marketing** | id_empleado, nombre, apellido, cargo, especialidad, email, telefono, fecha_contratacion, salario, habilidades_digitales | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), TEXT |
| **Asignacion_Proyecto** | id_asignacion, id_proyecto, id_empleado, rol_en_proyecto, fecha_asignacion, fecha_finalizacion_asignacion, horas_estimadas, progreso | INT, INT, INT, VARCHAR(50), DATE, DATE, DECIMAL(5,2), INT |
| **Reporte_Rendimiento** | id_reporte, id_proyecto, fecha_reporte, metricas_clave, analisis_resultados, recomendaciones, id_empleado_genero, periodo_reporte, tipo_reporte | INT, INT, DATE, TEXT, TEXT, TEXT, INT, VARCHAR(50), VARCHAR(50) |
| **Factura_Consultora** | id_factura, id_cliente, id_proyecto, fecha_emision, monto_total, estado_pago, fecha_vencimiento, servicios_detallados_texto, impuestos_aplicados | INT, INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), DATE, TEXT, DECIMAL(5,2) |

**Relaciones:**
*   Proyecto_Marketing (id_cliente) -> Cliente_Consultora (id_cliente) (Muchos a Uno)
*   Proyecto_Marketing (id_gerente_proyecto) -> Empleado_Marketing (id_empleado) (Muchos a Uno)
*   Asignacion_Proyecto (id_proyecto) -> Proyecto_Marketing (id_proyecto) (Muchos a Uno)
*   Asignacion_Proyecto (id_empleado) -> Empleado_Marketing (id_empleado) (Muchos a Uno)
*   Reporte_Rendimiento (id_proyecto) -> Proyecto_Marketing (id_proyecto) (Muchos a Uno)
*   Reporte_Rendimiento (id_empleado_genero) -> Empleado_Marketing (id_empleado) (Muchos a Uno)
*   Factura_Consultora (id_cliente) -> Cliente_Consultora (id_cliente) (Muchos a Uno)
*   Factura_Consultora (id_proyecto) -> Proyecto_Marketing (id_proyecto) (Muchos a Uno)
