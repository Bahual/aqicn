# Aqicn Home Assistant Sensor

Sensor Home Assistant para mostrar la calidad del aire en Temuco usando la API de AQICN.

## Qué hace

Este proyecto define sensores REST en Home Assistant que consultan la calidad del aire en Temuco (Las Encinas) desde:

- https://aqicn.org/

Los parámetros incluidos son:

- `temuco_aqi`: índice de calidad del aire `AQI` (correspondiente a PM2.5)
- `temuco_pm10`: concentración de PM10 en `µg/m³`
- `temuco_co`: concentración de monóxido de carbono `ppm`

## Archivo principal

- `aqicn.yaml`

## Cómo usarlo en Home Assistant

1. Obtén una API key de AQICN en https://aqicn.org/
2. Reemplaza `TOKEN` en `aqicn.yaml` por tu API key.
3. Copia `aqicn.yaml` en la carpeta `config` de tu Home Assistant y añade esto en `configuration.yaml`:

```yaml
sensor: !include aqicn.yaml
```

   Alternativa: puedes pegar directamente el contenido completo de `aqicn.yaml` dentro de `configuration.yaml` en lugar de usar `!include`.

4. Reinicia Home Assistant.

## Notas

- El sensor usa `platform: rest` y consulta la misma URL para cada entidad.
- `scan_interval` está configurado en 900 segundos (15 minutos) para no sobrecargar la API.
- Si algún valor no está disponible en la respuesta de la API, el sensor devolverá `0`.
- La documentación de la API usada es: https://aqicn.org/json-api/doc/

## Advertencia

Asegúrate de no subir tu `TOKEN` público ni compartirlo en repositorios abiertos.

## Licencia

Este repositorio es solo un ejemplo de integración de la API de AQICN con Home Assistant.
