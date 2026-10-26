# Adriano YTDownloader

**Descargador de videos y audio para Windows, portátil, sencillo y sin instalaciones adicionales.**

Adriano YTDownloader es una aplicación para descargar contenido multimedia mediante enlaces, con opciones de calidad, formato y ubicación de almacenamiento. Permite gestionar varias descargas simultáneamente y ejecutarse desde una carpeta local o instalarse en el perfil del usuario.

Integra las herramientas necesarias para funcionar sin instalar Python, FFmpeg ni motores JavaScript por separado.

## Características principales

- **Portabilidad:** transporta la aplicación en una memoria USB y úsala en diferentes equipos.
- **Instalación sencilla:** instala la aplicación en tu usuario sin permisos de administrador.
- **Descargas múltiples:** agrega varios enlaces, uno por línea.
- **Descargas simultáneas:** configura entre 1 y 8 tareas en paralelo.
- **Calidad y formato:** selecciona las opciones de descarga disponibles.
- **Gestión de descargas:** consulta y cancela tareas desde la aplicación.
- **Historial:** conserva registros de descargas y permite limpiarlos sin eliminar los archivos descargados.
- **Compatibilidad:** incorpora motores diferenciados para versiones modernas y antiguas de Windows.
- **Actualizaciones:** comprueba la disponibilidad de actualizaciones del motor oficial.

## 1. Cómo utilizar la aplicación

### Opción A: Uso portátil mediante USB

1. Descarga o copia la carpeta completa de Adriano YTDownloader.
2. Copia la carpeta a una memoria USB.
3. En el equipo donde quieras utilizarla, copia la carpeta al Escritorio, Documentos u otra ubicación.
4. Abre `Adriano YTDownloader.exe`.

No necesitas ejecutar un instalador ni configurar manualmente las herramientas internas.

**Importante:** conserva la estructura original de carpetas para garantizar que los componentes funcionen correctamente.

### Opción B: Instalar en el equipo

Si prefieres utilizar Adriano YTDownloader directamente desde Windows:

1. Ejecuta `Adriano YTDownloader.exe`.
2. Selecciona **Instalar en este equipo**.
3. La aplicación copiará sus componentes al perfil de tu usuario.
4. Se creará un acceso directo en el Escritorio.
5. Utiliza el acceso directo para abrir la aplicación sin conectar nuevamente el USB.

La instalación no requiere permisos de administrador y no copia tus descargas ni tu historial anterior.

## 2. Cómo descargar videos

1. Abre Adriano YTDownloader.
2. Pega uno o varios enlaces, colocando cada enlace en una línea diferente.
3. Selecciona el formato y la calidad deseados.
4. Elige la carpeta de destino.
5. Pulsa **Descargar**.

Puedes añadir nuevos enlaces mientras otras descargas continúan ejecutándose.

### Configuración inicial

| Configuración | Valor predeterminado |
|---|---|
| Formato | MP4 |
| Calidad | Máxima disponible |
| Descargas simultáneas | 3 |
| Límite configurable | De 1 a 8 tareas |
| Carpeta de destino | `Descargas/` |
| Subtítulos | No se descargan |

### Gestión de tareas

Desde la sección **Descargas** puedes seleccionar una tarea y cancelarla.

La opción **Limpiar historial** elimina únicamente los registros guardados. Los videos y archivos descargados permanecen en su ubicación.

## 3. Estructura de archivos

```text
Adriano YTDownloader/
│
├── Adriano YTDownloader.exe
├── Adriano YTDownloader.exe.config
├── LEEME.txt
│
├── Datos/
│   └── preferencias.xml
│
├── Descargas/
│
├── tools/
│   ├── modern/
│   │   ├── yt-dlp.exe
│   │   └── deno.exe
│   │
│   ├── compat/
│   │   └── yt-dlp.exe
│   │
│   ├── js/
│   │   ├── qjs.exe
│   │   └── libwinpthread-1.dll
│   │
│   └── media/
│       ├── ffmpeg.exe
│       ├── ffprobe.exe
│       └── *.dll
│
└── Licencias/
    ├── componentes.json
    └── ...
```

*La carpeta `Descargas` se utiliza como destino inicial y puede generarse durante el uso.*

**El único ejecutable que necesitas abrir directamente es `Adriano YTDownloader.exe`.**

Las carpetas `tools` y `Licencias`, así como el archivo `.exe.config`, deben permanecer junto a la aplicación. No elimines ni modifiques los componentes internos.

## 4. Portabilidad y almacenamiento

