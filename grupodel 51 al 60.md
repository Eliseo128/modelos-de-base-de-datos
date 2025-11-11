# 10 Grupos de Sistemas de Gestión Especializados

## Grupo 1: Sistema de Gestión de Clínica Veterinaria

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Mascota | id_mascota, nombre_mascota, especie, raza, fecha_nacimiento, peso_actual, color, id_propietario, fecha_registro, historial_vacunas | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), DATE, DECIMAL(5,2), VARCHAR(50), INT, DATE, TEXT |
| Propietario | id_propietario, nombre, apellido, direccion, telefono, email, dni, emergencia_contacto, fecha_registro, notas_adicionales | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(15), VARCHAR(100), DATE, TEXT |
| Veterinario | id_veterinario, nombre, apellido, especialidad, telefono, email, licencia_veterinaria, fecha_contratacion, horario_trabajo, salario | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, VARCHAR(100), DECIMAL(10,2) |
| Cita_Veterinaria | id_cita, id_mascota, id_veterinario, fecha_cita, hora_cita, motivo_consulta, sintomas, estado_cita, temperatura, frecuencia_cardiaca | INT, INT, INT, DATE, TIME, TEXT, TEXT, VARCHAR(50), DECIMAL(4,2), INT |
| Tratamiento | id_tratamiento, nombre_tratamiento, descripcion, costo_estimado, duracion_dias, frecuencia_aplicacion, tipo_medicamento, dosis_recomendada | INT, VARCHAR(100), TEXT, DECIMAL(10,2), INT, VARCHAR(50), VARCHAR(50), VARCHAR(100) |
| Historial_Medico | id_historial, id_mascota, id_veterinario, id_tratamiento, fecha_consulta, diagnostico, prescripciones, proxima_cita, costo_consulta | INT, INT, INT, INT, DATETIME, TEXT, TEXT, DATE, DECIMAL(10,2) |
| Vacuna | id_vacuna, nombre_vacuna, descripcion, especie_aplicable, edad_minima_meses, frecuencia_refuerzo, costo, proveedor, fecha_caducidad | INT, VARCHAR(100), TEXT, VARCHAR(50), INT, VARCHAR(50), DECIMAL(8,2), VARCHAR(100), DATE |

**Relaciones:**
- Cita_Veterinaria (id_mascota) → Mascota (id_mascota) (Muchos a Uno)
- Cita_Veterinaria (id_veterinario) → Veterinario (id_veterinario) (Muchos a Uno)
- Historial_Medico (id_mascota) → Mascota (id_mascota) (Muchos a Uno)
- Historial_Medico (id_veterinario) → Veterinario (id_veterinario) (Muchos a Uno)
- Historial_Medico (id_tratamiento) → Tratamiento (id_tratamiento) (Muchos a Uno)
- Mascota (id_propietario) → Propietario (id_propietario) (Muchos a Uno)

## Grupo 2: Sistema de Gestión de Academia de Música

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Estudiante_Musica | id_estudiante, nombre, apellido, fecha_nacimiento, instrumento_principal, nivel_actual, telefono, email, fecha_inscripcion, nombre_tutor | INT, VARCHAR(100), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(50), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(100) |
| Profesor_Musica | id_profesor, nombre, apellido, instrumento_especialidad, anos_experiencia, telefono, email, titulo_academico, fecha_contratacion, salario_hora | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), INT, VARCHAR(20), VARCHAR(100), VARCHAR(100), DATE, DECIMAL(8,2) |
| Clase_Musica | id_clase, id_estudiante, id_profesor, instrumento, nivel_clase, fecha_clase, hora_inicio, duracion_minutos, salon, concepto_ensenanza | INT, INT, INT, VARCHAR(50), VARCHAR(50), DATE, TIME, INT, VARCHAR(50), TEXT |
| Instrumento | id_instrumento, nombre_instrumento, tipo_instrumento, marca, modelo, numero_serie, estado_conservacion, fecha_adquisicion, costo_adquisicion | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), VARCHAR(50), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2) |
| Evaluacion_Musical | id_evaluacion, id_estudiante, id_profesor, fecha_evaluacion, instrumento, nivel_evaluado, puntuacion_tecnica, puntuacion_interpretacion, comentarios, recomendaciones | INT, INT, INT, DATE, VARCHAR(50), VARCHAR(50), DECIMAL(5,2), DECIMAL(5,2), TEXT, TEXT |
| Pago_Mensualidad | id_pago, id_estudiante, mes_pago, ano_pago, monto_pago, fecha_vencimiento, fecha_pago, metodo_pago, estado_pago, clases_include | INT, INT, VARCHAR(20), INT, DECIMAL(10,2), DATE, DATE, VARCHAR(50), VARCHAR(50), INT |
| Evento_Musical | id_evento, nombre_evento, tipo_evento, fecha_evento, hora_evento, lugar, descripcion, costo_entrada, capacidad_maxima, estado_evento | INT, VARCHAR(255), VARCHAR(50), DATE, TIME, VARCHAR(255), TEXT, DECIMAL(8,2), INT, VARCHAR(50) |

