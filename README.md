# Hellomatik Posts — Releases

Distribución de **Hellomatik Posts.app** (el panel de blog y casos de éxito
como app de Mac, patrón Moptions). Repo privado de la organización.

## Instalar

1. Descarga el `.dmg` de la [última release](../../releases/latest).
2. Ábrelo y arrastra **Hellomatik Posts** a Aplicaciones.
3. Primera apertura: clic derecho → **Abrir** (la firma es ad-hoc, sin
   Developer ID — Gatekeeper avisa solo la primera vez).

## Qué necesita la máquina (v1)

- El checkout del monorepo en `~/Documents/HELLOMATIK/CODIGO/services/app`
  (o `HM_POSTS_REPO` apuntando a él), con `npm` (Homebrew) y Docker para la
  BD. La app arranca backend, panel y asistente ella sola y los supervisa.

## Updates

La app trae updater integrado (firmado con minisign): comprueba
`latest.json` de la última release de este repo. Publicar versión nueva:

```bash
cd services/app/apps/admin/desktop-tauri && ./release.sh <versión>
```

El código fuente vive en el monorepo: `services/app/apps/admin/desktop-tauri/`.
