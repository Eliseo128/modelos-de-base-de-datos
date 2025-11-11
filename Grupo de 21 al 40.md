
**Grupo 21: Sistema de Gestión de una Agencia de Viajes**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Destino** | id_destino, nombre_destino, pais, continente, descripcion, atracciones_principales, clima, divisa_local | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), TEXT, TEXT, VARCHAR(50), VARCHAR(10) |
| **Paquete_Turistico** | id_paquete, nombre_paquete, descripcion, fecha_inicio, fecha_fin, id_destino, precio_adulto, precio_nino, cupo_maximo, incluye_vuelo, incluye_alojamiento | INT, VARCHAR(255), TEXT, DATE, DATE, INT, DECIMAL(10,2), DECIMAL(10,2), INT, BOOLEAN, BOOLEAN |
| **Cliente_Viajes** | id_cliente, nombre, apellido, email, telefono, direccion, fecha_registro, preferencias_viaje, pasaporte | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(255), DATE, TEXT, VARCHAR(50) |
| **Reserva_Viaje** | id_reserva, id_paquete, id_cliente, fecha_reserva, num_adultos, num_ninos, total_pagado, estado_reserva, fecha_vencimiento_pago, id_agente_venta | INT, INT, INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DATE, INT |
| **Vuelo** | id_vuelo, num_vuelo, aerolinea, origen, destino, fecha_salida, hora_salida, fecha_llegada, hora_llegada, precio_clase_economica, asientos_disponibles | INT, VARCHAR(20), VARCHAR(100), VARCHAR(100), VARCHAR(100), DATE, TIME, DATE, TIME, DECIMAL(10,2), INT |
| **Alojamiento** | id_alojamiento, nombre_hotel, tipo_alojamiento, direccion, ciudad, pais, estrellas, precio_noche_estandar, servicios_incluidos, telefono | INT, VARCHAR(255), VARCHAR(50), VARCHAR(255), VARCHAR(100), VARCHAR(50), INT, DECIMAL(10,2), TEXT, VARCHAR(20) |
| **Agente_Viajes** | id_agente, nombre, apellido, email, telefono, dni, fecha_contratacion, salario_base, comision_porcentaje | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(20), DATE, DECIMAL(10,2), DECIMAL(5,2) |

**Relaciones:**
*   Paquete_Turistico (id_destino) -> Destino (id_destino) (Muchos a Uno)
*   Reserva_Viaje (id_paquete) -> Paquete_Turistico (id_paquete) (Muchos a Uno)
*   Reserva_Viaje (id_cliente) -> Cliente_Viajes (id_cliente) (Muchos a Uno)
*   Reserva_Viaje (id_agente_venta) -> Agente_Viajes (id_agente) (Muchos a Uno)
*   Paquete_Turistico (incluye_vuelo, incluye_alojamiento) pueden relacionarse con Vuelo y Alojamiento de forma implícita o a través de tablas intermedias de detalles de paquete.

---

**Grupo 22: Sistema de Gestión de Escuela de Música**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Estudiante_Musica** | id_estudiante, nombre, apellido, fecha_nacimiento, email, telefono, instrumento_principal, nivel_habilidad, fecha_inscripcion, direccion | INT, VARCHAR(100), VARCHAR(100), DATE, VARCHAR(100), VARCHAR(20), VARCHAR(50), VARCHAR(50), DATE, VARCHAR(255) |
| **Profesor_Musica** | id_profesor, nombre, apellido, email, telefono, instrumento_especialidad, experiencia_anos, fecha_contratacion, salario_hora, disponibilidad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), INT, DATE, DECIMAL(5,2), TEXT |
| **Instrumento** | id_instrumento, nombre_instrumento, tipo_instrumento, fabricante, anio_fabricacion, costo_alquiler_mensual, estado_disponibilidad, num_serie | INT, VARCHAR(100), VARCHAR(50), VARCHAR(100), INT, DECIMAL(10,2), BOOLEAN, VARCHAR(50) |
| **Clase_Musica** | id_clase, nombre_clase, id_profesor, instrumento_enseñanza, nivel, duracion_minutos, horario, cupo_maximo, costo_clase, tipo_clase | INT, VARCHAR(100), INT, VARCHAR(50), VARCHAR(50), INT, VARCHAR(100), INT, DECIMAL(10,2), VARCHAR(50) |
| **Inscripcion_Clase** | id_inscripcion, id_estudiante, id_clase, fecha_inscripcion, estado_inscripcion, nota_final, comentarios_profesor | INT, INT, INT, DATE, VARCHAR(50), DECIMAL(4,2), TEXT |
| **Alquiler_Instrumento** | id_alquiler, id_estudiante, id_instrumento, fecha_inicio_alquiler, fecha_fin_alquiler, monto_pagado, estado_instrumento_alquiler, fecha_devolucion | INT, INT, INT, DATE, DATE, DECIMAL(10,2), VARCHAR(50), DATE |
| **Pago_Musica** | id_pago, id_estudiante, fecha_pago, monto, concepto, metodo_pago, id_inscripcion_asociada, estado_pago | INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(100), VARCHAR(50), INT, VARCHAR(50) |

**Relaciones:**
*   Clase_Musica (id_profesor) -> Profesor_Musica (id_profesor) (Muchos a Uno)
*   Inscripcion_Clase (id_estudiante) -> Estudiante_Musica (id_estudiante) (Muchos a Uno)
*   Inscripcion_Clase (id_clase) -> Clase_Musica (id_clase) (Muchos a Uno)
*   Alquiler_Instrumento (id_estudiante) -> Estudiante_Musica (id_estudiante) (Muchos a Uno)
*   Alquiler_Instrumento (id_instrumento) -> Instrumento (id_instrumento) (Muchos a Uno)
*   Pago_Musica (id_estudiante) -> Estudiante_Musica (id_estudiante) (Muchos a Uno)
*   Pago_Musica (id_inscripcion_asociada) -> Inscripcion_Clase (id_inscripcion) (Muchos a Uno)

---

**Grupo 23: Sistema de Gestión de Centro de Soporte Técnico**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Ticket_Soporte** | id_ticket, titulo, descripcion, fecha_creacion, estado, prioridad, id_cliente, id_agente_asignado, fecha_cierre, tipo_incidente, categoria, resolucion | INT, VARCHAR(255), TEXT, DATETIME, VARCHAR(50), VARCHAR(20), INT, INT, DATETIME, VARCHAR(50), VARCHAR(50), TEXT |
| **Cliente_Soporte** | id_cliente, nombre_empresa, contacto_principal, email_contacto, telefono_contacto, sector_empresa, fecha_registro, nivel_soporte, sitio_web | INT, VARCHAR(255), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(255) |
| **Agente_Soporte** | id_agente, nombre, apellido, email, telefono, especialidad, fecha_contratacion, nivel_experiencia, turno, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(50), VARCHAR(20) |
| **Interaccion** | id_interaccion, id_ticket, id_agente, fecha_interaccion, tipo_interaccion, descripcion_interaccion, archivos_adjuntos, duracion_minutos | INT, INT, INT, DATETIME, VARCHAR(50), TEXT, TEXT, INT |
| **Base_Conocimiento** | id_articulo, titulo_articulo, contenido_articulo, fecha_publicacion, autor, categoria_articulo, palabras_clave, veces_consultado, es_publico | INT, VARCHAR(255), TEXT, DATETIME, VARCHAR(100), VARCHAR(50), TEXT, INT, BOOLEAN |
| **Satisfaccion_Cliente** | id_encuesta, id_ticket, fecha_encuesta, calificacion_agente, calificacion_resolucion, comentarios_cliente, fecha_envio, fue_resuelto | INT, INT, DATETIME, INT, INT, TEXT, DATETIME, BOOLEAN |
| **SLA** | id_sla, nombre_sla, descripcion, tiempo_respuesta_horas, tiempo_resolucion_horas, prioridad_asociada, penalizacion_incumplimiento, es_activo | INT, VARCHAR(100), TEXT, INT, INT, VARCHAR(20), TEXT, BOOLEAN |

