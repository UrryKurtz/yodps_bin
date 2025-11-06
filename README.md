## YODPS — Yet One Distributed Processing System
© 2025 Yury Odnokurtsev / Urry Kurtz

**YODPS** is a high-performance, modular framework for distributed data acquisition, processing, visualization, and recording — designed as a flexible alternative to commercial automotive/robotic middleware solutions, where such systems exist.

---
## ✨ Features

**Communication layer** based on [ZeroMQ](https://github.com/zeromq/libzmq), supporting **TCP**, **IPC**, and **shared memory** transport, with or without a broker.

**Cross-platform**: x64 Linux & Windows, ARM64 Linux & QNX, Android, WebAssembly.

**Extensible viewer application** using SDL+rbfx and ImGui with next features:
  + Multi-camera video streaming
  + Creating and rendering 3D geometric objects and complex models in popular formats (OBJ, STL etc)
  + GUI overlay
  + Data viewer / plotter / generator
  + CAN/CANFD signal viewer
  + OBD2 param viewer
  + Simple Plugin API to extend functionality
  
**Default data acquisition nodes**:
  - PCAP/libtins (CAN/CANFD, UDP/TCP)
  - V4L2 cameras
  - Image/Video format converters
  - Audio/MIDI via ALSA/JACK Audio Connection Kit
  
**Recorder/Player**:
  - Foxglove studio MCAP
  - ADTF DAT v2.0 file format (using `adtf_file` library) 
  - PCAP

**Wanna know more?**: 
  - See the [MANIFESTO.md](MANIFESTO.md).
---
## 🚗 Deployment

YODPS target platforms include on-road and off-road vehicles, drones, marine vessels, locomotives, industrial machinery, specialized defense systems, including giant humanoid robots.

---
## Screenshots 

Now with docking.<br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_006.jpeg?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_006.jpeg?raw=true" width="25%">
</a>

Plugins: <br/><br/>
<b>Pub-Sub Test Plugin</b> sends/receives test messages. Very useful to check connections. <br/><br/>
<b>CAN Viewer Plugin</b> uses DBC files to show CAN messages and signals. <br/><br/>
<b>Data Viewer</b> Uses XML media descriptions to visualize structures. <br/><br/>
<b>Camera Plugin</b> Keeps presets for the virtual camera position. Creates a windows with additional 3D viewes.<br/><br/>
<b>GPS</b> shows OpenStreetMap. Optionally centers the map in the coordinates, received from gpsd daemon.<br/><br/>
<b>Video Streams</b> Shows video frames as a floating windows and/or as overlay sprites. <br/><br/>
<b>Polyline Viewer</b> has simple API to visualize any custom geometry data. 3D models, pointclouds, lines, graphic primitives (cube, cone, sphere etc).<br/><br/>
<b>OBD2 Plugin</b> Works with USB OBD2 dongle. Query values and converts them to a CAN message format so they could be visualized in the CAN viewer and Plotter. <br/><br/>
<b>Plotter</b> simple plotter plugin. <br/><br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_005.png?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_005.png?raw=true" width="50%">
</a>

Testing ARM64 port on RPi4.<br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_009.jpeg?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_009.jpeg?raw=true" width="25%">
</a>

Plotter plugin.<br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_004.png?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_004.png?raw=true" width="25%">
</a>

Viewer functionality split. Plugins API defined. GPS plugin gets map tails from OpenStreetMap<br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_003.png?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_003.png?raw=true" width="25%">
</a>

With video streams<br/>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_002.png?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_002.png?raw=true" width="25%">
</a>

The beginning. Polyline Viewer</br>
<a href="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_001.png?raw=true" target="_blank">
<img src="https://github.com/UrryKurtz/yodps_bin/blob/master/Doc/Screenshot_001.png?raw=true" width="25%">
</a>
---
## Videos
**Camera control, Video and Polyline Plugins demo**<br/>
<a href="https://youtu.be/yHRvpe6Kq-4" target="_blank">
<img src="https://img.youtube.com/vi/yHRvpe6Kq-4/hqdefault.jpg" width="25%">
</a>

**Open Street Map GPS Plugin**<br/>
<a href="https://youtu.be/4tj1m2y9mRg" target="_blank">
<img src="https://img.youtube.com/vi/4tj1m2y9mRg/hqdefault.jpg" width="25%">
</a>

**Plotter Plugin**<br/>
<a href="https://youtu.be/LsX0EGzu1fc" target="_blank">
<img src="https://img.youtube.com/vi/LsX0EGzu1fc/hqdefault.jpg" width="25%">
</a>

**Now with docking** (recorded with a mobile phone and USB HDMI video grabber)<br/>
<a href="https://youtu.be/B88OxGrW4sw" target="_blank">
<img src="https://img.youtube.com/vi/B88OxGrW4sw/hqdefault.jpg" width="25%">
</a>

**MCAP recorder node and Recorder controller plugin for Visualization**<br/>
<a href="https://youtu.be/mAF3oBv_RXg" target="_blank">
<img src="https://img.youtube.com/vi/mAF3oBv_RXg/hqdefault.jpg" width="25%">
</a>

**MCAP player node and Visualization controller plugin**<br/>
<a href="https://youtu.be/TjXcXtZIeSE" target="_blank">
<img src="https://img.youtube.com/vi/TjXcXtZIeSE/hqdefault.jpg" width="25%">
</a>
---
## 📦 Third-party dependencies
- [ZeroMQ (libzmq)](https://github.com/zeromq/libzmq) — MPL 2.0  
- [MCAP](https://github.com/foxglove/mcap) — MIT License  
- [libtins](https://github.com/mfontanini/libtins) — BSD 2-Clause License  
- [LVGL](https://github.com/lvgl/lvgl) — MIT License  
- [msgpack-c](https://github.com/msgpack/msgpack-c) — Boost Software License 1.0  
- [cereal](https://uscilab.github.io/cereal/) — BSD 3-Clause License
- [Urho3D](https://github.com/urho3d/Urho3D) — MIT License
- [rbfx](https://github.com/rbfx/rbfx) — MIT License
- [Dear ImGui](https://github.com/ocornut/imgui) — MIT License
- [httplib](https://github.com/yhirose/cpp-httplib) — MIT License
- [dbc_parser_cpp](https://github.com/LinuxDevon/dbc_parser_cpp) — MIT License
- [opendbc](https://github.com/commaai/opendbc) — MIT License
- [libjpeg-turbo](https://libjpeg-turbo.org/) — IJG (Independent JPEG Group) License, the Modified (3-clause) BSD License, and the zlib License
- [RtMidi](https://github.com/thestk/rtmidi) — MIT License with the added feature that modifications be sent to the developer
- [tinyxml2](https://github.com/leethomason/tinyxml2) — Zlib License
---
## 📜 License

This software is dual-licensed:

1. **Open Source License (GPLv3)**  
   You may use, modify, and distribute this software under the terms of the GNU General Public License version 3 (GPLv3).  
   See the [LICENSE.md](LICENSE.md) file for full details.

2. **Commercial License**  
   If you wish to use this software in a closed-source product, or without the obligations of GPLv3,  
   a commercial license is available for purchase.  
   Contact: **y.odnokurtsev@gmail.com**

By using this software, you agree to comply with the terms of one of the above licenses.

---
## 💾 Download

First binary release for x64 Linux, arm64 Linux, Android and x64 Windows coming soon.

---

