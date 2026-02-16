Este proyecto consiste en un Dashboard dinámico que muestra métricas, transacciones y gráficos en tiempo real, alimentado por una API en Node.js + Express.
Si la API no está activa, el sistema pasa automáticamente a Modo Demo, usando datos locales.

📁 Estructura del Proyecto
/ (raíz del repositorio)
├─ api/
│  ├─ server.js
│  ├─ seed.json
│  ├─ package.json
│  └─ src/
│     └─ routes/ (opcional)
└─ dashboard/
   ├─ index.html
   ├─ script.js
   ├─ style.css
   └─ data.json


🚀 Requisitos

Node.js 18 o superior
npm 8 o superior
Sistema operativo: Windows, macOS o Linux


🔌 1. Cómo activar la API
La API vive en la carpeta api del proyecto.
1) Entrar a la carpeta
Shellcd api``Mostrar más líneas
2) Instalar dependencias
Shellnpm installMostrar más líneas
3) (Opcional) Configurar el puerto en .env
Crea un archivo .env dentro de /api:
PORT=3000

Si no existe, la API usará el puerto 3000 por defecto.
4) Encender la API
Shellnpm run startMostrar más líneas
Para modo desarrollo con recarga automática:
Shellnpm run devMostrar más líneas

🟢 2. Ver el Dashboard funcionando
Una vez que la API está arriba, abre en tu navegador:
http://localhost:3000

(ó el puerto que configuraste)
El dashboard detectará automáticamente si la API está activa o no:




















EstadoIndicadorExplicación🟢 EN VIVO● EN VIVOLeyendo datos reales de seed.json🔴 MODO DEMO● MODO DEMOLeyendo datos de dashboard/data.json

📡 3. Endpoints de la API
GET /dashboard
Retorna las métricas y transacciones:
JSON{  "metrics": [ ... ],  "transactions": [ ... ]}Mostrar más líneas
Los datos provienen de:
api/seed.json


GET /health
Retorna estado del servidor:
JSON{ "ok": true, "uptime": 123.45 }Mostrar más líneas

📊 4. Funcionamiento del Dashboard
✔ Métricas
Se muestran tarjetas con valores de negocio (ventas, usuarios, tasa de rebote, etc).
✔ Gráfico (Chart.js)
Gráfico de líneas con las ventas por día.
✔ Búsqueda en vivo
El buscador filtra transacciones por ID o producto.
✔ Tabla dinámica
Muestra las últimas transacciones, ordenadas del más reciente al más antiguo.
✔ Modo DEMO automático
Si la API falla, se cargan datos desde:
dashboard/data.json

No requiere configuración adicional.

🧪 5. Cómo editar los datos

















ArchivoPropósitoapi/seed.jsonDatos reales que la API devuelvedashboard/data.jsonDatos de respaldo para Modo Demo
Puedes editar ambos archivos para mostrar tus propios datos.

🐛 6. Troubleshooting
❌ Error: EADDRINUSE: port 3000 already in use
El puerto está ocupado.
✔ Solución rápida: cambiar el puerto en .env
PORT=5173

✔ O matar el proceso:
Shellnetstat -ano | findstr :3000taskkill /PID <PID> /FMostrar más líneas

❌ Dashboard siempre queda en "MODO DEMO"
Posibles causas:

La API no está encendida
La API usa un puerto distinto (configura .env)
La API no responde correctamente en /dashboard


❌ API no carga seed.json
Asegúrate de que:

seed.json está en /api
Es un JSON válido y sin comas finales
