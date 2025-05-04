# AI Image Generator (ai-igen) Technical Reference Document

## Table of Contents

1. [API Documentation](#api-documentation)
2. [Configuration Options](#configuration-options)
3. [Command-Line Interface Reference](#command-line-interface-reference)
4. [File Formats and Data Structures](#file-formats-and-data-structures)
5. [Architectural Overview](#architectural-overview)

## API Documentation

The ai-igen project provides a RESTful API for generating images using stable diffusion.

### Endpoints

#### 1. Generate Image
*   **URL:** `/generate`
*   **Method:** `POST`
*   **Request Body:**
    *   `input_image`: The input image to generate from.
    *   `prompt`: The text prompt for the generated image.
    *   `num_images`: The number of images to generate.

#### 2. List Images
*   **URL:** `/images`
*   **Method:** `GET`

### Request/Response Examples

**Generate Image**
```bash
curl -X POST \
  http://localhost:8080/generate \
  -H 'Content-Type: application/json' \
  -d '{"input_image": "/path/to/input/image.jpg", "prompt": "A sunny day at the beach"}'
```

Response:
```json
{
    "image_urls": [
        "http://localhost:8080/images/1.jpg",
        "http://localhost:8080/images/2.jpg"
    ]
}
```

**List Images**
```bash
curl -X GET \
  http://localhost:8080/images
```

Response:
```json
{
    "image_urls": [
        "http://localhost:8080/images/1.jpg",
        "http://localhost:8080/images/2.jpg"
    ]
}
```

## Configuration Options

The ai-igen project uses a configuration file (`pyproject.toml`) to store settings.

### Environment Variables

*   `AI_IMAGE_WIDTH`: The width of the generated images.
*   `AI_IMAGE_HEIGHT`: The height of the generated images.
*   `AI_PROMPT`: The text prompt for the generated images.

### Command-Line Interface Reference

The ai-igen project provides a command-line interface using the `invoke` tool.

#### 1. Generate Image
```bash
invoke generate --input-image /path/to/input/image.jpg --prompt "A sunny day at the beach"
```

#### 2. List Images
```bash
invoke images
```

## File Formats and Data Structures

The ai-igen project uses the following file formats:

### Input/Output Image Files

*   JPEG (`.jpg`)
*   PNG (`.png`)

### Configuration File

*   PyTorch TOML configuration file (`pyproject.toml`)

### Model Output

*   Images in JPEG or PNG format.

## Architectural Overview

The ai-igen project uses a modular architecture to handle different tasks:

1.  **Input Image Preprocessing**: The input image is preprocessed using the `uv` library.
2.  **Text Prompt Encoding**: The text prompt is encoded using the `invoke` tool.
3.  **Image Generation**: The generated images are produced by the stable diffusion model.

The architecture can be broken down into the following components:

*   **`main.py`**: The main entry point for the ai-igen project, responsible for handling user input and generating images.
*   **`tasks.py`**: A module containing utility functions for tasks such as image preprocessing and prompt encoding.
*   **`Dockerfile`**: A Dockerfile for building a containerized version of the ai-igen project.