**Relaciones:**
*   Ticket_Soporte (id_cliente) -> Cliente_Soporte (id_cliente) (Muchos a Uno)
*   Ticket_Soporte (id_agente_asignado) -> Agente_Soporte (id_agente) (Muchos a Uno)
*   Interaccion (id_ticket) -> Ticket_Soporte (id_ticket) (Muchos a Uno)
*   Interaccion (id_agente) -> Agente_Soporte (id_agente) (Muchos a Uno)
*   Satisfaccion_Cliente (id_ticket) -> Ticket_Soporte (id_ticket) (Muchos a Uno)

---

**Grupo 24: Sistema de Gestión de Producción Audiovisual**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Proyecto_Audiovisual** | id_proyecto, titulo, tipo_produccion, fecha_inicio, fecha_fin_estimada, presupuesto, estado_proyecto, id_director, descripcion, distribucion_prevista | INT, VARCHAR(255), VARCHAR(50), DATE, DATE, DECIMAL(15,2), VARCHAR(50), INT, TEXT, VARCHAR(100) |
| **Miembro_Equipo** | id_miembro, nombre, apellido, rol, email, telefono, fecha_contratacion, salario_base, especialidad_tecnica, disponibilidad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(100), TEXT |
| **Rol_Produccion** | id_rol, nombre_rol, descripcion_rol, departamento, salario_promedio, habilidades_requeridas | INT, VARCHAR(50), TEXT, VARCHAR(50), DECIMAL(10,2), TEXT |
| **Escena** | id_escena, id_proyecto, numero_escena, descripcion_escena, localizacion, fecha_grabacion_estimada, hora_grabacion, actores_involucrados, equipos_especiales | INT, INT, INT, TEXT, VARCHAR(255), DATE, TIME, TEXT, TEXT |
| **Material_Grabado** | id_material, id_escena, tipo_material, duracion_segundos, formato_archivo, fecha_grabacion_real, ruta_almacenamiento, notas_tecnicas, version | INT, INT, VARCHAR(50), INT, VARCHAR(20), DATETIME, VARCHAR(255), TEXT, VARCHAR(10) |
| **Presupuesto_Detalle** | id_item_presupuesto, id_proyecto, categoria_gasto, descripcion_gasto, monto_estimado, monto_real, fecha_gasto, aprobado_por, tipo_moneda | INT, INT, VARCHAR(100), TEXT, DECIMAL(10,2), DECIMAL(10,2), DATE, VARCHAR(100), VARCHAR(10) |
| **Contrato_Talento** | id_contrato, id_proyecto, id_miembro, fecha_firma, salario_acordado, clausulas_especiales, duracion_contrato, rol_especifico | INT, INT, INT, DATE, DECIMAL(10,2), TEXT, VARCHAR(50), VARCHAR(100) |

**Relaciones:**
*   Proyecto_Audiovisual (id_director) -> Miembro_Equipo (id_miembro) (Muchos a Uno)
*   Miembro_Equipo (rol) -> Rol_Produccion (nombre_rol) (Muchos a Uno) - (considerando nombre como clave)
*   Escena (id_proyecto) -> Proyecto_Audiovisual (id_proyecto) (Muchos a Uno)
*   Material_Grabado (id_escena) -> Escena (id_escena) (Muchos a Uno)
*   Presupuesto_Detalle (id_proyecto) -> Proyecto_Audiovisual (id_proyecto) (Muchos a Uno)
*   Contrato_Talento (id_proyecto) -> Proyecto_Audiovisual (id_proyecto) (Muchos a Uno)
*   Contrato_Talento (id_miembro) -> Miembro_Equipo (id_miembro) (Muchos a Uno)

---

**Grupo 25: Sistema de Gestión de Centro de Reciclaje**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Material_Reciclable** | id_material, nombre_material, descripcion, tipo_material, precio_por_kg, unidad_medida, es_toxico, punto_acopio_recomendado, codigo_identificacion | INT, VARCHAR(100), TEXT, VARCHAR(50), DECIMAL(5,2), VARCHAR(20), BOOLEAN, VARCHAR(100), VARCHAR(50) |
| **Centro_Acopio** | id_centro, nombre_centro, direccion, telefono, email, horario_atencion, capacidad_toneladas, latitud, longitud | INT, VARCHAR(255), VARCHAR(255), VARCHAR(20), VARCHAR(100), TEXT, DECIMAL(10,2), DECIMAL(10,6), DECIMAL(10,6) |
| **Donante** | id_donante, nombre_donante, tipo_donante, telefono, email, direccion_donante, ruc_dni, fecha_registro, es_anonimo | INT, VARCHAR(255), VARCHAR(50), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), DATE, BOOLEAN |
| **Recepcion_Material** | id_recepcion, id_material, id_centro, id_donante, fecha_recepcion, cantidad_kg, estado_material, observaciones, id_empleado_recepciono | INT, INT, INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(50), TEXT, INT |
| **Procesamiento_Material** | id_procesamiento, id_recepcion, fecha_inicio_procesamiento, fecha_fin_procesamiento, tipo_proceso, cantidad_resultante_kg, subproductos, id_empleado_procesa, costo_procesamiento | INT, INT, DATETIME, DATETIME, VARCHAR(100), DECIMAL(10,2), TEXT, INT, DECIMAL(10,2) |
| **Empleado_Reciclaje** | id_empleado, nombre, apellido, dni, fecha_contratacion, cargo, turno, telefono, email, certificaciones | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, VARCHAR(50), VARCHAR(50), VARCHAR(20), VARCHAR(100), TEXT |
| **Venta_Material** | id_venta, id_material, id_cliente_comprador, fecha_venta, cantidad_kg_vendido, precio_por_kg_venta, total_venta, metodo_pago, id_empleado_venta | INT, INT, INT, DATETIME, DECIMAL(10,2), DECIMAL(5,2), DECIMAL(10,2), VARCHAR(50), INT |

**Relaciones:**
*   Recepcion_Material (id_material) -> Material_Reciclable (id_material) (Muchos a Uno)
*   Recepcion_Material (id_centro) -> Centro_Acopio (id_centro) (Muchos a Uno)
*   Recepcion_Material (id_donante) -> Donante (id_donante) (Muchos a Uno)
*   Recepcion_Material (id_empleado_recepciono) -> Empleado_Reciclaje (id_empleado) (Muchos a Uno)
*   Procesamiento_Material (id_recepcion) -> Recepcion_Material (id_recepcion) (Muchos a Uno)
*   Procesamiento_Material (id_empleado_procesa) -> Empleado_Reciclaje (id_empleado) (Muchos a Uno)
*   Venta_Material (id_material) -> Material_Reciclable (id_material) (Muchos a Uno)
*   Venta_Material (id_empleado_venta) -> Empleado_Reciclaje (id_empleado) (Muchos a Uno)

