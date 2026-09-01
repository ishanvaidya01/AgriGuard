<div align="center">
  
# AgriGuard

**The Next-Generation AI-Powered Crop Health Assistant**

[![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](#)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)](https://www.tensorflow.org/)
[![AI Powered](https://img.shields.io/badge/AI-Powered-purple.svg?style=for-the-badge)](#)

*AgriGuard is an intelligent, real-time crop disease diagnostic platform that goes beyond simple image classification. It uses deep learning and regional intelligence to help farmers identify crop diseases early and provides actionable, customized organic and inorganic remedies.*

[Features](#features) • [Why AgriGuard?](#how-agriguard-beats-the-competition) • [Architecture](#architecture) • [Deployment Status](#deployment-status) • [Getting Started](#getting-started)

**🏆 IEEE Promptathon Hackathon - 3rd Prize (Team 916X3)**

</div>

---

## Features

- **Instant AI-Powered Diagnosis**: Upload a photo of a crop leaf and our TensorFlow-powered AI instantly predicts the disease with granular confidence scoring.
- **Regional Disease Mapping**: An interactive Leaflet map that shows the top 5 most common diseases specific to your exact state or region, keeping farmers aware of local outbreaks.
- **Tailored Remedy Engine**: For every detected disease, the platform provides step-by-step actionable advice, dynamically split into **🌱 Organic** (bio-inputs) and **🧪 Inorganic** (chemical) approaches.
- **Market Connections (Kisaan Mart)**: Seamlessly connects farmers to direct-buyer marketplaces to reduce middlemen and maximize agricultural profits.
- **Localized Smart Ads**: Embedded marketplace features that dynamically suggest relevant farming tools and fertilizers based on the user's region and diagnosed diseases.
- **Premium Glassmorphism UI**: A vibrant, animated, and highly responsive user interface designed to feel modern, approachable, and fast on both mobile and desktop devices.

---

## How AgriGuard Beats the Competition

While there are other farming apps available, they often fail to bridge the gap between complex AI and actionable, localized advice for the everyday farmer. Here's how AgriGuard stands out:

| Feature | AgriGuard | Generic Farming Apps |
|---------|-----------|----------------------|
| **Core Metric** | Deep Learning Diagnosis + Regional Context | Basic Image Search |
| **Remedy Approach** | Dual-track (Organic & Inorganic steps) | Generic chemical advice |
| **User Experience** | Glassmorphic, highly animated, zero-friction | Cluttered, ad-heavy, complex |
| **Local Awareness** | Interactive state-by-state disease tracking | One-size-fits-all database |
| **Market Integration**| Direct link to Kisaan Mart & tool shops | No economic integration |

**In short:** Other apps just tell you what's wrong. **AgriGuard acts as your intelligent agronomist and business partner.**

---

## Architecture

AgriGuard is built on a clean, decoupled architecture designed for blazing-fast AI inference and seamless user experiences.

### Decoupled AI Engine
At the heart of the platform is the **FastAPI Prediction Engine**. Instead of bloat on the frontend, the UI is incredibly lightweight. The heavy lifting is offloaded to a Python backend running a highly optimized TensorFlow model trained on the PlantVillage dataset.
- **The true state of the crop is evaluated in milliseconds.**
- This allows for incredibly fast scaling and the ability to update the AI model on the fly without ever pushing frontend updates.

### Tech Stack
* **Frontend:**
  * **Vanilla JavaScript & HTML5** for lightning-fast, dependency-free UI rendering.
  * **Vanilla CSS** utilizing a premium design system (Glassmorphism, rich gradients, dynamic particle backgrounds, and fluid micro-animations).
  * **Leaflet.js** for interactive geographic mapping.
* **Backend:**
  * **FastAPI** for robust, high-performance API endpoints and handling image uploads asynchronously.
  * **TensorFlow & Keras** for deep learning image preprocessing and classification.
  * **Uvicorn** as the lightning-fast ASGI web server.

---

## Deployment Status

**AgriGuard is currently configured for local development and edge deployment.**

The frontend is fully statically generated and can be deployed easily on free static tiers (like GitHub Pages, Netlify, or Vercel). The backend AI engine is currently deployed on Render (`viridion-s.onrender.com`), but the repository includes all the necessary code to run the backend locally on your own machine. 

To experience the full power of the AI model with zero latency, local execution of the backend is recommended!

---

## Getting Started

### Prerequisites
- Python (3.11+)
- Node.js / HTTP Server (Optional, for serving frontend locally)

### 1. Clone the repository
```bash
git clone https://github.com/ishanvaidya01/AgriGuard.git
cd AgriGuard
```

### 2. Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# Start the FastAPI development server
python main.py
```
*The API will be available at `http://localhost:8000`*

### 3. Frontend Setup
Because the frontend is built with Vanilla JS, no build step is required! 
Simply serve the `frontend/` directory using any static file server:
```bash
# Using Python's built-in server
cd frontend
python -m http.server 3000
```
*Then open `http://localhost:3000` in your browser.*

---

## UI/UX Design Philosophy

AgriGuard was designed with a premium, vibrant aesthetic tailored to feel fresh and organic. 
- We completely avoid generic enterprise colors, utilizing curated green/teal HSL palettes and sleek glassmorphism.
- Every interaction—from uploading a leaf to viewing the results—is accompanied by subtle micro-animations to ensure the application feels responsive, dynamic, and alive.

---

## 👥 Team 916X3
- **Ishan Vaidya** - Frontend & Backend Integration
- *(IEEE Promptathon Hackathon)*

---

<div align="center">
  <i>Built with passion for the future of sustainable farming.</i>
</div>
