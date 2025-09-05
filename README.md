# Q-SEAL: Uncompromising Security for macOS with Device-Bound, PQ-Hybrid Encryption

## Project Overview

Q-SEAL, formerly known as Mace, is a cutting-edge command-line interface (CLI) tool designed to provide robust, device-bound, and post-quantum hybrid secure enclave streaming file encryption specifically for macOS environments. In an era where digital security is paramount, Q-SEAL stands out by offering an unparalleled level of data protection, ensuring that sensitive information remains confidential and inaccessible to unauthorized entities. This project represents a significant leap forward in personal and enterprise data security, leveraging advanced cryptographic techniques and hardware-backed security features inherent to modern macOS devices.

### What it Represents

Q-SEAL embodies the future of secure data handling. It represents a commitment to privacy and data integrity, offering a solution that is both powerful and user-friendly. By integrating with macOS's Secure Enclave, Q-SEAL provides a passwordless encryption experience, eliminating the vulnerabilities associated with traditional password-based systems. Its post-quantum hybrid approach proactively addresses the emerging threat of quantum computing to current cryptographic standards, ensuring long-term security for your data. This project is a testament to the idea that advanced security does not have to come at the cost of usability.

### Who it's For

Q-SEAL is an indispensable tool for:

*   **Individuals with Sensitive Data:** Anyone handling personal documents, financial records, or private communications who demands the highest level of security.
*   **Developers and Researchers:** Those working with proprietary code, confidential research data, or intellectual property that requires stringent protection.
*   **Businesses and Enterprises:** Organizations seeking to secure their internal documents, client data, and intellectual assets against sophisticated cyber threats and future cryptographic compromises.
*   **Privacy Advocates:** Individuals and groups committed to digital privacy who seek robust tools to protect their data from surveillance and unauthorized access.

### Why it's Important

The importance of Q-SEAL cannot be overstated in today's interconnected world. Data breaches are increasingly common, and the threat landscape is constantly evolving. Traditional encryption methods, while effective today, face an existential threat from the rapid advancements in quantum computing. Q-SEAL's significance lies in its:

1.  **Device-Bound Security:** By tying decryption to the Secure Enclave, Q-SEAL ensures that encrypted data can only be accessed on the specific macOS device where it was encrypted, even if the encrypted files are stolen.
2.  **Passwordless Operation:** This eliminates the weakest link in many security chains – human-chosen passwords. The Secure Enclave handles key management, providing a seamless and highly secure user experience.
3.  **Post-Quantum Hybrid Cryptography:** Q-SEAL integrates ML-KEM-1024, a leading post-quantum cryptographic algorithm, alongside established classical cryptography. This hybrid approach provides immediate protection against current threats while future-proofing data against the advent of quantum computers capable of breaking conventional encryption.
4.  **Ease of Use:** Despite its advanced underlying technology, Q-SEAL is designed to be intuitive for users, offering a straightforward command-line interface for encryption, decryption, and key management.
5.  **Comprehensive Data Protection:** Beyond simple file encryption, Q-SEAL offers features like folder encryption with auto-archiving, exclusion presets for development clutter, and preservation of macOS extended attributes, ensuring a holistic approach to data security.

Q-SEAL is more than just an encryption tool; it's a guardian for your digital life, providing peace of mind in an increasingly insecure world.

## Installation Instructions

Q-SEAL requires macOS 13+ and Xcode Command Line Tools. ML-KEM-1024 is mandatory for encryption/decryption, requiring a linked ML-KEM implementation (e.g., liboqs).

### Prerequisites

Before installing Q-SEAL, ensure you have the following:

*   **macOS 13 or newer:** Q-SEAL leverages features specific to modern macOS versions.
*   **Xcode Command Line Tools:** Install them by running `xcode-select --install` in your terminal.
*   **liboqs (Open Quantum Safe library):** This library provides the ML-KEM-1024 implementation. It is recommended to build `liboqs` from source to ensure compatibility with your macOS deployment target.

    **Building liboqs from source:**

    ```bash
    git clone https://github.com/open-quantum-safe/liboqs
    cd liboqs
    cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_DEPLOYMENT_TARGET=13.0 -DBUILD_SHARED_LIBS=OFF
    cmake --build build --config Release
    sudo cmake --install build
    ```

    *Note: Adjust `CMAKE_OSX_DEPLOYMENT_TARGET` to match your macOS version if different from 13.0. If you do not install into Homebrew's prefix, adjust `CMAKE_INSTALL_PREFIX` accordingly.*

### Installation Methods

#### 1. SwiftPM (Source Build)

This method allows you to build and install Q-SEAL directly from its source code using Swift Package Manager.

```bash
git clone https://github.com/AnubisQuantumCipher/mace
cd mace
swift build -c release
sudo install -m 0755 .build/release/mace /usr/local/bin/mace
mace --help
```

#### 2. One-liner Installer (Recommended for quick setup)