---

**Grupo 26: Sistema de Gestión de Guardería Infantil**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Nino** | id_nino, nombre, apellido, fecha_nacimiento, genero, id_padre_madre_principal, alergias, necesidades_especiales, grupo_asignado, fecha_inscripcion | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), INT, TEXT, TEXT, VARCHAR(50), DATE |
| **Padre_Madre** | id_padre_madre, nombre, apellido, email, telefono_principal, telefono_alternativo, direccion, dni, relacion_con_nino, profesion | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(20), VARCHAR(255), VARCHAR(20), VARCHAR(50), VARCHAR(100) |
| **Personal_Guarderia** | id_personal, nombre, apellido, cargo, email, telefono, fecha_contratacion, salario, dni, certificaciones, turno | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(20), TEXT, VARCHAR(50) |
| **Grupo_Ninos** | id_grupo, nombre_grupo, edad_minima, edad_maxima, id_personal_cargo, num_ninos_actual, capacidad_maxima, descripcion_actividades | INT, VARCHAR(50), INT, INT, INT, INT, INT, TEXT |
| **Actividad_Guarderia** | id_actividad, nombre_actividad, descripcion, horario, duracion_minutos, id_grupo, material_requerido, es_obligatoria | INT, VARCHAR(100), TEXT, VARCHAR(100), INT, INT, TEXT, BOOLEAN |
| **Asistencia_Nino** | id_asistencia, id_nino, fecha_asistencia, hora_entrada, hora_salida, estuvo_enfermo, notas_dia, id_personal_registro | INT, INT, DATE, TIME, TIME, BOOLEAN, TEXT, INT |
| **Pago_Mensualidad** | id_pago, id_nino, fecha_pago, monto_pagado, concepto, metodo_pago, mes_correspondiente, estado_pago, fecha_vencimiento | INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(100), VARCHAR(50), DATE, VARCHAR(50), DATE |

**Relaciones:**
*   Nino (id_padre_madre_principal) -> Padre_Madre (id_padre_madre) (Muchos a Uno)
*   Nino (grupo_asignado) -> Grupo_Ninos (nombre_grupo) (Muchos a Uno) - (considerando nombre como clave)
*   Grupo_Ninos (id_personal_cargo) -> Personal_Guarderia (id_personal) (Muchos a Uno)
*   Actividad_Guarderia (id_grupo) -> Grupo_Ninos (id_grupo) (Muchos a Uno)
*   Asistencia_Nino (id_nino) -> Nino (id_nino) (Muchos a Uno)
*   Asistencia_Nino (id_personal_registro) -> Personal_Guarderia (id_personal) (Muchos a Uno)
*   Pago_Mensualidad (id_nino) -> Nino (id_nino) (Muchos a Uno)

---

**Grupo 27: Sistema de Gestión de Lavandería**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Articulo_Ropa** | id_articulo, tipo_prenda, color, material, tamano, instrucciones_especiales, costo_lavado_estandar, estado_articulo, es_delicado, id_cliente | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), VARCHAR(20), TEXT, DECIMAL(5,2), VARCHAR(50), BOOLEAN, INT |
| **Cliente_Lavanderia** | id_cliente, nombre, apellido, telefono, email, direccion_recogida, direccion_entrega, fecha_registro, notas_cliente, preferencias_lavado | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(255), DATE, TEXT, TEXT |
| **Pedido_Lavanderia** | id_pedido, id_cliente, fecha_recepcion, fecha_entrega_estimada, fecha_entrega_real, estado_pedido, total_pedido, metodo_pago, id_empleado_recepcion, comentarios_cliente | INT, INT, DATETIME, DATE, DATETIME, VARCHAR(50), DECIMAL(10,2), VARCHAR(50), INT, TEXT |
| **Detalle_Pedido_Lavanderia** | id_detalle, id_pedido, id_articulo, cantidad, tipo_servicio, costo_servicio_individual, subtotal_item, manchas_detectadas, instrucciones_item | INT, INT, INT, INT, VARCHAR(50), DECIMAL(5,2), DECIMAL(10,2), TEXT, TEXT |
| **Empleado_Lavanderia** | id_empleado, nombre, apellido, cargo, fecha_contratacion, salario, turno, telefono, email, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(20), VARCHAR(100), VARCHAR(20) |
| **Maquina_Lavanderia** | id_maquina, tipo_maquina, marca, modelo, capacidad_kg, estado_operativo, ultima_revision, num_serie, es_lavadora, es_secadora | INT, VARCHAR(50), VARCHAR(100), VARCHAR(100), DECIMAL(5,2), VARCHAR(50), DATE, VARCHAR(50), BOOLEAN, BOOLEAN |
| **Reporte_Operacional** | id_reporte, fecha_reporte, id_empleado, num_pedidos_procesados, kg_ropa_procesada, tiempo_inactividad_maquinas, observaciones_turno, consumo_agua_litros | INT, DATE, INT, INT, DECIMAL(10,2), INT, TEXT, DECIMAL(10,2) |

**Relaciones:**
*   Articulo_Ropa (id_cliente) -> Cliente_Lavanderia (id_cliente) (Muchos a Uno)
*   Pedido_Lavanderia (id_cliente) -> Cliente_Lavanderia (id_cliente) (Muchos a Uno)
*   Pedido_Lavanderia (id_empleado_recepcion) -> Empleado_Lavanderia (id_empleado) (Muchos a Uno)
*   Detalle_Pedido_Lavanderia (id_pedido) -> Pedido_Lavanderia (id_pedido) (Muchos a Uno)
*   Detalle_Pedido_Lavanderia (id_articulo) -> Articulo_Ropa (id_articulo) (Muchos a Uno)
*   Reporte_Operacional (id_empleado) -> Empleado_Lavanderia (id_empleado) (Muchos a Uno)

---

**Grupo 28: Sistema de Gestión de Salón de Belleza/Estética**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Servicio_Estetica** | id_servicio, nombre_servicio, descripcion, precio, duracion_minutos, categoria_servicio, productos_usados, requiere_cita_previa | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, VARCHAR(50), TEXT, BOOLEAN |
| **Profesional_Estetica** | id_profesional, nombre, apellido, especialidad, email, telefono, fecha_contratacion, salario_base, comision_porcentaje, horario_trabajo | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), DECIMAL(5,2), TEXT |
| **Cliente_Estetica** | id_cliente, nombre, apellido, email, telefono, fecha_registro, preferencias_servicio, fecha_nacimiento, historial_alergias | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, TEXT, DATE, TEXT |
| **Cita_Estetica** | id_cita, id_cliente, id_profesional, id_servicio, fecha_cita, hora_cita, estado_cita, comentarios_cliente, precio_final_cita, duracion_real_minutos | INT, INT, INT, INT, DATE, TIME, VARCHAR(50), TEXT, DECIMAL(10,2), INT |
| **Producto_Venta** | id_producto_venta, nombre_producto, descripcion, precio_venta, stock, id_proveedor, marca, tipo_producto, fecha_vencimiento, codigo_barra | INT, VARCHAR(255), TEXT, DECIMAL(10,2), INT, INT, VARCHAR(100), VARCHAR(50), DATE, VARCHAR(50) |
| **Venta_Producto** | id_venta, id_cliente, id_profesional, fecha_venta, total_venta, metodo_pago, descuento_aplicado, numero_factura, estado_venta | INT, INT, INT, DATETIME, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2), VARCHAR(50), VARCHAR(50) |
| **Detalle_Venta_Producto** | id_detalle, id_venta, id_producto_venta, cantidad, precio_unitario_venta, subtotal, iva_aplicado, id_cita_asociada | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), INT |

