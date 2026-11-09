# Importación de Vehículos SAT — 2025 y 2026

## Archivos entregados

1. **`01_descarga_datos.py`** — Script de carga de datos:
   - Busca en la página de la SAT los `.zip` de 2025 y de lo que va de 2026.
   - Los descarga y descomprime dentro de la carpeta `Datos/`.
   - Lee todos los `.txt`/`.csv` descomprimidos y arma un solo dataset.
   - Guarda el resultado en `Datos/importacion_vehiculos_2025_2026.csv`.

2. **`02_exploracion_EDA.ipynb`** — Notebook con la exploración pedida:
   1. Vehículos livianos importados por tipo en 2025.
   2. Distribución de año-modelo de carros, pickups y SUV en 2025.
   3. Tipo de vehículo más importado en 2025.
   4. Meses con más importación de vehículos livianos.
   5. Comparación 2026 (meses transcurridos) vs. mismos meses de 2025, por tipo.

## Cómo correrlo

```bash
pip install requests beautifulsoup4 pandas matplotlib

python 01_descarga_datos.py
jupyter notebook 02_exploracion_EDA.ipynb
```

## Cosas que debes revisar tú (importante)

El sitio `portal.sat.gob.gt` tiene protección anti-bot, así que no pude
inspeccionar directamente el HTML de la página para confirmar:

- **El patrón exacto de las URLs de los `.zip`.** El script intenta
  encontrarlos solo (`PASO 1`). Si al correrlo ves el mensaje
  `[ATENCIÓN] No se encontraron enlaces .zip automáticamente`, abre la
  página en tu navegador, copia los enlaces de descarga de 2025 y de los
  meses de 2026 disponibles (clic derecho → *Copiar dirección del
  enlace*), y pégalos en la lista `ENLACES_MANUALES` al inicio del
  script.

- **Los nombres de columna reales dentro de los `.txt`.** Definí un
  diccionario `COLUMN_MAP` en `01_descarga_datos.py` con los alias más
  probables (`tipo`, `marca`, `linea`, `año`, `fecha`, etc.). Después de
  la primera corrida se genera `Datos/_columnas_detectadas.txt` con las
  columnas reales encontradas; si alguna no se tradujo bien, agrégala a
  `COLUMN_MAP` y vuelve a correr el script.

- **Los valores exactos de "tipo de vehículo".** En el notebook, la
  primera celda de la sección 1 imprime los valores únicos de
  `tipo_vehiculo` — ajusta la lista `TIPOS_LIVIANOS` con los nombres
  reales que veas ahí (ej. si la SAT usa "AUTOMOVIL" en mayúsculas o
  "PICK UP" con espacio).

Una vez ajustados esos dos o tres puntos con los datos reales, todo el
resto del pipeline (descarga → unificación → CSV → EDA) corre sin
necesidad de tocar nada más.
