---
title: HMI API
---

## Application Programming Interface

As the Human-Machine Interface subsystem, it is my responsibility to package and send instructions to nearly every other subsystem so that the user can control and utilize the features of the CropSCOUT. On this page, you can view all the messages I send and my subsystem receives. Every message fits within the packet specifications and is laid out by the class protocol, including prefix, suffix, source and destination IDs, and a message of less than 58 bytes.

### Subsystem Identification

The following table is the identifier for each subsystem from our team. These IDs will be used in the packaging of every message as the source or destination.

| Subsystem       | Identifier | Person               |
|-----------------|------------|----------------------|
| HMI             | h          | Jacob                |
| Communication   | c          | Cris                 |
| Wheels          | w          | Asadbek              |
| Pressure/Accelerometer | p          | Tyler                |
| Front Arm             | a          | Caleb                |
| Metal Detector  | m          | Aaron                |
| Temperature/Humidity   | t          | Isaiah               |
| Broadcast       | X          | System-Wide Messaging|

### Message Data Types

The following table is the types of data we will be using in each message. As you look at the messages on this page, please be aware of what each message abbreviation means.

| Description               | Prefix |
|----------------------------|--------|
| String (ASCII char array)  | S:     |
| Integer (8 Bit)            | I:     |
| Integer (16 Bit)           | IL:    |
| Float (32 Bit)             | F:     |

## Sent Messages

Most of the messages being sent are simply prompting the respective subsystem, but there are also the drive messages, which use strings, that will be assigned to buttons, to allow the user to directly control the wheels and arm.

### Message Type 1 -- Start Broadcast

* Broadcast: Everyone will turn on their debug LED and begin their systems
* When I receive it back, begin my system and tell the user that Start was successful
* If I don’t receive after 30 or so seconds, tell the user that Start was unsuccessful

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–11 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | ST:       | S:        | Start;     |
| Min        |           |           | Start;     |
| Max        |           |           | Start;     |
| Example    | ST:       | S:        | Start;     |

### Message Type 3 -- Wheel Drive Mode

* Allows the user to directly control the rover using the D-Pad on the HMI board.

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7              |
|------------|-----------|-----------|------------------------|
|            | Name      | Type      | Data                   |
|            | WD:       | S:        | F; / B; / R; / L;      |
| Min        |           |           | F; / B; / R; / L;      |
| Max        |           |           | F; / B; / R; / L;      |
| Example    | WD:       | S:        | F;                     |

### Message Type 4 -- Accelerometer Sensor Read

* Prompts the Accelerometer Sensor to send its reading

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | AR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | AR:       | S:        | Read;      |

### Message Type 5 -- Arm Drive Mode

* Allows the user to directly control the front arm using the D-Pad on the HMI board.

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7              |
|------------|-----------|-----------|------------------------|
|            | Name      | Type      | Data                   |
|            | AD:       | S:        | U; / D; / R; / L;      |
| Min        |           |           | U; / D; / R; / L;      |
| Max        |           |           | U; / D; / R; / L;      |
| Example    | AD:       | S:        | U;                     |

### Message Type 6 -- Temperature Sensor Read

* Prompts the Temperature Sensor to send its reading

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | TR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | TR:       | S:        | Read;      |

### Message Type 6 -- Temperature Unit Change

* Tells the Temperature Sensor to change its current unit of measurement

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7  |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | CU:       | S:        | C; / F;    |
| Min        |           |           | C; / F;    |
| Max        |           |           | C; / F;    |
| Example    | CU:       | S:        | C;         |

### Message Type 7 -- Humidity Sensor Read

* Prompts the Humidity Sensor to send its reading

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | HR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | HR:       | S:        | Read;      |

### Message Type 8 -- Metal Detector Read

* Prompts the Metal Detector to send its reading

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | MR:       | S:        | Read;      |
| Min        |           |           | Read;      |
| Max        |           |           | Read;      |
| Example    | MR:       | S:        | Read;      |

## Received Messages

The received messages are mainly the returned sensor data, but there are also a few error and acknowledgement messages.

### Message Type 4 -- Accelerometer Value

* Receives the Accelerometer Sensor Value as a Float

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | AV:       | F:        | ####;      |
| Min        |           |           | 0.0;       |
| Max        |           |           | 100.0;     |
| Example    | AV:       | F:        | 80.0;      |

### Message Type 5 -- Arm Position Acknowledge

* Receives the position achieved by the front arm as an int16 value.

|            | Bytes 1–3 | Bytes 4–6 | Bytes 7–8 |
|------------|-----------|-----------|-----------|
|            | Name      | Type      | Data      |
|            | AA:       | IL:       | #;        |
| Min        |           |           | -180;     |
| Max        |           |           | 180;      |
| Example    | AA:       | IL:       | 90;       |

### Message Type 5 -- Arm Status

* Receives the current status from the arm subsystem

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–12                     |
|------------|-----------|-----------|--------------------------------|
|            | Name      | Type      | Data                           |
|            | AS:       | S:        | Idle; / Moving; / Done; / Halted; |
| Min        |           |           | Idle; / Moving; / Done; / Halted; |
| Max        |           |           | Idle; / Moving; / Done; / Halted; |
| Example    | AS:       | S:        | Moving;                        |

### Message Type 5 -- Arm Error

* Receives the current error value from the arm subsystem

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7 |
|------------|-----------|-----------|-----------|
|            | Name      | Type      | Data      |
|            | AE:       | I:        | #;        |
| Min        |           |           | 0;        |
| Max        |           |           | 3;        |
| Example    | AE:       | I:        | 1;        |

### Message Type 6 -- Temperature Value and Unit

* Receives the Temperature Sensor Value as a Float and the current unit of measurement as a string

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 | Bytes 11–13 | Bytes 14–15 | Bytes 16–17 |
|------------|-----------|-----------|------------|--------------|--------------|--------------|
|            | Name      | Type      | Data       | Name         | Type         | Data         |
|            | TV:       | F:        | ####;      | TT:          | S:           | C; / F;      |
| Min        |           |           | -50.0;     |              |              | C; / F;      |
| Max        |           |           | 200.0;     |              |              | C; / F;      |
| Example    | TV:       | F:        | 76.5;      | TT:          | S:           | F;           |

### Message Type 7 -- Humidity Value

* Receives the Humidity Sensor Value as a Float

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–10 |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | HV:       | F:        | ####;      |
| Min        |           |           | 0.0;       |
| Max        |           |           | 100.0;     |
| Example    | HV:       | F:        | 31.2;      |

### Message Type 8 -- Metal Detector Value

* Receives the Metal Detector Value as a String

|            | Bytes 1–3 | Bytes 4–5 | Bytes 6–7  |
|------------|-----------|-----------|------------|
|            | Name      | Type      | Data       |
|            | MD:       | S:        | T; / F;    |
| Min        |           |           | F;         |
| Max        |           |           | T;         |
| Example    | MD:       | S:        | T;         |














