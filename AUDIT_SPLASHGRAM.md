# Аудит AyuGram Desktop для ребрендинга в Splashgram

Дата аудита: 23.09.2026. Исходный репозиторий: https://github.com/AyuGram/AyuGramDesktop.
Проверенная ветка: dev. HEAD: db3b9891cb0b04ebb7d8c0e71ada3bcc669b910a. Версия из Telegram/build/version: 7.0.9.
Рабочий каталог: C:/Users/spleshik/Documents/ChatGPT/Splashgram. Рабочее дерево чистое; remote origin указывает на репозиторий AyuGram.

## Структура и сборочная система

- Корневой CMakeLists.txt требует CMake 3.25 и проверяет политики до 3.31; project описан как AyuGram Desktop и имеет HOMEPAGE_URL https://ayugram.one.
- CMake подключает подмодуль cmake, затем собирает Telegram/CMakeLists.txt. Цель CMake называется Telegram, но OUTPUT_NAME для не-Apple платформы равен AyuGram.
- Telegram/configure.bat запускает configure.py. Для x64 run_cmake.py передает архитектуру x64 и toolset v143; основной генератор Visual Studio выбирается CMake. Вызов: configure.bat x64 -D TDESKTOP_API_ID=... -D TDESKTOP_API_HASH=....
- Telegram/build/prepare/win.bat запускает prepare.py. Скрипт требует Native Tools Prompt, создает ThirdParty и Libraries/win64, выставляет CMAKE_GENERATOR=Ninja Multi-Config и собирает зависимости в Debug и Release.
- По умолчанию для win64 выбирается Qt 5.15.19. Аргумент qt6 или ARM64 выбирает Qt 6.11.1.

В .gitmodules 37 подмодулей верхнего уровня; с вложенными зависимостями полный рекурсивный checkout содержит 41 submodule. Все зафиксированные подмодули и вложенные submodule checkout выполнены на требуемых SHA.

| Подмодуль | Зафиксированный SHA | Состояние |
|---|---|---|
| Telegram/ThirdParty/GSL | 87f9d768866548b5b86e72be66c60c5abd4d9b37 | инициализирован |
| Telegram/ThirdParty/MicroTeX | 7059649a44c24b640c831adef1e5f5b86e77299f | инициализирован |
| Telegram/ThirdParty/QR | 720f62bddb7226106071d4728c292cb1df519ceb | инициализирован |
| Telegram/ThirdParty/TooManyCooks | b86af81982860c96295a7e95e4c60cb335615cef | инициализирован |
| Telegram/ThirdParty/cld3 | b48dc46512566f5a2d41118c8c1116c4f96dc661 | инициализирован |
| Telegram/ThirdParty/cmark-gfm | 587a12bb54d95ac37241377e6ddc93ea0e45439b | инициализирован |
| Telegram/ThirdParty/expected | 292eff8bd8ee230a7df1d6a1c00c4ea0eb2f0362 | инициализирован |
| Telegram/ThirdParty/fcitx5-qt | c743b12e6780edf1dcfe9071531c80f050cacb95 | инициализирован |
| Telegram/ThirdParty/hime | 9b3e6f9ab59d1fe4d9de73d3bf0fed7789f921c5 | инициализирован |
| Telegram/ThirdParty/hunspell | 22c3381e2066bed616250d373fc5c935598b564a | инициализирован |
| Telegram/ThirdParty/kcoreaddons | fd84da51b554eac25e35b1e3f373edaab3029b15 | инициализирован |
| Telegram/ThirdParty/kimageformats | df82311a1081e576c4ac020204578bb8a81b21ec | инициализирован |
| Telegram/ThirdParty/libcbor | 170bee2b82cdb7b2ed25af301f62cb6efdd40ec1 | инициализирован |
| Telegram/ThirdParty/libfido2 | b974e7cf2ee7392134cc12c08b76a068cf250dd8 | инициализирован |
| Telegram/ThirdParty/libprisma | 23b0d70f9709da9b38561d5706891a134d18df76 | инициализирован |
| Telegram/ThirdParty/lz4 | 5ff839680134437dbf4678f3d0c7b371d84f4964 | инициализирован |
| Telegram/ThirdParty/nimf | 498ec7ffab3ac140c2469638a14451788f03e798 | инициализирован |
| Telegram/ThirdParty/range-v3 | a81477931a8aa2ad025c6bda0609f38e09e4d7ec | инициализирован |
| Telegram/ThirdParty/rlottie | 8c69fc20cf2e150db304311f1233a4b55a8892d7 | инициализирован |
| Telegram/ThirdParty/tgcalls | 2faee3b5524f54d56c91c2058c00e11c656a74b3 | инициализирован |
| Telegram/ThirdParty/xdg-desktop-portal | 23a76c392170dbbd26230f85ef56c3a57e52b857 | инициализирован |
| Telegram/ThirdParty/xxHash | bbb27a5efb85b92a0486cf361a8635715a53f6ba | инициализирован |
| Telegram/codegen | 8845d9d45ac754400e19cc2c706dba70a16ef0d5 | инициализирован |
| Telegram/lib_base | 82d182a275e197fd717fecc86193d9d91f4fc5b5 | инициализирован |
| Telegram/lib_crl | 7a165302fed408c84b2d1c2513e35a21a141da44 | инициализирован |
| Telegram/lib_icu | 7e55ddbcda78145b1fdb55c1f07f39299fa263f6 | инициализирован |
| Telegram/lib_lottie | 49d67cf66d3573cd71a3228af47a4ac59b64fc90 | инициализирован |
| Telegram/lib_qr | 6fdf60461444ba150e13ac36009c0ffce72c4c83 | инициализирован |
| Telegram/lib_rpl | c57cccffb01d85570decd7fccb88419c9a682e63 | инициализирован |
| Telegram/lib_spellcheck | 1f18c1e35b99697fe58d48d7f5a88e96c928128e | инициализирован |
| Telegram/lib_storage | ccdc72548a5065b5991b4e06e610d76bc4f6023e | инициализирован |
| Telegram/lib_tl | 7573852f2fb6ffad152092c71b15437162227147 | инициализирован |
| Telegram/lib_translate | 09c10726220e6862ca91d39b5dec5119aa0177bc | инициализирован |
| Telegram/lib_ui | ec0c178bd2aa2acab3c0ca001f18cf9ac8ab89a2 | инициализирован |
| Telegram/lib_webrtc | 52636e86eaa493de670daf71959d000b281bd153 | инициализирован |
| Telegram/lib_webview | 71c948902bfac5b25e90e1c9d1c8a34d1ee275c0 | инициализирован |
| cmake | f79a0e6acdae261270391253d24f47efb54e9a7d | инициализирован |