**Relaciones:**
- Clase_Musica (id_estudiante) → Estudiante_Musica (id_estudiante) (Muchos a Uno)
- Clase_Musica (id_profesor) → Profesor_Musica (id_profesor) (Muchos a Uno)
- Evaluacion_Musical (id_estudiante) → Estudiante_Musica (id_estudiante) (Muchos a Uno)
- Evaluacion_Musical (id_profesor) → Profesor_Musica (id_profesor) (Muchos a Uno)
- Pago_Mensualidad (id_estudiante) → Estudiante_Musica (id_estudiante) (Muchos a Uno)

## Grupo 3: Sistema de Gestión de Taller Automotriz

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Vehiculo | id_vehiculo, placa, marca, modelo, ano_fabricacion, color, numero_chasis, id_cliente, kilometraje_actual, tipo_combustible | INT, VARCHAR(20), VARCHAR(50), VARCHAR(50), INT, VARCHAR(30), VARCHAR(100), INT, INT, VARCHAR(30) |
| Cliente_Taller | id_cliente, nombre, apellido, direccion, telefono, email, dni, fecha_registro, preferencias_contacto, historial_vehiculos | INT, VARCHAR(100), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(100), VARCHAR(15), DATE, VARCHAR(50), TEXT |
| Mecanico | id_mecanico, nombre, apellido, especialidad, telefono, email, licencia_mecanico, fecha_contratacion, salario_hora, turno_trabajo | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(8,2), VARCHAR(50) |
| Orden_Servicio | id_orden, id_vehiculo, id_mecanico, fecha_ingreso, hora_ingreso, problema_reportado, diagnostico_inicial, estado_orden, prioridad, kilometraje_ingreso | INT, INT, INT, DATE, TIME, TEXT, TEXT, VARCHAR(50), VARCHAR(50), INT |
| Servicio_Taller | id_servicio, nombre_servicio, descripcion, tiempo_estimado_horas, costo_mano_obra, tipo_servicio, garantia_meses, requerimientos_especiales | INT, VARCHAR(100), TEXT, DECIMAL(4,2), DECIMAL(10,2), VARCHAR(50), INT, TEXT |
| Repuesto | id_repuesto, nombre_repuesto, descripcion, marca_compatible, modelo_compatible, stock_actual, precio_compra, precio_venta, proveedor, numero_parte | INT, VARCHAR(255), TEXT, VARCHAR(50), VARCHAR(50), INT, DECIMAL(10,2), DECIMAL(10,2), VARCHAR(100), VARCHAR(100) |
| Factura_Taller | id_factura, id_orden, fecha_emision, subtotal_repuestos, subtotal_mano_obra, iva, total_factura, estado_pago, metodo_pago, observaciones_finales | INT, INT, DATE, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), VARCHAR(50), VARCHAR(50), TEXT |

**Relaciones:**
- Vehiculo (id_cliente) → Cliente_Taller (id_cliente) (Muchos a Uno)
- Orden_Servicio (id_vehiculo) → Vehiculo (id_vehiculo) (Muchos a Uno)
- Orden_Servicio (id_mecanico) → Mecanico (id_mecanico) (Muchos a Uno)
- Factura_Taller (id_orden) → Orden_Servicio (id_orden) (Muchos a Uno)

