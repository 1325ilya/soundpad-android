# SoundPad Android

Автономная сборка Android APK + Magisk-модуля через GitHub Actions.

Что есть в репозитории:

- `.github/workflows/build-release.yml` — workflow, который сам создаёт минимальный Android-проект, собирает APK, упаковывает Magisk-модуль и публикует GitHub Release.
- APK собирается как debug-сборка, потому что для production release нужна ваша подпись/keystore.
- Magisk-модуль упаковывается в `SoundPad-magisk-module.zip`.

## Как запустить

Workflow запускается автоматически при push в `main`. Также его можно запустить вручную: **Actions → Build APK and Magisk module → Run workflow**.

После успешной сборки появятся:

- Artifacts: `soundpad-apk-module-source`.
- GitHub Release с тегом вида `v1.0.<run_number>`.

## Ограничение

Реальная подмешка аудио в микрофонный канал зависит от прошивки, root, Magisk, аудиодрайвера и политики Android 13+. В текущей автосборке модуль безопасный: он не пишет микрофон, не отправляет файлы в интернет и не меняет system partition напрямую.
