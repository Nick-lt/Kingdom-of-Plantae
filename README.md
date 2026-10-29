# Flora – zgadnij roślinę (Android)

Gra działa w całości offline. Postęp jest zapisywany w pamięci aplikacji (localStorage) i przetrwa restart telefonu; znika dopiero po odinstalowaniu aplikacji lub wyczyszczeniu jej danych, więc w Statystyki → Dane jest eksport i import postępu.

## Najprościej: APK z GitHuba (bez Android Studio)
1. Załóż puste repozytorium na github.com i wgraj do niego całą zawartość tego folderu (z ukrytym katalogiem `.github`).
2. Wejdź w **Actions → Build APK → Run workflow** (uruchamia się też sam po każdym pushu).
3. Po ok. 5–8 minutach pobierz z wyniku przebiegu artefakt **Flora-APK** (w środku `app-debug.apk`).
4. Przekaż plik znajomym. Na telefonie trzeba zezwolić na instalację z nieznanych źródeł dla aplikacji, z której otwierany jest plik.

APK jest podpisany kluczem debugowym: działa i instaluje się normalnie, ale nadaje się do rozdawania znajomym, nie do Google Play.

## Android Studio
```
npm install
npx capacitor-assets generate --android
npx cap sync android
npx cap open android      # Build → Build APK(s)
```
Wymagania: Node 22+, JDK 21.

## Zmiany w grze
Edytuj `www/index.html`, potem `npx cap sync android` i zbuduj ponownie.

## Wersja bez instalacji (PWA)
Folder `www/` można wystawić pod dowolnym adresem HTTPS (np. GitHub Pages). W Chrome na Androidzie: menu → „Dodaj do ekranu głównego”. Działa offline dzięki `sw.js`.