**Relaciones:**
*   Cita_Estetica (id_cliente) -> Cliente_Estetica (id_cliente) (Muchos a Uno)
*   Cita_Estetica (id_profesional) -> Profesional_Estetica (id_profesional) (Muchos a Uno)
*   Cita_Estetica (id_servicio) -> Servicio_Estetica (id_servicio) (Muchos a Uno)
*   Venta_Producto (id_cliente) -> Cliente_Estetica (id_cliente) (Muchos a Uno)
*   Venta_Producto (id_profesional) -> Profesional_Estetica (id_profesional) (Muchos a Uno)
*   Detalle_Venta_Producto (id_venta) -> Venta_Producto (id_venta) (Muchos a Uno)
*   Detalle_Venta_Producto (id_producto_venta) -> Producto_Venta (id_producto_venta) (Muchos a Uno)
*   Detalle_Venta_Producto (id_cita_asociada) -> Cita_Estetica (id_cita) (Muchos a Uno)

---

**Grupo 29: Sistema de Gestión de Galería de Arte**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Obra_Arte** | id_obra, titulo, id_artista, anio_creacion, tecnica, dimensiones, valor_estimado, fecha_adquisicion, estado_conservacion, ubicacion_actual, descripcion | INT, VARCHAR(255), INT, INT, VARCHAR(100), VARCHAR(50), DECIMAL(15,2), DATE, VARCHAR(50), VARCHAR(100), TEXT |
| **Artista** | id_artista, nombre, apellido, nacionalidad, fecha_nacimiento, biografia, estilo_principal, sitio_web, fecha_fallecimiento | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, TEXT, VARCHAR(100), VARCHAR(255), DATE |
| **Exposicion** | id_exposicion, nombre_exposicion, descripcion, fecha_inicio, fecha_fin, sala, curador, costo_entrada, num_obras_expuestas, tema_exposicion | INT, VARCHAR(255), TEXT, DATETIME, DATETIME, VARCHAR(100), VARCHAR(100), DECIMAL(10,2), INT, VARCHAR(100) |
| **Obra_Exposicion** | id_obra_exp, id_obra, id_exposicion, fecha_montaje, fecha_desmontaje, posicion_en_sala, es_destacada, valor_asegurado_expo | INT, INT, INT, DATETIME, DATETIME, VARCHAR(50), BOOLEAN, DECIMAL(15,2) |
| **Cliente_Galeria** | id_cliente, nombre, apellido, email, telefono, direccion, fecha_registro, preferencias_arte, presupuesto_inversion | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(255), DATE, TEXT, DECIMAL(15,2) |
| **Venta_Obra** | id_venta, id_obra, id_cliente, fecha_venta, precio_final_venta, metodo_pago, id_empleado_venta, comision_galeria, fecha_entrega_obra | INT, INT, INT, DATETIME, DECIMAL(15,2), VARCHAR(50), INT, DECIMAL(5,2), DATE |
| **Empleado_Galeria** | id_empleado, nombre, apellido, cargo, email, telefono, fecha_contratacion, salario, especialidad_arte, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(100), VARCHAR(20) |

**Relaciones:**
*   Obra_Arte (id_artista) -> Artista (id_artista) (Muchos a Uno)
*   Obra_Exposicion (id_obra) -> Obra_Arte (id_obra) (Muchos a Uno)
*   Obra_Exposicion (id_exposicion) -> Exposicion (id_exposicion) (Muchos a Uno)
*   Venta_Obra (id_obra) -> Obra_Arte (id_obra) (Muchos a Uno)
*   Venta_Obra (id_cliente) -> Cliente_Galeria (id_cliente) (Muchos a Uno)
*   Venta_Obra (id_empleado_venta) -> Empleado_Galeria (id_empleado) (Muchos a Uno)

---

**Grupo 30: Sistema de Gestión de Centro de Idiomas**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Idioma** | id_idioma, nombre_idioma, familia_linguistica, nivel_dificultad_promedio, num_hablantes_estimado, es_popular | INT, VARCHAR(50), VARCHAR(50), VARCHAR(20), BIGINT, BOOLEAN |
| **Curso_Idioma** | id_curso, nombre_curso, id_idioma, nivel_curso, duracion_semanas, precio, cupo_maximo, horario_clase, material_incluido, fecha_inicio_oferta | INT, VARCHAR(100), INT, VARCHAR(50), INT, DECIMAL(10,2), INT, VARCHAR(100), TEXT, DATE |
| **Estudiante_Idioma** | id_estudiante, nombre, apellido, fecha_nacimiento, email, telefono, idioma_nativo, fecha_inscripcion, nivel_conocimiento_idioma | INT, VARCHAR(100), VARCHAR(100), DATE, VARCHAR(100), VARCHAR(20), VARCHAR(50), DATE, VARCHAR(50) |
| **Profesor_Idioma** | id_profesor, nombre, apellido, email, telefono, idioma_enseñanza, nivel_dominio, fecha_contratacion, salario_hora, nacionalidad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), VARCHAR(50), DATE, DECIMAL(5,2), VARCHAR(50) |
| **Inscripcion_Idioma** | id_inscripcion, id_estudiante, id_curso, fecha_inscripcion, estado_inscripcion, nota_final_curso, fecha_finalizacion, id_profesor_asignado | INT, INT, INT, DATE, VARCHAR(50), DECIMAL(4,2), DATE, INT |
| **Material_Didactico** | id_material, nombre_material, tipo_material, descripcion, editorial, costo, id_idioma, nivel_asociado, fecha_publicacion, es_obligatorio | INT, VARCHAR(255), VARCHAR(50), TEXT, VARCHAR(100), DECIMAL(10,2), INT, VARCHAR(50), DATE, BOOLEAN |
| **Evaluacion_Idioma** | id_evaluacion, id_inscripcion, tipo_evaluacion, fecha_evaluacion, puntaje_obtenido, ponderacion, comentarios_profesor, habilidades_evaluadas | INT, INT, VARCHAR(50), DATE, DECIMAL(5,2), DECIMAL(3,2), TEXT, TEXT |

