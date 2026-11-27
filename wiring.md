# Wiring / Bekötés

Based on the supplied installation guide; verify on each unit. Wire colours are installation-specific.

| AUX wire / vezeték | BSS138 HV side | BSS138 LV side | ESP32 |
| --- | --- | --- | --- |
| Yellow / sárga TX | HV1 | LV1 | GPIO16 RX |
| White / fehér RX | HV2 | LV2 | GPIO17 TX |
| Red / piros +5 V | HV | — | VIN (separate 5 V branch / külön tápág) |
| Black / fekete GND | GND | GND | GND |
| ESP32 3.3 V supply | — | LV | 3V3 |

Channels 3 and 4 are unused. All grounds are common. HV and LV power rails must not be joined. See the PDF for electrical safety and optional-switch limitations.

A 3. és 4. csatorna üres. Minden GND közös. A HV és LV tápágakat tilos összekötni. A biztonsági előírásokat és az opcionális kapcsoló korlátait lásd a PDF-ben.
