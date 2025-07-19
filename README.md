# Password-authentication-system
Password Authentication FSM
# 🔐 Password Authentication System (RTL Design)

A synthesizable RTL module that authenticates a 4-digit password using a finite state machine (FSM). Designed from a hardware security perspective to demonstrate input handling, verification logic, and lockout mechanisms.

---

## 💡 Overview

This project simulates a basic password authentication system using Verilog HDL. The module compares user-entered digits against a stored password and grants access on successful match. Failed attempts are tracked and can trigger a system lockout.

---

## 🧩 RTL Architecture

### FSM States
| State    | Description                   |
|----------|-------------------------------|
| `IDLE`   | System waits for password input |
| `INPUT`  | Collects 4-digit user input     |
| `VERIFY` | Compares input with stored password |
| `SUCCESS`| Grants access if match         |
| `FAIL`   | Denies access and increments fail counter |
| `LOCKED` | Locks system after 3 failed attempts |

### Stored Password
- Default: `1, 2, 3, 4` (can be modified in RTL code)

### Inputs
- `clk` : Clock signal
- `rst` : Reset signal
- `user_input [3:0]` : 4-bit digit input
- `enter` : Input strobe

### Outputs
- `access_granted` : High when authentication succeeds
- `locked` : High after multiple failed attempts

---

## 🔧 Files

| File              | Description                     |
|-------------------|---------------------------------|
| `pass_auth.v`      | RTL Verilog code                |
| `pass_auth_tb.v`   | Improved testbench with task-based input |
| `test.vcd`         | Waveform file (generated during simulation) |

---

## 🧪 Simulation Strategy
# Compile
iverilog -o pass_auth_tb src/pass_auth.v testbench/pass_auth_tb.v

# Run
vvp pass_auth_tb

# View waveform
gtkwave test.vcd
### Simulator Used:
- ModelSim / Vivado / GTKWave

### Testbench Scenarios:
- ✅ Correct password: grants access
- ❌ Incorrect password: denies access
- 🔒 Lockout after 3 wrong attempts
- 🔄 Reset and retry post lockout

### Sample Waveform Output
> Includes transitions through `IDLE → INPUT → VERIFY → SUCCESS/FAIL/LOCKED`

---

## 📈 Future Improvements

- Integrate password hashing (e.g., SHA-256)
- UART interface for input/output
- Random password generation
- UVM-based testbench

---

## 📚 References

- RTL FSM design patterns
- [Three-Level Password Authentication](https://www.jetir.org/papers/JETIR2310609.pdf)
- [Graphical Passwords in RTL](https://www.ijert.org/research/graphical-password-authentication-system-IJERTV2IS90953.pdf)

---

## 🛠️ Author

**Jayant** — RTL Design Engineer  
Passionate about secure hardware systems and VLSI innovation.

---

## 🚀 License

This project is open-source. Feel free to fork, modify, and explore!

