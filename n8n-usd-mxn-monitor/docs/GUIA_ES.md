# Mini proyecto n8n: Monitor USD/MXN con validación de datos

Archivo: monitor_usd_mxn.json (probado: importa y corre sin errores, sin credenciales).

## Qué hace (7 nodos)
1. Disparador manual y otro programado (días hábiles 8 AM, hora CDMX).
2. HTTP Request: trae 30 días de tipo de cambio USD/MXN de un API público (Frankfurter, sin llave).
3. Code (JavaScript): valida la calidad de los datos (vacíos, no numéricos, negativos, fechas duplicadas) y calcula KPIs: último, promedio, mínimo, máximo y cambio % del periodo.
4. IF: si hay problemas de datos o el cambio supera 1.5%, va a "alerta"; si no, a "todo normal".
5. Set: arma el mensaje final en texto.

## Cómo usarlo (unos 10 minutos)
1. Abre n8n (cuenta de prueba en n8n.io o n8n instalado en tu compu).
2. Crea un workflow nuevo, menú de tres puntos, "Import from File", elige monitor_usd_mxn.json.
3. Da clic en "Execute workflow" y abre cada nodo para ver los datos que entran y salen.
4. Reto opcional: cambia el umbral de 1.5 en el nodo Code, o agrega al final un nodo de Gmail o Google Sheets para mandar o guardar el mensaje.
