# AQICN Home Assistant Sensor

Configuracion de sensores REST para Home Assistant que consulta la calidad del aire de Temuco (estacion Las Encinas) usando la API de AQICN/WAQI.

## Contenido

El repositorio incluye un archivo principal:

- `aqicn.yaml`: define tres sensores `platform: rest` para Home Assistant.

## Sensores incluidos

Los sensores consultan el endpoint:

- `https://api.waqi.info/feed/chile/las-encinas-temuco/?token=TOKEN`

Entidades definidas:

- `temuco_aqi`: indice de calidad del aire (`AQI`)
- `temuco_pm10`: concentracion de `PM10` en `ug/m3`
- `temuco_co`: concentracion de monoxido de carbono en `ppm`

## Instalacion

1. Obtén una API key de AQICN en `https://aqicn.org/`.
2. Reemplaza `TOKEN` dentro de `aqicn.yaml` por tu API key.
3. Copia `aqicn.yaml` a la carpeta `config` de Home Assistant.
4. Incluye el archivo en tu `configuration.yaml`:

```yaml
sensor: !include aqicn.yaml
```

Tambien puedes copiar el contenido completo de `aqicn.yaml` directamente dentro de `configuration.yaml` si no quieres usar `!include`.

5. Reinicia Home Assistant.

## Detalles tecnicos

- Los tres sensores usan `platform: rest`.
- Todos consultan la misma URL y extraen distintos campos desde la respuesta JSON.
- `scan_interval` esta configurado en `900` segundos (15 minutos).
- Si la API no devuelve un valor esperado, el sensor responde con `0`.

## Referencias

- Sitio de AQICN: `https://aqicn.org/`
- Documentacion de la API: `https://aqicn.org/json-api/doc/`

## Recomendaciones

- No publiques tu `TOKEN` en repositorios abiertos.
- Si vas a versionar una configuracion real, usa secretos o variables separadas para credenciales.

## Alcance

Este repositorio es un ejemplo simple de integracion entre Home Assistant y la API de AQICN.
