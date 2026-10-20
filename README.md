# lookout-thunderbird-fix
LookOut Fix for Thunderbird (Up to 159.* ESR)

# LookOut Fix para Thunderbird (Hasta versión 159.* o más)

## ¿Por qué se creó esta versión?
La extensión oficial de LookOut dejó de ser compatible con las versiones recientes de 64 bits de Mozilla Thunderbird.

Debido a que el manifiesto original imponía un límite estricto de versión máxima (`strict_max_version`), Thunderbird desactivaba automáticamente el complemento al actualizar el programa, impidiendo a los usuarios decodificar los archivos adjuntos `Winmail.dat` / `TNEF`. Dado que el repositorio original no mantiene actualizaciones de compatibilidad activas para estas ramas ESR, se ha creado esta versión corregida para mantener el complemento funcionando sin problemas.

---

## ¿Cómo se ha modificado?
Para restaurar la compatibilidad total sin alterar las funciones principales de la extensión, se aplicaron los siguientes cambios directamente sobre el paquete:

1. **Corrección del manifiesto (`manifest.json`):**
   * Se extrajo el contenido del paquete y se editó el archivo `manifest.json`.
   * Se actualizó la propiedad `strict_max_version` al valor `"*"` dentro de la configuración de Gecko, eliminando el bloqueo artificial de versión desde Thunderbird 115+ hasta la 159.* ESR.

2. **Estandarización del ID y nombre de la extensión:**
   * Se alineó el ID interno del complemento a `lookout@s3_fix_version`.
   * Se renombró el archivo final a `lookout@s3_fix_version.xpi` para facilitar su despliegue automatizado (vía carpeta de sistema `distribution/extensions` o inyección en perfil de usuario).

3. **Reempaquetado:**
   * Se volvió a comprimir la estructura actualizada en un archivo `.xpi` limpio, probado tanto para instalación manual como para despliegue por script en entornos corporativos.

---

## Guía de Instalación
1. Descarga el archivo `lookout@s3_fix_version.xpi` adjunto abajo en la sección **Assets**.
2. Abre Thunderbird y ve a **Complementos y temas** (`Ctrl + Mayús + A`).
3. Haz clic en el icono de la rueda dentada ⚙️ arriba a la derecha y selecciona **Instalar complemento desde archivo...**
4. Selecciona el archivo `.xpi` descargado y confirma la instalación.
