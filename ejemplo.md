from django.db import models


class Propietario(models.Model):
    id_propietario = models.AutoField(primary_key=True)
    nombre = models.CharField(max_length=100)
    apellido = models.CharField(max_length=100)
    direccion = models.CharField(max_length=255)
    telefono = models.CharField(max_length=20)
    email = models.CharField(max_length=100)
    dni = models.CharField(max_length=15)
    emergencia_contacto = models.CharField(max_length=100)
    fecha_registro = models.DateField()
    notas_adicionales = models.TextField(blank=True, null=True)

    def __str__(self):
        return f"{self.nombre} {self.apellido}"


class Mascota(models.Model):
    id_mascota = models.AutoField(primary_key=True)
    nombre_mascota = models.CharField(max_length=100)
    especie = models.CharField(max_length=50)
    raza = models.CharField(max_length=50)
    fecha_nacimiento = models.DateField()
    peso_actual = models.DecimalField(max_digits=5, decimal_places=2)
    color = models.CharField(max_length=50)
    id_propietario = models.ForeignKey(Propietario, on_delete=models.CASCADE, related_name='mascotas')
    fecha_registro = models.DateField()
    historial_vacunas = models.TextField(blank=True, null=True)

    def __str__(self):
        return self.nombre_mascota


class Veterinario(models.Model):
    id_veterinario = models.AutoField(primary_key=True)
    nombre = models.CharField(max_length=100)
    apellido = models.CharField(max_length=100)
    especialidad = models.CharField(max_length=100)
    telefono = models.CharField(max_length=20)
    email = models.CharField(max_length=100)
    licencia_veterinaria = models.CharField(max_length=50)
    fecha_contratacion = models.DateField()
    horario_trabajo = models.CharField(max_length=100)
    salario = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return f"{self.nombre} {self.apellido}"


class Tratamiento(models.Model):
    id_tratamiento = models.AutoField(primary_key=True)
    nombre_tratamiento = models.CharField(max_length=100)
    descripcion = models.TextField()
    costo_estimado = models.DecimalField(max_digits=10, decimal_places=2)
    duracion_dias = models.IntegerField()
    frecuencia_aplicacion = models.CharField(max_length=50)
    tipo_medicamento = models.CharField(max_length=50)
    dosis_recomendada = models.CharField(max_length=100)

    def __str__(self):
        return self.nombre_tratamiento


class Vacuna(models.Model):
    id_vacuna = models.AutoField(primary_key=True)
    nombre_vacuna = models.CharField(max_length=100)
    descripcion = models.TextField()
    especie_aplicable = models.CharField(max_length=50)
    edad_minima_meses = models.IntegerField()
    frecuencia_refuerzo = models.CharField(max_length=50)
    costo = models.DecimalField(max_digits=8, decimal_places=2)
    proveedor = models.CharField(max_length=100)
    fecha_caducidad = models.DateField()

    def __str__(self):
        return self.nombre_vacuna


class CitaVeterinaria(models.Model):
    id_cita = models.AutoField(primary_key=True)
    id_mascota = models.ForeignKey(Mascota, on_delete=models.CASCADE, related_name='citas')
    id_veterinario = models.ForeignKey(Veterinario, on_delete=models.CASCADE, related_name='citas')
    fecha_cita = models.DateField()
    hora_cita = models.TimeField()
    motivo_consulta = models.TextField()
    sintomas = models.TextField(blank=True, null=True)
    estado_cita = models.CharField(max_length=50)
    temperatura = models.DecimalField(max_digits=4, decimal_places=2, blank=True, null=True)
    frecuencia_cardiaca = models.IntegerField(blank=True, null=True)

    def __str__(self):
        return f"Cita #{self.id_cita} - {self.id_mascota.nombre_mascota}"


class HistorialMedico(models.Model):
    id_historial = models.AutoField(primary_key=True)
    id_mascota = models.ForeignKey(Mascota, on_delete=models.CASCADE, related_name='historiales')
    id_veterinario = models.ForeignKey(Veterinario, on_delete=models.CASCADE, related_name='historiales')
    id_tratamiento = models.ForeignKey(Tratamiento, on_delete=models.SET_NULL, null=True, related_name='historiales')
    fecha_consulta = models.DateTimeField()
    diagnostico = models.TextField()
    prescripciones = models.TextField(blank=True, null=True)
    proxima_cita = models.DateField(blank=True, null=True)
    costo_consulta = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return f"Historial #{self.id_historial} - {self.id_mascota.nombre_mascota}"