**Relaciones:**
*   Curso_Idioma (id_idioma) -> Idioma (id_idioma) (Muchos a Uno)
*   Inscripcion_Idioma (id_estudiante) -> Estudiante_Idioma (id_estudiante) (Muchos a Uno)
*   Inscripcion_Idioma (id_curso) -> Curso_Idioma (id_curso) (Muchos a Uno)
*   Inscripcion_Idioma (id_profesor_asignado) -> Profesor_Idioma (id_profesor) (Muchos a Uno)
*   Material_Didactico (id_idioma) -> Idioma (id_idioma) (Muchos a Uno)
*   Evaluacion_Idioma (id_inscripcion) -> Inscripcion_Idioma (id_inscripcion) (Muchos a Uno)

---

**Grupo 31: Sistema de Gestión de Zoológico/Parque Natural**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Animal** | id_animal, nombre_animal, especie, fecha_nacimiento, genero, id_recinto, dieta, estado_salud, fecha_adquisicion, origen, chip_identificacion | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), INT, TEXT, VARCHAR(50), DATE, VARCHAR(100), VARCHAR(50) |
| **Recinto** | id_recinto, nombre_recinto, tipo_habitat, capacidad_animales, dimensiones_m2, ubicacion, temperatura_controlada, ultima_limpieza, descripcion_caracteristicas | INT, VARCHAR(100), VARCHAR(50), INT, DECIMAL(10,2), VARCHAR(100), BOOLEAN, DATETIME, TEXT |
| **Cuidador** | id_cuidador, nombre, apellido, especialidad_animal, email, telefono, fecha_contratacion, salario, turno, certificaciones | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), TEXT |
| **Actividad_Cuidado** | id_actividad, id_animal, id_cuidador, fecha_actividad, tipo_actividad, observaciones, duracion_minutos, medicamentos_administrados | INT, INT, INT, DATETIME, VARCHAR(100), TEXT, INT, TEXT |
| **Visitante** | id_visitante, nombre, apellido, email, telefono, tipo_entrada_comprada, fecha_visita, pais_origen, es_membresia_anual | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), DATE, VARCHAR(50), BOOLEAN |
| **Entrada** | id_entrada, tipo_entrada, descripcion, precio, validez_dias, beneficios_incluidos, es_para_nino, es_para_adulto | INT, VARCHAR(50), TEXT, DECIMAL(5,2), INT, TEXT, BOOLEAN, BOOLEAN |
| **Venta_Entrada** | id_venta, id_visitante, id_entrada, fecha_venta, cantidad, total_pagado, metodo_pago, fecha_uso_entrada, id_empleado_venta | INT, INT, INT, DATETIME, INT, DECIMAL(10,2), VARCHAR(50), DATE, INT |

**Relaciones:**
*   Animal (id_recinto) -> Recinto (id_recinto) (Muchos a Uno)
*   Actividad_Cuidado (id_animal) -> Animal (id_animal) (Muchos a Uno)
*   Actividad_Cuidado (id_cuidador) -> Cuidador (id_cuidador) (Muchos a Uno)
*   Venta_Entrada (id_visitante) -> Visitante (id_visitante) (Muchos a Uno)
*   Venta_Entrada (id_entrada) -> Entrada (id_entrada) (Muchos a Uno)
*   Venta_Entrada (id_empleado_venta) -> Cuidador (id_cuidador) (Muchos a Uno) - (Si los cuidadores también venden entradas, si no, se necesitaría una entidad Empleado General)

---

**Grupo 32: Sistema de Gestión de Centro de Llamadas/Call Center**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Llamada** | id_llamada, id_agente, id_cliente, fecha_hora_inicio, fecha_hora_fin, duracion_segundos, tipo_llamada, resultado_llamada, grabacion_url, motivo_llamada, calificacion_cliente | INT, INT, INT, DATETIME, DATETIME, INT, VARCHAR(50), VARCHAR(50), VARCHAR(255), TEXT, INT |
| **Agente_Call_Center** | id_agente, nombre, apellido, email, telefono, fecha_contratacion, salario, turno, habilidades_idiomas, estado_agente, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), TEXT, VARCHAR(50), VARCHAR(20) |
| **Cliente_Call_Center** | id_cliente, nombre_empresa, contacto_principal, email_contacto, telefono_contacto, sector, fecha_registro, historial_problemas, nivel_satisfaccion | INT, VARCHAR(255), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, TEXT, DECIMAL(4,2) |
| **Problema_Reportado** | id_problema, id_llamada, descripcion_problema, estado_problema, fecha_resolucion_estimada, prioridad, id_agente_resolvio, tipo_problema, comentarios_resolucion | INT, INT, TEXT, VARCHAR(50), DATE, VARCHAR(20), INT, VARCHAR(50), TEXT |
| **Encuesta_Satisfaccion** | id_encuesta, id_llamada, fecha_encuesta, calificacion_general, calificacion_agente, comentarios, fecha_envio_encuesta, fue_completada | INT, INT, DATETIME, INT, INT, TEXT, DATETIME, BOOLEAN |
| **Campana** | id_campana, nombre_campana, descripcion, fecha_inicio, fecha_fin, tipo_campana, objetivo, publico_objetivo, presupuesto_campana | INT, VARCHAR(255), TEXT, DATE, DATE, VARCHAR(50), TEXT, TEXT, DECIMAL(10,2) |
| **Participacion_Campana** | id_participacion, id_agente, id_campana, fecha_inicio_participacion, fecha_fin_participacion, num_llamadas_realizadas, num_exitos, tiempo_promedio_llamada | INT, INT, INT, DATE, DATE, INT, INT, INT |

**Relaciones:**
*   Llamada (id_agente) -> Agente_Call_Center (id_agente) (Muchos a Uno)
*   Llamada (id_cliente) -> Cliente_Call_Center (id_cliente) (Muchos a Uno)
*   Problema_Reportado (id_llamada) -> Llamada (id_llamada) (Muchos a Uno)
*   Problema_Reportado (id_agente_resolvio) -> Agente_Call_Center (id_agente) (Muchos a Uno)
*   Encuesta_Satisfaccion (id_llamada) -> Llamada (id_llamada) (Muchos a Uno)
*   Participacion_Campana (id_agente) -> Agente_Call_Center (id_agente) (Muchos a Uno)
*   Participacion_Campana (id_campana) -> Campana (id_campana) (Muchos a Uno)

---

**Grupo 33: Sistema de Gestión de Consultorio Dental**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Paciente_Dental** | id_paciente, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, num_seguro_dental, fecha_registro, historial_medico_previo | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, TEXT |
| **Odontologo** | id_odontologo, nombre, apellido, especialidad, telefono, email, licencia_dental, fecha_contratacion, salario, turno | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2), VARCHAR(50) |
| **Cita_Dental** | id_cita, id_paciente, id_odontologo, fecha_cita, hora_cita, motivo_cita, estado_cita, comentarios, tipo_tratamiento | INT, INT, INT, DATE, TIME, TEXT, VARCHAR(50), TEXT, VARCHAR(100) |
| **Tratamiento_Dental** | id_tratamiento, nombre_tratamiento, descripcion, costo_promedio, duracion_estimada_minutos, es_invasivo, requiere_anestesia, materiales_comunes | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, BOOLEAN, BOOLEAN, TEXT |
| **Historial_Tratamiento** | id_historial, id_cita, id_paciente, id_odontologo, id_tratamiento, fecha_realizacion, notas_tratamiento, costo_final, piezas_dentales_afectadas | INT, INT, INT, INT, INT, DATETIME, TEXT, DECIMAL(10,2), TEXT |
| **Factura_Dental** | id_factura, id_paciente, fecha_emision, total_factura, estado_pago, metodo_pago, fecha_vencimiento, id_cita_asociada, descuento_aplicado | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE, INT, DECIMAL(5,2) |
| **Material_Odontologico** | id_material, nombre_material, descripcion, stock_actual, fecha_caducidad, id_proveedor, costo_unitario, tipo_material, ubicacion_almacen | INT, VARCHAR(255), TEXT, INT, DATE, INT, DECIMAL(10,2), VARCHAR(50), VARCHAR(100) |

