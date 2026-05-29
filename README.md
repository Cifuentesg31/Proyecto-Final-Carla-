# PROYECTO FINAL CARLA 

## Autores
- Camilo Cifuentes
- Gabriel Duarte
  
## Descripción
Este proyecto implementa un controlador autónomo de vehículo en CARLA que sigue una trayectoria definida por waypoints utilizando el modelo cinemático de bicicleta y el algoritmo Pure Pursuit.

El vehículo puede:
- Arrancar desde cualquier punto de la pista.
- Seguir los waypoints progresivamente sin saltos falsos.
- Ajustar velocidad según proximidad a la trayectoria.
- Controlar la dirección, aceleración y freno en tiempo real.

Está diseñado para el mapa RaceTrack y permite demostrar el comportamiento de un vehículo autónomo siguiendo una ruta cerrada.

---

## Contenido
- follow_recorded_waypoints.py – Script principal que controla el vehículo.
- racetrack_waypoints_trimmed.csv – Archivo CSV con los waypoints de la pista.
- Dependencias: Python 3.6+, CARLA Python API (carla), módulos estándar (math, csv, time, sys).

---

---

## Requisitos
- CARLA 0.8.x o superior.
- Python 3.6+.
- Mapa RaceTrack cargado en CARLA.
- El archivo CSV de waypoints y el script .py deben estar en la misma carpeta.

---

## Instalación (GitHub)

1. Clona el repositorio:

```bash
git clone https://github.com/usuario/repositorio-carla-waypoints.git
cd repositorio-carla-waypoints
```

2. Instala dependencias de Python, si no las tienes:

```bash
pip install carla
```

---

## Uso

### 1. Iniciar CARLA Server

```bash
cd /path/to/CARLA

# Linux
./CarlaUE4.sh /Game/Maps/RaceTrack -windowed -carla-server -benchmark -fps=20

# Windows
# CarlaUE4.exe /Game/Maps/RaceTrack -windowed -carla-server -benchmark -fps=20
```

### 2. Ejecutar el script de seguimiento

```bash
cd /path/to/proyecto_final
python3 follow_recorded_waypoints.py
```

El script:
- Detecta automáticamente el waypoint más cercano a la posición inicial del vehículo.
- Finaliza cuando el vehículo completa una vuelta desde el punto inicial.
- Imprime información de cada paso: posición, velocidad, dirección, error lateral y progreso.

---

## Configuración adicional

- Para cambiar la velocidad máxima, modifica la función calculate_target_speed() en el script.
- Para ajustar la agresividad del control lateral, modifica lookahead_gain y min_lookahead en calculate_pure_pursuit_steering().
- No es necesario modificar start_x y start_y; el script detecta automáticamente la posición inicial del vehículo.

---

## Notas importantes

- Funciona únicamente con RaceTrack. Si se cambia de mapa, se deben generar nuevos waypoints.
- El vehículo debe iniciarse sobre o muy cerca de la pista.
- La lógica anti-salto evita que el vehículo “salte” a otra zona de la pista cercana.
- La posición inicial real del vehículo se usa para calcular el primer waypoint.

---

## Licencia

Este proyecto se distribuye bajo licencia MIT.

---

## Compatibilidad con Ubuntu

- El proyecto funciona también en Ubuntu.
- Comandos para Linux:

```bash
cd /path/to/CARLA
./CarlaUE4.sh /Game/Maps/RaceTrack -windowed -carla-server -benchmark -fps=20

cd /path/to/proyecto_final
python3 follow_recorded_waypoints.py
```

- Python 3.6+ y CARLA Python API son requeridos.
- Todo lo demás del código es cross-platform.
