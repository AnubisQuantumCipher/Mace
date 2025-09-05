# Q-SEAL: Fortifying macOS with Quantum-Resistant, Device-Bound Cryptography

## The Quantum Imperative: Securing Tomorrow's Data, Today

In an increasingly precarious digital landscape, the integrity and confidentiality of sensitive information are under constant siege. Traditional cryptographic paradigms, while robust against current threats, face an existential challenge from the nascent power of quantum computing. Q-SEAL, formerly known as Mace, emerges as a vanguard solution, offering an unparalleled synthesis of advanced cryptographic principles and the inherent hardware-backed security of macOS Secure Enclave technology. This command-line interface (CLI) tool is meticulously engineered to provide device-bound, post-quantum hybrid secure enclave streaming file encryption, establishing a new benchmark for data protection in high-stakes environments.

### A Paradigm Shift in Digital Sovereignty

Q-SEAL transcends conventional encryption utilities; it embodies a strategic commitment to digital sovereignty and enduring data integrity. It represents a proactive defense against both present-day sophisticated cyber threats and the looming specter of quantum cryptanalysis. By seamlessly integrating with macOS's Secure Enclave, Q-SEAL delivers a **passwordless cryptographic experience**, fundamentally mitigating the human element often exploited in security breaches. Its **post-quantum hybrid architecture**, specifically incorporating ML-KEM-1024, ensures that your data remains impervious to the cryptographic breakthroughs anticipated with the advent of large-scale quantum computers. This project is a testament to the principle that uncompromising security can, and must, coexist with operational efficiency and user accessibility.

### The Strategic Advantage: Who Benefits from Q-SEAL?

Q-SEAL is an indispensable asset for entities and individuals operating at the forefront of security, privacy, and technological innovation:

*   **Cryptographers and Security Researchers:** Delve into a real-world implementation of post-quantum cryptography (ML-KEM-1024) integrated with hardware security modules. Analyze its modular AEAD and composite encapsulation design, and contribute to the evolution of quantum-resistant solutions.
*   **Programmers and System Architects:** Leverage a robust, Swift-based CLI tool for secure file operations. Understand its interaction with low-level macOS security frameworks and its application in building secure software ecosystems.
*   **Reverse Engineers and Threat Analysts:** Examine a sophisticated encryption mechanism designed for resilience. Q-SEAL offers a compelling case study in modern cryptographic engineering, providing insights into advanced data protection strategies and their underlying implementations.
*   **Government Officials and Agencies:** Secure classified information, sensitive communications, and critical infrastructure data against state-sponsored threats and future quantum attacks. Q-SEAL provides a verifiable, device-bound encryption solution compliant with stringent security mandates.
*   **Enterprises and Intellectual Property Holders:** Protect proprietary algorithms, trade secrets, and confidential client data with a solution that ensures data remains tied to authorized devices, even in the event of physical compromise.
*   **Privacy Advocates and High-Value Individuals:** Reclaim control over your digital footprint. Q-SEAL offers an ironclad defense against unauthorized access, ensuring personal and professional communications remain private and secure.

### Why Q-SEAL is Critical: Navigating the Future of Cybersecurity

The imperative for Q-SEAL is underscored by the escalating frequency and sophistication of cyberattacks, coupled with the imminent threat posed by quantum computing. Its critical importance stems from several foundational pillars:

1.  **Hardware-Anchored, Device-Bound Security:** Q-SEAL leverages the macOS Secure Enclave, a dedicated hardware security module, to generate and manage cryptographic keys. This ensures that decryption keys are never exposed to the main processor and are inextricably linked to the specific device. Even if encrypted data is exfiltrated, it remains undecipherable without the authorized hardware, providing an unparalleled layer of physical and logical security.
2.  **Elimination of Password Vulnerabilities:** By adopting a passwordless operational model, Q-SEAL eradicates the weakest link in most security chains: human-generated passwords. Authentication and key management are handled transparently and securely by the Secure Enclave, drastically reducing the attack surface associated with brute-force, phishing, or credential stuffing attacks.
3.  **Proactive Quantum Resistance (ML-KEM-1024 Integration):** The integration of ML-KEM-1024 (Module-Lattice-based Key Encapsulation Mechanism), a leading candidate for post-quantum cryptography, positions Q-SEAL at the forefront of future-proof security. This hybrid approach ensures that data encrypted today will remain secure against the theoretical capabilities of future quantum computers, providing long-term confidentiality and integrity.
4.  **Modular AEAD and Composite Encapsulation:** Q-SEAL's design incorporates Authenticated Encryption with Associated Data (AEAD) and a sophisticated composite encapsulation scheme. This modularity enhances cryptographic agility and ensures robust integrity checks, preventing tampering and unauthorized modifications to encrypted data.
5.  **Operational Simplicity for Complex Security:** Despite its advanced cryptographic underpinnings, Q-SEAL is engineered for intuitive command-line interaction. This balance of profound security and operational ease makes it accessible to a broad spectrum of technical users, from developers to security professionals, enabling widespread adoption of best-in-class encryption practices.
6.  **Comprehensive Data Lifecycle Protection:** Beyond mere file encryption, Q-SEAL offers nuanced features such as automated folder archiving, intelligent exclusion presets for development environments (e.g., `.git`, `node_modules`), and meticulous preservation of macOS extended attributes. This holistic approach ensures that the entire data lifecycle, from creation to storage, is protected with granular control.

