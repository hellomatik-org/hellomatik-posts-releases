# Hellomatik Posts — Releases

Distribución de **Hellomatik Posts.app**: el panel de blog y casos de éxito de
Hellomatik como aplicación de Mac (Apple Silicon).

Este repositorio contiene **solo los artefactos publicados** — el DMG, el paquete
del actualizador y su firma. Es público porque el actualizador integrado necesita
poder descargar `latest.json` sin autenticarse; los binarios no llevan dentro
ninguna credencial. El código fuente vive en el monorepo, que sigue siendo
privado: `services/app/apps/admin/desktop-tauri/`.

## Instalar

1. Descarga el `.dmg` de la [última release](../../releases/latest).
2. Ábrelo y arrastra **Hellomatik Posts** a Aplicaciones.
3. **La primera vez, clic derecho → Abrir.** Con doble clic macOS la bloquea: la
   app va firmada con firma propia, no con un Developer ID de pago, así que
   Gatekeeper avisa una vez. Después se abre normal.

## Qué necesita la máquina

**Nada.** La app trae dentro su servidor y su panel, y crea su propia base de
datos vacía en `~/Library/Application Support`. No necesita el repositorio, ni
Node, ni Docker, ni ninguna clave.

Eso cubre escribir, editar, imágenes, vista previa y exportar. Lo que **sí**
necesita el repositorio es el **asistente** —el agente que redacta— y las
**portadas ilustradas**, porque el primero va con Claude Code y tu cuenta, y las
segundas con una clave de un modelo de imagen que no viaja aquí. Ambas cosas
están explicadas en `apps/admin/assistant/INSTALACION.md` dentro del monorepo.

## Actualizaciones

La app se actualiza sola: comprueba el `latest.json` de la última release de este
repositorio y verifica la firma antes de instalar nada.

Para publicar una versión nueva, desde el monorepo:

```bash
cd services/app/apps/admin/desktop-tauri
./construye-servidor.sh     # el servidor que viaja dentro
./prepara-bundle.sh         # panel + motor de Prisma + sharp, con sus comprobaciones
./release.sh <versión>      # compila, firma y publica aquí
```
