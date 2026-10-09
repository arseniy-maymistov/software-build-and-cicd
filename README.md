# TRSPO Labs: Systems Programming, Build Toolchains, and Software Security

Three laboratory assignments completed for the course **Modern Software Development Technologies** (*Технологии разработки современного программного обеспечения*, TRSPO), Peter the Great St. Petersburg Polytechnic University, 2026.

The labs explore three different parts of the software development lifecycle: Windows process instrumentation, Linux build and linking techniques, and security analysis methods for a CI/CD workflow.

## Lab 1 — Process Event Monitoring

**Report:** [`trspo1.docx`](trspo1.docx)

A Windows systems-programming lab focused on observing and changing the behavior of a target process using a DLL and WinAPI hooks.

The report documents:
- A test target process that opens a file and enumerates files in its working directory.
- A DLL injector that selects a target process by PID or process name.
- A 64-bit inline-hooking mechanism using a 14-byte indirect jump.
- Hooks for `CreateFileW`, `FindFirstFileW`, and `FindNextFileW`.
- Logging of selected function calls and timestamps to a separate console application.
- A TCP connection between the injector and the injected DLL for configuration and log delivery.
- A demonstration mode in which a configured filename is hidden from the target process's file-opening and file-enumeration operations.

**Main concepts:** WinAPI, DLL injection, API hooking, process memory protection, Windows x64 calling conventions, Winsock, TCP sockets, concurrency and synchronization.

> This lab demonstrates low-level process instrumentation. Such techniques should only be tested in processes and environments where you have explicit authorization.

## Lab 2 — Compiler, Linker, and Dynamic Libraries

**Report:** [`trspo2.docx`](trspo2.docx)

A build-systems lab that renders a text message into a PNG image using a TrueType font and compares three ways of building and loading the application.

The report describes:
- Rendering text into an 800 × 200 image buffer using FreeType.
- Writing the rendered image to PNG using libpng and zlib.
- A `Makefile` that automates the build process.
- A statically linked application.
- A dynamically loaded version that uses `dlopen()` and `dlsym()` to resolve library functions at runtime.
- A position-independent blob version built without the standard C library and loaded through an ELF loader.
- Timing the program's execution and reporting the generated image.

**Main concepts:** C, GNU `make`, Makefiles, static linking, dynamic loading, shared libraries, `dlopen()`, `dlsym()`, ELF, position-independent code, FreeType, libpng and zlib.

The report describes the implementation and build layout; the source files and build artifacts are not included in this repository, so the programs cannot be rebuilt from the report files alone.

## Lab 3 — SAST and SCA for a CI/CD Pipeline

**Report:** [`trspo3.docx`](trspo3.docx)

A software-security lab focused on selecting static-analysis and dependency-analysis tools for the **BlogAtor** project as part of a planned CI/CD workflow.

The report covers:

- **SAST methods:** lexical/pattern analysis, data-flow analysis, control-flow analysis, taint analysis and symbolic execution.
- **SAST tool comparison:** Joern and CodeQL, including their analysis models, query approaches, language support, integration options and learning curve.
- **SCA methods:** manifest and binary analysis, transitive dependency discovery, vulnerability-database matching and license analysis.
- **SCA tool comparison:** OWASP Dependency-Check and Snyk Open Source.
- An overview of the current BlogAtor architecture and the need to introduce automated security checks into its build workflow.

The report's conclusion favors **CodeQL** for SAST and **OWASP Dependency-Check** for SCA in the described BlogAtor context. This lab is a review and comparison of methods and tools; it does **not** document a completed CI/CD integration. The report identifies implementation and integration as subsequent work.

**Main concepts:** CI/CD, application security, SAST, SCA, CodeQL, Joern, OWASP Dependency-Check, Snyk Open Source, dependency vulnerabilities and software licenses.

## Repository Contents

| File | Description |
|---|---|
| `trspo1.docx` | Lab 1 report — process monitoring and API hooking |
| `trspo2.docx` | Lab 2 report — Makefile, linking modes and ELF-loaded blob |
| `trspo3.docx` | Lab 3 report — SAST/SCA methods and tool comparison for BlogAtor |
| `README.md` | English overview of the three labs |