## Grupo 4: Sistema de Gestión de Gimnasio y Fitness

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Miembro_Gimnasio | id_miembro, nombre, apellido, fecha_nacimiento, genero, telefono, email, fecha_inscripcion, tipo_membresia, estado_membresia | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(50) |
| Entrenador | id_entrenador, nombre, apellido, especialidad, certificaciones, telefono, email, fecha_contratacion, salario_hora, horario_disponible | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), TEXT, VARCHAR(20), VARCHAR(100), DATE, DECIMAL(8,2), VARCHAR(100) |
| Clase_Grupo | id_clase, nombre_clase, tipo_ejercicio, id_entrenador, hora_inicio, duracion_minutos, salon, capacidad_maxima, nivel_dificultad, descripcion | INT, VARCHAR(100), VARCHAR(50), INT, TIME, INT, VARCHAR(50), INT, VARCHAR(50), TEXT |
| Membresia | id_membresia, tipo_membresia, duracion_meses, costo_mensual, beneficios, acceso_salon, acceso_clases, acceso_piscina, estado_disponible | INT, VARCHAR(50), INT, DECIMAL(10,2), TEXT, BOOLEAN, BOOLEAN, BOOLEAN, BOOLEAN |
| Asistencia | id_asistencia, id_miembro, fecha_entrada, hora_entrada, hora_salida, tipo_actividad, calorias_quemadas_estimadas, entrenador_asignado | INT, INT, DATE, TIME, TIME, VARCHAR(100), INT, INT |
| Pago_Membresia | id_pago, id_miembro, fecha_pago, monto_pago, periodo_cubierto, metodo_pago, referencia_pago, estado_pago, proximo_vencimiento | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), VARCHAR(100), VARCHAR(50), DATE |
| Equipo_Gimnasio | id_equipo, nombre_equipo, tipo_equipo, marca, modelo, fecha_adquisicion, estado_conservacion, ultimo_mantenimiento, proximo_mantenimiento | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), VARCHAR(50), DATE, VARCHAR(50), DATE, DATE |

**Relaciones:**
- Miembro_Gimnasio (tipo_membresia) → Membresia (tipo_membresia) (Muchos a Uno)
- Clase_Grupo (id_entrenador) → Entrenador (id_entrenador) (Muchos a Uno)
- Asistencia (id_miembro) → Miembro_Gimnasio (id_miembro) (Muchos a Uno)
- Asistencia (entrenador_asignado) → Entrenador (id_entrenador) (Muchos a Uno)
- Pago_Membresia (id_miembro) → Miembro_Gimnasio (id_miembro) (Muchos a Uno)

## Grupo 5: Sistema de Gestión de Agencia de Viajes

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Cliente_Viajes | id_cliente, nombre, apellido, pasaporte, fecha_nacimiento, nacionalidad, telefono, email, preferencias_viaje, restricciones_medicas | INT, VARCHAR(100), VARCHAR(100), VARCHAR(50), DATE, VARCHAR(50), VARCHAR(20), VARCHAR(100), TEXT, TEXT |
| Agente_Viajes | id_agente, nombre, apellido, telefono, email, fecha_contratacion, especialidad_destinos, idiomas, salario, nivel_experiencia | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, VARCHAR(100), VARCHAR(100), DECIMAL(10,2), VARCHAR(50) |
| Paquete_Turistico | id_paquete, nombre_paquete, destino_principal, duracion_dias, temporada, precio_base, descripcion, incluye_vuelo, incluye_hotel, incluye_tours | INT, VARCHAR(255), VARCHAR(100), INT, VARCHAR(50), DECIMAL(10,2), TEXT, BOOLEAN, BOOLEAN, BOOLEAN |
| Reserva_Viaje | id_reserva, id_cliente, id_agente, id_paquete, fecha_reserva, fecha_salida, fecha_regreso, numero_viajeros, estado_reserva, total_pago | INT, INT, INT, INT, DATE, DATE, DATE, INT, VARCHAR(50), DECIMAL(10,2) |
| Hotel | id_hotel, nombre_hotel, destino, categoria_estrellas, direccion, telefono, email, servicios_include, habitaciones_disponibles, precio_noche | INT, VARCHAR(255), VARCHAR(100), INT, VARCHAR(255), VARCHAR(20), VARCHAR(100), TEXT, INT, DECIMAL(8,2) |
| Vuelo | id_vuelo, aerolinea, numero_vuelo, ciudad_origen, ciudad_destino, fecha_salida, hora_salida, fecha_llegada, hora_llegada, clase_vuelo | INT, VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(100), DATE, TIME, DATE, TIME, VARCHAR(50) |
| Pago_Viaje | id_pago, id_reserva, fecha_pago, monto_pago, metodo_pago, estado_pago, referencia_transaccion, cuotas_pago, fecha_proximo_pago | INT, INT, DATE, DECIMAL(10,2), VARCHAR(50), VARCHAR(50), VARCHAR(100), INT, DATE |

