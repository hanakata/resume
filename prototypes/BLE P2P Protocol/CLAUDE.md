## CLAUDE.md: Low-Power BLE P2P Protocol (Android)

### Project Overview
A decentralized, internet-independent broadcasting network for Android. It uses BLE Advertising to transmit a 20-byte high-density packet for emergency alerts and hyper-local commerce.

### Technical Stack
* **Min SDK:** 31 (Android 12) / **Target SDK:** 34+ (Android 14/15)
* **Language:** Kotlin / Coroutines / Flow
* **Core APIs:** `BluetoothLeScanner`, `BluetoothLeAdvertiser`, `CompanionDeviceManager` (for persistence), `ForegroundService` (with `dataSync` type).

### Core Design Principles
1. **Battery-First Scanning:** Use `SCAN_MODE_LOW_POWER` with `ScanFilter`. Let the Bluetooth chip handle filtering; do not wake the CPU unless a specific Service UUID is detected.
2. **Opportunistic Sync:** Align scan windows with system-wide wakeups to minimize additional battery drain.
3. **Hardware Abstraction:** Isolate BLE logic from business logic to handle manufacturer-specific battery optimizations.

### Implementation Guide: Low-Power Persistent Scanner

```kotlin
// CRITICAL: Background Scan Settings for 2026 Android
val scanSettings = ScanSettings.Builder()
    .setScanMode(ScanSettings.SCAN_MODE_LOW_POWER) // Target: <1% battery per hour
    .setCallbackType(ScanSettings.CALLBACK_TYPE_ALL_MATCHES)
    .setMatchMode(ScanSettings.MATCH_MODE_AGGRESSIVE) // Pick up even weak signals
    .setNumOfMatches(ScanSettings.MATCH_NUM_ONE_ADVERTISEMENT) // Wake up on first packet
    .build()

// 20-Byte Packet Structure (Binary Schema)
// [1b: Ver][8b: PhoneHash][6b: Geo24][2b: Time][1b: Flags][2b: CRC]
```

### Key Tasks for Claude
- [ ] **Implement `BleBroadcastService`:** A Foreground Service using `type="dataSync"` to bypass background execution limits.
- [ ] **Optimization:** Implement an adaptive duty cycle that scales scanning frequency based on `SignificantMotion` sensor events.
- [ ] **Data Packing:** Create a `PacketEncoder` that compresses `Double` coordinates into 24-bit integers and generates 64-bit Phone Hashes.
- [ ] **Verification:** Generate a unit test to verify CRC16 integrity of the 20-byte payload.

### Manufacturer-Specific Notes
* **Samsung/Oppo/Xiaomi:** Must use `PowerManager.isIgnoringBatteryOptimizations()` check and prompt user to whitelist the app.
* **Pixel:** Utilize `CompanionDeviceManager` to maintain a persistent connection or "association" to the BLE environment.