Q-SEAL is not merely a tool; it is a strategic imperative for anyone committed to safeguarding digital assets in an era of unprecedented technological evolution and persistent cyber threats. It represents the convergence of cutting-edge cryptography, hardware-backed security, and pragmatic usability, delivering peace of mind in a world that increasingly demands it.

## Installation Instructions: Deploying Q-SEAL

Q-SEAL is designed for macOS environments (version 13 and newer) and requires the Xcode Command Line Tools. A critical component for its post-quantum capabilities is the ML-KEM-1024 implementation, which necessitates linking with a compatible library such as `liboqs`.

### Essential Prerequisites

Before proceeding with the installation of Q-SEAL, ensure your system meets the following foundational requirements:

*   **macOS Operating System:** Version 13 (Ventura) or later. Q-SEAL leverages specific APIs and security features introduced in modern macOS releases.
*   **Xcode Command Line Tools:** These tools provide essential compilers, linkers, and system headers necessary for building Swift projects. Install them via your terminal:
    ```bash
    xcode-select --install
    ```
*   **liboqs (Open Quantum Safe Library):** This library is paramount for Q-SEAL's post-quantum capabilities, providing the ML-KEM-1024 implementation. For optimal compatibility and to avoid potential linker warnings related to deployment targets, it is **highly recommended to build `liboqs` directly from its source code**.

    **Step-by-Step Guide: Building `liboqs` from Source**

    1.  **Clone the `liboqs` repository:**
        ```bash
        git clone https://github.com/open-quantum-safe/liboqs
        cd liboqs
        ```
    2.  **Configure the build with CMake:**
        ```bash
        cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_DEPLOYMENT_TARGET=13.0 -DBUILD_SHARED_LIBS=OFF
        ```
        *Note: Adjust `-DCMAKE_OSX_DEPLOYMENT_TARGET=13.0` to match your specific macOS version if it differs from 13.0. This ensures that `liboqs` is compiled with the correct deployment target for your system.*
    3.  **Compile `liboqs`:**
        ```bash
        cmake --build build --config Release
        ```
    4.  **Install `liboqs` to your system:**
        ```bash
        sudo cmake --install build
        ```
        *Important: If you choose not to install `liboqs` into the default Homebrew prefix (`/usr/local`), you must adjust the `CMAKE_INSTALL_PREFIX` during the CMake configuration step accordingly. Ensure that the installed `liboqs` is discoverable by your system's linker.*

### Q-SEAL Installation Methods

Once the prerequisites are satisfied, you can proceed with installing Q-SEAL using one of the following methods:

#### Method 1: Swift Package Manager (Source Build) - Recommended for Developers and Custom Deployments

This method provides maximum control over the build process and is ideal for developers, security researchers, or those requiring specific build configurations.

1.  **Clone the Q-SEAL repository:**
    ```bash
    git clone https://github.com/AnubisQuantumCipher/mace
    cd mace
    ```
2.  **Build Q-SEAL in release mode:**
    ```bash
    swift build -c release
    ```
    This command compiles the Q-SEAL binary and its dependencies.
3.  **Install the Q-SEAL binary to your system's PATH:**
    ```bash
    sudo install -m 0755 .build/release/mace /usr/local/bin/mace
    ```
    This command places the `mace` executable in a standard location accessible from your terminal.
4.  **Verify the installation:**
    ```bash
    mace --help
    ```
    A successful installation will display the Q-SEAL command-line help documentation.

#### Method 2: One-Liner Installer - Recommended for Quick Setup and General Users