**Relaciones:**
*   Cita_Dental (id_paciente) -> Paciente_Dental (id_paciente) (Muchos a Uno)
*   Cita_Dental (id_odontologo) -> Odontologo (id_odontologo) (Muchos a Uno)
*   Historial_Tratamiento (id_cita) -> Cita_Dental (id_cita) (Muchos a Uno)
*   Historial_Tratamiento (id_paciente) -> Paciente_Dental (id_paciente) (Muchos a Uno)
*   Historial_Tratamiento (id_odontologo) -> Odontologo (id_odontologo) (Muchos a Uno)
*   Historial_Tratamiento (id_tratamiento) -> Tratamiento_Dental (id_tratamiento) (Muchos a Uno)
*   Factura_Dental (id_paciente) -> Paciente_Dental (id_paciente) (Muchos a Uno)
*   Factura_Dental (id_cita_asociada) -> Cita_Dental (id_cita) (Muchos a Uno)

---

**Grupo 34: Sistema de Gestión de Tienda de Mascotas**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Animal_Tienda** | id_animal, nombre_animal, especie, raza, fecha_nacimiento, genero, precio_venta, estado_salud, fecha_ingreso, chip_identificacion, vacunas_aplicadas | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), DATE, CHAR(1), DECIMAL(10,2), VARCHAR(50), DATE, VARCHAR(50), TEXT |
| **Producto_Mascota** | id_producto, nombre_producto, descripcion, precio_venta, stock, id_categoria, id_proveedor, para_especie, tamano_animal, marca, fecha_vencimiento | INT, VARCHAR(255), TEXT, DECIMAL(10,2), INT, INT, INT, VARCHAR(50), VARCHAR(50), VARCHAR(100), DATE |
| **Categoria_Mascota** | id_categoria, nombre_categoria, descripcion_categoria, es_comida, es_juguete, aplica_para_especie | INT, VARCHAR(100), TEXT, BOOLEAN, BOOLEAN, VARCHAR(100) |
| **Cliente_Mascota** | id_cliente, nombre, apellido, telefono, email, direccion, fecha_registro, num_mascotas, tipo_mascota_preferido | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), DATE, INT, VARCHAR(50) |
| **Venta_Tienda_Mascota** | id_venta, fecha_venta, id_cliente, id_empleado, total_venta, metodo_pago, descuento_aplicado, numero_ticket, estado_venta | INT, DATETIME, INT, INT, DECIMAL(10,2), VARCHAR(50), DECIMAL(5,2), VARCHAR(50), VARCHAR(50) |
| **Detalle_Venta_Tienda_Mascota** | id_detalle, id_venta, id_producto, cantidad, precio_unitario_venta, subtotal, iva_aplicado, id_animal_vendido | INT, INT, INT, INT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(5,2), INT |
| **Empleado_Tienda_Mascota** | id_empleado, nombre, apellido, cargo, dni, fecha_contratacion, salario, turno, telefono, email | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(20), VARCHAR(100) |

**Relaciones:**
*   Producto_Mascota (id_categoria) -> Categoria_Mascota (id_categoria) (Muchos a Uno)
*   Venta_Tienda_Mascota (id_cliente) -> Cliente_Mascota (id_cliente) (Muchos a Uno)
*   Venta_Tienda_Mascota (id_empleado) -> Empleado_Tienda_Mascota (id_empleado) (Muchos a Uno)
*   Detalle_Venta_Tienda_Mascota (id_venta) -> Venta_Tienda_Mascota (id_venta) (Muchos a Uno)
*   Detalle_Venta_Tienda_Mascota (id_producto) -> Producto_Mascota (id_producto) (Muchos a Uno)
*   Detalle_Venta_Tienda_Mascota (id_animal_vendido) -> Animal_Tienda (id_animal) (Muchos a Uno)

---

**Grupo 35: Sistema de Gestión de Escuela de Baile**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Estudiante_Baile** | id_estudiante, nombre, apellido, fecha_nacimiento, genero, email, telefono, estilo_preferido, nivel_experiencia, fecha_inscripcion, direccion | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(100), VARCHAR(20), VARCHAR(50), VARCHAR(50), DATE, VARCHAR(255) |
| **Instructor_Baile** | id_instructor, nombre, apellido, email, telefono, estilo_especialidad, experiencia_anos, fecha_contratacion, salario_hora, disponibilidad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(50), INT, DATE, DECIMAL(5,2), TEXT |
| **Estilo_Baile** | id_estilo, nombre_estilo, descripcion, origen, popularidad, musica_asociada, es_pareja | INT, VARCHAR(50), TEXT, VARCHAR(50), INT, TEXT, BOOLEAN |
| **Clase_Baile** | id_clase, nombre_clase, id_instructor, id_estilo, nivel, duracion_minutos, horario, cupo_maximo, costo_clase, sala | INT, VARCHAR(100), INT, INT, VARCHAR(50), INT, VARCHAR(100), INT, DECIMAL(10,2), VARCHAR(50) |
| **Inscripcion_Clase_Baile** | id_inscripcion, id_estudiante, id_clase, fecha_inscripcion, estado_inscripcion, fecha_finalizacion, comentarios_instructor, pago_realizado | INT, INT, INT, DATE, VARCHAR(50), DATE, TEXT, BOOLEAN |
| **Evento_Baile** | id_evento, nombre_evento, descripcion, fecha_evento, hora_evento, lugar, costo_entrada, tipo_evento, organizador, invitados_especiales | INT, VARCHAR(255), TEXT, DATE, TIME, VARCHAR(255), DECIMAL(10,2), VARCHAR(50), VARCHAR(100), TEXT |
| **Participacion_Evento_Baile** | id_participacion, id_estudiante, id_evento, rol_participante, fecha_registro, calificacion_desempeno, comentarios_organizador | INT, INT, INT, VARCHAR(50), DATETIME, DECIMAL(4,2), TEXT |

**Relaciones:**
*   Clase_Baile (id_instructor) -> Instructor_Baile (id_instructor) (Muchos a Uno)
*   Clase_Baile (id_estilo) -> Estilo_Baile (id_estilo) (Muchos a Uno)
*   Inscripcion_Clase_Baile (id_estudiante) -> Estudiante_Baile (id_estudiante) (Muchos a Uno)
*   Inscripcion_Clase_Baile (id_clase) -> Clase_Baile (id_clase) (Muchos a Uno)
*   Participacion_Evento_Baile (id_estudiante) -> Estudiante_Baile (id_estudiante) (Muchos a Uno)
*   Participacion_Evento_Baile (id_evento) -> Evento_Baile (id_evento) (Muchos a Uno)

---