**Relaciones:**
- Reserva_Viaje (id_cliente) → Cliente_Viajes (id_cliente) (Muchos a Uno)
- Reserva_Viaje (id_agente) → Agente_Viajes (id_agente) (Muchos a Uno)
- Reserva_Viaje (id_paquete) → Paquete_Turistico (id_paquete) (Muchos a Uno)
- Pago_Viaje (id_reserva) → Reserva_Viaje (id_reserva) (Muchos a Uno)

## Grupo 6: Sistema de Gestión de Consultorio Psicológico

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Paciente_Psicologia | id_paciente, nombre, apellido, fecha_nacimiento, genero, ocupacion, telefono, email, motivo_consulta, historial_psicologico | INT, VARCHAR(100), VARCHAR(100), DATE, CHAR(1), VARCHAR(100), VARCHAR(20), VARCHAR(100), TEXT, TEXT |
| Psicologo | id_psicologo, nombre, apellido, especialidad, telefono, email, licencia_profesional, fecha_contratacion, enfoque_terapeutico, salario_hora | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, VARCHAR(100), DECIMAL(8,2) |
| Sesion_Terapia | id_sesion, id_paciente, id_psicologo, fecha_sesion, hora_inicio, duracion_minutos, tipo_sesion, objetivos_sesion, notas_terapeuta, tareas_asignadas | INT, INT, INT, DATE, TIME, INT, VARCHAR(50), TEXT, TEXT, TEXT |
| Diagnostico | id_diagnostico, id_paciente, id_psicologo, fecha_diagnostico, codigo_cie10, descripcion_diagnostico, severidad, plan_tratamiento, pronostico | INT, INT, INT, DATE, VARCHAR(20), TEXT, VARCHAR(50), TEXT, VARCHAR(100) |
| Terapia | id_terapia, nombre_terapia, descripcion, duracion_estimada_sesiones, enfoque_terapeutico, indicaciones, contraindicaciones, efectividad_porcentaje | INT, VARCHAR(100), TEXT, INT, VARCHAR(100), TEXT, TEXT, DECIMAL(5,2) |
| Evaluacion_Psicologica | id_evaluacion, id_paciente, id_psicologo, fecha_evaluacion, tipo_prueba, resultados_cuantitativos, interpretacion, recomendaciones, fecha_proxima_evaluacion | INT, INT, INT, DATE, VARCHAR(100), TEXT, TEXT, TEXT, DATE |
| Factura_Psicologia | id_factura, id_paciente, fecha_emision, concepto_servicios, subtotal_sesiones, iva, total_factura, estado_pago, metodo_pago, sesiones_cubiertas | INT, INT, DATE, TEXT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), VARCHAR(50), VARCHAR(50), INT |

