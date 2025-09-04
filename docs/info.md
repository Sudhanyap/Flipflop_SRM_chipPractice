## How it works

This project implements a **D Flip-Flop (DFF)** using standard digital logic gates.

The **D Flip-Flop** captures the value of the `D` input on the **rising edge of the clock (CLK)** and holds it stable at the output `Q` until the next rising edge.

If a **reset (RST)** input is included, setting `RST` high will **clear the output `Q` to 0 asynchronously**.

The circuit is built using **standard cells from the SkyWater 130nm library** and is designed to run on TinyTapeout hardware.

### Logic behavior

| CLK | RST | D | Q (Next State) |
|-----|-----|---|----------------|
| ↑   |  0  | 0 | 0              |
| ↑   |  0  | 1 | 1              |
| ↑   |  1  | X | 0              |

Where `↑` represents a **rising edge of the clock**.

---

## How to test

### Connect Inputs:
- `CLK` → Clock signal (start with **10 MHz or lower**).
- `D` → Data input (manual switch or external signal).
- `RST` → Reset signal (active **HIGH**).

### Procedure:
1. Hold `RST = 1` to **clear the output** (`Q = 0`).
2. Release `RST = 0` to **enable normal operation**.
3. Provide a **clock signal** on `CLK`.
4. Change `D` **before the rising edge** of `CLK`.
5. Observe `Q`:
   - At each rising edge, `Q` will **take the value of `D`**.

### Expected Output:
- When the clock rises, `Q` **follows `D`** and stays constant until the next rising edge.
- When `RST` is **high**, `Q` is **forced to 0**.

---

## External hardware

For testing on the TinyTapeout board, you may use the following external hardware:

### Clock source:
- A **10 MHz signal generator**, or  
- The **default TinyTapeout onboard clock**.

### Input switches:
- One switch for `D`.
- One switch for `RST`.

### Output indicator:
- **LED connected to `Q`** to visualize the output state.
