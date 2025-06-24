# PocketChat Ecosystem

Welcome to PocketChat - a secure, end-to-end encrypted messaging system that prioritises privacy and user control.

## Overview

PocketChat consists of three main components that work together to provide secure messaging:

1. **[Drive Backend](https://github.com/pocketchat/drive-backend)** - Local API server handling encryption and storage
2. **[Drive Frontend](https://github.com/pocketchat/drive-frontend)** - React/Next.js user interface
3. **[Relay Server](https://github.com/pocketchat/relay-server)** - Zero-knowledge message relay service

## Quick Start

### For Users

1. **Visit the PocketChat website**: [pocketchat.joebroughton.tech](https://pocketchat.joebroughton.tech)
2. **Follow the setup guide**: Complete step-by-step instructions for all platforms
3. **Use the Drive Linker**: Automated setup script that coordinates all components

### For Developers

Each repository contains developer-focused documentation. Check out the READMEs in the appropriate repositories.

## Architecture

### Security Model

Checkout [SECURITY_MODEL.MD](https://github.com/PocketChat/Relay-Server/blob/master/SECURITY_MODEL.md) for more detail

PocketChat implements a **zero-knowledge architecture**:

- **End-to-End Encryption**: Messages encrypted client-side before transmission
- **Triple-Layer Security**: AES + RSA for message transmission, and passkey-based local storage encryption
- **Digital Signatures**: Cryptographic message authentication
- **Local-First**: Sensitive data never leaves your device unencrypted

### Component Interaction


```
                       ┌─────────────────┐
                       │   Drive Linker  │
                       │   (Setup Tool)  │
                       └─────────────────┘
                          │           │
                          ▼           ▼
        ┌─────────────────┐           ┌─────────────────┐
        │  Drive Frontend │──────────▶│  Drive Backend  │
        │   (Next.js UI)  │◀──────────│  (FastAPI Local)│
        └─────────────────┘           └─────────────────┘
                ▲ │
                │ ▼
        ┌─────────────────┐
        │  Relay Server   │
        │ (Message Relay) │
        └─────────────────┘
```

### (Simplified) Data Flow

1. **Message Creation**: User types message in Frontend
2. **Local Encryption**: Backend encrypts with recipient's public key
3. **Relay Transmission**: Encrypted message sent to Relay Server
4. **Message Retrieval**: When online, recipient's backend polls Relay Server
5. **Local Decryption**: Backend decrypts with recipient's private key and saves locally
6. **Display**: Frontend displays decrypted message

## Repository Structure

### [Drive Backend](https://github.com/pocketchat/drive-backend)

- **Language**: Python (FastAPI)
- **Purpose**: Local encryption, key management, and storage
- **Key Features**: Triple-layer encryption, digital signatures, local storage

### [Drive Frontend](https://github.com/pocketchat/drive-frontend)

- **Language**: TypeScript (Next.js/React)
- **Purpose**: User interface and client-side operations
- **Key Features**: Chat interface, enrollment wizard, responsive design

### [Relay Server](https://github.com/pocketchat/relay-server)

- **Language**: Python (FastAPI + PostgreSQL)
- **Purpose**: Zero-knowledge message relay
- **Key Features**: Identity authentication, automatic cleanup, rate limiting

### [Drive-Linker](https://github.com/pocketchat/drive-linker)

- **Language**: System scripts + submodules
- **Purpose**: Quick single repo pull and command for running Drive-Frontend and Drive-Backend
- **Key Features**: One liner start command

### [Website](https://github.com/pocketchat/pocket-chat-website)

- **Language**: TypeScript (Next.js)
- **Purpose**: Documentation and setup guides
- **Key Features**: Interactive guides, multi-platform instructions

## Version Compatibility

All repositories use coordinated versioning:

| Version | Backend  | Frontend | Relay    | Status  |
| ------- | -------- | -------- | -------- | ------- |
| 0.1.x   | ✅ 0.1.0 | ✅ 0.1.0 | ✅ 0.1.0 | Current |

## Contributing

We welcome contributions! Each repository has detailed contributing guidelines:

- [Backend Contributing Guide](https://github.com/pocketchat/drive-backend/blob/main/CONTRIBUTING.md)
- [Frontend Contributing Guide](https://github.com/pocketchat/drive-frontend/blob/main/CONTRIBUTING.md)
- [Relay Contributing Guide](https://github.com/pocketchat/relay-server/blob/main/CONTRIBUTING.md)

### Coordinated Development

When contributing across repositories:

1. **Version Sync**: Major.minor versions must match across repos
2. **Testing**: Test integration between all three components
3. **Documentation**: Update relevant documentation in all affected repos
4. **Security**: Follow our security guidelines for cryptographic changes

## Security

Security is our top priority. Please review:

- [Security Model Documentation](https://github.com/pocketchat/relay-server/blob/main/SECURITY_MODEL.md)
- [Vulnerability Reporting](https://github.com/pocketchat/drive-backend/blob/main/SECURITY.md)

### Reporting Security Issues

**Do not report security vulnerabilities through public issues.**

Email: [joe@moored.to](mailto:joe@moored.to)

## License

All PocketChat components are licensed under the Apache License 2.0, which requires attribution and preserves copyright notices.

- [Drive Backend License](https://github.com/pocketchat/drive-backend/blob/main/LICENSE)
- [Drive Frontend License](https://github.com/pocketchat/drive-frontend/blob/main/LICENSE)
- [Relay Server License](https://github.com/pocketchat/relay-server/blob/main/LICENSE)
- [Website License](https://github.com/pocketchat/website/blob/main/LICENSE)

## Community

- **Issues**: Report bugs and request features in individual repositories
- **Discussions**: General questions and community chat
- **Documentation**: User guides at [pocketchat.joebroughton.tech](https://pocketchat.joebroughton.tech)

## Roadmap

- Lets see where things go

---

**PocketChat** - Privacy is right in your pocket.