**Grupo 36: Sistema de Gestión de Consultorio Psicológico**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Paciente_Psicologia** | id_paciente, nombre, apellido, fecha_nacimiento, genero, direccion, telefono, email, profesion, fecha_registro, motivo_consulta_inicial | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(100), DATE, TEXT |
| **Psicologo** | id_psicologo, nombre, apellido, especialidad, email, telefono, fecha_contratacion, salario, licencia_colegiado, enfoque_terapeutico | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(100) |
| **Sesion** | id_sesion, id_paciente, id_psicologo, fecha_sesion, hora_sesion, tipo_sesion, duracion_minutos, notas_sesion, diagnostico_actual, costo_sesion | INT, INT, INT, DATETIME, TIME, VARCHAR(50), INT, TEXT, TEXT, DECIMAL(10,2) |
| **Diagnostico** | id_diagnostico, nombre_diagnostico, descripcion_corta, cie_10_codigo, dsm_5_codigo, tratamientos_sugeridos, es_cronico | INT, VARCHAR(255), TEXT, VARCHAR(20), VARCHAR(20), TEXT, BOOLEAN |
| **Factura_Psicologia** | id_factura, id_paciente, fecha_emision, total_factura, estado_pago, metodo_pago, fecha_vencimiento, id_sesion_asociada, descuento_aplicado | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE, INT, DECIMAL(5,2) |
| **Historial_Clinico_Psicologia** | id_historial, id_paciente, fecha_actualizacion, antecedentes_familiares, antecedentes_personales, medicamentos_actuales, resumen_evolucion, id_psicologo_tratante | INT, INT, DATETIME, TEXT, TEXT, TEXT, TEXT, INT |
| **Recurso_Psicologico** | id_recurso, nombre_recurso, tipo_recurso, descripcion, autor, fecha_publicacion, url_recurso, tema_principal, publico_objetivo | INT, VARCHAR(255), VARCHAR(50), TEXT, VARCHAR(100), DATE, VARCHAR(255), VARCHAR(100), VARCHAR(100) |

**Relaciones:**
*   Sesion (id_paciente) -> Paciente_Psicologia (id_paciente) (Muchos a Uno)
*   Sesion (id_psicologo) -> Psicologo (id_psicologo) (Muchos a Uno)
*   Factura_Psicologia (id_paciente) -> Paciente_Psicologia (id_paciente) (Muchos a Uno)
*   Factura_Psicologia (id_sesion_asociada) -> Sesion (id_sesion) (Muchos a Uno)
*   Historial_Clinico_Psicologia (id_paciente) -> Paciente_Psicologia (id_paciente) (Muchos a Uno)
*   Historial_Clinico_Psicologia (id_psicologo_tratante) -> Psicologo (id_psicologo) (Muchos a Uno)

---

**Grupo 37: Sistema de Gestión de Concesionaria de Autos**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Auto** | id_auto, marca, modelo, anio, color, tipo_combustible, kilometraje, precio_venta, estado_auto, num_vin, fecha_ingreso_concesionaria, tipo_transmision | INT, VARCHAR(50), VARCHAR(50), INT, VARCHAR(20), VARCHAR(50), INT, DECIMAL(15,2), VARCHAR(50), VARCHAR(50), DATE, VARCHAR(50) |
| **Cliente_Concesionaria** | id_cliente, nombre, apellido, telefono, email, direccion, dni, fecha_registro, presupuesto_maximo, preferencias_auto | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), DATE, DECIMAL(15,2), TEXT |
| **Vendedor** | id_vendedor, nombre, apellido, email, telefono, fecha_contratacion, salario_base, comision_porcentaje, dni, num_ventas_mes | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), DECIMAL(5,2), VARCHAR(20), INT |
| **Venta_Auto** | id_venta, id_auto, id_cliente, id_vendedor, fecha_venta, precio_final_venta, metodo_pago, tiene_financiamiento, fecha_entrega_auto, garantia_meses | INT, INT, INT, INT, DATETIME, DECIMAL(15,2), VARCHAR(50), BOOLEAN, DATE, INT |
| **Servicio_Postventa** | id_servicio, nombre_servicio, descripcion, costo_estandar, duracion_horas, requiere_cita, tipo_mantenimiento, id_taller_asociado | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, BOOLEAN, VARCHAR(100), INT |
| **Cita_Servicio** | id_cita_servicio, id_cliente, id_auto, id_servicio, fecha_cita, hora_cita, estado_cita, comentarios_cliente, fecha_finalizacion_servicio | INT, INT, INT, INT, DATE, TIME, VARCHAR(50), TEXT, DATETIME |
| **Taller_Asociado** | id_taller, nombre_taller, direccion, telefono, email, persona_contacto, especialidades, horario_atencion | INT, VARCHAR(255), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(100), TEXT, TEXT |

**Relaciones:**
*   Venta_Auto (id_auto) -> Auto (id_auto) (Muchos a Uno)
*   Venta_Auto (id_cliente) -> Cliente_Concesionaria (id_cliente) (Muchos a Uno)
*   Venta_Auto (id_vendedor) -> Vendedor (id_vendedor) (Muchos a Uno)
*   Cita_Servicio (id_cliente) -> Cliente_Concesionaria (id_cliente) (Muchos a Uno)
*   Cita_Servicio (id_auto) -> Auto (id_auto) (Muchos a Uno)
*   Cita_Servicio (id_servicio) -> Servicio_Postventa (id_servicio) (Muchos a Uno)
*   Servicio_Postventa (id_taller_asociado) -> Taller_Asociado (id_taller) (Muchos a Uno)

---

**Grupo 38: Sistema de Gestión de Centro Deportivo Amateur**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Deportista** | id_deportista, nombre, apellido, fecha_nacimiento, genero, email, telefono, deporte_principal, nivel_habilidad, fecha_registro, lesiones_previas | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(100), VARCHAR(20), VARCHAR(50), VARCHAR(50), DATE, TEXT |
| **Deporte** | id_deporte, nombre_deporte, descripcion, num_jugadores_equipo, es_individual, reglas_basicas, tipo_superficie | INT, VARCHAR(50), TEXT, INT, BOOLEAN, TEXT, VARCHAR(50) |
| **Equipo** | id_equipo, nombre_equipo, id_deporte, fecha_fundacion, entrenador, capitan, num_jugadores_actual, categoria_edad, colores_equipo | INT, VARCHAR(100), INT, DATE, VARCHAR(100), VARCHAR(100), INT, VARCHAR(50), VARCHAR(50) |
| **Partido** | id_partido, id_deporte, fecha_partido, hora_partido, lugar_partido, id_equipo_local, id_equipo_visitante, resultado_local, resultado_visitante, arbitro | INT, INT, DATE, TIME, VARCHAR(100), INT, INT, INT, INT, VARCHAR(100) |
| **Inscripcion_Equipo** | id_inscripcion, id_deportista, id_equipo, fecha_inscripcion, rol_en_equipo, num_camiseta, es_titular, fecha_baja_equipo | INT, INT, INT, DATE, VARCHAR(50), INT, BOOLEAN, DATE |
| **Instalacion_Deportiva** | id_instalacion, nombre_instalacion, tipo_instalacion, ubicacion, capacidad_personas, costo_alquiler_hora, es_techada, horario_disponible, descripcion_equipamiento | INT, VARCHAR(255), VARCHAR(100), VARCHAR(255), INT, DECIMAL(10,2), BOOLEAN, TEXT, TEXT |
| **Reserva_Instalacion** | id_reserva, id_deportista_reserva, id_instalacion, fecha_reserva, hora_inicio, hora_fin, duracion_horas, motivo_reserva, monto_pagado, estado_reserva | INT, INT, INT, DATE, TIME, TIME, DECIMAL(5,2), TEXT, DECIMAL(10,2), VARCHAR(50) |

