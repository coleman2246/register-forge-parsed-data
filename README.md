# RegForge Parsed Register Maps

Structured JSON register maps extracted from IC datasheets, ready for use in embedded development tools, code generators, and hardware abstraction layers.

Browse and interact with these register maps at **[regforge.dev](https://regforge.dev/browse)**.

## Structure

```
├── pdf/          # Extracted from PDF datasheets via LLM-powered parsing
├── svd/          # Imported from CMSIS-SVD XML definitions
├── manifest.json # Source metadata for PDF-parsed devices
└── README.md
```

## PDF-Parsed Files

Register maps extracted from manufacturer PDF datasheets using [RegForge](https://regforge.dev)'s Docling ML + multi-LLM extraction pipeline. Each file contains registers, fields, bit ranges, reset values, and descriptions verified against source document evidence.

**Naming**: `{device}_{provider}_{model}_{timestamp}.json`

**Supported vendors**: Analog Devices, Bosch Sensortec, Maxim, NXP, STMicroelectronics, Texas Instruments, and more.

## SVD-Imported Files

Register maps imported from [CMSIS-SVD](https://arm-software.github.io/CMSIS_5/SVD/html/index.html) XML definitions. These cover microcontroller families from STMicroelectronics (STM32), Espressif (ESP32), Raspberry Pi (RP2040/RP2350), Microchip (SAMD21/SAMR21), and Atmel (AVR).

**Naming**: `{device_slug}.json`

## JSON Schema

Each file contains a `RegisterMap` object:

```json
{
  "device": "Device Name",
  "vendor": "Manufacturer",
  "description": "Brief description",
  "source_type": "pdf" | "svd",
  "registers": [
    {
      "name": "REGISTER_NAME",
      "address": "0x00",
      "width": 8,
      "reset_value": "0x00",
      "description": "Register description",
      "fields": [
        {
          "name": "FIELD_NAME",
          "bits": "7:4",
          "access": "RW",
          "reset_value": "0x0",
          "description": "Field description"
        }
      ]
    }
  ],
  "peripherals": [ ... ],
  "metadata": { ... }
}
```

## License

The register definitions are derived from publicly available datasheets and CMSIS-SVD files. Refer to the original manufacturer documentation for authoritative specifications.
