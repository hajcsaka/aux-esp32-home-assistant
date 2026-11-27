# AUX ESP32 → Home Assistant

Local control of an AUX air conditioner using ESP32, ESPHome and the [GrKoR AUX AC component](https://github.com/GrKoR/esphome_aux_ac_component).

Installation and documentation by **Attila Hajcsák, Hungary**. This repository documents a specific installation; it is not a replacement for the upstream component.

[Magyar leírás](README.hu.md)

## Installation guides

- [English guide (PDF)](AUX_ESP32_Integration_Guide_EN.pdf)
- [Magyar útmutató (PDF)](AUX_ESP32_Integracios_utmutato_HU.pdf)

Both guides include the wiring diagram, assembly photographs, configuration example and commissioning notes.

## Documented hardware

| Item | Model |
| --- | --- |
| Indoor unit | AUX Console Pro AMCO-H12/4R3DA-2 (2022) |
| Original Wi-Fi module | AUXWIFI0001-A1 / BroadLink BL3353-P |
| Controller | ESP-WROOM-32 development board, CH340 USB-C |
| Level converter | Four-channel BSS138 bidirectional module |
| Connection | Original five-pin connector, four populated wires |

The installer reports local control, bidirectional UART communication, temperature, mode and fan-speed adjustment without the original Wi-Fi module or manufacturer cloud.

## Configuration status

**This setup runs successfully on three AUX Console Pro AMCO-H12/4R3DA-2 units in my home. The standalone YAML example is based on my working bedroom configuration, with credentials replaced by ESPHome secret references. The PDFs contain an earlier configuration example; use [aux-ac.example.yaml](aux-ac.example.yaml) for the current configuration.** Compare it with your hardware and validate it with your ESPHome version before flashing. Tested ESPHome/Home Assistant versions and an upstream commit have not yet been recorded. The example references the upstream `master` branch, which can change.

Credentials are represented by `!secret` references. Keep real Wi-Fi passwords and API keys in a local `secrets.yaml`; never commit them.

Compatibility is documented only for the hardware above. Connector pinout, wire colours, voltage and available supply current must be checked on each unit.

## Electrical safety

Disconnect the air conditioner from mains before wiring. The circuit may not be isolated from mains: do not connect USB while the ESP32 is powered by the air conditioner. The documented arrangement uses 5 V at VIN/HV and 3.3 V at LV; do not apply 12 V or join the HV and LV supply rails. All grounds are common in this arrangement. See the full guide before assembly.

The optional VIN switch may not fully power down the ESP32 because data lines can backfeed power. It is not an isolation or safety switch.

## Magyar összefoglaló

A projekt egy AUX Console Pro klíma helyi Home Assistant-vezérlésének megvalósítását mutatja be ESP32 és ESPHome segítségével. A magyar PDF tartalmazza a bekötést, a szerelési fotókat és az üzembe helyezés leírását.

**A megoldás három azonos AUX Console Pro AMCO-H12/4R3DA-2 klímámon működik.** A külön YAML-fájl a működő hálószobai konfigurációmon alapul, a titkos adatokat `!secret` hivatkozások helyettesítik. A PDF-ek korábbi példát tartalmaznak; az aktuális konfiguráció az [aux-ac.example.yaml](aux-ac.example.yaml) fájlban található. A leírt bekötés nem tekinthető minden AUX-modellre érvényesnek. A biztonsági előírásokat a teljes útmutatóban olvasd el.

## Credits

- Hardware installation and guides: Attila Hajcsák.
- AUX ESPHome component: [GrKoR/esphome_aux_ac_component](https://github.com/GrKoR/esphome_aux_ac_component), distributed separately under its own license.

When reporting compatibility, include the exact indoor-unit model, controller board, ESPHome version and upstream component revision. Remove credentials and personal network details from any logs you share.

## Files you can use directly

- [Wiring diagram](wiring.svg) / [wiring table](wiring.md)
- [ESPHome example](aux-ac.example.yaml) — based on the owner’s working bedroom configuration, with credentials removed
- [Secrets template](secrets.example.yaml) — placeholders only

Copy `aux-ac.example.yaml` to your local ESPHome configuration, and copy `secrets.example.yaml` to `secrets.yaml`. Fill in your own credentials and a valid ESPHome API encryption key. Validate the configuration with your installed ESPHome release before flashing. No firmware binary is supplied.

![Wiring diagram](wiring.svg)

## Assembly photographs

Extracted from the Hungarian guide. File numbering is for reference and does not indicate assembly order. Pin labels and the wiring table take precedence over wire colours.

![Assembly view 1](assembly-1.jpg)
![Assembly view 2](assembly-2.jpg)
![Assembly view 3](assembly-3.jpg)
![Assembly view 4](assembly-4.jpg)

## Reuse and licensing

An explicit license for the original guides and photographs has not yet been selected by the author. Public availability alone is not an open-source license. The upstream component retains its own license; its source code is not included here.

## OTA compatibility

The bare `ota: encryption:` block is intentional: OTA inherits the API encryption key. Use a compatible ESPHome release; encrypted OTA is available from ESPHome 2026.9.0. For existing older firmware, follow the [official OTA migration instructions](https://esphome.io/components/ota/esphome/#enabling-encryption-on-an-existing-device). This sanitized example has not been independently compiled during publication.

## Questions

Open an [issue](https://github.com/hajcsaka/aux-esp32-home-assistant/issues) if you have a question. I spent a lot of time getting this working and am happy to help where I can. Include your model and ESPHome version, and remove passwords and API keys before sharing configuration or logs.

## OTA-kompatibilitás

Az üres OTA `encryption:` blokk szándékos: az API titkosítási kulcsát használja. A titkosított OTA ESPHome 2026.9.0-tól érhető el. Régebbi, már telepített firmware frissítésénél kövesd a [hivatalos átállási útmutatót](https://esphome.io/components/ota/esphome/#enabling-encryption-on-an-existing-device).

## Kérdések, segítség

Ha kérdésed van, nyiss egy [Issue-t](https://github.com/hajcsaka/aux-esp32-home-assistant/issues). Sok időmbe telt, mire összeállt a működő megoldás; szívesen segítek, amiben tudok. Írd meg a klíma pontos típusát és az ESPHome-verziót, de jelszót vagy API-kulcsot ne ossz meg.
