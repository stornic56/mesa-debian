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

## License

This packaging and backporting work is licensed under the **GPLv3 License**. Upstream Mesa source code remains under its original licenses (MIT/X11).
