# rey-qt6Dell

Tema oscuro para la pantalla de inicio de sesión de **SDDM**, escrito en QML y
preparado para versiones de SDDM compiladas con Qt 6.

## Características

- Fondo configurable mediante `theme.conf` (por defecto, `wall.png`).
- Selector de usuario con imagen, campo de contraseña e indicador de Bloq Mayús.
- Selectores de sesión y distribución del teclado.
- Reloj analógico y digital, fecha y controles para suspender, reiniciar o apagar.
- Diseño con tonos oscuros y acentos rojos.

## Requisitos

- SDDM con soporte para Qt 6 y el módulo `SddmComponents`.
- Qt Quick 2.15.
- Las fuentes e iconos que use el sistema para las imágenes de usuario y las
  banderas del teclado.

La compatibilidad concreta depende de cómo se haya compilado SDDM en la
distribución.

## Instalación

Desde la raíz del proyecto, copia los archivos del tema al directorio de temas
de SDDM:

```sh
sudo install -d /usr/share/sddm/themes/rey-qt6Dell
sudo cp -a "$PWD"/. /usr/share/sddm/themes/rey-qt6Dell/
```

Selecciona el tema en la configuración de SDDM. Por ejemplo, crea
`/etc/sddm.conf.d/theme.conf` con este contenido:

```ini
[Theme]
Current=rey-qt6Dell
```

Si ya existe una configuración de SDDM, comprueba cuál archivo define `[Theme]`
y cambia su opción `Current` en lugar de reemplazar otras opciones existentes.
Los cambios se aplicarán al reiniciar SDDM o el equipo; cerrar la sesión puede
terminar la sesión gráfica actual.

## Prueba

En sistemas que incluyen `sddm-greeter`, puedes previsualizar el tema sin
configurarlo como tema activo:

```sh
sddm-greeter --test-mode --theme /usr/share/sddm/themes/rey-qt6Dell
```

La disponibilidad y las opciones de este modo de prueba pueden variar según la
versión de SDDM.

## Estructura

- `Main.qml`: pantalla, selección de usuario y sesión, reloj y acciones de
  energía.
- `theme.conf`: configuración del tema; actualmente establece el fondo.
- `metadata.desktop`: metadatos que SDDM usa para identificar el tema.
- `reyComponents/`: componentes QML reutilizables para la tarjeta de usuario,
  contraseña, texto y constantes.
- Archivos PNG: fondo e iconos de controles.

Para cambiar el fondo, edita la opción `background` en `theme.conf` y coloca la
imagen correspondiente en el directorio del tema.

## Licencia

`metadata.desktop` declara **CC-BY-SA** para el tema. Algunos componentes
incluyen avisos de copyright y licencia propios: consérvalos y consulta esos
avisos antes de redistribuir o modificar los archivos.
