# Pip te lo explica · bot de clips de GTA 6

Cada 3 horas, GitHub Actions:
1. Busca en la API oficial de Twitch los clips de **Grand Theft Auto VI** más vistos de las últimas 6 h (salta los que parecen spoilers).
2. Los descarga y los monta en vertical: gancho arriba, clip en el centro, crédito al streamer y Pip en la esquina.
3. Los sube a la rama `media` de este repo (se sirven públicos por jsDelivr).
4. Los programa en Buffer, en todos tus canales de YouTube/TikTok/Instagram.

## Claves necesarias (Settings → Secrets and variables → Actions → New repository secret)

| Secreto | Dónde se saca |
|---|---|
| `TWITCH_CLIENT_ID` *(opcional)* | dev.twitch.tv/console → Register Your Application (OAuth Redirect: `http://localhost`, categoría: Application Integration) |
| `TWITCH_CLIENT_SECRET` *(opcional)* | En la misma app → New Secret |
| `BUFFER_API_KEY` | publish.buffer.com/settings/api |
| `ANTHROPIC_API_KEY` *(opcional)* | console.anthropic.com — si está, los ganchos y títulos los escribe Claude; si no, usa plantillas |

## Ajustes opcionales (pestaña Variables)

- `DRAFT_MODE` = `true` → los deja como borradores en Buffer para que los apruebes tú.
- `CLIPS_PER_RUN` = cuántos clips por ejecución (por defecto 2).
- `TARGET_SERVICES` = `youtube,tiktok,instagram`.

Para lanzarlo al momento: pestaña **Actions → Pip GTA6 bot → Run workflow**.
- `STREAMERS` = lista de canales de Twitch separados por comas (se usa si no hay claves de Twitch).