Группы подмодулей: AyuGram: codegen, lib_ui, lib_tl, lib_icu; desktop-app: cmake, lib_base, lib_crl, lib_lottie, lib_qr, lib_rpl, lib_spellcheck, lib_storage, lib_translate, lib_webrtc, lib_webview, libprisma, MicroTeX, rlottie; third-party: GSL, QR, TooManyCooks, cld3, cmark-gfm, expected, fcitx5-qt, hime, hunspell, kcoreaddons, kimageformats, libcbor, libfido2, lz4, nimf, range-v3, tgcalls, xdg-desktop-portal, xxHash.
Вложенные submodule: Telegram/ThirdParty/libcbor/doxygen-theme, Telegram/ThirdParty/range-v3/doc/gh-pages, cmake/external/glib/cppgir и cmake/external/glib/cppgir/expected-lite.

Основные Windows-стадии prepare.py: patches, msys64, python, NuGet, jom, gyp, lzma, xz, zlib, mozjpeg, openssl3, opus, rnnoise, gas-preprocessor, dav1d, openh264, libavif, libde265, libwebp, libheif, libjxl, libvpx, liblcms2, nv-codec-headers, regex, ffmpeg, openal-soft, breakpad, tg_angle, qt5, tg_owt, ada, protobuf, tde2e. Стадии собирают статические библиотеки и Qt, поэтому одного клонирования исходников недостаточно. libiconv и crashpad относятся к macOS; stackwalk включается только опцией build-stackwalk.

## Файлы идентичности, которые надо менять в первом проходе

| Файл | Что задает |
|---|---|
| CMakeLists.txt:7,19-24 | минимальная версия CMake, DESCRIPTION и HOMEPAGE_URL |
| Telegram/CMakeLists.txt:24-26,100-104,2332-2348,2454-2462,2498-2510,2684-2709 | Ayu-список исходников/иконок, bundle id, имя бинарника, API defines и Linux/XDG имена |
| Telegram/SourceFiles/core/version.h:22-24 | AppNameOld, AppName, AppFile |
| Telegram/SourceFiles/platform/win/windows_app_user_model_id.cpp:29-31,216,348-370 | Windows AUMID, имена ярлыков и Alpha-ярлыка |
| Telegram/SourceFiles/platform/win/specific_win.cpp:238-258,320-329 | APPDATA каталоги и старые ярлыки; здесь нужна миграция AyuGram в Splashgram |
| Telegram/Resources/winrc/Telegram.rc:39,64,67 | icon256.ico и Windows VERSIONINFO |
| Telegram/Resources/winrc/Updater.rc:55,58 | метаданные Updater.exe |
| Telegram/build/setup.iss:1-6,21-27,44-52,72-86,99-108 | имя, URL, exe, Inno AppId, setup filename и пути установки |
| Telegram/SourceFiles/_other/updater_win.cpp:207,380-387 | AyuGram.exe в логике обновления |
| Telegram/SourceFiles/_other/startup_task_win.cpp:49 | путь к exe для автозапуска |
| Telegram/SourceFiles/storage/localstorage.cpp:563-574 и Telegram/SourceFiles/ayu/utils/rc_manager.cpp:15 | URL сервера автообновлений/remote config |
| Telegram/SourceFiles/ayu/ayu_lang.cpp:118-124 | URL репозитория языков AyuGram |
| Telegram/SourceFiles/ayu/ui/settings/settings_main.cpp:73,104,148-183 | название в Settings и официальные каналы/сайт |
| Telegram/Resources/langs/lang.strings:8624-9035 | видимые строки AyuGram и ключи ayu_* |
| lib/xdg/com.ayugram.desktop.desktop, lib/xdg/com.ayugram.desktop.metainfo.xml, lib/xdg/com.ayugram.desktop.service | Linux desktop-id, метаданные, DBus service; три файла физически переименовать в com.splashgram.desktop.* |
| Telegram/Resources/uwp/AppX/AppxManifest.xml:10-18,30-51 | отдельные Telegram Store Identity, Executable и DisplayName; они не попали в поиск AyuGram, но для полного ребрендинга тоже обязательны |

Проверка конфигурационных заголовков: Telegram/SourceFiles/config.h существует, но не содержит AyuGram identity; отдельного base_config.h в checkout нет. API ID/hash задаются CMake defines через configure.bat, а имя/идентификаторы — в перечисленных version/CMake/platform/resource файлах.

Физические переименования: lib/xdg/com.ayugram.desktop.desktop -> com.splashgram.desktop.desktop, .metainfo.xml -> com.splashgram.desktop.metainfo.xml, .service -> com.splashgram.desktop.service. Если внутренний namespace тоже переименовывается, каталог Telegram/SourceFiles/ayu, Telegram/lib_ui/ayu и qrc/ayu потребуют отдельного согласованного рефакторинга; механически менять ayu_* нельзя, потому что это имена API, translation keys, include paths и TL-generated hooks (например is_ayuNoforwards/is_ayuRestricted).

Критические решения до кода: сгенерировать новый уникальный Windows AUMID (например, Splashgram.SplashgramDesktop), новый GUID Inno Setup вместо 53F49750-6209-4FBF-9CA8-7A333C87D666, новые XDG/AppX identifiers и новый домен обновлений. Старые AppNameOld, APPDATA/AyuGram каталоги и ярлыки оставить в migration path, чтобы обновление не создало пустой профиль. Не заменять без проверки upstream URLs, GitHub/Crowdin/Telegram usernames и ссылки на исходный AyuGram проект.

