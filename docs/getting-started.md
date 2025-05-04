# Getting Started with AI-igen
==========================

Welcome to AI-igen, an open-source image generator project. This guide will walk you through the process of setting up and running the project.

## Prerequisites and System Requirements
--------------------------------------

### Operating System

*   **Windows**: Windows 10 or later (64-bit)
*   **macOS**: macOS High Sierra or later
*   **Linux**: Any Linux distribution with Python 3.8 or later installed

### Software Dependencies

*   **Python 3.8 or later**
*   **Docker** (optional, but recommended for efficient use)

### Additional Requirements

*   **A compatible image format** (e.g., PNG, JPEG)
*   **A suitable device with a compatible display** (for rendering generated images)

## Installation Instructions
------------------------

### Step 1: Clone the Repository

Open your terminal or command prompt and navigate to the directory where you want to clone the repository. Then, run the following command:

```bash
git clone https://github.com/charudatta10/ai-igen.git
```

### Step 2: Navigate to the Project Directory

Once the cloning process is complete, navigate to the project directory using the `cd` command:

```bash
cd ai-igen
```

### Step 3: Install Dependencies (if not already done)

Run the following commands to install dependencies:

```bash
pip install -r requirements.txt
docker-compose up -d
```

The first command installs the required packages specified in `requirements.txt`. The second command builds and starts a Docker container for efficient use.

### Step 4: Configure Environment Variables

Edit the `.env` file to set your environment variables:

```bash
nano .env
```

Add your preferred image dimensions (e.g., width, height) and any other required settings as key-value pairs. Save the changes.

## Basic Configuration
---------------------

### Update the `main.py` File

Open the `main.py` file in a text editor (like `nano` or `vim`) to configure the project:

```python
import uvicorn

# Set your image dimensions here
image_width = 512
image_height = 512

if __name__ == "__main__":
    uvicorn.run("tasks:app", host="0.0.0.0", port=8000, debug=True)
```

Replace `tasks:app` with the actual name of your app.

### Run the Project

Finally, run the project using the following command:

```bash
invoke
```

## Running a Simple Example
-------------------------

To generate an image, run the following command in the project directory:

```bash
python main.py --width 512 --height 512 --output output_image.png
```

This will create a new image file named `output_image.png` with dimensions specified in the `.env` file.

## Where to Go Next
-------------------

Congratulations on setting up and running AI-igen for the first time! You can explore more features by checking out our:

*   [Documentation](README.md): Learn about the project's architecture, usage, and best practices.
*   [GitHub Repository](https://github.com/charudatta10/ai-igen): Browse through open-source code and issues.

Join our community to discuss AI-igen with other users, share ideas, and contribute to its growth!