**Relaciones:**
- Sesion_Terapia (id_paciente) → Paciente_Psicologia (id_paciente) (Muchos a Uno)
- Sesion_Terapia (id_psicologo) → Psicologo (id_psicologo) (Muchos a Uno)
- Diagnostico (id_paciente) → Paciente_Psicologia (id_paciente) (Muchos a Uno)
- Diagnostico (id_psicologo) → Psicologo (id_psicologo) (Muchos a Uno)
- Evaluacion_Psicologica (id_paciente) → Paciente_Psicologia (id_paciente) (Muchos a Uno)
- Evaluacion_Psicologica (id_psicologo) → Psicologo (id_psicologo) (Muchos a Uno)
- Factura_Psicologia (id_paciente) → Paciente_Psicologia (id_paciente) (Muchos a Uno)

## Grupo 7: Sistema de Gestión de Estudio Fotográfico

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Cliente_Foto | id_cliente, nombre, apellido, telefono, email, direccion, tipo_cliente, fecha_registro, preferencias_estilo, eventos_anteriores | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(50), DATE, TEXT, TEXT |
| Fotografo | id_fotografo, nombre, apellido, especialidad, telefono, email, equipo_camara, anos_experiencia, fecha_contratacion, tarifa_hora | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), TEXT, INT, DATE, DECIMAL(8,2) |
| Sesion_Foto | id_sesion, id_cliente, id_fotografo, tipo_sesion, fecha_sesion, hora_inicio, duracion_horas, ubicacion, concepto_artistico, estado_sesion | INT, INT, INT, VARCHAR(50), DATE, TIME, DECIMAL(4,2), VARCHAR(255), TEXT, VARCHAR(50) |
| Album_Fotos | id_album, id_sesion, nombre_album, cantidad_fotos, formato_entrega, fecha_entrega, estado_album, precio_album, notas_edicion | INT, INT, VARCHAR(255), INT, VARCHAR(50), DATE, VARCHAR(50), DECIMAL(10,2), TEXT |
| Equipo_Fotografia | id_equipo, tipo_equipo, marca, modelo, numero_serie, fecha_adquisicion, estado_funcionamiento, valor_actual, fecha_ultimo_mantenimiento | INT, VARCHAR(100), VARCHAR(50), VARCHAR(50), VARCHAR(100), DATE, VARCHAR(50), DECIMAL(10,2), DATE |
| Paquete_Servicios | id_paquete, nombre_paquete, descripcion, horas_cobertura, cantidad_fotos, tipo_edicion, precio_paquete, servicios_include, estado_disponible | INT, VARCHAR(100), TEXT, DECIMAL(4,2), INT, VARCHAR(50), DECIMAL(10,2), TEXT, BOOLEAN |
| Factura_Fotografia | id_factura, id_cliente, id_sesion, fecha_emision, concepto_servicios, subtotal_paquete, extras_adicionales, descuento, total_factura, estado_pago | INT, INT, INT, DATE, TEXT, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), VARCHAR(50) |

**Relaciones:**
- Sesion_Foto (id_cliente) → Cliente_Foto (id_cliente) (Muchos a Uno)
- Sesion_Foto (id_fotografo) → Fotografo (id_fotografo) (Muchos a Uno)
- Album_Fotos (id_sesion) → Sesion_Foto (id_sesion) (Muchos a Uno)
- Factura_Fotografia (id_cliente) → Cliente_Foto (id_cliente) (Muchos a Uno)
- Factura_Fotografia (id_sesion) → Sesion_Foto (id_sesion) (Muchos a Uno)

