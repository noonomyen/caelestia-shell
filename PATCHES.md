# Patches

## v2.5.0-patch1

### Added
- **Intel GPU Utilization (Xe & i915):**
  - Added sysfs RC6 idle residency tracking for Intel `xe` (`gtidle/idle_residency_ms`) and `i915` (`rc6_residency_ms`) drivers.
  - Added `Intel` option to `GpuType` enum and the Settings (`ServicesPage`) dropdown.
- **Build Version Suffix:**
  - Added `VERSION_SUFFIX` (defaults to `-patch1`) in `CMakeLists.txt` while preserving numeric compatibility for CMake's `project()`.

### Modified Files
- `CMakeLists.txt`
- `modules/nexus/pages/ServicesPage.qml`
- `plugin/src/Caelestia/Config/enums.hpp`
- `plugin/src/Caelestia/Services/gpu.hpp`
- `plugin/src/Caelestia/Services/gpu.cpp`
