# 📍 Gestión de Puntos de Venta

Aplicación web para gestión de puntos de venta con Google Maps, geolocalización automática, zonificación por cuadrantes y exportación de datos.

## ✨ Características

- **Geolocalización Automática**: Convierte direcciones en coordenadas usando Google Geocoding API
- **Visualización en Mapa**: Muestra todos los puntos de venta en Google Maps interactivo
- **Zonificación**: Dibuja polígonos personalizados para crear zonas/cuadrantes
- **Carga de Archivos Excel**: Importa múltiples puntos desde archivos .xlsx o .xls
- **Exportación de Datos**: Descarga los datos con coordenadas en formato Excel
- **Interfaz Moderna**: Diseño responsive y fácil de usar
- **Estadísticas en Tiempo Real**: Visualiza el número de puntos y zonas creadas

## 🚀 Inicio Rápido

### Prerrequisitos

Necesitas obtener una **Google Maps API Key** con los siguientes servicios habilitados:
- Maps JavaScript API
- Geocoding API
- Drawing Library
- Places API

### Configuración

1. **Obtener API Key de Google Maps**:
   - Ve a [Google Cloud Console](https://console.cloud.google.com/)
   - Crea un nuevo proyecto o selecciona uno existente
   - Habilita las APIs mencionadas arriba
   - Crea credenciales (API Key)
   - Restringe la clave por dominio para seguridad

2. **Configurar la Aplicación**:
   - Abre `index.html`
   - Busca la línea: 
     ```html
     <script src="https://maps.googleapis.com/maps/api/js?key=TU_API_KEY&callback=initMap&libraries=drawing,places" async defer></script>
     ```
   - Reemplaza `TU_API_KEY` con tu API Key de Google Maps

3. **Ejecutar la Aplicación**:
   - Simplemente abre `index.html` en tu navegador web
   - O puedes usar un servidor web local:
     ```bash
     python -m http.server 8000
     # O con Node.js
     npx http-server
     ```

## 📚 Cómo Usar

### 1. Agregar Puntos Manualmente

1. Ingresa el **nombre del punto de venta** (ej: "JUMBO CHIA")
2. Ingresa la **dirección completa** (ej: "Calle 123 #45-67, Bogotá, Colombia")
3. Haz clic en **"Agregar Punto"**
4. El punto aparecerá automáticamente en el mapa

### 2. Cargar Archivo Excel

1. Prepara un archivo Excel con las siguientes columnas:
   - `NOMBRE PV` o `NOMBRE`: Nombre del punto de venta
   - `DIRECCION`: Dirección completa del punto

2. Haz clic en **"📂 Cargar Archivo Excel"**
3. Selecciona tu archivo
4. Los puntos se geocodificarán y agregarán automáticamente

**Ejemplo de formato Excel**:

| NOMBRE PV | DIRECCION |
|-----------|----------|
| JUMBO CHIA | Av. Pradilla #250, Chía, Cundinamarca |
| EXITO ZIPAQUIRA | Calle 15 #4-70, Zipaquirá, Cundinamarca |

### 3. Dibujar Zonas

1. Haz clic en **"Dibujar Zona"**
2. Haz clic en el mapa para crear los vértices del polígono
3. Haz clic en el primer punto para cerrar el polígono
4. Puedes editar la zona arrastrando los vértices

### 4. Exportar Datos

1. Haz clic en **"Exportar Datos"**
2. Se descargará un archivo Excel con:
   - Nombre del punto
   - Dirección
   - Latitud
   - Longitud

## 📦 Estructura del Proyecto

```
sales-point-management/
│
├── index.html          # Archivo principal de la aplicación
├── README.md           # Este archivo
└── datos-ejemplo.xlsx  # (Opcional) Archivo de ejemplo
```

## 🛠️ Tecnologías Utilizadas

- **HTML5/CSS3**: Estructura y estilos
- **JavaScript (Vanilla)**: Lógica de la aplicación
- **Google Maps API**: Mapas, geocodificación y dibujo
- **SheetJS (xlsx.js)**: Lectura y escritura de archivos Excel

## 🎯 Arquitectura Sugerida (Basada en Gemini)

Esta aplicación sigue la arquitectura recomendada:

1. **Base de Datos**: Los datos se manejan en memoria (puedes conectar a Firestore o Google Sheets)
2. **Normalización**: Los nombres se pueden limpiar con Vertex AI
3. **Geolocalización**: Se usa Places API para obtener coordenadas
4. **Zonificación**: Sistema de polígonos para crear cuadrantes
5. **Visualización**: Google Maps SDK para mostrar todo en el mapa

## 🔒 Seguridad

**Importante**: Protege tu API Key:

1. **Restricciones de dominio**: En Google Cloud Console, restringe el uso de la clave a tu dominio
2. **Restricciones de API**: Limita la clave solo a las APIs necesarias
3. **No expongas la clave**: Si vas a hacer público el código, usa variables de entorno

## 📊 Limitaciones y Consideraciones

- **Límite de Geocodificación**: Google tiene límites de uso gratuito
  - 40,000 solicitudes por mes gratis
  - Se agrega delay automático entre solicitudes al cargar archivos masivos

- **Calidad de Datos**: La precisión depende de la calidad de las direcciones
  - Usa direcciones completas con ciudad y país
  - Verifica manualmente los puntos críticos

## 🔧 Próximas Mejoras

- [ ] Integración con Google Sheets para almacenamiento persistente
- [ ] Optimización de rutas con Route Optimization API
- [ ] Análisis automático de qué puntos caen en cada zona
- [ ] Exportación de zonas en formato GeoJSON
- [ ] Dashboard con métricas y estadísticas avanzadas
- [ ] Normalización de nombres con Vertex AI

## 👤 Autor

**Jorge Hugo Perez**  
Desarrollado para Eficacia - Gestión de Puntos de Venta

## 📝 Licencia

Este proyecto es de código abierto y está disponible bajo la Licencia MIT.

## 🤝 Contribuciones

Las contribuciones son bienvenidas:

1. Haz fork del proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## ❓ Soporte

Si tienes preguntas o problemas:
- Abre un [Issue](https://github.com/jorgeicone/sales-point-management/issues)
- Contacta al autor

---

⭐ Si este proyecto te fue útil, considera darle una estrella!