## Grupo 8: Sistema de Gestión de Escuela de Idiomas

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Estudiante_Idiomas | id_estudiante, nombre, apellido, fecha_nacimiento, nacionalidad, telefono, email, idioma_nativo, fecha_inscripcion, nivel_inicial | INT, VARCHAR(100), VARCHAR(100), DATE, VARCHAR(50), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, VARCHAR(50) |
| Profesor_Idiomas | id_profesor, nombre, apellido, idiomas_ensenar, anos_experiencia, telefono, email, titulos_certificaciones, fecha_contratacion, salario_hora | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), INT, VARCHAR(20), VARCHAR(100), TEXT, DATE, DECIMAL(8,2) |
| Curso_Idioma | id_curso, idioma, nivel_curso, descripcion, duracion_semanas, horas_semana, precio_curso, materiales_include, nivel_minimo_requerido | INT, VARCHAR(50), VARCHAR(50), TEXT, INT, INT, DECIMAL(10,2), TEXT, VARCHAR(50) |
| Matricula | id_matricula, id_estudiante, id_curso, fecha_matricula, horario_clases, salon_asignado, estado_matricula, fecha_inicio, fecha_fin | INT, INT, INT, DATE, VARCHAR(100), VARCHAR(50), VARCHAR(50), DATE, DATE |
| Evaluacion_Idioma | id_evaluacion, id_estudiante, id_curso, fecha_evaluacion, tipo_evaluacion, puntaje_gramatica, puntaje_comprension, puntaje_oral, nivel_alcanzado | INT, INT, INT, DATE, VARCHAR(50), DECIMAL(5,2), DECIMAL(5,2), DECIMAL(5,2), VARCHAR(50) |
| Material_Didactico | id_material, nombre_material, tipo_material, idioma_destinado, nivel_aplicable, descripcion, stock_disponible, fecha_adquisicion, costo_unitario | INT, VARCHAR(255), VARCHAR(50), VARCHAR(50), VARCHAR(50), TEXT, INT, DATE, DECIMAL(8,2) |
| Pago_Matricula | id_pago, id_estudiante, id_matricula, fecha_pago, monto_pago, concepto_pago, metodo_pago, estado_pago, referencia_transaccion | INT, INT, INT, DATE, DECIMAL(10,2), VARCHAR(100), VARCHAR(50), VARCHAR(50), VARCHAR(100) |

**Relaciones:**
- Matricula (id_estudiante) → Estudiante_Idiomas (id_estudiante) (Muchos a Uno)
- Matricula (id_curso) → Curso_Idioma (id_curso) (Muchos a Uno)
- Evaluacion_Idioma (id_estudiante) → Estudiante_Idiomas (id_estudiante) (Muchos a Uno)
- Evaluacion_Idioma (id_curso) → Curso_Idioma (id_curso) (Muchos a Uno)
- Pago_Matricula (id_estudiante) → Estudiante_Idiomas (id_estudiante) (Muchos a Uno)
- Pago_Matricula (id_matricula) → Matricula (id_matricula) (Muchos a Uno)

## Grupo 9: Sistema de Gestión de Spa y Bienestar

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Cliente_Spa | id_cliente, nombre, apellido, telefono, email, fecha_nacimiento, genero, alergias_conocidas, condiciones_medicas, preferencias_tratamiento | INT, VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), DATE, CHAR(1), TEXT, TEXT, TEXT |
| Terapeuta_Spa | id_terapeuta, nombre, apellido, especialidad, telefono, email, certificaciones, fecha_contratacion, horario_trabajo, salario_hora | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), TEXT, DATE, VARCHAR(100), DECIMAL(8,2) |
| Tratamiento_Spa | id_tratamiento, nombre_tratamiento, descripcion, duracion_minutos, categoria, precio_base, beneficios, contraindicaciones, productos_utilizados | INT, VARCHAR(100), TEXT, INT, VARCHAR(50), DECIMAL(10,2), TEXT, TEXT, TEXT |
| Reserva_Spa | id_reserva, id_cliente, id_terapeuta, fecha_reserva, hora_inicio, duracion_minutos, estado_reserva, notas_cliente, sala_asignada, tipo_pago | INT, INT, INT, DATE, TIME, INT, VARCHAR(50), TEXT, VARCHAR(50), VARCHAR(50) |
| Producto_Spa | id_producto, nombre_producto, marca, tipo_producto, descripcion, stock_actual, precio_compra, precio_venta, fecha_caducidad, proveedor | INT, VARCHAR(255), VARCHAR(100), VARCHAR(50), TEXT, INT, DECIMAL(8,2), DECIMAL(8,2), DATE, VARCHAR(100) |
| Membresia_Spa | id_membresia, tipo_membresia, duracion_meses, costo_mensual, tratamientos_include, descuento_productos, acceso_instalaciones, estado_disponible | INT, VARCHAR(50), INT, DECIMAL(10,2), TEXT, DECIMAL(5,2), BOOLEAN, BOOLEAN |
| Factura_Spa | id_factura, id_cliente, id_reserva, fecha_emision, subtotal_tratamientos, descuento_membresia, iva, total_factura, metodo_pago, estado_pago | INT, INT, INT, DATE, DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), DECIMAL(10,2), VARCHAR(50), VARCHAR(50) |

