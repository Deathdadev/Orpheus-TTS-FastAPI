# 🎙️ Orpheus-TTS-FastAPI

![Orpheus TTS Banner](https://camo.githubusercontent.com/3c99649fc863a790e02b208591bcdadb1daf399f5170b879e63a73731ed0275c/68747470733a2f2f6c65782d61752e6769746875622e696f2f4f7270686575732d466173744150492f42616e6e65722e706e67)

A Pinokio script for running [Orpheus-FastAPI](https://github.com/Lex-au/Orpheus-FastAPI) - a high-performance text-to-speech API service built on the Llama-3b backbone.

[![Apache License 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/Lex-au/Orpheus-FastAPI/blob/main/LICENSE)

## 🌟 Overview

Orpheus TTS is an open-source text-to-speech system that demonstrates the emergent capabilities of using LLMs for speech synthesis. This repository provides a Pinokio script for easy deployment of the Orpheus-FastAPI server, which offers:

- OpenAI-compatible API endpoints
- Modern web interface with waveform visualization
- Support for 8 different voices with emotion tags
- High-performance processing optimized for RTX GPUs

## ✨ Features

- **One-Click Deployment**: Easy setup through Pinokio
- **OpenAI API Compatible**: Drop-in replacement for OpenAI's `/v1/audio/speech` endpoint
- **Multiple Voices**: 8 different voice options with unique characteristics
- **Emotion Tags**: Support for laughter, sighs, and other emotional expressions
- **Unlimited Audio Length**: Generate audio of any length through intelligent batching
- **Web UI Configuration**: Configure all server settings directly from the interface
- **Hardware Optimization**: Automatic detection and optimization for different GPUs

## 🔧 Prerequisites

- [LM Studio](https://lmstudio.ai/) must be installed and running locally
- Pinokio environment
- CUDA-compatible GPU recommended (RTX series for best performance)
- Python 3.8-3.11 (Python 3.12 is not supported)

## 🚀 Quick Start

1. Install [LM Studio](https://lmstudio.ai/)
2. Set up your [Pinokio](https://pinokio.computer/) environment
3. Run this script through Pinokio
4. LM Studio will automatically download and load the Orpheus model
5. Access the web interface at http://localhost:5005/
6. Use the API endpoints as documented in the [Orpheus-FastAPI documentation](https://github.com/Lex-au/Orpheus-FastAPI#api-usage)

## 🎧 Voice Options

The system supports 8 different voices, each with unique characteristics:

- `tara`: Female, conversational, clear
- `leah`: Female, warm, gentle
- `jess`: Female, energetic, youthful
- `leo`: Male, authoritative, deep
- `dan`: Male, friendly, casual
- `mia`: Female, professional, articulate
- `zac`: Male, enthusiastic, dynamic
- `zoe`: Female, calm, soothing

## 🔄 Emotion Tags

Add expressiveness to your text with emotion tags:

- `<laugh>`: Add laughter
- `<sigh>`: Add a sigh
- `<chuckle>`: Add a chuckle
- And more: `<cough>`, `<sniffle>`, `<groan>`, `<yawn>`, `<gasp>`

Example: `"Well, that's interesting <laugh> I hadn't thought of that before."`

## 🖥️ Technical Details

### Pinokio Script Workflow

1. **Installation** (`install.js`):
   - Clones the Orpheus-FastAPI repository from GitHub
   - Installs PyTorch with hardware-specific optimizations
   - Uses the fast `uv` package manager instead of traditional pip
   - Installs additional dependencies like gradio and devicetorch

2. **Startup** (`start.js`):
   - Manages the LM Studio server (stops existing instances, starts with CORS enabled)
   - Downloads and loads the `lex-au/Orpheus-3b-FT-Q8_0` model
   - Launches the FastAPI server with the Python app
   - Automatically opens the Web UI when ready

3. **Maintenance**:
   - Update functionality to keep both the Pinokio script and Orpheus-FastAPI up to date
   - Reset option to completely remove the app and start fresh

### Hardware Optimization

The system features intelligent hardware detection that automatically optimizes performance based on your hardware capabilities:

- **NVIDIA GPUs**: Uses CUDA 12.1 optimizations (special handling for 50-series GPUs with CUDA 12.8)
- **AMD GPUs**: Uses DirectML on Windows and ROCm 6.0 on Linux
- **CPU-only**: Configures for optimal CPU performance
- **Platform-specific**: Different configurations for Windows, macOS, and Linux

### Model Options

The Orpheus-FastAPI supports different quantized versions of the model:

- **Q8_0** (Default): `lex-au/Orpheus-3b-FT-Q8_0` - High-quality 8-bit quantization
- **Q4_K_M**: `lex-au/Orpheus-3b-FT-Q4_K_M` - Balanced quality/speed with 4-bit quantization
- **Q2_K**: `lex-au/Orpheus-3b-FT-Q2_K` - Ultra-fast inference with 2-bit quantization (~50% faster than Q8_0)

Lower bit models (Q2_K, Q4_K_M) can provide approximately 2x realtime performance on high-end GPUs while maintaining good audio quality.

## 📚 Learn More

For more detailed information about the API endpoints, configuration options, and technical details, visit the [Orpheus-FastAPI GitHub repository](https://github.com/Lex-au/Orpheus-FastAPI).

## 📄 License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.
