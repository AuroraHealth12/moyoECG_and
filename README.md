## Android app for receiving moyoECG data

This is a major rework of the previous version, with added support of BLE connection and firmware upload capability.


App is divided into interface and service (so that connection isn't lost when window is switched). Service stores all data and makes them available to the interface via broadcasting.

BLE connection code is really bad in this version and needs major rework (it restarts BLE until it gets connected - couldn't find another way out of locked state when service discovery fails). Once connection is established, it seems to be reliable.

Data parsing happens in parse_chr_ecg_data function inside ble_moyoecg_service.java. Then it goes through ecg_processor class which stores ECG in memory and then broadcasts them to the interface app , and saves them to file csv (if saving mode is turned on).