For users seeking a streamlined and automated installation process, the one-liner script provides a convenient solution. This script handles the cloning, building, and installation steps automatically.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AnubisQuantumCipher/mace/main/script/install.sh)"
```

*Note on `liboqs` Warnings:* If, after using the one-liner installer, you encounter linker warnings or errors related to `liboqs` deployment targets, it indicates a potential mismatch between the pre-compiled `liboqs` and your macOS environment. In such cases, it is strongly advised to follow the detailed `liboqs` source build instructions provided in the 


Prerequisites section. Building `liboqs` from source ensures full compatibility and resolves most common installation issues.

## Operationalizing Q-SEAL: A Comprehensive Usage Guide

Q-SEAL provides a powerful yet intuitive command-line interface, designed for seamless integration into your security workflows. The following sections detail the core functionalities and their applications, empowering users to harness the full potential of device-bound, post-quantum hybrid encryption.

### Key Management: Establishing Your Secure Identity

At the heart of Q-SEAL's security model is its robust key management system, leveraging the macOS Secure Enclave for hardware-backed cryptographic operations. All keys generated are device-bound and non-exportable, ensuring maximum security.

*   **Key Generation (Passwordless, Device-Bound):**
    ```bash
    mace keygen --label <your-label>
    ```
    This command initiates the creation of a new local identity. The Secure Enclave generates a P-256 elliptic curve key pair and an ML-KEM-1024 key pair, which are then securely stored within the hardware. A public key (`~/.mace/<your-label>.pub`) is generated for distribution to recipients, enabling them to encrypt data specifically for your device. This process requires no password input, as authentication is handled by the Secure Enclave's biometric or passcode mechanisms when your session is unlocked.

*   **Quick Setup (Identity + Defaults):**
    ```bash
    mace setup --label <your-label>
    ```
    For rapid deployment, this command streamlines the identity creation process, setting up a new key pair with default configurations and generating the corresponding public key.

*   **Rotating Identity:**
    ```bash
    mace key-rotate --label <your-label>
    ```
    In scenarios requiring periodic key updates or compromise mitigation, this command allows for the secure rotation of your local identity. A fresh Secure Enclave P-256 and ML-KEM-1024 key pair is generated, and a new public key is written to `~/.mace/<your-label>.pub` for subsequent distribution. This ensures forward secrecy and limits the impact of potential future key compromises.

### Data Encryption: Securing Your Files and Folders

Q-SEAL provides flexible options for encrypting individual files or entire directories, incorporating advanced features for metadata preservation and selective exclusion.

*   **Encrypting a File:**
    ```bash
    mace encrypt --recipient <your-label> file1.txt
    ```
    This command encrypts `file1.txt` for the specified recipient(s). Q-SEAL employs a sophisticated cryptographic scheme involving Header HMAC-SHA-384 for integrity verification and AES-256-GCM for high-throughput authenticated encryption. The associated data (AD) mechanism binds the header MAC to the ciphertext, preventing tampering and ensuring the authenticity of the encrypted stream.

*   **Encrypting a Folder (Auto-archive):**
    ```bash
    mace encrypt --recipient <your-label> MyProject/
    ```
    To secure entire project directories or collections of files, Q-SEAL offers an intelligent folder encryption capability. This command automatically archives the `MyProject/` directory into a `.tar` file before encryption, maintaining directory structure and file permissions. Advanced exclusion options are available:
    *   **Development Exclusion Preset:** Use `--exclude-preset dev` to automatically skip common development clutter such as `.git` repositories, `.build` directories, `node_modules`, and other transient files, ensuring only relevant data is encrypted.
    *   **Custom Exclusions:** Employ `--exclude "*.log" --exclude .DS_Store` to define custom patterns for files or directories to be excluded from the encryption process.
    *   **Metadata Preservation:** By default, Q-SEAL preserves macOS extended attributes (xattrs) and Access Control Lists (ACLs) during encryption, maintaining crucial file system metadata. To omit this, use `--no-preserve-xattrs`.

### Data Decryption and Verification: Accessing and Validating Encrypted Assets

Q-SEAL simplifies the decryption process, leveraging the Secure Enclave for a passwordless experience, and provides robust mechanisms for verifying the integrity and authenticity of encrypted data.

*   **Decrypting a File (Passwordless, Device-Bound):**
    ```bash
    mace decrypt file1.mace
    ```
    This command decrypts `file1.mace`. The decryption process is entirely passwordless, relying on the Secure Enclave to securely unlock the file encryption key. This seamless operation enhances user experience without compromising security, as the key material never leaves the hardware boundary.

*   **Decrypting and Extracting Folder Archives:**
    ```bash
    mace decrypt --extract MyProject.tar.mace
    ```
    For encrypted folder archives, this command decrypts the `.mace` file and automatically extracts its contents. To remove the intermediate `.tar` file after successful extraction, use the `--remove-archive` flag.

*   **One-Step Extraction:**
    ```bash
    mace extract MyProject.tar.mace
    ```
    This convenient command automatically detects the tar payload within the `.mace` file and performs a combined decryption and extraction operation.

*   **Verifying Header Integrity:**
    ```bash
    mace verify file1.mace
    ```
    This command performs structural checks on the encrypted file's header, validating its format and ensuring it conforms to Q-SEAL's specifications. This is a quick integrity check that does not require Secure Enclave interaction.

*   **Verifying Authenticity (Passwordless):**
    ```bash
    mace verify --auth file1.mace
    ```
    For a comprehensive authenticity verification, this command performs a full check, including the header MAC and all GCM tags embedded within the encrypted stream. This operation leverages the Secure Enclave for passwordless authentication, ensuring that the data has not been tampered with and originates from an authorized source.

*   **Rekeying (Adding Recipients):**
    ```bash
    mace rekey --pub ~/.mace/laptop.pub --input file1.mace --output file1.mace.new
    ```
    This powerful feature allows for the addition of new recipients to an already encrypted file without re-encrypting the entire payload. Q-SEAL re-encapsulates the existing file key for the new recipient, making it accessible to them while leaving the original encrypted data untouched. This is particularly useful for collaborative environments or when sharing encrypted data with new team members.

*   **Inspecting Recipients:**
    ```bash
    mace recipients list file1.mace
    ```
    This command provides a clear overview of all authorized recipients for a given encrypted file, enhancing transparency and auditability.

*   **Limits (Nonce/Size Guidance):**
    ```bash
    mace limits
    ```
    Provides guidance on nonce usage and size limitations, crucial for maintaining cryptographic hygiene and preventing potential vulnerabilities related to nonce reuse or excessive data volumes.

### Operational Insights and System Diagnostics

Q-SEAL includes utilities for system information and configuration management, crucial for troubleshooting and maintaining optimal security posture.

*   **System Information:**
    ```bash
    mace sysinfo [--json]
    ```
    This command provides detailed information about the device's security posture, including Biometry status, FIPS compliance status, and the presence of the ML-KEM shim. The `--json` flag outputs the information in a machine-readable JSON format, facilitating integration with automated security auditing tools.

### Configuration Management

Q-SEAL allows for user-level configuration to tailor its behavior to specific preferences. Configuration settings are stored in `~/.config/mace/config.toml`.

*   **Show Configuration:**
    ```bash
    mace config show
    ```
*   **Set Configuration:**
    ```bash
    mace config set banner=false
    mace config set theme=dark
    ```
    Supported keys include `banner` (true/false), `color` (true/false), and `theme` ("auto"|"dark"|"light"|"mono").

## The Q-SEAL Security Policy: Unwavering Principles

Q-SEAL is built upon a foundation of stringent security principles, designed to provide maximum protection and user assurance:

*   **Passwordless Posture:** All cryptographic operations that require access to sensitive key material leverage the macOS Secure Enclave. This means that when your macOS session is unlocked (via password, Touch ID, or Face ID), Q-SEAL can perform cryptographic operations without requiring additional password prompts. This design significantly reduces the risk of phishing attacks and keylogger compromises.
*   **Device-Bound Keys (ThisDeviceOnly):** The cryptographic keys generated and utilized by Q-SEAL are inextricably linked to the specific macOS device's Secure Enclave. This 


means the keys are generated and stored within the Secure Enclave and cannot be extracted or migrated to another device. Even if an attacker gains access to your encrypted files, they cannot decrypt them without physical access to your specific macOS device and its unlocked Secure Enclave.
*   **Non-Exportable Keys:** The keys managed by Q-SEAL within the Secure Enclave are explicitly marked as non-exportable. This critical security feature prevents the keys from ever leaving the Secure Enclave, even through sophisticated software attacks or forensic analysis. This design choice provides a robust defense against key exfiltration.
*   **ML-KEM-1024 Integration:** The mandatory inclusion of ML-KEM-1024 ensures that key encapsulation mechanisms are resistant to attacks from future quantum computers. This hybrid approach combines the strengths of classical cryptography for performance and established security with the forward-looking protection of post-quantum algorithms.
*   **Auditable and Transparent Operations:** While leveraging hardware-backed security, Q-SEAL aims for transparency in its operations. The command-line interface provides clear feedback, and the underlying design principles are openly documented, allowing for scrutiny by security professionals and cryptographers.

## Command Reference: A Quick Overview

For a concise reference of Q-SEAL's primary commands and their functionalities, consult the table below:

| Command | Synopsis | Authentication/User Interaction | Key Security & Notes |
|---|---|---|---|
| `mace keygen --label <id>` | Creates a new local identity (Secure Enclave P-256 + ML-KEM-1024) and writes the public key to `~/.mace/<id>.pub`. | No explicit prompts; leverages macOS session unlock. | Keys are device-bound and non-exportable, residing within the Secure Enclave. |
| `mace encrypt --recipient <id> <file>` | Encrypts a specified file for one or more recipients. | Not required. | Employs Header HMAC-SHA-384 and AES-256-GCM streaming; Associated Data (AD) binds header MAC for integrity. |
| `mace decrypt <file.mace>` | Decrypts an encrypted file. | No explicit prompts; leverages macOS session unlock. | Passwordless decryption; relies on device-bound keys in the Secure Enclave. |
| `mace verify <file.mace>` | Performs structural checks on the encrypted file's header. | Not required. | Validates header format and integrity without full decryption. |
| `mace verify --auth <file.mace>` | Conducts a full authenticity check, including header MAC and all GCM tags. | No explicit prompts; leverages macOS session unlock. | Passwordless authenticity verification, ensuring data has not been tampered with. |
| `mace sysinfo [--json]` | Displays device posture, FIPS status, and ML-KEM shim presence. | Not required. | Provides crucial environmental and security status for diagnostics and compliance. |
| `mace rekey --pub ~/.mace/<id>.pub ... --input in.mace --output out.mace` | Adds new recipients to an existing encrypted file by re-encapsulating the file key. | Requires Secure Enclave interaction for key access. | Re-encapsulates the existing file key; the encrypted payload remains untouched, ensuring efficiency. |
| `mace key-rotate --label <id>` | Rotates the local identity, generating a fresh Secure Enclave P-256 + ML-KEM-1024 key pair. | Requires Secure Enclave interaction for key generation. | Writes a new public key to `~/.mace/<id>.pub` for distribution, enhancing forward secrecy. |

## Contributing to Q-SEAL: Join the Vanguard of Quantum-Resistant Security

We welcome and encourage contributions from cryptographers, developers, security researchers, and enthusiasts who share our vision for a more secure digital future. Your expertise can help fortify Q-SEAL and expand its capabilities. To contribute, please adhere to the following guidelines:

1.  **Code of Conduct:** We are committed to fostering an open and welcoming environment. Please review and abide by our Code of Conduct (link to be provided in `CODE_OF_CONDUCT.md`).
2.  **Reporting Issues:** If you discover a bug, security vulnerability, or have a feature request, please open an issue on the GitHub repository. Provide detailed information, including steps to reproduce, expected behavior, and your system configuration.
3.  **Feature Development & Bug Fixes:**
    *   Fork the repository and create a new branch for your contributions.
    *   Ensure your code adheres to the existing coding style and conventions.
    *   Write clear, concise commit messages.
    *   Include comprehensive unit tests for new features or bug fixes.
    *   Submit a Pull Request (PR) to the `main` branch. Provide a detailed description of your changes and their impact.
4.  **Documentation Improvements:** High-quality documentation is crucial. We welcome contributions to improve clarity, accuracy, and completeness of the README, man pages, and any future documentation.

For more detailed instructions on setting up your development environment and contributing code, please refer to the `CONTRIBUTING.md` file (to be created).

## License

This project is licensed under the [LICENSE_FILE_NAME] - see the [LICENSE_FILE_NAME] file for details. (Note: Please replace `[LICENSE_FILE_NAME]` with the actual license file name, e.g., `LICENSE.md` or `LICENSE.txt`)

## Contact

For general inquiries, support, or to discuss potential collaborations, please utilize the GitHub issues page. For sensitive security disclosures, please refer to our security policy (to be provided in `SECURITY.md`).

---

*This README was meticulously crafted by Manus AI, leveraging advanced natural language generation and an understanding of cryptographic principles to articulate the profound significance of Q-SEAL.*

