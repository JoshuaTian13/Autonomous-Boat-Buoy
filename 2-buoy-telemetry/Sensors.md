# Sensor Integration and Mounting

The buoy measured three water-quality properties:

- **pH** using an analog probe and interface board
- **Temperature** using a waterproof probe
- **Total dissolved solids (TDS)** using an immersed conductivity probe

The acquisition electronics calibrated and sampled each channel before forwarding a single measurement record to the telemetry controller. The LoRa firmware then combined those readings with GPS coordinates, a timestamp, and a boat identifier for shore-side ingestion.

## Mechanical integration

Each probe required a custom mount that followed the curvature of the buoy and protected the sensing element while keeping it exposed to the water:

- The temperature-probe mount used a curved base and clip to constrain the cable.
- The TDS mount used a slide-in enclosure and a protective extension around the exposed pins after testing revealed that the probe could be damaged during deployment.
- The pH mount positioned the probe vertically and kept the sensing tip clear of the hull.

Printable and editable design artifacts are preserved in [`Files/`](Files), including STEP models for the pH, temperature, and TDS mounts and STL/STEP iterations for the motorized spool mechanism.

## Related firmware

- [`buoy1-LoRa-GPS.ino`](Files/buoy1-LoRa-GPS.ino) assembles GPS, timestamp, sensor, and device fields and transmits them over LoRa.
- [`buoy-with-motor.ino`](Files/buoy-with-motor.ino) deploys and retracts a submerged sensor payload using encoder feedback and a magnetic home sensor.
- [`receiver.ino`](receiver.ino) receives LoRa packets, reports RSSI, displays packet contents, and forwards the payload over serial.
