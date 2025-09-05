# Q-SEAL: The Apex of macOS Cryptographic Security – Quantum-Resistant, Device-Bound, and Engineered for the Future

## Unveiling Q-SEAL: A Strategic Imperative in an Evolving Threat Landscape

In an era defined by unprecedented digital vulnerabilities and the imminent dawn of quantum computing, the safeguarding of sensitive information transcends mere best practice—it becomes a strategic imperative. Q-SEAL, formerly known as Mace, stands as a monumental leap forward in cryptographic defense. This meticulously engineered command-line interface (CLI) tool delivers an unparalleled synthesis of **device-bound, post-quantum hybrid secure enclave streaming file encryption**, exclusively tailored for the macOS ecosystem. Q-SEAL is not merely a utility; it is a declaration of digital sovereignty, a bulwark against the most sophisticated cyber threats, and a testament to the enduring power of cryptographic innovation.

### A New Epoch of Digital Trust: What Q-SEAL Embodies

Q-SEAL is the embodiment of next-generation security, a testament to the relentless pursuit of uncompromised data protection. It represents:

*   **Unassailable Confidentiality:** By leveraging the inherent hardware-backed security of the macOS Secure Enclave, Q-SEAL ensures that your most critical data remains perpetually confidential, accessible only under the most stringent, hardware-enforced conditions.
*   **Future-Proof Resilience:** The integration of cutting-edge post-quantum cryptography (specifically ML-KEM-1024) fortifies your data against the theoretical, yet rapidly approaching, threat of quantum cryptanalysis. Q-SEAL ensures that the secrets you protect today remain inviolable for decades to come.
*   **Operational Excellence:** Despite its profound cryptographic depth, Q-SEAL is designed for intuitive, seamless integration into existing workflows. Its passwordless operation, powered by the Secure Enclave, eliminates the most common vectors of human error and credential compromise, streamlining security without sacrificing strength.
*   **A Commitment to Digital Freedom:** In a world where data is increasingly weaponized, Q-SEAL empowers individuals, enterprises, and governmental bodies to reclaim control over their digital assets, ensuring privacy, integrity, and the freedom to operate securely.

### The Vanguard of Security: Who Stands to Gain from Q-SEAL?

Q-SEAL is an indispensable strategic asset for a diverse spectrum of high-stakes stakeholders, each finding unparalleled value in its robust capabilities:

*   **For the Cryptographer & Security Researcher:** Dive into a living, breathing implementation of advanced cryptographic primitives. Explore the intricate dance between ML-KEM-1024 and traditional AES-256-GCM, the nuances of modular AEAD, and the secure interaction with hardware enclaves. Q-SEAL offers a fertile ground for analysis, validation, and the advancement of quantum-resistant cryptographic research.
*   **For the Elite Programmer & System Architect:** Integrate a battle-hardened, Swift-native encryption solution into your mission-critical applications. Understand the elegant design patterns for secure file I/O, the robust error handling, and the seamless interaction with macOS security frameworks. Q-SEAL is a blueprint for building truly secure software ecosystems.
*   **For the Reverse Engineer & Threat Analyst:** Unravel the layers of a state-of-the-art encryption scheme. Q-SEAL presents a formidable challenge and an invaluable learning opportunity, showcasing the techniques employed to create resilient, tamper-evident data containers. Its design provides deep insights into defensive cryptographic engineering.
*   **For Government Officials & National Security Agencies:** Secure classified communications, sensitive intelligence, and critical infrastructure data with a solution engineered for compliance and resilience against state-sponsored adversaries. Q-SEAL offers verifiable, device-bound encryption, aligning with the most stringent security mandates and providing a crucial layer of defense in an increasingly complex geopolitical landscape.
*   **For Forward-Thinking Enterprises & Intellectual Property Stewards:** Protect your most valuable assets—proprietary algorithms, trade secrets, client data, and strategic communications—from industrial espionage and data exfiltration. Q-SEAL ensures that your intellectual capital remains tethered to authorized devices, even in the face of physical compromise or insider threats.
*   **For Privacy Advocates & High-Value Individuals:** Reassert control over your digital life. Q-SEAL provides an ironclad defense against unauthorized surveillance and data breaches, ensuring that your personal and professional communications remain sacrosanct and private.

