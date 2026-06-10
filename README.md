# Mesa Debian Backports (mesa-debian)

This repository hosts `.debdiff` files dedicated to backporting modern **Mesa** versions to **Debian Trixie**. 

These diffs include all necessary build-dependency adaptations, toolchain downgrades (like LLVM), and other fixes required to build updated graphics drivers on Trixie. All changes are derived from upstream Mesa source code with explicit patches for Debian compatibility.

---

## Looking for the Files?

All version-specific patches, package modifications, and complete `.debdiff` logs are organized in the releases section. 

Go straight to [Releases](https://stornic56hub.duckdns.org/git/stornic56/mesa-debian/releases) section to download the standalone `.debdiff` files for specific versions.

---

## Repository Contents

* **debdiffs/**: Contains the raw `.debdiff` source files for historical tracking and direct inspection.
* **README.md**: This documentation file.
* **LICENSE**: Licensing information (GPLv3).

---

## Installation Guide

These `.debdiff` files are designed to be applied to a local Mesa build environment or backports testing setup, not directly installed on production systems without verification.

1.  Download the `.debdiff` file corresponding to your target version from the [Releases](https://stornic56hub.duckdns.org/git/stornic56/mesa-debian/releases) section.
2.  Apply the patch using `debdiff` or `patch` tools in a controlled environment (e.g., Google Cloud VM, Docker container).
3.  Verify build dependencies are met for Debian Trixie (see recent commits for specific version requirements).

---

## Security and Stability Notes

* **Toolchain Adjustments:** Toolchain downgrades (e.g., LLVM) are included to ensure compatibility with Debian Trixie's current toolset.
* **License:** Packaging work is licensed under GPLv3. Upstream Mesa source code remains under its original licenses (MIT/X11).

---
## ⚠️ Test Packages (.deb)

The packages in the "Releases" section are binaries compiled solely for testing purposes. They include everything necessary to run on Debian stable, but **are not officially signed** by Debian Backports.

⛔ Do not install them on production systems without verifying their integrity using the SHA256 checksums provided in GitHub releases.

### Installation Guide (Quick Start)
1. Download the file from [Releases](https://github.com/stornic56/mesa-debian/releases/v25.3.3)
2. Extract: `tar -xzf mesa_25.3.3_test_packages.tar.gz`

---

### Option 1: Install AMD64 Only
This is the safer option and recommended for most users on modern hardware with AMD or Intel GPUs. It excludes OpenCL i386 packages which may cause conflicts in Debian Trixie.

```bash
sudo dpkg -i --force-overwrite \
    mesa-libgallium_25.3.3-1~bpo13+1_amd64.deb \
    libgbm1_25.3.3-1~bpo13+1_amd64.deb \
    libgl1-mesa-dri_25.3.3-1~bpo13+1_amd64.deb \
    libglx-mesa0_25.3.3-1~bpo13+1_amd64.deb \
    libegl-mesa0_25.3.3-1~bpo13+1_amd64.deb \
    mesa-vulkan-drivers_25.3.3-1~bpo13+1_amd64.deb \
    mesa-drm-shim_25.3.3-1~bpo13+1_amd64.deb

# Fix dependencies:
sudo apt install -f
```

---

### Option 2: Install Full (AMD64 + i386 recommended for Gaming)
This option includes all packages including i386 versions for compatibility testing and gaming scenarios that require 32-bit libraries. **Use with caution** as some OpenCL i386 packages may cause conflicts in Debian Trixie.

```bash
sudo dpkg -i --force-overwrite \
    mesa-libgallium_25.3.3-1~bpo13+1_amd64.deb \
    mesa-libgallium_25.3.3-1~bpo13+1_i386.deb \
    libgbm1_25.3.3-1~bpo13+1_amd64.deb \
    libgbm1_25.3.3-1~bpo13+1_i386.deb \
    libgl1-mesa-dri_25.3.3-1~bpo13+1_amd64.deb \
    libgl1-mesa-dri_25.3.3-1~bpo13+1_i386.deb \
    libglx-mesa0_25.3.3-1~bpo13+1_amd64.deb \
    libglx-mesa0_25.3.3-1~bpo13+1_i386.deb \
    libegl-mesa0_25.3.3-1~bpo13+1_amd64.deb \
    libegl-mesa0_25.3.3-1~bpo13+1_i386.deb \
    mesa-vulkan-drivers_25.3.3-1~bpo13+1_amd64.deb \
    mesa-vulkan-drivers_25.3.3-1~bpo13+1_i386.deb \
    mesa-drm-shim_25.3.3-1~bpo13+1_amd64.deb \
    mesa-drm-shim_25.3.3-1~bpo13+1_i386.deb

# Fix dependencies:
sudo apt install -f
```

---

### Optional: Install OpenCL (Rusticl) for AMD64 Only
If you want to test the 64-bit OpenCL driver on compatible hardware, install it separately after the main packages:

```bash
sudo dpkg -i mesa-opencl-icd_25.3.3-1~bpo13+1_amd64.deb
```

---

### ⚠️ Important Notes
| Aspect | Details |
| :--- | :--- |
| **Production Use** | These packages are for testing only. Verify with SHA256 checksums before using on production systems. |
| **32-bit Packages** | The archive includes both `amd64` (recommended) and `i386` packages. Some i386 OpenCL packages may cause conflicts in Debian Trixie. |
| **Verification** | Use `sha256sum -c SHA256SUMS.txt` to verify package integrity after extraction. |
| **Architecture** | Most modern GPUs on Debian Trixie should work correctly with AMD64 packages only. i386 is optional for legacy compatibility. |


---

## License

This packaging and backporting work is licensed under the **GPLv3 License**. Upstream Mesa source code remains under its original licenses (MIT/X11).
