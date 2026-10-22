# Changan E-Star DBC File

CAN bus database (DBC) file for the **Changan E-Star** electric vehicle.

## Overview

This DBC file defines the CAN bus messages and signals observed on a Changan E-Star. It can be used with tools such as:

- [cantools](https://github.com/cantools/cantools)
- SavvyCAN
- BusMaster
- Vector CANdb++
- python-can

## Nodes (ECUs)

| Node | Description |
|------|-------------|
| `Driving` | On while driving |
| `Always` | Always on, even while parking |
| `Acceories` | Doors and lights |
| `Battery` | Battery management |
| `A/C` | Air conditioning (defined, no messages yet) |

## Messages

### 465 (0x1D1) — `First`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Accelerator_Position` | 47 | 8 | Motorola (BE) | Unsigned | 0.393701 | 0 | % | 0–100 |
| `Brake_Switch` | 55 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–100 |

**Brake Switch value table:**

| Raw | Meaning |
|-----|---------|
| 0 | Off |
| 64 | On |

---

### 674 (0x2A2) — `Power`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Power_Consumption` | 55 | 16 | Motorola (BE) | Unsigned | 0.0004 | 0 | kW | 0–1 |
| `Drive_Mode` | 31 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |

**Drive Mode value table:**

| Raw | Meaning |
|-----|---------|
| 9 | S_B- |
| 17 | B- |
| 26 | B+ |
| 52 | Long_Milage |

---

### 648 (0x288) — `Acceories`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Doors` | 23 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |
| `Lights` | 15 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |

**Doors value table (bitmask):**

| Raw | Meaning |
|-----|---------|
| 8 | Back Door Open |
| 16 | RR Door Open |
| 32 | RL Door Open |
| 40 | RL + Back Door Open |
| 56 | RR + RL + Back Door Open |
| 64 | FR Door Open |
| 128 | FL Door Open |
| 184 | FL + RR + RL + Back Door Open |
| 192 | FL + FR Door Open |
| 208 | FL + FR + RR Door Open |
| 240 | FL + FR + RL + RR Door Open |
| 248 | All Doors Open |

**Lights value table:**

| Raw | Meaning |
|-----|---------|
| 16 | Right Signal Blink |
| 64 | Left Signal Blink |
| 80 | Hazard Blink |

---

### 520 (0x208) — `Wheel_Speed`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Wheel_Speed_RR` | 7 | 16 | Motorola (BE) | Unsigned | 0.06 | 0 | km/h | 0–1 |
| `Wheel_Speed_RL` | 23 | 16 | Motorola (BE) | Unsigned | 0.06 | 0 | km/h | 0–1 |
| `Wheel_Speed_FR` | 39 | 16 | Motorola (BE) | Unsigned | 0.06 | 0 | km/h | 0–1 |
| `Wheel_Speed_FR7` | 55 | 16 | Motorola (BE) | Unsigned | 0.06 | 0 | km/h | 0–1 |

---

### 804 (0x324) — `Coolant`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Coolant_Temp` | 15 | 8 | Motorola (BE) | Unsigned | 0.5556 | -17.7778 | °C | 0–1 |

---

### 616 (0x268) — `Gear_Position`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Gear_Position` | 15 | 16 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |

**Gear Position value table:**

| Raw | Meaning |
|-----|---------|
| 16 | N (Neutral) |
| 283 | S (Sport) |
| 2329 | R (Reverse) |
| 2586 | P (Park) |
| 2843 | D (Drive) |

---

### 658 (0x292) — `Drive_Mode`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Drive_Mode` | 31 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |

**Drive Mode value table:**

| Raw | Meaning |
|-----|---------|
| 9 | S_B- |
| 17 | B- |
| 26 | B+ |
| 52 | Long_Milage |

---

### 384 (0x180) — `Steering_Angle`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Steering_Angle` | 7 | 16 | Motorola (BE) | Signed | 0.1 | 0 | ° | 0–1 |

---

### 952 (0x3B8) — `Battery_Voltage`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Battery_Voltage` | 7 | 16 | Motorola (BE) | Unsigned | 0.1 | 0 | V | 0–1 |

---

### 2147484338 (0x80000072) — `Battery`

| Signal | Start Bit | Length | Byte Order | Sign | Factor | Offset | Unit | Range |
|--------|-----------|--------|------------|------|--------|--------|------|-------|
| `Battery_SOC` | 63 | 8 | Motorola (BE) | Unsigned | 0.5 | 0 | % | 0–100 |
| `Remaining_Charge_Time` | 55 | 8 | Motorola (BE) | Unsigned | 1 | 0 | min | 0–100 |
| `Charger_Plugged?` | 47 | 8 | Motorola (BE) | Unsigned | 1 | 0 | — | 0–1 |

**Charger Plugged value table:**

| Raw | Meaning |
|-----|---------|
| 0 | No |
| 32 | Yes |

## Usage

### Python (cantools)

```python
import can
import cantools

db = cantools.database.load_file('Changan_E-Star.dbc')

bus = can.interface.interface('socketcan', channel='can0')

while True:
    msg = bus.recv()
    try:
        decoded = db.decode_message(msg.arbitration_id, msg.data)
        print(f"0x{msg.arbitration_id:X}: {decoded}")
    except KeyError:
        pass  # Message not in DBC
```

### Decode a single frame

```python
import cantools

db = cantools.database.load_file('Changan_E-Star.dbc')
msg = db.get_message_by_name('Battery_SOC')
# or decode by ID:
decoded = db.decode_message(2147484338, bytes.fromhex('...'))
```

## Disclaimer

This DBC file is reverse-engineered and provided as-is for educational and research purposes. Use at your own risk. Always verify signal values against your vehicle before making any decisions based on this data.

## Contributing

Contributions are welcome! If you discover additional messages or signals, please open a pull request or issue.

## License

This project is open source. See the repository for license details.
