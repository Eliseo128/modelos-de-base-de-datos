# models.py
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
    nombre = models.CharField(max_lengt_