### The Imperative of Q-SEAL: Navigating the Quantum Horizon

The urgency for Q-SEAL is amplified by the escalating sophistication of cyberattacks and the impending quantum threat. Its critical importance is anchored in several foundational pillars, each representing a distinct advantage:

1.  **Hardware-Anchored, Device-Bound Security:** Q-SEAL leverages the macOS Secure Enclave, a dedicated, isolated hardware security module, to generate, store, and manage cryptographic keys. This architectural choice ensures that decryption keys are never exposed to the main CPU, are immune to software-based attacks, and are inextricably linked to the specific macOS device. The implication is profound: even if encrypted data is exfiltrated, it remains an impenetrable cipher without physical access to the authorized hardware and its unlocked Secure Enclave. This creates an unparalleled physical and logical security perimeter.
2.  **Elimination of the Human Element: Passwordless Operation:** The most significant vulnerability in any security chain is often the human factor. Q-SEAL fundamentally addresses this by adopting a passwordless operational model. Authentication and key management are handled transparently and securely by the Secure Enclave, relying on macOS session unlock mechanisms (e.g., Touch ID, Face ID, or system password). This drastically reduces the attack surface against brute-force, phishing, and credential stuffing attacks, transforming a common weakness into an inherent strength.
3.  **Proactive Quantum Resistance: ML-KEM-1024 Integration:** The integration of ML-KEM-1024 (Module-Lattice-based Key Encapsulation Mechanism), a leading candidate in the NIST Post-Quantum Cryptography Standardization process, positions Q-SEAL at the absolute forefront of future-proof security. This **hybrid cryptographic approach** seamlessly combines the proven efficiency of classical AES-256-GCM with the forward-looking protection of ML-KEM-1024. This ensures that data encrypted today will remain secure against the theoretical capabilities of future quantum computers, guaranteeing long-term confidentiality and integrity against even the most advanced adversaries.
4.  **Modular AEAD and Composite Encapsulation: Cryptographic Agility:** Q-SEAL's design incorporates Authenticated Encryption with Associated Data (AEAD) and a sophisticated composite encapsulation scheme. This modularity not only enhances cryptographic agility—allowing for future algorithm updates with minimal disruption—but also ensures robust integrity checks. This prevents any form of tampering or unauthorized modification to encrypted data, guaranteeing its authenticity from source to destination.
5.  **Operational Simplicity for Unrivaled Security:** Despite its deeply sophisticated cryptographic underpinnings, Q-SEAL is engineered for intuitive command-line interaction. This delicate balance of profound security and operational ease makes it accessible to a broad spectrum of technical users, from seasoned cryptographers to system administrators, enabling widespread adoption of best-in-class encryption practices without a steep learning curve.
6.  **Comprehensive Data Lifecycle Protection: Beyond Basic Encryption:** Q-SEAL extends beyond mere file encryption, offering nuanced features that provide holistic data protection across its entire lifecycle. This includes automated folder archiving, intelligent exclusion presets for development environments (e.g., `.git`, `node_modules`, build artifacts), and meticulous preservation of macOS extended attributes (xattrs) and Access Control Lists (ACLs). This ensures that not only the data content but also its critical metadata and structural integrity are preserved and protected.

Q-SEAL is not merely a tool; it is a strategic imperative for anyone committed to safeguarding digital assets in an era of unprecedented technological evolution and persistent cyber threats. It represents the convergence of cutting-edge cryptography, hardware-backed security, and pragmatic usability, delivering unparalleled peace of mind in a world that increasingly demands it.

