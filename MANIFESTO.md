# 🧠 YODPS Manifesto

## 1. Certification and Language Choice
Production systems must comply with certification standards.  
For this reason, **C/C++** has been chosen as the primary development language, following **MISRA C/C++** guidelines and using a **qualified toolchain** aligned with **ISO 26262** requirements.  

No matter how convenient Python may be, the final implementations of business functions must be written in **C or C++** and **YODPS** is being developing to create and test them **as-is** on the target hardware.  

Other languages such as **Python**, **Rust**, and **Java** may be used for integration and data exchange with external systems — but **not** for safety-critical logic execution.  

---

## 2. Data Format and Serialization
Currently, there are **no officially certified serialization libraries** (such as Protocol Buffers, FlatBuffers, or Cap’n Proto).  
Therefore, **YODPS** uses a **binary array format representing plain C structs** as the standard for data exchange.  

Serialization is treated as an **optional** and **non-essential** operation, suitable only for non-critical use cases such as logging, inter-process communication, or integration with external tools.  

The binary format ensures:
- **Deterministic behavior**  
- **Zero-copy data transfer**  
- **Compatibility between modules without intermediate transformations**

Developers of **ADTF 2.x** already embraced this idea — one function produces a C struct, another consumes it.  
**YODPS** continues this approach, solving the fundamental problem of **data exchange between system modules** in a platform-agnostic way.  
If a subsystem uses a different data representation (for example, endianness or alignment),
the conversion is handled on that subsystem’s side, without affecting the performance or determinism of the rest of the system.

---

## 3. Architecture and Purpose
**YODPS** provides an abstraction layer designed to simplify:
- Development of business functions  
- Recording and replay of trace data  
- Data analysis and data-injection during testing  

Its foundation is a **publish-subscribe architecture**, proven to be the most reliable and scalable model for ADAS/AD systems and distributed frameworks.  

YODPS does **not** lock the developer to a specific transport or middleware.  
It preserves a **uniform data-exchange model**, allowing seamless transition between **ZeroMQ**, **SOME/IP**, **DDS**, or any other communication backend.  

---

## 4. Implementation and Platform
The base (developer-friendly) version of **YODPS** is built on the **ZeroMQ** messaging library and is fully **cross-platform**, supporting **Linux x64**, **ARM64**, **QNX**, and **Windows**.  

> **Core idea:**  
> Develop and debug business logic on a PC under Linux, Windows, or any POSIX-compatible OS, then run the exact same code on the target ECU.

Further adaptation is achieved by implementing platform-specific classes for the target environment — whether **bare-metal**, **RTOS**, or a proprietary **automotive OS**.  

This approach minimizes the gap between development and production, ensuring **predictable behavior** and **deterministic execution** from prototype to certified system.  

---

## 5. Typical Dataflow
**YODPS** supports flexible hybrid workflows:  you can **inject data from a PC into target systems (live injection)**, **record streams from the target to the PC** for offline analysis, and freely **mix live and replayed streams**. This enables **HIL/SIL setups** and mixed configurations where some components run on the **ECU** and others on **desktop**, without modifying production code or reducing performance of unaffected modules.

A typical **YODPS** dataflow follows a complete closed-loop cycle:

1. **Data acquisition** using built-in YODPS nodes such as **CAN/CAN-FD**, **UDP/TCP**, **V4L**, and other hardware or network interfaces.  
2. **Data processing** through user-defined **business functions**, wrapped as YODPS nodes. These can operate in both **live** and **replay** configurations.  
3. **Visualization** of raw and processed data, along with the output of business logic, through compatible viewers and analysis tools.  
4. **Control feedback** — sending actuator or system commands back into the environment using **CAN/CAN-FD** or **UDP/TCP** nodes.  
5. **Integration with simulators** such as **Gazebo**, **CarMaker**, or other virtual environments, either in **real-time processing** or through **trace replay** pipelines.  



This structure allows **YODPS** to act as a **unified middleware** for live data processing, offline analysis, and closed-loop testing — fully consistent with real-world automotive system behavior.  
