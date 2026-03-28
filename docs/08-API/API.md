---
title: HMI API
---

## Application Programming Interface
Overview

### Subsystem Identification

| Subsystem       | Identifier | Person               |
|-----------------|------------|----------------------|
| HMI             | h          | Jacob                |
| Communication   | c          | Cris                 |
| Wheels          | w          | Asadbek              |
| Pressure/Accel. | p          | Tyler                |
| Arm             | a          | Caleb                |
| Metal Detector  | m          | Aaron                |
| Temp/Humidity   | t          | Isaiah               |
| Broadcast       | X          | System-Wide Messaging|

### Message Data Types

| Description               | Prefix |
|----------------------------|--------|
| String (ASCII char array)  | S:     |
| Integer (8 Bit)            | I:     |
| Float (32 Bit)             | F:     |

## Sent Messages

### Message Type 1 -- Start Broadcast

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–11 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | ST:       | S:        | Start;     |
| Min        |           |           | Start;     |
| Max        |           |           | Start;     |
| Example    | ST:       | S:        | Start;     |

### Message Type 3 -- Wheel Drive Mode

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7              |
|------------|-----------|-----------|------------------------|
|            | Name      | Type      | Data                   |
|            | WD:       | S:        | F; / B; / R; / L;      |
| Min        |           |           | F; / B; / R; / L;      |
| Max        |           |           | F; / B; / R; / L;      |
| Example    | WD:       | S:        | F;                     |

### Message Type 4 -- Accelerometer Sensor Read

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | AR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | AR:       | S:        | Read;      |

### Message Type 5 -- Arm Drive Mode

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7              |
|------------|-----------|-----------|------------------------|
|            | Name      | Type      | Data                   |
|            | AD:       | S:        | U; / D; / R; / L;      |
| Min        |           |           | U; / D; / R; / L;      |
| Max        |           |           | U; / D; / R; / L;      |
| Example    | AD:       | S:        | U;                     |

### Message Type 6 -- Temperature Sensor Read

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | TR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | TR:       | S:        | Read;      |

### Message Type 6 -- Temperature Unit Change

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7  |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | CU:       | S:        | C; / F;    |
| Min        |           |           | C; / F;    |
| Max        |           |           | C; / F;    |
| Example    | CU:       | S:        | C;         |

### Message Type 7 -- Humidity Sensor Read

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | HR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | HR:       | S:        | Read;      |

### Message Type 8 -- Metal Detector Read

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | MR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | MR:       | S:        | Read;      |

## Received Messages

### Message Type 4 -- Accelerometer Value

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | AV:       | F:        | ####;      |
| Min        |           |           | 0.0;       |
| Max        |           |           | 100.0;     |
| Example    | AV:       | F:        | 80.0;      |

### Message Type 5 -- Arm Position Acknowledge

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7 |
|------------|-----------|-----------|-----------|
|            | Name      | Type      | Data      |
|            | AA:       | I:        | #;        |
| Min        |           |           | -180;     |
| Max        |           |           | 180;      |
| Example    | AA:       | I:        | 90;       |

### Message Type 5 -- Arm Status

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–12                     |
|------------|-----------|-----------|--------------------------------|
|            | Name      | Type      | Data                           |
|            | AS:       | S:        | Idle; / Moving; / Done; / Halted; |
| Min        |           |           | Idle; / Moving; / Done; / Halted; |
| Max        |           |           | Idle; / Moving; / Done; / Halted; |
| Example    | AS:       | S:        | Moving;                        |

### Message Type 5 -- Arm Error

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7 |
|------------|-----------|-----------|-----------|
|            | Name      | Type      | Data      |
|            | AE:       | I:        | #;        |
| Min        |           |           | 0;        |
| Max        |           |           | 3;        |
| Example    | AE:       | I:        | 1;        |

### Message Type 6 -- Temperature Value and Unit

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 | Bytes 11–13 | Bytes 14–15 | Bytes 16–17 |
|------------|-----------|-----------|------------|--------------|--------------|--------------|
|            | Name      | Type      | Data       | Name         | Type         | Data         |
|            | TR:       | F:        | ####;      | TT:          | S:           | C; / F;      |
| Min        |           |           | -50.0;     |              |              | C; / F;      |
| Max        |           |           | 200.0;     |              |              | C; / F;      |
| Example    | TR:       | F:        | 76.5;      | TT:          | S:           | F;           |

### Message Type 7 -- Humidity Value

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | HV:       | F:        | ####;      |
| Min        |           |           | 0.0;       |
| Max        |           |           | 100.0;     |
| Example    | HV:       | F:        | 31.2;      |

### Message Type 8 -- Metal Detector Value

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7  |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | MD:       | S:        | T; / F;    |
| Min        |           |           | F;         |
| Max        |           |           | T;         |
| Example    | MD:       | S:        | T;         |














