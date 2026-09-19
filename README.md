# ReLight - Skyrim SE/VR

Lighting in Skyrim has always been a mess of engine limits and broken node references. ReLight hooks directly into the renderer's light pass to fix flicker, handle dynamic light limits, and fix startup scene graph node crashes—without needing bulky external DLL overrides.

---

## What It Does

* **Native Light Limit Fix:** Stops lights from popping in and out when you look around in dense cells.
* **ShadowSceneNode Crash Fix:** Prevents startup crashes when light nodes get set up before menu cells load.
* **Dynamic Node Injections:** Safely hooks directional and point lights into the scene graph at runtime.

---

## Installation

1. Drop `ReLight.dll` and `ReLight.pdb` into `Data/SKSE/Plugins/`.
2. Launch the game through SKSE.
3. Done. No extra INIs to mess with unless you want custom logging.

---

## Requirements

* **SKSE64** (Current runtime for SE/AE/VR)
* **Address Library for SKSE Plugins**

---

## Known Incompatibilities

* **NativeMeshLightFlickerFix.dll** (v1.5.1 or older): Crashes the engine on startup inside `ShadowSceneNode`. Disable or remove it—ReLight already covers light limit handling natively.
* Any legacy plugin attempting to hook directly into `BSShadowLight::Init` at the same memory address.

---

## Troubleshooting

If you crash on startup, check `Data/SKSE/Plugins/ReLight.log`. If it died before reaching the main menu, make sure you don't have conflicting mesh flicker DLLs active in your load order.
