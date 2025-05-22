# Wastelands Architecture

## Overview

Wastelands is designed as a cybersecurity learning platform with local AI assistance. The architecture focuses on providing a guided, game-like learning experience while maintaining security and privacy.

## Core Components

### Learning System

The learning system organizes cybersecurity education into missions, quests, and objectives:

```
┌─────────────────────────────────────────────────────────────┐
│                        MISSIONS                              │
│          (Complete Learning Paths - e.g., Web Security)      │
└────────────────────────────┬────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────┐
│                         QUESTS                               │
│          (Specific Learning Tasks - e.g., XSS Attacks)       │
└────────────────────────────┬────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────┐
│                       OBJECTIVES                             │
│      (Measurable Outcomes - e.g., Identify DOM-based XSS)    │
└─────────────────────────────────────────────────────────────┘
```

### Local AI Assistant

The AI assistant is built on local models to ensure privacy and offline capability:

- **Engine**: Ollama/llama.cpp for efficient inference
- **Models**: Smaller, specialized models for cybersecurity assistance
- **Interaction**: Command-line and GUI interfaces
- **Limitations**: Restricted to local models only

### Tool Integration

Security tools are wrapped with educational interfaces:

- **Tool Wrappers**: Simplified interfaces with educational guidance
- **Documentation**: Integrated help and explanations
- **Execution**: Sandboxed environments for safe practice
- **Categories**: Network, Web, Crypto, Forensics, etc.

### Challenge Environment

Isolated environments for hands-on practice:

- **Sandboxing**: Containerization for safe execution
- **Scenarios**: Real-world security situations
- **Validation**: Automatic checking of solutions
- **Progression**: Increasing difficulty levels

## Data Flow

```
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│  User Input   │────▶│  AI Assistant │────▶│    Response   │
└───────┬───────┘     └───────┬───────┘     └───────────────┘
        │                     │
        │                     ▼
        │             ┌───────────────┐
        │             │  Knowledge    │
        │             │  Base (Local) │
        │             └───────────────┘
        │
        ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│  Tool Request │────▶│  Tool Wrapper │────▶│    Results    │
└───────────────┘     └───────┬───────┘     └───────────────┘
                              │
                              ▼
                      ┌───────────────┐
                      │  Sandboxed    │
                      │  Environment  │
                      └───────────────┘
```

## Security Considerations

- **Isolation**: All tools run in sandboxed environments
- **Privacy**: No data sent to external services
- **Permissions**: Least privilege principle for all components
- **Monitoring**: Activity logging for educational purposes
- **Content Control**: Responsible security education focus

## Technical Implementation

- **Frontend**: Simple CLI and web interface
- **Backend**: Python and Bash for tool integration
- **AI**: Ollama for model management
- **Containerization**: Docker for challenges and tools
- **Data Storage**: Local files and SQLite for progress tracking

## Limitations

- **AI Capabilities**: Limited by local model size and capabilities
- **Tool Coverage**: Initial focus on common security tools
- **Challenge Complexity**: Simplified versions of real-world scenarios
- **Resource Requirements**: Depends on local hardware for AI performance