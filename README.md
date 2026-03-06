# **Automated Build Repository of Emulators for TSP**

This repository provides a streamlined, automated pipeline for building and periodically updating high-quality emulators and Libretro cores specifically optimized for the **TrimUI Smart Pro (TSP)**.

The "spirit" of this project is to bridge the gap between upstream source code and the unique hardware requirements of the Allwinner A133P SoC. We leverage GitHub Actions to ensure users have access to the latest features and performance improvements without needing to manage complex local cross-compilation environments.

## **🚀 The Core Mission**

* **Native ARM64 Performance:** Every build targets the arm64-v8a architecture using QEMU-based virtualization or optimized cross-compilation toolchains.  
* **Custom SDL2 Integration:** We link against a specialized **SDL2 2.26.1** blob tailored for the TSP, ensuring proper input mapping, display scaling, and hardware acceleration.  
* **Automation-First:** Using GitHub Actions, we track upstream development branches (like dev for SimCoupe or master for HatariB) to deliver fresh binaries whenever updates occur.  
* **Optimized Toolchains:** Builds are performed in controlled Debian 11/Ubuntu 20.04 environments to ensure stability and compatibility with the TSP’s glibc version.

## **🛠️ Build Philosophy & Safeguards**

To maintain a reliable build pipeline, every script in this repository adheres to a strict "Safeguard Protocol":

1. **Ownership Persistence:** Automatic chown and git config safe.directory fixes to prevent Git "dubious ownership" errors during containerized builds.  
2. **Memory Management:** Throttled linking, host-side cache clearing, and memory swap allocation to prevent QEMU from stalling during heavy compilation tasks.  
3. **Clean Room Environment:** Every build starts from a fresh container to prevent dependency "poisoning" and ensure reproducible results.  
4. **Source Patching:** Automatic application of critical fixes (e.g., mallinfo swaps, legacy function mapping) to ensure compatibility with modern glibc/linux environments.

## **📦 Current Coverage**

The repository provides automated workflows for a diverse range of systems:

* **Libretro Cores:** Flycast (Dreamcast), HatariB (Atari ST), Zelda Classic, OpenBOR, and more.  
* **Standalone Emulators:** SimCoupe (SAM Coupé), XRoar (Dragon 32/64 / CoCo), and TI-99/4A Sim.  
* **Frontend:** Optimized builds of RetroArch for the TSP platform.

## **⚠️ Disclaimer & Support**

**This project is provided "as-is" for the community.**

* **No Support:** This project has **no support**. There is no official troubleshooting, "help desk," or technical assistance for these builds. You will have to run an ldd on each artifact in order to get the correct .so libs. And there are no ROMs provided in this repository.
* **Use at Your Own Risk:** While we strive for stability, these are automated builds from development branches. They may contain bugs or performance regressions from upstream sources.  
* **Community Driven:** If a build fails or a core needs a patch, users are encouraged to explore the workflow logs and contribute a fix via Pull Request.
* **Credits:** Please check the corresponding licenses of the emulators before using and or distributing them. And give credit to their authors.

Enjoy .. 🍻
