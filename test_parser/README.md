# Link map files for parser testing

This directory contains link map files which should be correctly
handled/parsed by parser in `mapfile.py`.


## common_input_section.map

Generated from `examples/bluetooth/blufi` for esp32s3 target. This map contains
`COMMON` input sections. Test for https://github.com/espressif/esp-idf-size/issues/1


## region_overflow.map

Generated from `examples/get-started/hello_world` for esp32 target with
`CONFIG_ESP32_USE_FIXED_STATIC_RAM_SIZE=y` and `CONFIG_ESP32_FIXED_STATIC_RAM_SIZE=0x0`.
The linkage fails because `dram0_0_seg` is not big enough and there is no ELF file
generated.

