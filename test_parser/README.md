# Link map files for parser testing

This directory contains link map files which should be correctly
handled/parsed by parser in `mapfile.py`.


## legacy directory

This directory contains map files used for legacy version testing.


## common_input_section.map

Generated from `examples/bluetooth/blufi` for esp32s3 target. This map contains
`COMMON` input sections. Test for https://github.com/espressif/esp-idf-size/issues/1


## region_overflow.map

Generated from `examples/get-started/hello_world` for esp32 target with
`CONFIG_ESP32_USE_FIXED_STATIC_RAM_SIZE=y` and `CONFIG_ESP32_FIXED_STATIC_RAM_SIZE=0x0`.
The linkage fails because `dram0_0_seg` is not big enough and there is no ELF file
generated.


## output_section_alignment.map

Generated from `examples/wifi/iperf` for esp32 target. Output section can have
alignment/fill at the beginning, prior the first input section.


## fill_input_section.map

Input section may be followed by \*fill\*, which was not accounted because
of bug in the parser, where it was not correctly setting "in_input_section"
state.


## explicit_bytes.map

Generated from `examples/get-started/hello_world` for esp32 target, with
the updated linker script, which adds `LONG(0)` output section data.
https://sourceware.org/binutils/docs/ld/Output-Section-Data.html.


## input_section_out_of_range.map

Generated from `examples/peripherals/lcd/mipi_dsi` for esp32p4 target.
The linker map might include an output section featuring an input section with
an address which is not within the output section range.


## empty_sections.map

Generated from `examples/get-started/hello_world` for esp32 target, with
the updated linker script, which adds empty sections.
https://github.com/espressif/esp-idf/commit/2b36636f6fb11e37671d384055db47ca2e0446ed
The linker map might include an output section without address and size.