Adriano YTDownloader organiza su información de la siguiente manera:

| Elemento | Ubicación |
|---|---|
| Preferencias | `Datos/` |
| Historial | `Datos/` |
| Videos descargados | `Descargas/` inicialmente |
| Motores y dependencias | `tools/` |
| Licencias | `Licencias/` |

Las rutas ubicadas dentro del paquete se guardan de forma relativa. Esto permite trasladar la carpeta entre equipos o memorias USB, incluso cuando cambia la letra de la unidad.

**Consideraciones importantes:**

- Si seleccionas una carpeta externa, esa ruta solo funcionará en los equipos donde exista.
- No ejecutes varias instancias compartiendo simultáneamente la misma carpeta de datos.
- Para trasladar tus preferencias e historial, conserva la carpeta `Datos`.
- Se necesita conexión a Internet para realizar descargas y verificar actualizaciones.

## 5. Compatibilidad con Windows

La aplicación incorpora herramientas diferentes según la versión y arquitectura del sistema operativo.

| Sistema operativo | Motor multimedia | Motor JavaScript |
|---|---|---|
| Windows 11 x64 | yt-dlp oficial | Deno |
| Windows 10 x64 | yt-dlp oficial | Deno |
| Windows 7/8 y sistemas de 32 bits | yt-dlp compatible de nicolaasjan | QuickJS |

Para los sistemas antiguos se incluye una compilación de FFmpeg de 32 bits.

### Requisitos y limitaciones

- **Windows 10/11 x64:** compatibilidad prevista con el motor oficial.
- **Windows 7:** requiere Service Pack 1 y las actualizaciones necesarias del sistema.
- **Sistemas antiguos:** pueden necesitar componentes UCRT y certificados de seguridad actualizados.
- **.NET Framework:** la interfaz puede utilizar .NET 4.x o .NET 2.0/3.5, según la disponibilidad y compatibilidad del equipo.
- **Arquitectura ARM:** no se garantiza compatibilidad.
- **Instalaciones modificadas o reducidas de Windows:** funcionamiento no garantizado.

**Nota:** la compatibilidad con Windows 7 todavía no se ha verificado en un equipo físico real.

## 6. Actualizaciones

Al iniciar Adriano YTDownloader, la aplicación intenta comprobar las actualizaciones disponibles para el motor oficial.

- Si existe conexión a Internet, se realiza la comprobación.
- Si no existe conexión, se informa que no fue posible verificar las actualizaciones.
- El motor compatible destinado a sistemas antiguos se conserva independientemente del oficial.

Esto evita sustituir el motor compatible por una versión oficial que no funciona en Windows 7.

## 7. Componentes y licencias

Adriano YTDownloader integra herramientas de terceros que cuentan con sus propios autores, proyectos y condiciones de licencia.

| Componente | Proyecto oficial o fuente |
|---|---|
| yt-dlp | https://github.com/yt-dlp/yt-dlp |
| yt-dlp compatible | https://github.com/nicolaasjan/yt-dlp |
| FFmpeg para Win32 | https://github.com/sudo-nautilus/FFmpeg-Builds-Win32 |
| Código fuente FFmpeg | https://github.com/FFmpeg/FFmpeg/tree/n6.0 |
| QuickJS | https://bellard.org/quickjs/ |
| Deno | https://github.com/denoland/deno |

Las licencias y atribuciones correspondientes se encuentran en la carpeta `Licencias/`.

El archivo `Licencias/componentes.json` contiene información sobre los componentes distribuidos con la aplicación.

**Importante:** los componentes de terceros mantienen sus respectivas licencias. La distribución de Adriano YTDownloader debe respetar sus condiciones.

## 8. Avisos importantes

Adriano YTDownloader facilita la descarga y gestión de contenido multimedia, pero la disponibilidad de las descargas depende de los servicios de origen, de los motores utilizados y de sus posibles cambios.

El usuario es responsable de descargar únicamente contenido para el que tenga autorización y de respetar los derechos de autor y las condiciones de uso de cada plataforma.

La aplicación necesita conexión a Internet para descargar contenido. Su funcionamiento puede verse afectado por cambios en las plataformas compatibles.

## Autor

**Adrián Hernández**

Ingeniero en Ciencias de la Computación

Desarrollo de software y herramientas de productividad.

**Repositorio:** https://github.com/Ssamaeljs/adrian-yt-downloader

---

*Adriano YTDownloader — Una herramienta práctica para descargar y gestionar contenido multimedia desde Windows.*