# DIY VGA Graphics Card Concept (Vero Board Prototype)

## Overview
A shrine‑safe VGA graphics card built on vero board using:
- SPI GPIO expanders (one per channel)
- R‑2R resistor ladders (DACs for analog RGB + monochrome)
- Sync stabilization circuitry (HSYNC + VSYNC buffers)

## Color Depth
- 4 bits per channel (RGB) → 16 levels each → 4096 colors total
- 4‑bit monochrome channel → 16 grayscale levels
- Combiner circuitry → merges monochrome with RGB when needed

## Block Diagram (Textual)

[MCU / Pi Pico / STM32]
        |
        |--- SPI Bus -------------------------
        |                                     |
   [SPI Expander R] --> [R‑2R Ladder] --> VGA Red
   [SPI Expander G] --> [R‑2R Ladder] --> VGA Green
   [SPI Expander B] --> [R‑2R Ladder] --> VGA Blue
   [SPI Expander M] --> [R‑2R Ladder] --> Monochrome
                                        |
                                        +--> Combiner --> VGA RGB (overlay)

[MCU GPIO] --> HSYNC --> [Buffer/Schmitt Trigger] --> VGA HSYNC
[MCU GPIO] --> VSYNC --> [Buffer/Schmitt Trigger] --> VGA VSYNC

## Key Notes
- R‑2R ladders: 4 resistors per channel, precision values for clean analog output.
- SPI expanders: e.g., MCP23S17 or similar, one per channel.
- Sync stabilization: Schmitt triggers or logic buffers to ensure stable high/low pulses.
- Monochrome combiner: analog switch or resistor summing network to overlay grayscale.

## Build Roadmap
1. Prototype one channel (Red) with 4‑bit R‑2R ladder.
2. Add HSYNC + VSYNC generation and stabilization.
3. Expand to full RGB (3 channels).
4. Add monochrome channel + combiner.
5. Test at low resolution (e.g., 320×240), then refine toward 640×480.

## Outcome
- RGB output: 4096 colors
- Monochrome output: 16 grayscale levels
- Stable sync signals: clean VGA display lock
- Shrine‑safe vero board prototype: modular, hackable, expandable