## Installation Instructions: Deploying Q-SEAL – A Guide for the Discerning Professional

Q-SEAL is meticulously designed for optimal performance and security within macOS environments (version 13 and newer). Its post-quantum capabilities are intrinsically linked to the ML-KEM-1024 implementation, necessitating a robust integration with a compatible library such as `liboqs`.

### Essential Prerequisites: Laying the Foundation for Uncompromised Security

Before embarking on the deployment of Q-SEAL, ensure your system is prepared with the following foundational components:

*   **macOS Operating System:** Q-SEAL demands macOS Ventura (version 13) or a later iteration. This requirement stems from its reliance on specific APIs and advanced security features introduced in these modern macOS releases, which are crucial for its Secure Enclave integration and overall performance.
*   **Xcode Command Line Tools:** These indispensable tools provide the core development components, including compilers (Clang), linkers, and essential system headers, which are vital for the successful compilation of Swift projects. Install them via your terminal with the following command:
    ```bash
    xcode-select --install
    ```
*   **liboqs (Open Quantum Safe Library):** This library is the cornerstone of Q-SEAL's post-quantum capabilities, providing the robust ML-KEM-1024 implementation. To ensure absolute compatibility and to circumvent potential linker warnings or errors related to deployment targets, it is **imperative to build `liboqs` directly from its source code**. This guarantees that `liboqs` is compiled precisely for your system's architecture and macOS version.

    **Step-by-Step Guide: Building `liboqs` from Source for Optimal Integration**

    1.  **Acquire the `liboqs` Repository:** Begin by cloning the official `liboqs` GitHub repository to your local machine:
        ```bash
        git clone https://github.com/open-quantum-safe/liboqs
        cd liboqs
        ```
    2.  **Configure the Build Environment with CMake:** Utilize CMake to configure the `liboqs` build process. Pay close attention to the `CMAKE_OSX_DEPLOYMENT_TARGET` flag, which must accurately reflect your specific macOS version. This critical step ensures that `liboqs` is compiled with the correct deployment target, preventing compatibility issues.
        ```bash
        cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_DEPLOYMENT_TARGET=13.0 -DBUILD_SHARED_LIBS=OFF
        ```
        *Note: If your macOS version differs from 13.0, **adjust `-DCMAKE_OSX_DEPLOYMENT_TARGET=13.0` accordingly** (e.g., `14.0` for Sonoma). This precise targeting is vital for seamless integration.*
    3.  **Compile `liboqs`:** Execute the build command to compile the `liboqs` library. This process may take several minutes depending on your system's specifications.
        ```bash
        cmake --build build --config Release
        ```
    4.  **Install `liboqs` to Your System:** Finally, install the compiled `liboqs` library to a location accessible by your system's linker. The default installation path is typically `/usr/local/lib` and `/usr/local/include`.
        ```bash
        sudo cmake --install build
        ```
        *Critical Note: Should you opt for a non-standard installation path for `liboqs` (e.g., not within Homebrew's default prefix), you **must** explicitly adjust the `CMAKE_INSTALL_PREFIX` during the CMake configuration step. Furthermore, ensure that the chosen installation directory is included in your system's linker search paths to guarantee that Q-SEAL can locate and link against `liboqs` successfully.*

### Q-SEAL Deployment Methods: Choose Your Path to Enhanced Security

Once all prerequisites are meticulously satisfied, you can proceed with the deployment of Q-SEAL using one of the following highly effective methods:

#### Method 1: Swift Package Manager (Source Build) – The Definitive Choice for Developers, Researchers, and Custom Deployments

This method offers the utmost control over the build process, making it the preferred choice for developers, security researchers, and environments requiring bespoke configurations or in-depth analysis of the source code.

1.  **Clone the Q-SEAL Repository:** Obtain the Q-SEAL source code by cloning its official GitHub repository:
    ```bash
    git clone https://github.com/AnubisQuantumCipher/mace
    cd mace
    ```
2.  **Build Q-SEAL in Release Mode:** Compile the Q-SEAL binary and its dependencies, optimizing for performance and stability. This command ensures that the final executable is production-ready.
    ```bash
    swift build -c release
    ```
3.  **Install the Q-SEAL Executable:** Place the compiled `mace` executable into a standard system location, making it globally accessible from any terminal session.
    ```bash
    sudo install -m 0755 .build/release/mace /usr/local/bin/mace
    ```
4.  **Validate the Installation:** Confirm the successful deployment of Q-SEAL by invoking its help documentation:
    ```bash
    mace --help
    ```
    A successful output indicates that Q-SEAL is correctly installed and ready for operation.

#### Method 2: One-Liner Installer – Expedited Deployment for General Users and Rapid Setup

For users prioritizing speed and simplicity, the one-liner installer provides an automated, streamlined deployment process. This script intelligently handles the cloning, building, and installation steps, minimizing manual intervention.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AnubisQuantumCipher/mace/main/script/install.sh)"
```

*Important Note on `liboqs` Linker Warnings:* Should you encounter any linker warnings or errors pertaining to `liboqs` deployment targets after utilizing the one-liner installer, it typically signifies a version mismatch or an incompatible pre-compiled `liboqs` binary. In such instances, it is **strongly recommended to revert to the detailed `liboqs` source build instructions** provided in the "Essential Prerequisites" section. Building `liboqs` from source guarantees precise compatibility with your macOS environment, resolving most common installation anomalies and ensuring Q-SEAL's full functionality.

## Operationalizing Q-SEAL: A Comprehensive Guide to Unlocking Advanced Security

Q-SEAL offers a powerful yet intuitively designed command-line interface, engineered for seamless integration into your existing security workflows. The following sections provide an exhaustive overview of its core functionalities and their strategic applications, empowering you to harness the full spectrum of device-bound, post-quantum hybrid encryption.

### Key Management: Forging Your Immutable Digital Identity

At the very core of Q-SEAL's formidable security architecture lies its robust key management system, which leverages the macOS Secure Enclave for hardware-backed cryptographic operations. Every key generated by Q-SEAL is inherently **device-bound** and **non-exportable**, guaranteeing an unparalleled degree of security and control over your cryptographic assets.

*   **Key Generation (Passwordless, Device-Bound):**
    ```bash
    mace keygen --label <your-label>
    ```
    This command initiates the creation of a new, unique local identity. The Secure Enclave, an isolated hardware component, generates a highly secure P-256 elliptic curve key pair and an ML-KEM-1024 key pair. These cryptographic assets are then securely provisioned and stored within the hardware, never exposed to the main system. A corresponding public key (`~/.mace/<your-label>.pub`) is generated for secure distribution to your intended recipients, enabling them to encrypt data specifically for your device. This entire process is elegantly passwordless, as authentication is seamlessly handled by the Secure Enclave's biometric (Touch ID/Face ID) or passcode mechanisms when your macOS session is unlocked, providing both convenience and ironclad security.

*   **Quick Setup (Identity + Defaults):**
    ```bash
    mace setup --label <your-label>
    ```
    For rapid deployment scenarios, this command streamlines the identity creation process. It efficiently sets up a new key pair with optimal default configurations and generates the necessary public key, allowing for immediate secure operations.

*   **Rotating Identity: Maintaining Forward Secrecy and Mitigating Compromise:**
    ```bash
    mace key-rotate --label <your-label>
    ```
    In dynamic security environments, periodic key updates are paramount. This command facilitates the secure rotation of your local identity. A fresh Secure Enclave P-256 and ML-KEM-1024 key pair is generated, and a new public key is written to `~/.mace/<your-label>.pub` for subsequent distribution. This proactive measure ensures forward secrecy, significantly limiting the impact of any potential future key compromises and enhancing long-term cryptographic hygiene.

### Data Encryption: Architecting Impenetrable Digital Envelopes

Q-SEAL provides sophisticated and flexible options for encrypting both individual files and entire directories, incorporating advanced features for meticulous metadata preservation and intelligent selective exclusion, ensuring comprehensive data protection.

*   **Encrypting a File: Precision Security for Individual Assets:**
    ```bash
    mace encrypt --recipient <your-label> file1.txt
    ```
    This command encrypts `file1.txt` for the specified recipient(s). Q-SEAL employs a highly sophisticated cryptographic scheme that combines a Header HMAC-SHA-384 for robust integrity verification with AES-256-GCM for high-throughput authenticated encryption. The Authenticated Data (AD) mechanism cryptographically binds the header MAC to the ciphertext, creating an unbreakable link that prevents any form of tampering or unauthorized modification to the encrypted stream, guaranteeing its authenticity and integrity.

*   **Encrypting a Folder (Auto-archive): Comprehensive Project Protection:**
    ```bash
    mace encrypt --recipient <your-label> MyProject/
    ```
    To secure entire project directories, code repositories, or collections of sensitive files, Q-SEAL offers an intelligent folder encryption capability. This command automatically archives the `MyProject/` directory into a `.tar` file *before* encryption, meticulously preserving the original directory structure, file permissions, and timestamps. This ensures that the integrity of your project is maintained within the encrypted archive. Furthermore, Q-SEAL provides advanced exclusion options for granular control:
    *   **Development Exclusion Preset:** Utilize `--exclude-preset dev` to intelligently skip common development clutter such as `.git` repositories, `.build` directories, `node_modules`, `Pods`, and other transient or generated files. This ensures that only relevant, sensitive data is encrypted, optimizing performance and storage.
    *   **Custom Exclusions:** Employ `--exclude "*.log" --exclude .DS_Store` to define bespoke patterns for files or directories that should be excluded from the encryption process. This allows for highly customized security policies.
    *   **Metadata Preservation:** By default, Q-SEAL meticulously preserves macOS extended attributes (xattrs) and Access Control Lists (ACLs) during the encryption process, maintaining crucial file system metadata. For scenarios where this metadata is not required or undesirable, use the `--no-preserve-xattrs` flag to omit it.

### Data Decryption and Verification: Unlocking and Validating Encrypted Intelligence

Q-SEAL simplifies the decryption process, leveraging the Secure Enclave for a truly passwordless experience, and provides robust, cryptographically sound mechanisms for verifying the integrity and authenticity of your encrypted data.

*   **Decrypting a File (Passwordless, Device-Bound): Seamless Access to Protected Data:**
    ```bash
    mace decrypt file1.mace
    ```
    This command initiates the decryption of `file1.mace`. The decryption process is entirely passwordless, relying on the Secure Enclave to securely unlock the file encryption key. This seamless operation significantly enhances user experience without compromising security, as the sensitive key material never leaves the hardware boundary of the Secure Enclave, remaining protected from software-based attacks.

*   **Decrypting and Extracting Folder Archives: Restoring Project Integrity:**
    ```bash
    mace decrypt --extract MyProject.tar.mace
    ```
    For encrypted folder archives, this command performs a dual function: it decrypts the `.mace` file and then automatically extracts its contents, restoring the original directory structure and files. To ensure a clean workspace, use the `--remove-archive` flag to delete the intermediate `.tar` file after successful extraction.

*   **One-Step Extraction: Expedited Archive Recovery:**
    ```bash
    mace extract MyProject.tar.mace
    ```
    This convenient command intelligently detects the tar payload within the `.mace` file and executes a combined decryption and extraction operation in a single, efficient step, streamlining the recovery of archived projects.

*   **Verifying Header Integrity: Initial Data Validation:**
    ```bash
    mace verify file1.mace
    ```
    This command performs essential structural checks on the encrypted file's header. It validates the header's format and ensures its conformity to Q-SEAL's specifications. This provides a rapid, initial integrity check that does not require interaction with the Secure Enclave, making it ideal for quick assessments.

*   **Verifying Authenticity (Passwordless): Cryptographic Assurance of Data Origin and Integrity:**
    ```bash
    mace verify --auth file1.mace
    ```
    For a comprehensive and cryptographically rigorous authenticity verification, this command performs a full check, encompassing the header MAC (Message Authentication Code) and all GCM (Galois/Counter Mode) tags embedded within the encrypted stream. This operation leverages the Secure Enclave for passwordless authentication, providing an ironclad guarantee that the data has not been tampered with and originates from an authorized, trusted source. This is crucial for forensic analysis and ensuring data provenance.

*   **Rekeying (Adding Recipients): Dynamic Access Management:**
    ```bash
    mace rekey --pub ~/.mace/laptop.pub --input file1.mace --output file1.mace.new
    ```
    This powerful feature enables dynamic access management by allowing the addition of new recipients to an already encrypted file *without* requiring the re-encryption of the entire payload. Q-SEAL efficiently re-encapsulates the existing file key for the new recipient, making the data accessible to them while leaving the original encrypted data untouched. This is an invaluable capability for collaborative environments, secure data sharing with new team members, or evolving access control requirements.

*   **Inspecting Recipients: Transparency in Access Control:**
    ```bash
    mace recipients list file1.mace
    ```
    This command provides a clear, auditable overview of all authorized recipients for a given encrypted file, enhancing transparency and facilitating robust access control management.

*   **Limits (Nonce/Size Guidance): Maintaining Cryptographic Hygiene:**
    ```bash
    mace limits
    ```
    This command provides essential guidance on nonce usage and size limitations. Adhering to these guidelines is crucial for maintaining cryptographic hygiene, preventing potential vulnerabilities related to nonce reuse, and ensuring optimal performance and security for large data volumes.

### Operational Insights and System Diagnostics: Ensuring Optimal Security Posture

Q-SEAL integrates essential utilities for comprehensive system information and configuration management, which are vital for proactive troubleshooting, maintaining optimal security posture, and ensuring compliance.

*   **System Information: Real-time Security Posture Assessment:**
    ```bash
    mace sysinfo [--json]
    ```
    This command delivers detailed, real-time information about the device's security posture. This includes the status of Biometry (Touch ID/Face ID), FIPS (Federal Information Processing Standards) compliance status, and the crucial presence and operational status of the ML-KEM shim. The optional `--json` flag outputs this critical information in a machine-readable JSON format, facilitating seamless integration with automated security auditing tools, compliance systems, and continuous monitoring platforms.

### Configuration Management: Tailoring Q-SEAL to Your Operational Needs

Q-SEAL offers granular user-level configuration options, allowing you to precisely tailor its behavior to align with your specific operational preferences and security policies. Configuration settings are persistently stored in `~/.config/mace/config.toml`.

*   **Show Current Configuration:**
    ```bash
    mace config show
    ```
    Displays the current Q-SEAL configuration settings.
*   **Set Configuration Parameters:**
    ```bash
    mace config set banner=false
    mace config set theme=dark
    ```
    Supported configuration keys include `banner` (boolean: `true` or `false` to control the display of the Q-SEAL banner on first run), `color` (boolean: `true` or `false` for terminal output coloring), and `theme` (string: `


