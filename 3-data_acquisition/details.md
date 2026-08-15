# Data Acquisition — Technical Notes

## Purpose

Acquire calibrated pH, temperature, and TDS readings for the instrumented buoy, then forward a compact measurement record to the ESP32 telemetry controller.

## Hardware

- Arduino Uno, Mega, and Nano boards used during subsystem prototyping
- ESP32 telemetry controller
- pH, TDS, and waterproof temperature probes
- pH, TDS, and temperature calibration references
- Breadboards, protoboard, jumper wiring, and soldered interconnects
- Hall-effect sensor for detecting the depth mechanism's home position

## Integration workflow

1. Characterize each sensor against its calibration reference.
2. Oversample and filter analog measurements to reduce noise.
3. Validate the sensor channels independently before combining them.
4. Forward the consolidated record from the Arduino DAQ controller to the ESP32 over serial.
5. Append GPS, timestamp, and device fields before LoRa transmission.
6. Compare received packets with the source readings during pool and field tests.

The final telemetry packet was designed to map directly to the shore-side relational schema: one location-time record associated with pH, temperature, and dissolved-solids measurements.
