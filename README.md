# FPGA Lab 2 — Decoders and Latch Inference

**Verilog · Decoders · Combinational Logic · Latch Inference**

Former repository name: `FPGA2`.

Six decoder exercises compare independent `if` statements, `if/else`, and `case` branches. Some variants deliberately retain a previous output to illustrate latch behavior. 译码器写法与锁存行为对比实验。

| Example | Implementation | Behavior |
| --- | --- | --- |
| [a1](examples/decoder_case_a1.v) | Separate `if` statements | One-hot decoding for all eight binary inputs |
| [a2](examples/decoder_case_a2.v) | `if/else` chain | One-hot decoding for all eight binary inputs |
| [b1](examples/decoder_case_b1.v) | Incomplete `case` | Addresses 6 and 7 retain the previous output |
| [b2](examples/decoder_case_b2.v) | Complete `case` with default | One-hot decoding with a default output |
| [c1](examples/decoder_case_c1.v) | Partial decoder, `out = out` | Addresses outside 0–2 retain the previous output |
| [c2](examples/decoder_case_c2.v) | Partial decoder with default | Addresses outside 0–2 output zero |

Each file contains its RTL module and the original testbench. The latch examples are kept for comparison; they are not interchangeable combinational decoders. X/Z input behavior also depends on the coding style.

## Run an existing testbench

Requires Icarus Verilog (`iverilog` and `vvp`):

```bash
mkdir -p build
iverilog -g2012 -s tb_decoder_case_b2 -o build/decoder.vvp examples/decoder_case_b2.v
cd build
vvp -n decoder.vvp
```

Use the matching `tb_decoder_case_*` name for another example. The original testbenches print expected and actual values, and some generate VCD traces. Review their output: not every reported failure returns a failing process exit code. Synthesis reports are not included.

[FPGA lab index](https://github.com/chengmiao2005/FPGA-Labs) · [Original-to-current file map](docs/FILE_MAP.md)

[Validation record](docs/VALIDATION.md)