"auto"|"dark"|"light"|"mono" for terminal theme preferences).

## The Q-SEAL Security Policy: Unwavering Principles of Cryptographic Assurance

Q-SEAL is architected upon a bedrock of stringent security principles, meticulously designed to deliver maximum protection and unwavering user assurance. These principles are non-negotiable and form the very essence of Q-SEAL's trustworthiness:

*   **Passwordless Posture: Eliminating Credential Vulnerabilities:** All cryptographic operations within Q-SEAL that necessitate access to sensitive key material are seamlessly integrated with the macOS Secure Enclave. This means that once your macOS session is unlocked (via your system password, Touch ID, or Face ID), Q-SEAL can execute cryptographic functions without requiring any additional password prompts. This design choice dramatically reduces the attack surface associated with traditional password-based systems, mitigating risks from phishing, keyloggers, and brute-force attacks. The user experience is streamlined, while security is inherently elevated.
*   **Device-Bound Keys (ThisDeviceOnly): Immutable Hardware-Software Linkage:** The cryptographic keys generated, stored, and utilized by Q-SEAL are inextricably linked to the specific macOS device's Secure Enclave. This fundamental principle ensures that these keys are generated and reside exclusively within the Secure Enclave's isolated hardware environment and **cannot be extracted or migrated** to any other device. Consequently, even in the highly improbable event that an adversary gains access to your encrypted data, it remains an undecipherable cipher without physical access to your authorized macOS device and its unlocked Secure Enclave. This creates an unparalleled, hardware-enforced security perimeter.
*   **Non-Exportable Keys: Preventing Key Exfiltration:** The keys managed by Q-SEAL within the Secure Enclave are explicitly provisioned with a non-exportable attribute. This critical security feature provides an ironclad guarantee that the keys will **never leave the Secure Enclave**, even through sophisticated software exploits, forensic analysis, or malicious insider actions. This design choice represents a robust defense against key exfiltration, a common and devastating attack vector.
*   **ML-KEM-1024 Integration: Proactive Quantum Resilience:** The mandatory inclusion and utilization of ML-KEM-1024 (Module-Lattice-based Key Encapsulation Mechanism) ensures that Q-SEAL's key encapsulation processes are inherently resistant to attacks from future quantum computers. This **hybrid cryptographic approach** intelligently combines the established security and performance of classical AES-256-GCM with the forward-looking, quantum-resistant properties of ML-KEM-1024. This strategic foresight guarantees that data encrypted with Q-SEAL today will remain confidential and integral against the theoretical capabilities of even the most advanced quantum adversaries of tomorrow.
*   **Auditable and Transparent Operations: Trust Through Scrutiny:** While leveraging the opaque nature of hardware-backed security, Q-SEAL is committed to transparency in its operational logic. The command-line interface provides clear, actionable feedback, and the underlying design principles are openly documented. This commitment to transparency allows for rigorous scrutiny by the global security community, cryptographers, and independent auditors, fostering trust and enabling continuous improvement.