For a quick and easy installation, you can use the provided one-liner script. This script automates the process of downloading, building, and installing Q-SEAL.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/AnubisQuantumCipher/mace/main/script/install.sh)"
```

*Note: If you encounter deployment target warnings related to `liboqs` after using the one-liner installer, it is recommended to build `liboqs` from source as described in the Prerequisites section.*

## Usage (Q-SEAL)

Q-SEAL provides a straightforward command-line interface for all its functionalities. Here are some common commands:

*   **Key Generation (Passwordless, Device-Bound):**
    ```bash
    mace keygen --label <your-label>
    ```
    This command creates a local identity using your Secure Enclave, generating device-bound, non-exportable keys.

*   **Quick Setup (Identity + Defaults):**
    ```bash
    mace setup --label <your-label>
    ```

*   **Encrypting a File:**
    ```bash
    mace encrypt --recipient <your-label> file1.txt
    ```
    Encrypts `file1.txt` for the specified recipient. Q-SEAL uses Header HMAC-SHA-384 and AES-256-GCM streaming.

*   **Encrypting a Folder (Auto-archive):**
    ```bash
    mace encrypt --recipient <your-label> MyProject/
    ```
    Encrypts the entire `MyProject/` folder. You can use `--exclude-preset dev` to skip common development clutter (e.g., `.git`, `.build`, `node_modules`) or `--exclude "*.log"` for custom exclusions. Metadata is preserved by default; use `--no-preserve-xattrs` to omit macOS extended attributes/ACLs.

*   **Decrypting a File (Passwordless, Device-Bound):**
    ```bash
    mace decrypt file1.mace
    ```
    Decrypts `file1.mace` using your device-bound Secure Enclave key. No password prompts are required.

*   **Decrypting and Extracting Folder Archives:**
    ```bash
    mace decrypt --extract MyProject.tar.mace
    ```
    Decrypts and extracts the contents of `MyProject.tar.mace`. Use `--remove-archive` to delete the `.tar` file after extraction.

*   **One-step Extraction:**
    ```bash
    mace extract MyProject.tar.mace
    ```
    Automatically detects and extracts the tar payload.

*   **Verifying Header:**
    ```bash
    mace verify file1.mace
    ```
    Performs structural checks on the encrypted file's header.

*   **Verifying Authenticity (Passwordless):**
    ```bash
    mace verify --auth file1.mace
    ```
    Conducts a full authenticity check, including header MAC and all GCM tags, using your Secure Enclave key.

*   **Rekeying (Adding Recipients):**
    ```bash
    mace rekey --pub ~/.mace/laptop.pub --input file1.mace --output file1.mace.new
    ```
    Adds new recipients to an existing encrypted file by re-encapsulating the file key. The payload remains unchanged.

*   **Rotating Identity:**
    ```bash
    mace key-rotate --label <your-label>
    ```
    Rotates your local identity (Secure Enclave P-256 + ML-KEM-1024) and writes a fresh public key to `~/.mace/<your-label>.pub` for distribution.

*   **Inspecting Recipients:**
    ```bash
    mace recipients list file1.mace
    ```

*   **Limits (Nonce/Size Guidance):**
    ```bash
    mace limits
    ```

## Policy

Q-SEAL enforces a **passwordless posture**, meaning all cryptographic operations leverage Secure Enclave keys when your macOS session is unlocked. This eliminates the need for password prompts, streamlining the user experience while enhancing security. The keys are **device-bound (ThisDeviceOnly)** and **non-exportable**, ensuring that your encryption keys never leave the Secure Enclave and are inextricably linked to your specific device.

## Command Reference

| Command | Synopsis | Auth/UI | Notes |
|---|---|---|---|
| `mace keygen --label <id>` | Create local identity (SE P‑256 + ML‑KEM‑1024; write `~/.mace/<id>.pub`) | No prompts | Device‑bound, non‑exportable keys (Secure Enclave). |
| `mace encrypt --recipient <id> <file>` | Encrypt file to recipient(s) | Not required | Header HMAC-SHA-384; AES-256-GCM streaming; AD binds header MAC. |
| `mace decrypt <file.mace>` | Decrypt file | No prompts | Passwordless; device‑bound (Secure Enclave). |
| `mace verify <file.mace>` | Structural checks only | Not required | Parses/validates header format. |
| `mace verify --auth <file.mace>` | Full authenticity (header MAC + all GCM tags) | No prompts | Passwordless authenticity verification. |
| `mace sysinfo [--json]` | Biometry/FIPS/liboqs status | Not required | Shows posture and environment for troubleshooting. |
| `mace rekey --pub ~/.mace/<id>.pub ... --input in.mace --output out.mace` | Add recipients (header-only) | Required | Re-encapsulates existing fileKey; payload untouched. |
| `mace key-rotate --label <id>` | Rotate local identity | Required | Writes fresh `~/.mace/<id>.pub` for distribution. |

## Contributing

We welcome contributions to Q-SEAL! Please refer to the `CONTRIBUTING.md` (if available) for guidelines on how to contribute. If you find any issues or have suggestions, please open an issue on the GitHub repository.

## License

This project is licensed under the [LICENSE_FILE_NAME] - see the [LICENSE_FILE_NAME] file for details.

## Contact

For any inquiries or support, please refer to the GitHub issues page or contact the project maintainers.

---

*This README was generated by Manus AI.*