**Relaciones:**
- Reserva_Spa (id_cliente) → Cliente_Spa (id_cliente) (Muchos a Uno)
- Reserva_Spa (id_terapeuta) → Terapeuta_Spa (id_terapeuta) (Muchos a Uno)
- Factura_Spa (id_cliente) → Cliente_Spa (id_cliente) (Muchos a Uno)
- Factura_Spa (id_reserva) → Reserva_Spa (id_reserva) (Muchos a Uno)

## Grupo 10: Sistema de Gestión de Constructora

| Entidad | Atributos | Tipo de Campo |
|---------|-----------|---------------|
| Proyecto_Construccion | id_proyecto, nombre_proyecto, direccion, tipo_construccion, fecha_inicio, fecha_fin_estimada, presupuesto_total, estado_proyecto, descripcion, cliente_contratante | INT, VARCHAR(255), VARCHAR(255), VARCHAR(100), DATE, DATE, DECIMAL(12,2), VARCHAR(50), TEXT, VARCHAR(255) |
| Cliente_Constructora | id_cliente, nombre_empresa, representante_legal, telefono, email, direccion, ruc, tipo_cliente, fecha_registro, proyectos_anteriores | INT, VARCHAR(255), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(255), VARCHAR(20), VARCHAR(50), DATE, TEXT |
| Ingeniero | id_ingeniero, nombre, apellido, especialidad, telefono, email, colegiado, fecha_contratacion, salario_mensual, proyectos_asignados | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), VARCHAR(100), VARCHAR(50), DATE, DECIMAL(10,2), INT |
| Obrero | id_obrero, nombre, apellido, oficio, telefono, fecha_contratacion, salario_diario, turno_trabajo, especialidad, estado_contrato | INT, VARCHAR(100), VARCHAR(100), VARCHAR(100), VARCHAR(20), DATE, DECIMAL(8,2), VARCHAR(50), VARCHAR(100), VARCHAR(50) |
| Material_Construccion | id_material, nombre_material, tipo_material, unidad_medida, stock_actual, precio_unitario, proveedor, fecha_ultima_compra, calidad_estandar | INT, VARCHAR(255), VARCHAR(100), VARCHAR(50), INT, DECIMAL(10,2), VARCHAR(100), DATE, VARCHAR(50) |
| Avance_Proyecto | id_avance, id_proyecto, fecha_avance, porcentaje_completado, actividades_realizadas, problemas_encontrados, recursos_utilizados, observaciones_supervisor | INT, INT, DATE, DECIMAL(5,2), TEXT, TEXT, TEXT, TEXT |
| Factura_Constructora | id_factura, id_proyecto, id_cliente, fecha_emision, concepto_servicios, subtotal_materiales, subtotal_mano_obra, iva, total_factura, estado_pago | INT, INT, INT, DATE, TEXT, DECIMAL(12,2), DECIMAL(12,2), DECIMAL(12,2), DECIMAL(12,2), VARCHAR(50) |

**Relaciones:**
- Proyecto_Construccion (cliente_contratante) → Cliente_Constructora (id_cliente) (Muchos a Uno)
- Avance_Proyecto (id_proyecto) → Proyecto_Construccion (id_proyecto) (Muchos a Uno)
- Factura_Constructora (id_proyecto) → Proyecto_Construccion (id_proyecto) (Muchos a Uno)
- Factura_Constructora (id_cliente) → Cliente_Constructora (id_cliente) (Muchos a Uno)

Cada sistema mantiene relaciones de integridad referencial y sigue un diseño normalizado, con al menos 7 campos por entidad y relaciones claramente definidas entre las tablas.
