# N-Layer Image Processing Neural Network

A configurable multi-layer neural network implementation for image classification tasks, featuring both training and inference capabilities with backpropagation optimization.

## Overview

This project implements a flexible N-layer neural network designed for image processing and classification. The system consists of:

- **Java Neural Network** (`NLayer.java`): Core implementation with configurable architecture
- **Python Image Preprocessor** (`WOOHOO.py`): Image preprocessing pipeline for neural network input
- **Configuration System**: Flexible configuration files for different network architectures
- **Training Data**: Preprocessed image data represented as normalized pixel values

## Architecture

### Neural Network Features
- **Configurable Architecture**: Support for any number of layers and nodes per layer
- **Sigmoid Activation**: Uses sigmoid activation function with derivative support
- **Backpropagation Training**: Gradient descent optimization with configurable learning rate
- **Weight Management**: Random initialization, manual setting, or loading from saved weights
- **Error Monitoring**: Configurable error thresholds and iteration limits

### Current Configuration
The main configuration (`ImageProcessingConfig.txt`) defines a network with:
- **Input Layer**: 13,000 nodes (representing flattened image data)
- **Hidden Layers**: 25 → 5 → 5 nodes
- **Output Layer**: 5 nodes (classification categories)
- **Network Topology**: 13000-25-5-5

## Files Structure

### Core Implementation
- `NLayer.java` - Main neural network implementation
- `NLayer.class` - Compiled Java bytecode

### Image Preprocessing
- `WOOHOO.py` - Python script for image preprocessing
  - Converts images to grayscale
  - Removes background using AI-based segmentation
  - Centers and crops images to fixed size
  - Outputs 120×100 pixel images as BMP format

### Configuration Files
- `ImageProcessingConfig.txt` - Main network configuration
- `config2N1.txt` - Alternative 2-1-1 network configuration
- `config3N3.txt` - Alternative 2-1-1-3 network configuration

### Training Data
- `{1-6}-{1-5}.txt` - Preprocessed image data files (13,000 normalized pixel values per file)
- `2activations.txt`, `3activations.txt` - Test case configurations for smaller networks
- `weights.txt` - Saved neural network weights

## Configuration Parameters

| Parameter | Description |
|-----------|-------------|
| `netConfig` | Network architecture (e.g., "13000-25-5-5") |
| `numTestCases` | Number of training/test images |
| `errorThreshold` | Training stops when error drops below this value |
| `maxIters` | Maximum training iterations |
| `lambda` | Learning rate for backpropagation |
| `willTrain` | Enable/disable training mode |
| `useRandomWeights` | Initialize weights randomly |
| `useLoadedWeights` | Load weights from file |
| `willSaveWeights` | Save weights after training |

## Usage

### Training a New Model
1. Configure network parameters in `ImageProcessingConfig.txt`
2. Set `willTrain = true`
3. Run: `java NLayer [config_file]`

### Running Inference
1. Set `willTrain = false` in configuration
2. Ensure weights are loaded (`useLoadedWeights = true`)
3. Run: `java NLayer [config_file]`

### Image Preprocessing
```python
python WOOHOO.py
```
Processes `one v6.JPG` and outputs normalized pixel data suitable for neural network input.

## Data Format

- **Image Data**: Each `{n}-{m}.txt` file contains 13,000 space-separated normalized pixel values (0.0-1.0)
- **Target Outputs**: One-hot encoded classifications in configuration file
- **Weights**: Space-separated floating-point values organized by layer

## Output Classification

Based on the target outputs in the configuration, the network classifies images into 5 categories:
- Category 1: `targetOutput_*_0 = 1.0`
- Category 2: `targetOutput_*_1 = 1.0`  
- Category 3: `targetOutput_*_2 = 1.0`
- Category 4: `targetOutput_*_3 = 1.0`
- Category 5: `targetOutput_*_4 = 1.0`

## Dependencies

### Java
- JDK 8 or higher
- Standard Java libraries (Properties, IO)

### Python
- NumPy
- PIL (Python Imaging Library)
- SciPy
- rembg (for background removal)

## Author
Anish Jain (Version 4.30.24)
