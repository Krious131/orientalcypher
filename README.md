# Orbital Cipher — Free Flight

A markerless, free-flight 3D space experience built with Vite and Three.js. It uses the supplied satellite GLB files, a locally bundled Earth texture, and a browser-based AES-GCM telemetry mission. It does not request camera access or use AR.js/Hiro tracking.

## Run locally

1. Open this folder in VS Code.
2. In the integrated terminal, run `npm install` once.
3. Run `npm run dev -- --host 0.0.0.0 --port 5173`.
4. Open [http://localhost:5173/](http://localhost:5173/) in a modern browser.
5. Drag to orbit around the satellite and scroll or pinch to zoom. On a phone, tap **MOTION**, then turn or tilt the phone to look around. Drag and pinch continue to work while motion control is enabled. Select AIM or either AcrimSAT option in the left panel.
6. In Mission Control, edit the telemetry payload if you like, select **Encrypt Packet**, then **Transmit to Ground**, and finally **Run Tamper Challenge**. The ground station must authenticate and recover the message before the tamper test becomes available.

The first install needs internet access for the npm packages. The satellite GLBs, Draco decoder, and Earth texture are included locally after that. Web Crypto and phone motion sensors work on localhost and HTTPS origins. On iOS, Safari asks for motion permission after you tap **MOTION**.

## Mission behavior

- Encryption uses the browser's Web Crypto API with AES-256-GCM, a new random 96-bit IV, and a 128-bit authentication tag.
- The encryption key and telemetry remain in the current page's memory. Only the XP score is saved in local storage.
- The transmission is a visual simulation inside the 3D scene; no radio link or external service is contacted.
- The tamper challenge flips one ciphertext bit and demonstrates that AES-GCM rejects the altered packet before releasing plaintext.
- Earth, orbit, and the ground station are visual scale approximations for an educational experience, not live orbital data.

## Assets and attribution

- The AIM and AcrimSAT models were provided by the project owner. Their original source and reuse terms were not supplied with the files.
- Earth surface map: NASA Earth Observatory, [Blue Marble: Next Generation — January base map](https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/base-map/), 5400 × 2700 global JPEG. The map is a satellite-data composite produced by Reto Stöckli and NASA Goddard Space Flight Center.
- Draco decoder files are copied from the installed Three.js package and served locally from `public/draco/`.