**Relaciones:**
*   Equipo (id_deporte) -> Deporte (id_deporte) (Muchos a Uno)
*   Partido (id_deporte) -> Deporte (id_deporte) (Muchos a Uno)
*   Partido (id_equipo_local) -> Equipo (id_equipo) (Muchos a Uno)
*   Partido (id_equipo_visitante) -> Equipo (id_equipo) (Muchos a Uno)
*   Inscripcion_Equipo (id_deportista) -> Deportista (id_deportista) (Muchos a Uno)
*   Inscripcion_Equipo (id_equipo) -> Equipo (id_equipo) (Muchos a Uno)
*   Reserva_Instalacion (id_deportista_reserva) -> Deportista (id_deportista) (Muchos a Uno)
*   Reserva_Instalacion (id_instalacion) -> Instalacion_Deportiva (id_instalacion) (Muchos a Uno)

---

**Grupo 39: Sistema de Gestión de Editorial (Libros)**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Libro_Editorial** | id_libro, titulo, id_autor_principal, isbn, fecha_publicacion, num_paginas, id_genero, precio_tapa, stock_almacen, id_editor, estado_publicacion, formato | INT, VARCHAR(255), INT, VARCHAR(13), DATE, INT, INT, DECIMAL(10,2), INT, INT, VARCHAR(50), VARCHAR(50) |
| **Autor_Editorial** | id_autor, nombre, apellido, nacionalidad, fecha_nacimiento, biografia, email, sitio_web, fecha_fallecimiento | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, TEXT, VARCHAR(100), VARCHAR(255), DATE |
| **Genero_Literario** | id_genero, nombre_genero, descripcion, es_ficcion, epoca_popular, publico_objetivo | INT, VARCHAR(50), TEXT, BOOLEAN, VARCHAR(50), VARCHAR(100) |
| **Editor** | id_editor, nombre, apellido, email, telefono, fecha_contratacion, salario, especialidad_genero, departamento, dni | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(10,2), VARCHAR(100), VARCHAR(50), VARCHAR(20) |
| **Contrato_Autor** | id_contrato, id_libro, id_autor_principal, fecha_firma, porcentaje_regalias, monto_adelanto, fecha_fin_contrato, clausulas_especiales, id_agente_literario | INT, INT, INT, DATE, DECIMAL(5,2), DECIMAL(10,2), DATE, TEXT, INT |
| **Distribuidor** | id_distribuidor, nombre_distribuidor, contacto_principal, telefono, email, direccion_almacen, pais_distribucion, tipo_distribucion | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(50), VARCHAR(50) |
| **Envio_Libros** | id_envio, id_libro, id_distribuidor, fecha_envio, cantidad_enviada, costo_envio, estado_envio, fecha_recepcion_esperada, numero_seguimiento | INT, INT, INT, DATETIME, INT, DECIMAL(10,2), VARCHAR(50), DATE, VARCHAR(50) |

**Relaciones:**
*   Libro_Editorial (id_autor_principal) -> Autor_Editorial (id_autor) (Muchos a Uno)
*   Libro_Editorial (id_genero) -> Genero_Literario (id_genero) (Muchos a Uno)
*   Libro_Editorial (id_editor) -> Editor (id_editor) (Muchos a Uno)
*   Contrato_Autor (id_libro) -> Libro_Editorial (id_libro) (Muchos a Uno)
*   Contrato_Autor (id_autor_principal) -> Autor_Editorial (id_autor) (Muchos a Uno)
*   Envio_Libros (id_libro) -> Libro_Editorial (id_libro) (Muchos a Uno)
*   Envio_Libros (id_distribuidor) -> Distribuidor (id_distribuidor) (Muchos a Uno)

---

**Grupo 40: Sistema de Gestión de Empresas de Limpieza**

| Entidad | Atributos | Tipo de Campo |
|---|---|---|
| **Cliente_Limpieza** | id_cliente, nombre_empresa, contacto_principal, email_contacto, telefono_contacto, direccion_servicio, tipo_negocio, fecha_inicio_contrato, estado_contrato, frecuencia_servicio | INT, VARCHAR(255), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(255), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(50) |
| **Servicio_Limpieza** | id_servicio, nombre_servicio, descripcion, costo_estandar, duracion_estimada_horas, productos_usados, requiere_equipo_especial, categoria_servicio | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, TEXT, BOOLEAN, VARCHAR(50) |
| **Empleado_Limpieza** | id_empleado, nombre, apellido, dni, fecha_contratacion, salario_hora, turno, telefono, email, certificaciones_seguridad | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(5,2), VARCHAR(50), VARCHAR(20), VARCHAR(100), TEXT |
| **Programacion_Servicio** | id_programacion, id_cliente, id_servicio, fecha_programada, hora_inicio, hora_fin, estado_servicio, observaciones_cliente, id_empleado_asignado | INT, INT, INT, DATETIME, TIME, TIME, VARCHAR(50), TEXT, INT |
| **Factura_Limpieza** | id_factura, id_cliente, fecha_emision, monto_total, estado_pago, metodo_pago, fecha_vencimiento, id_programacion_asociada, impuestos_aplicados | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), DATE, INT, DECIMAL(5,2) |
| **Material_Limpieza** | id_material, nombre_material, descripcion, stock_actual, fecha_caducidad, id_proveedor, costo_unitario, tipo_material, ubicacion_almacen | INT, VARCHAR(255), TEXT, INT, DATE, INT, DECIMAL(10,2), VARCHAR(50), VARCHAR(100) |
| **Uso_Material** | id_uso, id_programacion, id_material, cantidad_usada, fecha_registro, id_empleado_registro, comentarios_uso | INT, INT, INT, DECIMAL(8,2), DATETIME, INT, TEXT |

**Relaciones:**
*   Programacion_Servicio (id_cliente) -> Cliente_Limpieza (id_cliente) (Muchos a Uno)
*   Programacion_Servicio (id_servicio) -> Servicio_Limpieza (id_servicio) (Muchos a Uno)
*   Programacion_Servicio (id_empleado_asignado) -> Empleado_Limpieza (id_empleado) (Muchos a Uno)
*   Factura_Limpieza (id_cliente) -> Cliente_Limpieza (id_cliente) (Muchos a Uno)
*   Factura_Limpieza (id_programacion_asociada) -> Programacion_Servicio (id_programacion) (Muchos a Uno)
*   Uso_Material (id_programacion) -> Programacion_Servicio (id_programacion) (Muchos a Uno)
*   Uso_Material (id_material) -> Material_Limpieza (id_material) (Muchos a Uno)
*   Uso_Material (id_empleado_registro) -> Empleado_Limpieza (id_empleado) (Muchos a Uno)

---

