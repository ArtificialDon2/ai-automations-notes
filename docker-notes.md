# Docker Basics

## What’s the difference between IDEs and Docker?
- **IDE (e.g. VS Code, PyCharm):** Your *writing desk* where you draft your work.  
  - You write and test code.  
  - It relies on your computer’s setup (installed runtimes, libraries, etc.).  
  - Doesn’t guarantee code will run the same way elsewhere.  

- **Docker:** Lets you package your app and everything it needs into a container.
  - Think of a container as a mini-computer with its own filesystem, runtime, and libraries. 
  - Runs the same way on any computer with Docker installed.  
  - Used in real-world professional environments to avoid “works on my machine” problems.  

---

## Core Concepts
- **Container** – a lightweight, isolated environment where your app runs.  
- **Image** – a blueprint for containers, like a frozen recipe.  
- **Dockerfile** – the recipe instructions for building an image.  
- **Build** – turning a Dockerfile into an image.  
- **Run** – starting a container from an image.    
- **Network** – how containers communicate with each other or the outside world.