## Иконки и ресурсы логотипа

- Windows exe и установщик: Telegram/Resources/art/icon256.ico. Ссылка на него находится в Telegram/Resources/winrc/Telegram.rc:39 и Telegram/build/setup.iss:25.
- Переключаемые значки панели задач/трея: Telegram/Resources/art/ayu/<variant>/app_icon.ico, варианты перечислены в Telegram/CMakeLists.txt и упакованы через Telegram/Resources/qrc/ayu/ayu.qrc. Для Splashgram заменить набор ico и обновить qrc/пути.
- PNG-набор для установок и Linux: Telegram/Resources/art/icon16.png, icon32.png, icon48.png, icon64.png, icon128.png, icon256.png, icon512.png и соответствующие @2x; CMake переименовывает их в com.ayugram.desktop.png.
- Монохромный трей: Telegram/Resources/icons/tray_monochrome*.svg.
- macOS assets (если сохраняется мультиплатформенная сборка): Telegram/Telegram/Images.xcassets/Icon.appiconset, Icon.iconset и AppIcon-*.icon.

## Полная инвентаризация literal AyuGram/ayugram

Поиск выполнен командой rg -i -l с исключением .git, Telegram/ThirdParty и этого отчёта. Получено 355 файлов (683 совпадения); отдельный поиск по Telegram/ThirdParty дал 0 файлов. Список ниже является точным снимком на момент аудита:

