# High-Dimensional Image Search using R-Tree Indexing

A scalable content-based image retrieval system that combines **Vision Transformer embeddings** with a custom-built **high-dimensional R-Tree index** for efficient nearest-neighbor image search.

Developed as part of the DBMS Laboratory under Prof. Pabitra Mitra at IIT Kharagpur, this project focuses on fast semantic image retrieval using learned vector embeddings and spatial indexing techniques.

The system:
- extracts semantic image embeddings using **DINOv2**
- indexes embeddings using a custom **R-Tree implementation in C++**
- exposes the backend to Python using **PyBind11**
- provides an interactive GUI for image querying and retrieval

---

# Features

## Semantic Image Retrieval
- Uses **DINOv2-small Vision Transformer** embeddings
- Learns compact **25-dimensional feature vectors**
- Preserves semantic similarity between visually related images

## High-Dimensional R-Tree Index
- Custom R-Tree implementation in **C++**
- Supports:
  - insertion
  - nearest-neighbor search
  - k-NN traversal
  - bounding region optimization
- Optimized node split heuristics for high-dimensional vectors

## Fast Query Processing
- Efficient indexing for large embedding datasets
- Lower query latency compared to:
  - SQLite indexing
  - Extendible hashing approaches

## Python Integration
- Exposed C++ backend to Python using **PyBind11**
- Enables seamless interoperability between:
  - high-performance indexing layer
  - Python ML pipeline

## Interactive GUI
- Tkinter-based image search interface
- Allows:
  - image querying
  - nearest-neighbor visualization
  - responsive retrieval interaction

---

# Tech Stack

- **C++17** — Core R-Tree implementation
- **Python** — ML pipeline and interface
- **PyBind11** — Python bindings for C++ backend
- **PyTorch** — DINOv2 embedding extraction
- **Tkinter** — GUI interface
- **STL-10 Dataset** — Image dataset for evaluation

---

# System Architecture

```text
Input Images
      ↓
DINOv2 Embedding Extraction
      ↓
25-Dimensional Feature Vectors
      ↓
Custom R-Tree Index (C++)
      ↓
k-NN Search Traversal
      ↓
Python Interface via PyBind11
      ↓
Tkinter GUI Visualization
```

---

# Project Structure

```text
DBMS_LAB_Image_Search_Using_Rtree/
│
├── interface_rtree.py        # GUI interface
├── rtree.cpp                 # R-Tree implementation
├── Makefile_rtree            # Build configuration
├── requirements.txt          # Python dependencies
├── stl10_binary/             # STL-10 dataset
├── embeddings/               # Extracted feature vectors
├── queries/                  # Query image samples
└── README.md
```

---

# Dataset

The project uses the **STL-10 dataset** for image retrieval experiments.

Dataset source:
http://ai.stanford.edu/~acoates/stl10/

---

# Core Concepts Implemented

## Feature Extraction
- Vision Transformer embeddings using DINOv2
- Semantic representation learning
- Embedding preprocessing pipeline

## Spatial Indexing
- High-dimensional R-Tree construction
- Bounding rectangle optimization
- Node split heuristics
- Nearest-neighbor traversal

## Database Systems Concepts
- Index structures
- Query optimization
- Throughput and latency benchmarking
- High-dimensional indexing tradeoffs

---

# Performance Evaluation

The system was benchmarked against:
- SQLite indexing
- Extendible hashing

Results demonstrated:
- lower query latency
- improved retrieval throughput
- scalable nearest-neighbor search performance

especially for larger embedding datasets.

---

# Setup and Installation

## 1. Create Virtual Environment (Optional)

```bash
python -m venv venv
```

### Linux/macOS

```bash
source venv/bin/activate
```

### Windows

```bash
venv\Scripts\activate
```

---

## 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

---

## 3. Install C++ Build Tools

### Linux/macOS

```bash
sudo apt install build-essential
```

### Windows

Install:
- MSVC
or
- mingw-w64

---

## 4. Download STL-10 Dataset

```bash
mkdir -p stl10_binary

wget http://ai.stanford.edu/~acoates/stl10/stl10_binary.tar.gz

tar -xzvf stl10_binary.tar.gz -C stl10_binary
```

Windows users can download and extract manually.

---

# Build Instructions

## Build the R-Tree Executable

```bash
make -f Makefile_rtree
```

---

## Build Python Extension using PyBind11

```bash
c++ -O3 -Wall -shared -std=c++17 -fPIC \
$(python3 -m pybind11 --includes) \
rtree.cpp -o rtree.so \
$(python3-config --ldflags)
```

---

# Usage

## Extract Embeddings

```bash
./rtree_image_search extract stl10_binary
```

---

## Build the R-Tree Index

```bash
./rtree_image_search build stl10_binary
```

---

## Query using R-Tree

```bash
./rtree_image_search query stl10_binary
```

---

## Launch GUI Interface

```bash
python interface_rtree.py
```

---

# Sample Workflow

1. Load STL-10 dataset
2. Generate DINOv2 embeddings
3. Build high-dimensional R-Tree index
4. Submit image query
5. Retrieve nearest semantic neighbors
6. Display results in GUI

---

# Learning Outcomes

This project provided practical experience with:
- high-dimensional indexing
- database access methods
- nearest-neighbor search
- vector embeddings
- Vision Transformers
- ML systems integration
- C++/Python interoperability
- query performance optimization

---

# Acknowledgements

Developed as part of the DBMS Laboratory under Prof. Pabitra Mitra at IIT Kharagpur.