## Command Reference: A Concise Tactical Overview

For a rapid and comprehensive understanding of Q-SEAL's primary commands and their critical functionalities, consult the following tactical reference table:

| Command | Synopsis | Authentication/User Interaction | Key Security & Notes |
|---|---|---|---|
| `mace keygen --label <id>` | Creates a new local identity (Secure Enclave P-256 + ML-KEM-1024) and writes the public key to `~/.mace/<id>.pub`. | No explicit prompts; leverages macOS session unlock. | Keys are device-bound and non-exportable, residing within the Secure Enclave. This is the foundation of Q-SEAL's hardware-backed security. |
| `mace encrypt --recipient <id> <file>` | Encrypts a specified file for one or more designated recipients. | Not required. | Employs Header HMAC-SHA-384 for integrity and AES-256-GCM streaming for authenticated encryption. Associated Data (AD) cryptographically binds the header MAC, ensuring tamper-evidence. |
| `mace decrypt <file.mace>` | Decrypts an encrypted file. | No explicit prompts; leverages macOS session unlock. | Passwordless decryption, relying on the device-bound keys securely held within the Secure Enclave. The key material never leaves the hardware. |
| `mace verify <file.mace>` | Performs essential structural checks on the encrypted file's header. | Not required. | Validates the header's format and structural integrity without requiring full decryption or Secure Enclave interaction. |
| `mace verify --auth <file.mace>` | Conducts a full authenticity check, encompassing the header MAC and all GCM tags within the encrypted stream. | No explicit prompts; leverages macOS session unlock. | Provides cryptographic assurance that the data has not been tampered with and originates from an authorized source. |
| `mace sysinfo [--json]` | Displays critical device posture information, including Biometry status, FIPS compliance, and ML-KEM shim presence. | Not required. | Essential for diagnostics, compliance auditing, and assessing the security environment. JSON output available for automation. |
| `mace rekey --pub ~/.mace/<id>.pub ... --input in.mace --output out.mace` | Adds new recipients to an existing encrypted file by efficiently re-encapsulating the file key. | Requires Secure Enclave interaction for key access. | The encrypted payload remains untouched, ensuring efficiency and minimizing re-encryption overhead. Ideal for dynamic access management. |
| `mace key-rotate --label <id>` | Rotates the local identity, generating a fresh Secure Enclave P-256 + ML-KEM-1024 key pair. | Requires Secure Enclave interaction for key generation. | Writes a new public key to `~/.mace/<id>.pub` for distribution, significantly enhancing forward secrecy and cryptographic hygiene. |

