# Rocky Agent Sound — Hook para Claude Code

Reproduce un sonido aleatorio de Rocky (`Rocky_A.mp3` o `Rocky_B.mp3`) en Claude Code cuando:

- **Claude solicita permiso** para ejecutar una herramienta (`PermissionRequest`)
- **Claude termina de responder** y espera tu input (`Stop`)

Cada vez que se dispara el hook, se selecciona aleatoriamente uno de los dos sonidos Rocky.

## Requisitos

- Windows 10/11
- Claude Code
- PowerShell (incluido en Windows)
- Node.js (para instalación vía npm)

## Instalación rápida (recomendada)

```bash
npx @renatopuente/rocky-agent-sound
```

Esto descarga e instala el paquete automáticamente sin necesidad de clonar el repositorio.

## El instalador:

1. Copia `Rocky_A.mp3` y `Rocky_B.mp3` a `~/sounds/`
2. Agrega los hooks automáticamente a `~/.claude/settings.json`
3. Muestra la ruta de los MP3 y los eventos configurados

Reinicia Claude Code después de instalarlo.

## Desinstalación

```bash
npx @renatopuente/rocky-agent-sound rocky-uninstall
```

O si ya instalaste el paquete globalmente:

```bash
rocky-uninstall
```

### El desinstalador:

1. Elimina los hooks de Rocky de `~/.claude/settings.json` (sin tocar otros hooks)
2. Borra `~/sounds/Rocky_A.mp3` y `~/sounds/Rocky_B.mp3`
3. Elimina `~/sounds/` si quedó vacía

Reinicia Claude Code después de desinstalarlo.

## Instalación manual

1. Clona o descarga este repositorio.
2. Copia `Rocky_A.mp3` y `Rocky_B.mp3` a una carpeta de tu preferencia.
3. Abre el archivo de configuración global de Claude Code: `C:\\Users\\<TuUsuario>\\.claude\\settings.json`
4. Agrega los hooks dentro de la clave `"hooks"` usando el comando de PowerShell con selección aleatoria.

## Personalización

- **Volumen:** Cambia `$mp.Volume = 1.0` a cualquier valor entre 0.0 y 1.0.
- **Sonido:** Reemplaza los archivos Rocky con cualquier MP3 que quieras usar.
- **Disparador:** Elimina el bloque `PermissionRequest` o `Stop` si solo quieres uno de los dos.

## Cómo funciona

Claude Code soporta hooks — comandos de shell que se ejecutan en eventos específicos del ciclo de vida del agente. Este paquete usa `System.Windows.Media.MediaPlayer` de PowerShell para reproducir aleatoriamente uno de los sonidos Rocky de forma asíncrona cuando Claude necesita tu atención.

---

Hecho por [@renatopuente](https://github.com/renatopuente)