- .github/CONTRIBUTING.md
- .github/ISSUE_TEMPLATE/BUG_REPORT.yml
- .github/ISSUE_TEMPLATE/config.yml
- .gitmodules
- CMakeLists.txt
- docs/building-linux.md
- docs/building-mac.md
- docs/building-win.md
- lib/xdg/com.ayugram.desktop.desktop
- lib/xdg/com.ayugram.desktop.metainfo.xml
- lib/xdg/com.ayugram.desktop.service
- README-RU.md
- README.md
- Telegram/build/setup.iss
- Telegram/cmake/td_ui.cmake
- Telegram/CMakeLists.txt
- Telegram/lib_icu/CMakeLists.txt
- Telegram/lib_tl/tl/generate_tl.py
- Telegram/lib_ui/ayu/ayu_ui_settings.cpp
- Telegram/lib_ui/ayu/ayu_ui_settings.h
- Telegram/lib_ui/ui/style/style_core_font.cpp
- Telegram/Resources/langs/lang.strings
- Telegram/Resources/qrc/telegram/telegram.qrc
- Telegram/Resources/winrc/Telegram.rc
- Telegram/Resources/winrc/Updater.rc
- Telegram/SourceFiles/_other/packer.cpp
- Telegram/SourceFiles/_other/startup_task_win.cpp
- Telegram/SourceFiles/_other/updater_osx.m
- Telegram/SourceFiles/_other/updater_win.cpp
- Telegram/SourceFiles/api/api_bot.cpp
- Telegram/SourceFiles/api/api_editing.cpp
- Telegram/SourceFiles/api/api_peer_search.cpp
- Telegram/SourceFiles/api/api_polls.cpp
- Telegram/SourceFiles/api/api_send_progress.cpp
- Telegram/SourceFiles/api/api_sending.cpp
- Telegram/SourceFiles/api/api_unread_things.cpp
- Telegram/SourceFiles/api/api_updates.cpp
- Telegram/SourceFiles/api/api_views.cpp
- Telegram/SourceFiles/api/api_who_reacted.cpp
- Telegram/SourceFiles/apiwrap.cpp
- Telegram/SourceFiles/ayu/ayu_infra.cpp
- Telegram/SourceFiles/ayu/ayu_infra.h
- Telegram/SourceFiles/ayu/ayu_lang.cpp
- Telegram/SourceFiles/ayu/ayu_lang.h
- Telegram/SourceFiles/ayu/ayu_settings.cpp
- Telegram/SourceFiles/ayu/ayu_settings.h
- Telegram/SourceFiles/ayu/ayu_state.cpp
- Telegram/SourceFiles/ayu/ayu_state.h
- Telegram/SourceFiles/ayu/ayu_url_handlers.cpp
- Telegram/SourceFiles/ayu/ayu_url_handlers.h
- Telegram/SourceFiles/ayu/ayu_worker.cpp
- Telegram/SourceFiles/ayu/ayu_worker.h
- Telegram/SourceFiles/ayu/data/ayu_database.cpp
- Telegram/SourceFiles/ayu/data/ayu_database.h
- Telegram/SourceFiles/ayu/data/entities.h
- Telegram/SourceFiles/ayu/data/messages_storage.cpp
- Telegram/SourceFiles/ayu/data/messages_storage.h
- Telegram/SourceFiles/ayu/features/filters/filters_cache_controller.cpp
- Telegram/SourceFiles/ayu/features/filters/filters_cache_controller.h
- Telegram/SourceFiles/ayu/features/filters/filters_controller.cpp
- Telegram/SourceFiles/ayu/features/filters/filters_controller.h
- Telegram/SourceFiles/ayu/features/filters/filters_utils.cpp
- Telegram/SourceFiles/ayu/features/filters/filters_utils.h
- Telegram/SourceFiles/ayu/features/forward/ayu_forward_rich.cpp
- Telegram/SourceFiles/ayu/features/forward/ayu_forward_rich.h
- Telegram/SourceFiles/ayu/features/forward/ayu_forward.cpp
- Telegram/SourceFiles/ayu/features/forward/ayu_forward.h
- Telegram/SourceFiles/ayu/features/forward/ayu_sync.cpp
- Telegram/SourceFiles/ayu/features/forward/ayu_sync.h
- Telegram/SourceFiles/ayu/features/message_shot/message_shot_theme_state.cpp
- Telegram/SourceFiles/ayu/features/message_shot/message_shot_theme_state.h
- Telegram/SourceFiles/ayu/features/message_shot/message_shot.cpp
- Telegram/SourceFiles/ayu/features/message_shot/message_shot.h
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/linux/streamer_mode_linux.cpp
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/linux/streamer_mode_linux.h
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/mac/streamer_mode_mac.h
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/mac/streamer_mode_mac.mm
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/platform_streamer_mode.h
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/win/streamer_mode_win.cpp
- Telegram/SourceFiles/ayu/features/streamer_mode/platform/win/streamer_mode_win.h
- Telegram/SourceFiles/ayu/features/streamer_mode/streamer_mode.cpp
- Telegram/SourceFiles/ayu/features/streamer_mode/streamer_mode.h
- Telegram/SourceFiles/ayu/features/translator/ayu_translate_provider.cpp
- Telegram/SourceFiles/ayu/features/translator/ayu_translate_provider.h
- Telegram/SourceFiles/ayu/features/translator/ayu_translator.cpp
- Telegram/SourceFiles/ayu/features/translator/ayu_translator.h
- Telegram/SourceFiles/ayu/features/translator/html_parser.cpp
- Telegram/SourceFiles/ayu/features/translator/html_parser.h
- Telegram/SourceFiles/ayu/features/translator/implementations/base.cpp
- Telegram/SourceFiles/ayu/features/translator/implementations/base.h
- Telegram/SourceFiles/ayu/features/translator/implementations/google.cpp
- Telegram/SourceFiles/ayu/features/translator/implementations/google.h
- Telegram/SourceFiles/ayu/features/translator/implementations/yandex.cpp
- Telegram/SourceFiles/ayu/features/translator/implementations/yandex.h
- Telegram/SourceFiles/ayu/libs/json_ext.hpp
- Telegram/SourceFiles/ayu/ui/ayu_icons.style
- Telegram/SourceFiles/ayu/ui/ayu_logo.cpp
- Telegram/SourceFiles/ayu/ui/ayu_logo.h
- Telegram/SourceFiles/ayu/ui/ayu_styles.style
- Telegram/SourceFiles/ayu/ui/ayu_userpic.cpp
- Telegram/SourceFiles/ayu/ui/ayu_userpic.h
- Telegram/SourceFiles/ayu/ui/boxes/donate_info_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/donate_info_box.h
- Telegram/SourceFiles/ayu/ui/boxes/donate_qr_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/donate_qr_box.h
- Telegram/SourceFiles/ayu/ui/boxes/edit_mark_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/edit_mark_box.h
- Telegram/SourceFiles/ayu/ui/boxes/font_selector.cpp
- Telegram/SourceFiles/ayu/ui/boxes/font_selector.h
- Telegram/SourceFiles/ayu/ui/boxes/import_filters_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/import_filters_box.h
- Telegram/SourceFiles/ayu/ui/boxes/message_shot_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/message_shot_box.h
- Telegram/SourceFiles/ayu/ui/boxes/plugin_info_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/plugin_info_box.h
- Telegram/SourceFiles/ayu/ui/boxes/theme_selector_box.cpp
- Telegram/SourceFiles/ayu/ui/boxes/theme_selector_box.h
- Telegram/SourceFiles/ayu/ui/components/avatar_corners_preview.cpp
- Telegram/SourceFiles/ayu/ui/components/avatar_corners_preview.h
- Telegram/SourceFiles/ayu/ui/components/icon_picker.cpp
- Telegram/SourceFiles/ayu/ui/components/icon_picker.h
- Telegram/SourceFiles/ayu/ui/components/image_view.cpp
- Telegram/SourceFiles/ayu/ui/components/image_view.h
- Telegram/SourceFiles/ayu/ui/components/message_preview.cpp
- Telegram/SourceFiles/ayu/ui/components/message_preview.h
- Telegram/SourceFiles/ayu/ui/components/saved_music.cpp
- Telegram/SourceFiles/ayu/ui/components/saved_music.h
- Telegram/SourceFiles/ayu/ui/context_menu/context_menu.cpp
- Telegram/SourceFiles/ayu/ui/context_menu/context_menu.h
- Telegram/SourceFiles/ayu/ui/context_menu/menu_item_subtext.cpp
- Telegram/SourceFiles/ayu/ui/context_menu/menu_item_subtext.h
- Telegram/SourceFiles/ayu/ui/message_history/history_inner.cpp
- Telegram/SourceFiles/ayu/ui/message_history/history_inner.h
- Telegram/SourceFiles/ayu/ui/message_history/history_item.cpp
- Telegram/SourceFiles/ayu/ui/message_history/history_item.h
- Telegram/SourceFiles/ayu/ui/message_history/history_section.cpp
- Telegram/SourceFiles/ayu/ui/message_history/history_section.h
- Telegram/SourceFiles/ayu/ui/settings/ayu_builder.cpp
- Telegram/SourceFiles/ayu/ui/settings/ayu_builder.h
- Telegram/SourceFiles/ayu/ui/settings/ayu_settings.style
- Telegram/SourceFiles/ayu/ui/settings/filters/edit_filter.cpp
- Telegram/SourceFiles/ayu/ui/settings/filters/edit_filter.h
- Telegram/SourceFiles/ayu/ui/settings/filters/per_dialog_filter.cpp
- Telegram/SourceFiles/ayu/ui/settings/filters/per_dialog_filter.h
- Telegram/SourceFiles/ayu/ui/settings/filters/settings_filters_list.cpp
- Telegram/SourceFiles/ayu/ui/settings/filters/settings_filters_list.h
- Telegram/SourceFiles/ayu/ui/settings/settings_appearance.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_appearance.h
- Telegram/SourceFiles/ayu/ui/settings/settings_ayu_utils.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_ayu_utils.h
- Telegram/SourceFiles/ayu/ui/settings/settings_ayu.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_ayu.h
- Telegram/SourceFiles/ayu/ui/settings/settings_chats.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_chats.h
- Telegram/SourceFiles/ayu/ui/settings/settings_filters.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_filters.h
- Telegram/SourceFiles/ayu/ui/settings/settings_general.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_general.h
- Telegram/SourceFiles/ayu/ui/settings/settings_main.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_main.h
- Telegram/SourceFiles/ayu/ui/settings/settings_other.cpp
- Telegram/SourceFiles/ayu/ui/settings/settings_other.h
- Telegram/SourceFiles/ayu/ui/utils/ayu_profile_values.cpp
- Telegram/SourceFiles/ayu/ui/utils/ayu_profile_values.h
- Telegram/SourceFiles/ayu/ui/utils/color_cut_quantizer.cpp
- Telegram/SourceFiles/ayu/ui/utils/color_cut_quantizer.h
- Telegram/SourceFiles/ayu/ui/utils/color_utils.cpp
- Telegram/SourceFiles/ayu/ui/utils/color_utils.h
- Telegram/SourceFiles/ayu/ui/utils/itunes_search.cpp
- Telegram/SourceFiles/ayu/ui/utils/itunes_search.h
- Telegram/SourceFiles/ayu/ui/utils/palette.cpp
- Telegram/SourceFiles/ayu/ui/utils/palette.h
- Telegram/SourceFiles/ayu/utils/ayu_mapper.cpp
- Telegram/SourceFiles/ayu/utils/ayu_mapper.h
- Telegram/SourceFiles/ayu/utils/qt_key_modifiers_extended.h
- Telegram/SourceFiles/ayu/utils/rc_manager.cpp
- Telegram/SourceFiles/ayu/utils/rc_manager.h
- Telegram/SourceFiles/ayu/utils/telegram_helpers.cpp
- Telegram/SourceFiles/ayu/utils/telegram_helpers.h
- Telegram/SourceFiles/ayu/utils/windows_utils.cpp
- Telegram/SourceFiles/ayu/utils/windows_utils.h
- Telegram/SourceFiles/boxes/about_box.cpp
- Telegram/SourceFiles/boxes/filters/edit_filter_chats_list.cpp
- Telegram/SourceFiles/boxes/peer_list_box.cpp
- Telegram/SourceFiles/boxes/peer_list_box.h
- Telegram/SourceFiles/boxes/peer_list_controllers.cpp
- Telegram/SourceFiles/boxes/send_files_box.cpp
- Telegram/SourceFiles/boxes/send_files_box.h
- Telegram/SourceFiles/boxes/share_box.cpp
- Telegram/SourceFiles/boxes/sticker_set_box.cpp
- Telegram/SourceFiles/calls/calls_userpic.cpp
- Telegram/SourceFiles/calls/group/calls_group_members_row.cpp
- Telegram/SourceFiles/chat_helpers/emoji_list_widget.cpp
- Telegram/SourceFiles/chat_helpers/field_autocomplete.cpp
- Telegram/SourceFiles/chat_helpers/gifs_list_widget.cpp
- Telegram/SourceFiles/chat_helpers/message_field.cpp
- Telegram/SourceFiles/chat_helpers/stickers_list_widget.cpp
- Telegram/SourceFiles/chat_helpers/tabbed_panel.cpp
- Telegram/SourceFiles/chat_helpers/ttl_media_layer_widget.cpp
- Telegram/SourceFiles/core/application.cpp
- Telegram/SourceFiles/core/click_handler_types.cpp
- Telegram/SourceFiles/core/core_settings.cpp
- Telegram/SourceFiles/core/crash_report_window.cpp
- Telegram/SourceFiles/core/crash_reports.cpp
- Telegram/SourceFiles/core/launcher.cpp
- Telegram/SourceFiles/core/local_url_handlers.cpp
- Telegram/SourceFiles/core/phone_click_handler.cpp
- Telegram/SourceFiles/core/ui_integration.cpp
- Telegram/SourceFiles/core/update_checker.cpp
- Telegram/SourceFiles/core/version.h
- Telegram/SourceFiles/data/components/promo_suggestions.cpp
- Telegram/SourceFiles/data/components/sponsored_messages.cpp
- Telegram/SourceFiles/data/data_channel.cpp
- Telegram/SourceFiles/data/data_chat_filters.cpp
- Telegram/SourceFiles/data/data_chat_participant_status.cpp
- Telegram/SourceFiles/data/data_chat.cpp
- Telegram/SourceFiles/data/data_document_resolver.cpp
- Telegram/SourceFiles/data/data_folder.cpp
- Telegram/SourceFiles/data/data_histories.cpp
- Telegram/SourceFiles/data/data_message_reactions.cpp
- Telegram/SourceFiles/data/data_peer_values.cpp
- Telegram/SourceFiles/data/data_peer.cpp
- Telegram/SourceFiles/data/data_replies_list.cpp
- Telegram/SourceFiles/data/data_session.cpp
- Telegram/SourceFiles/data/data_stories.cpp
- Telegram/SourceFiles/data/data_user.cpp
- Telegram/SourceFiles/data/stickers/data_custom_emoji.cpp
- Telegram/SourceFiles/dialogs/dialogs_inner_widget.cpp
- Telegram/SourceFiles/dialogs/dialogs_row.cpp
- Telegram/SourceFiles/dialogs/dialogs_widget.cpp
- Telegram/SourceFiles/dialogs/ui/dialogs_layout.cpp
- Telegram/SourceFiles/dialogs/ui/dialogs_stories_list.cpp
- Telegram/SourceFiles/dialogs/ui/top_peers_strip.cpp
- Telegram/SourceFiles/export/output/export_output_html.cpp
- Telegram/SourceFiles/history/history_inner_widget.cpp
- Telegram/SourceFiles/history/history_item_components.cpp
- Telegram/SourceFiles/history/history_item_helpers.cpp
- Telegram/SourceFiles/history/history_item_text.cpp
- Telegram/SourceFiles/history/history_item.cpp
- Telegram/SourceFiles/history/history_widget.cpp
- Telegram/SourceFiles/history/history.cpp
- Telegram/SourceFiles/history/view/controls/history_view_compose_controls.cpp
- Telegram/SourceFiles/history/view/controls/history_view_voice_record_bar.cpp
- Telegram/SourceFiles/history/view/controls/history_view_webpage_processor.cpp
- Telegram/SourceFiles/history/view/history_view_about_view.cpp
- Telegram/SourceFiles/history/view/history_view_bottom_info.cpp
- Telegram/SourceFiles/history/view/history_view_chat_section.cpp
- Telegram/SourceFiles/history/view/history_view_context_menu.cpp
- Telegram/SourceFiles/history/view/history_view_element.cpp
- Telegram/SourceFiles/history/view/history_view_element.h
- Telegram/SourceFiles/history/view/history_view_group_call_bar.cpp
- Telegram/SourceFiles/history/view/history_view_list_widget.cpp
- Telegram/SourceFiles/history/view/history_view_message.cpp
- Telegram/SourceFiles/history/view/history_view_pinned_section.cpp
- Telegram/SourceFiles/history/view/history_view_reply.cpp
- Telegram/SourceFiles/history/view/history_view_scheduled_section.cpp
- Telegram/SourceFiles/history/view/history_view_send_action.cpp
- Telegram/SourceFiles/history/view/history_view_service_message.cpp
- Telegram/SourceFiles/history/view/history_view_top_bar_widget.cpp
- Telegram/SourceFiles/history/view/history_view_translate_bar.cpp
- Telegram/SourceFiles/history/view/history_view_translate_tracker.cpp
- Telegram/SourceFiles/history/view/media/history_view_document.cpp
- Telegram/SourceFiles/history/view/media/history_view_gif.cpp
- Telegram/SourceFiles/history/view/media/history_view_media_grouped.cpp
- Telegram/SourceFiles/history/view/media/history_view_media_grouped.h
- Telegram/SourceFiles/history/view/media/history_view_media_unwrapped.cpp
- Telegram/SourceFiles/history/view/media/history_view_photo.cpp
- Telegram/SourceFiles/history/view/media/history_view_poll.cpp
- Telegram/SourceFiles/history/view/media/history_view_similar_channels.cpp
- Telegram/SourceFiles/history/view/media/history_view_sticker.cpp
- Telegram/SourceFiles/history/view/media/history_view_theme_document.cpp
- Telegram/SourceFiles/history/view/media/history_view_web_page.cpp
- Telegram/SourceFiles/history/view/reactions/history_view_reactions_button.cpp
- Telegram/SourceFiles/history/view/reactions/history_view_reactions_list.cpp
- Telegram/SourceFiles/history/view/reactions/history_view_reactions_selector.cpp
- Telegram/SourceFiles/history/view/reactions/history_view_reactions.cpp
- Telegram/SourceFiles/info/info_top_bar.cpp
- Telegram/SourceFiles/info/info_wrap_widget.cpp
- Telegram/SourceFiles/info/media/info_media_provider.cpp
- Telegram/SourceFiles/info/peer_gifts/info_peer_gifts_common.cpp
- Telegram/SourceFiles/info/profile/info_profile_actions.cpp
- Telegram/SourceFiles/info/profile/info_profile_badge.cpp
- Telegram/SourceFiles/info/profile/info_profile_cover.cpp
- Telegram/SourceFiles/info/profile/info_profile_inner_widget.cpp
- Telegram/SourceFiles/info/profile/info_profile_shared_media_classic.cpp
- Telegram/SourceFiles/info/profile/info_profile_top_bar.cpp
- Telegram/SourceFiles/info/saved/info_saved_music_common.cpp
- Telegram/SourceFiles/info/settings/info_settings_widget.cpp
- Telegram/SourceFiles/inline_bots/bot_attach_web_view.cpp
- Telegram/SourceFiles/intro/intro_qr.cpp
- Telegram/SourceFiles/intro/intro_step.cpp
- Telegram/SourceFiles/intro/intro_widget.cpp
- Telegram/SourceFiles/iv/iv_controller.cpp
- Telegram/SourceFiles/lang/translate_provider.cpp
- Telegram/SourceFiles/main/main_session.cpp
- Telegram/SourceFiles/mainwidget.cpp
- Telegram/SourceFiles/media/stories/media_stories_controller.cpp
- Telegram/SourceFiles/media/stories/media_stories_repost_view.cpp
- Telegram/SourceFiles/media/view/media_view_overlay_widget.cpp
- Telegram/SourceFiles/media/view/media_view_pip.cpp
- Telegram/SourceFiles/menu/menu_send.cpp
- Telegram/SourceFiles/platform/linux/main_window_linux.cpp
- Telegram/SourceFiles/platform/linux/specific_linux.cpp
- Telegram/SourceFiles/platform/mac/global_menu_mac.mm
- Telegram/SourceFiles/platform/mac/main_window_mac.mm
- Telegram/SourceFiles/platform/mac/specific_mac_p.mm
- Telegram/SourceFiles/platform/mac/tray_mac.mm
- Telegram/SourceFiles/platform/mac/window_title_mac.mm
- Telegram/SourceFiles/platform/win/main_window_win.cpp
- Telegram/SourceFiles/platform/win/specific_win.cpp
- Telegram/SourceFiles/platform/win/tray_win.cpp
- Telegram/SourceFiles/platform/win/windows_app_user_model_id.cpp
- Telegram/SourceFiles/settings/cloud_password/settings_cloud_password_email.cpp
- Telegram/SourceFiles/settings/sections/settings_chat.cpp
- Telegram/SourceFiles/settings/sections/settings_information.cpp
- Telegram/SourceFiles/settings/sections/settings_main.cpp
- Telegram/SourceFiles/settings/sections/settings_notifications.cpp
- Telegram/SourceFiles/settings/sections/settings_premium.cpp
- Telegram/SourceFiles/settings/settings_builder.cpp
- Telegram/SourceFiles/settings/settings_common_session.cpp
- Telegram/SourceFiles/settings/settings_experimental.cpp
- Telegram/SourceFiles/settings/settings_scale_preview.cpp
- Telegram/SourceFiles/storage/localimageloader.cpp
- Telegram/SourceFiles/storage/localstorage.cpp
- Telegram/SourceFiles/storage/storage_sparse_ids_list.cpp
- Telegram/SourceFiles/tray.cpp
- Telegram/SourceFiles/ui/boxes/choose_font_box.cpp
- Telegram/SourceFiles/ui/chat/attach/attach_bot_webview.cpp
- Telegram/SourceFiles/ui/chat/chat_style.cpp
- Telegram/SourceFiles/ui/chat/group_call_userpics.cpp
- Telegram/SourceFiles/ui/chat/message_bubble.cpp
- Telegram/SourceFiles/ui/controls/compose_ai_button_factory.cpp
- Telegram/SourceFiles/ui/controls/userpic_button.cpp
- Telegram/SourceFiles/ui/controls/who_reacted_context_action.cpp
- Telegram/SourceFiles/ui/effects/outline_segments.cpp
- Telegram/SourceFiles/ui/effects/reaction_fly_animation.cpp
- Telegram/SourceFiles/ui/effects/round_checkbox.cpp
- Telegram/SourceFiles/ui/empty_userpic.cpp
- Telegram/SourceFiles/ui/peer/video_userpic_player.cpp
- Telegram/SourceFiles/ui/unread_badge.cpp
- Telegram/SourceFiles/ui/userpic_view.cpp
- Telegram/SourceFiles/ui/widgets/chat_filters_tabs_strip.cpp
- Telegram/SourceFiles/ui/widgets/multi_select.cpp
- Telegram/SourceFiles/window/main_window.cpp
- Telegram/SourceFiles/window/notifications_manager_default.cpp
- Telegram/SourceFiles/window/notifications_manager.cpp
- Telegram/SourceFiles/window/section_widget.cpp
- Telegram/SourceFiles/window/themes/window_themes_cloud_list.cpp
- Telegram/SourceFiles/window/themes/window_themes_embedded.cpp
- Telegram/SourceFiles/window/window_controller.cpp
- Telegram/SourceFiles/window/window_filters_menu.cpp
- Telegram/SourceFiles/window/window_main_menu.cpp
- Telegram/SourceFiles/window/window_peer_menu.cpp
- Telegram/SourceFiles/window/window_session_controller.cpp
- Telegram/SourceFiles/window/window_session_controller.h