## Contributing to Q-SEAL: Join the Vanguard of Quantum-Resistant Security

We extend a formal invitation to cryptographers, developers, security researchers, and dedicated enthusiasts to contribute to the evolution of Q-SEAL. Your expertise is invaluable in fortifying this critical project and expanding its capabilities in the face of emerging threats. To ensure a collaborative and effective development environment, please adhere to the following guidelines:

1.  **Code of Conduct:** Our community is built on respect and professionalism. Please review and strictly abide by our Code of Conduct (link to be provided in `CODE_OF_CONDUCT.md`). This document outlines the expected behavior and standards for all contributors.
2.  **Reporting Issues and Vulnerabilities:** Should you discover a bug, identify a potential security vulnerability, or have a compelling feature request, please open an issue on the official GitHub repository. When reporting, provide comprehensive details, including precise steps to reproduce the issue, the expected behavior, and your system's configuration. For sensitive security disclosures, please refer to our dedicated security policy (to be provided in `SECURITY.md`).
3.  **Feature Development & Bug Fixes:**
    *   **Fork the Repository:** Begin by forking the Q-SEAL repository and creating a new, descriptively named branch for your contributions.
    *   **Adhere to Coding Standards:** Ensure your code strictly adheres to the existing coding style, conventions, and architectural patterns established within the project. Consistency is paramount for maintainability and readability.
    *   **Atomic Commits:** Write clear, concise, and atomic commit messages that accurately describe the purpose and scope of each change.
    *   **Comprehensive Testing:** All new features or bug fixes **must** be accompanied by comprehensive unit tests. These tests should validate the functionality and prevent regressions.
    *   **Pull Request Submission:** Submit a Pull Request (PR) to the `main` branch. Your PR description should provide a detailed explanation of your changes, their rationale, and their impact on the project.
4.  **Documentation Improvements:** High-quality, precise documentation is as critical as robust code. We actively welcome contributions to enhance the clarity, accuracy, and completeness of the README, man pages, and any future technical documentation. Your efforts in this area directly contribute to the project's accessibility and usability.

For more granular instructions on setting up your development environment, running tests, and contributing code, please consult the `CONTRIBUTING.md` file (to be created).

## License

This project is licensed under the [LICENSE_FILE_NAME] - see the [LICENSE_FILE_NAME] file for details. (Note: Please replace `[LICENSE_FILE_NAME]` with the actual license file name, e.g., `LICENSE.md` or `LICENSE.txt`)

## Contact

For general inquiries, technical support, or to explore potential strategic collaborations, please utilize the GitHub issues page. For sensitive security disclosures, please refer to our dedicated security policy (to be provided in `SECURITY.md`).

---

*This README was meticulously crafted by Manus AI, leveraging advanced natural language generation and a profound understanding of cryptographic principles to articulate the strategic significance and technical prowess of Q-SEAL. Your feedback is invaluable in our continuous pursuit of excellence.*

