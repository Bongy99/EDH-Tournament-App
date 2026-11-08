# EDH Tournament Manager: guida all'installazione

## Opzione A: installazione diretta come PWA (consigliata, Android e iPhone, gratis)
1. Carica il contenuto della cartella `www/` su un hosting HTTPS gratuito (GitHub Pages, Netlify, Cloudflare Pages: basta trascinare la cartella).
2. Apri l'indirizzo dal telefono.
   - Android (Chrome): menu ⋮ → "Installa app".
   - iPhone (Safari): Condividi → "Aggiungi alla schermata Home".
3. L'app si apre a schermo intero, funziona offline e salva i dati sul telefono.

## Opzione B: APK Android / app iOS con Capacitor
Servono Node.js 18+ e, per Android, Android Studio (per iOS: un Mac con Xcode).
```
npm install
npx cap add android      # e/o: npx cap add ios
npx cap sync
npx cap open android     # in Android Studio: Build → Build APK(s)
```
L'APK generato si installa direttamente sul telefono (abilita "Installa app sconosciute").
Cambia `appId` in `capacitor.config.json` con un identificativo tuo (es. `it.mionome.edhmanager`).
Per pubblicare sugli store servono un account Google Play (25 $ una tantum) o Apple Developer (99 $/anno).

Dopo ogni modifica a `www/index.html` esegui `npx cap sync`.

## Opzione C: APK senza installare nulla (build automatica su GitHub)
1. Crea un repository su github.com e carica tutto il contenuto di questa cartella, incluso `.github/workflows/build-apk.yml`
   (se la cartella nascosta `.github` non si carica, su GitHub scegli "Add file → Create new file", scrivi il nome
   `.github/workflows/build-apk.yml` e incolla il contenuto del file `build-apk.yml` presente qui).
2. Vai nella scheda **Actions** → **Build APK** → **Run workflow**.
3. Dopo circa 5 minuti apri l'esecuzione completata e scarica **edh-manager-apk** dalla sezione Artifacts: dentro c'è `app-debug.apk`.
4. Copia l'APK sul telefono e aprilo (abilita "Installa app sconosciute" quando richiesto).