В эту выборку входят комментарии и Ayu-функциональность. Для рабочего ребрендинга сначала менять identity/UI/network файлы из таблицы выше, затем пройти остальные совпадения. Не переименовывать автоматически Telegram upstream credits и URL, пока не утверждены новые адреса.

## Windows: что установить

| Компонент | Версия/состав | Источник требования |
|---|---|---|
| Visual Studio | Visual Studio 2026 (18.x) или Build Tools 18.x; C++ workload, MSVC v143 (v14.44-17.14), C++ MFC v14.44 x86/x64, C++ ATL v14.44 x86/x64 | docs/building-win.md:12-19 |
| Toolset/terminal | x64 Native Tools; запуск vcvars64.bat -vcvars_ver=14.44. CMake helper использует -T v143; v145 по умолчанию не использовать для Win7-совместимого билда | docs/building-win.md:28-39, cmake/run_cmake.py |
| Windows SDK | Windows 11 SDK 10.0.26100.0 | docs/building-win.md:19 |
| CMake | 3.25 <= version <= 3.31 согласно cmake_minimum_required; для этого checkout ставить CMake 3.31.x и добавить в PATH | CMakeLists.txt:7 |
| Ninja | Ninja доступен в PATH; prepare.py задает Ninja Multi-Config и вызывает ninja для Breakpad/tg_owt | Telegram/build/prepare/prepare.py:95-102, 1422-1429 |
| Python | Python 3.10 в PATH; prepare.py создает ThirdParty/python и ставит pywin32, six, meson | docs/building-win.md:23-26, prepare.py:485-492 |
| Git | Git for Windows с recursive submodule support | docs/building-win.md:25-48 |
| MSYS2 | snapshot msys2-base-x86_64-20250830.sfx.exe; пакеты make, mingw-w64-x86_64-diffutils, gperf, nasm, perl, pkgconf | prepare.py:465-482 |
| NASM | MSYS2 NASM; при ошибке libvpx docs требуют откат до NASM 3.01 | docs/building-win.md:60-64 |
| Perl | mingw-w64-x86_64-perl из MSYS2; нужен OpenSSL/части multimedia | prepare.py:476-481 |
| NuGet | nuget.exe latest в ThirdParty/NuGet | prepare.py:494-498 |
| jom | jom_1_1_3.zip, распакованный в ThirdParty/jom | prepare.py:500-505 |
| Qt | x64 default 5.15.19; Qt6 optional 6.11.1 через prepare.py qt6 | Telegram/build/qt_version.py |
| Дополнительно для полного installer pipeline | Inno Setup (iscc), 7-Zip/архиватор; подпись требует собственный SignTool/сертификат. Это не нужно для голого out/Release/Splashgram.exe, но нужно для setup.exe | Telegram/build/setup.iss, Telegram/build/build.bat |

