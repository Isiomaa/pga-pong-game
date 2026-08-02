# pga-pong-game

# FPGA Pong Game — 4-Way Moving Paddle

A fully functional Pong game implemented on an FPGA using VHDL, with real-time graphics rendered directly to a VGA display and paddle movement controlled by onboard buttons.

## Overview

This project extends a basic Pong game starter into a 4-way controlled paddle system — the paddle can move up, down, left, and right in response to button presses, with all motion synchronized to the display's refresh tick and constrained within the playable game area.

Built for EECE 412: Advanced Digital Systems Design Lab at Howard University, targeting a **Nexys A7-100T** FPGA board.

## How It Works

The design is split across three VHDL modules:

- **`vga_sync`** — generates the timing signals (horizontal/vertical sync, pixel tick, blanking) required to drive a standard VGA display.
- **`pong_graph_st`** — contains the game logic: paddle position tracking, boundary checking, and pixel-level rendering of the paddle against the game field.
- **`pong_top_st`** — top-level module that ties the display timing and game logic together and maps them to the board's physical I/O.

Paddle movement is handled by dedicated processes that check button state on every refresh tick and update the paddle's position if it stays within the playable boundaries — preventing it from moving off-screen in any direction.

The `.xdc` constraint file maps the design's ports to physical FPGA pins: VGA RGB output to the board's VGA connector, button inputs to the four directional controls, and status signals (pixel tick, blanking, sync) to onboard LEDs for debugging.

## Tech Stack

- **Language:** VHDL
- **Hardware:** Nexys A7-100T FPGA
- **Toolchain:** Xilinx Vivado (synthesis, implementation, bitstream generation)
- **Output:** VGA display

## Status

Verified working on physical hardware — paddle responds correctly to all four directional inputs with real-time VGA output.