Проверка текущего PATH: Git 2.53.0.windows.2 и Python 3.12.10 найдены; CMake, Ninja, Perl, NASM, MSBuild/cl, Inno Setup, dotnet и vswhere не найдены. Visual Studio/Build Tools в PATH не обнаружены. Python 3.12 не заменяет документированный Python 3.10 для prepare.py; поставить 3.10 side-by-side и запускать его из Native Tools Prompt. В документации есть терминологическое расхождение: Visual Studio указана как 2026/v145, а обязательный target toolset и vcvars_ver остаются v143/14.44; ориентироваться на установленный MSVC v143 и -vcvars_ver=14.44.

API: TDESKTOP_API_ID и TDESKTOP_API_HASH передаются в configure.bat/CMake compile definitions. Их не хранить в git и не печатать в логи CI; использовать GitHub Actions secrets. В исходном docs сейчас стоят публичные тестовые значения, их нельзя переносить в Splashgram Release.

### Диск

На момент аудита C: имеет 83.90 GiB свободного места. Полный рекурсивный checkout занимает около 0.24 GiB, .git около 0.76 GiB; GitHub API оценивает основной репозиторий в 307067 KB. Размеры подмодулей в API не дают полной картины (часть URL/истории недоступна через этот endpoint), а build outputs в эти цифры не входят.

В документации нет hard minimum. Исторический Windows workflow AyuGram специально удалял *.pdb/*.pch/*.obj и в commit 0116f098f8 указывал, что cache должен помещаться в 10 GB. Для практического билда x64 рекомендую иметь не менее 60 GiB свободного места перед первым prepare; 40 GiB — нижний рабочий порог после очистки debug intermediates. Для одновременных Debug+Release, x86/ARM64 или Qt5+Qt6 закладывать 80-100 GiB. Текущих 83.90 GiB достаточно для одного x64 цикла с очисткой, но запас небольшой.

## GitHub Actions и локальный билд

- В текущем dev нет .github/workflows; GitHub API для репозитория возвращает total_count=0. Поэтому встроенного Release workflow, который можно запустить сейчас, нет.
- Исторический workflow удален коммитом 5a015888d4. Он запускал windows-latest, checkout с submodules, кеш Libraries, prepare.py skip-release и только Debug-сборку; артефакты были Telegram.exe/Updater.exe. Он не формировал Release и не был Splashgram-aware.
- Локальный путь после единственного prepare: configure.bat x64 с собственными defines, затем cmake --build ..\out --config Release --parallel или Visual Studio Build Telegram Release. Он дает полный контроль над API, подписью и отладкой и не зависит от cache/quota.
- CI после создания нового workflow будет стабильнее для повторяемых чистых Release-сборок при кэше Libraries, изолирует секреты и не занимает локальный диск. Первый прогон без cache дольше и может упереться в cache-size/runner timeout; потребуется явно добавить Release, secrets, artifact upload, новые имена Splashgram и проверку хэшей.

Рекомендация: для первого ребрендингового цикла использовать локальный x64 build (сначала prepare, затем Debug smoke test и Release), а после фиксации идентификаторов добавить отдельный windows-2026 Release workflow с cache key по HEAD/prepare.py/SDK, API secrets и артефактами. Не считать исторический workflow готовым релизным конвейером.

## План ребрендинга

1. Зафиксировать продуктовые значения: Splashgram, splashgram, bundle/AUMID/XDG id, publisher, домен обновлений, GitHub/Crowdin/Telegram usernames и политику совместимости с профилем AyuGram.
2. Сделать identity pass: root/Telegram CMake, version.h, output_name, Windows rc/Updater rc, AppUserModelId, setup.iss, AppX, XDG files, updater/startup paths. Согласовать Telegram.exe против Splashgram.exe во всех build.bat/setup.iss переменных; сейчас эти файлы используют разные имена.
3. Заменить UI/localization strings и AyuGram URLs в SourceFiles/ayu, lang.strings, settings/about/links. Ключи ayu_* и каталог ayu переименовывать только отдельным механическим коммитом с полным пересбором generated translation/style files.
4. Заменить icon256.ico, variant app_icon.ico, PNG/SVG и при необходимости mac assets; проверить ресурсный qrc и taskbar reload.
5. Добавить миграцию профилей/ярлыков AyuGram -> Splashgram, новый updater endpoint и signing/installer identity. Проверить чистую установку, обновление поверх AyuGram, single-instance, startup, taskbar pin, uninstall.
6. Собрать x64 Debug и Release, проверить отсутствие старых identity strings командой rg, проверить VERSIONINFO/AUMID/иконку у exe и запустить smoke tests. После этого вынести Release в Actions.

## Команды проверки после изменений

    git submodule update --init --recursive
    rg -n -i --hidden --glob '!.git/**' --glob '!Telegram/ThirdParty/**' 'AyuGram|ayugram|com\.ayugram|one\.ayugram'
    configure.bat x64 -D TDESKTOP_API_ID=%SPLASHGRAM_API_ID% -D TDESKTOP_API_HASH=%SPLASHGRAM_API_HASH%
    cmake --build ..\out --config Release --parallel

Отчёт содержит исходный снимок аудита; после него был выполнен отдельный implementation pass. API credentials в репозитории не добавлялись.

## Implementation pass

После аудита внесен рабочий ребрендинговый проход: literal AyuGram/ayugram в исходниках, CMake, ресурсах и скриптах заменены на Splashgram/splashgram; изменены AppId/AUMID/Inno GUID; добавлены Splashgram AppDataFolderName, SplashgramForcePortable и SplashgramAlpha/Beta data markers; Windows data теперь идет в %APPDATA%\\Splashgram, а Ayu settings/database/languages получают отдельные имена внутри tdata. Старые Telegram/AyuGram каталоги не мигрируются и не перезаписываются.

Иконки перевязаны через переименованные каталоги Telegram/Resources/art/splashgram и Telegram/Resources/icons/splashgram; qrc и C++ paths проверены, все 32 qrc references разрешаются. Графическое содержимое существующих ico/svg/png сохранено, потому что отдельный макет Splashgram в задаче не предоставлен.

Оставшиеся AyuGram/ayugram совпадения намеренные: URLs источников в .gitmodules, комментарии/alias внутри зафиксированных сторонних подмодулей и upstream-compatible protocol names. Оставшиеся TelegramDesktop/org.telegram строки относятся к webview API, Telegram protocol compatibility или историческому cleanup старых Linux files.

Проверки после изменений: git diff --check, Python AST parse для измененных .py, XML parse AppX/qrc/metainfo, проверка существования всех qrc source paths. Полный CMake/Release build не запускался: в текущем PATH нет CMake, Ninja, MSVC/MSBuild и Windows SDK.
