# FlipVision - Intelligent E-Commerce Platform with AI Vision

> An AI-powered e-commerce platform that detects product brand names, assesses freshness levels, and extracts expiry dates from product images using advanced computer vision techniques.

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/)
[![Django Version](https://img.shields.io/badge/django-4.2%2B-brightgreen)](https://www.djangoproject.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-Active-success)]()

---

## Overview

**FlipVision** is an intelligent e-commerce platform developed for the **Flipkart Grid 6.0 Robotic Challenge**. It combines a robust Django backend with advanced machine learning models to provide:

- 🏷️ **Brand Detection** - Automatically identify product brands and details from images using YOLO and PaddleOCR
- 🍃 **Freshness Assessment** - Evaluate the freshness of unpacked products using computer vision
- 📅 **Expiry Date Detection** - Extract and verify expiry dates from product packaging
- 🛒 **Complete E-Commerce Platform** - Full customer, seller, and admin functionality
- 📊 **Multi-Role Support** - Dedicated workflows for customers, sellers, and administrators

This solution is designed to enhance product quality assurance and inventory management in modern e-commerce operations.

---

## Key Features

### 🏷️ Brand Name Detection
- **YOLO-based Text Region Detection** - Identifies areas containing product information
- **PaddleOCR Integration** - Extracts brand names, product types, and flavor details
- **Accurate Text Recognition** - Supports multiple languages and formats

### 🍃 Freshness Detection
- **Unpacked Product Analysis** - Specialized model for fruits and vegetables
- **Visual Quality Assessment** - Uses YOLO and ResNet50 for accuracy
- **Freshness Scoring** - Provides numerical freshness levels
- **Shelf-Life Estimation** - Predicts remaining product lifespan

### 📅 Expiry Date Detection
- **Region Detection** - YOLO identifies date areas on packaging
- **OCR Extraction** - Faster R-CNN with ResNet45 for text capture
- **Date Parsing** - Regex-based validation for DMY/MDY formats
- **Verification** - Ensures date accuracy and feasibility

### 🛒 E-Commerce Features
- **Product Management** - Add, edit, and manage product listings
- **Shopping Cart** - Full cart functionality with quantity management
- **Order Management** - Complete order lifecycle from creation to delivery
- **Wishlist** - Save favorite items for later
- **Seller Verification** - Admin approval system for sellers
- **Order Tracking** - Real-time order status updates

---

## 🛠️ Technology Stack

### Backend
- **Django 4.2** - Web framework for building scalable applications
- **Django ORM** - Object-Relational Mapping for database operations
- **Django REST** - RESTful API endpoints
- **SQLite 3** - Database (production: PostgreSQL recommended)

### Machine Learning & Computer Vision
- **YOLO** - Object detection for product regions and text areas
- **PaddleOCR** - Optical Character Recognition (multilingual support)
- **ResNet50** - Deep learning for freshness classification
- **Faster R-CNN** - Advanced text detection
- **OpenCV** - Image processing and manipulation

### Frontend
- **HTML5/CSS3** - Semantic markup and responsive styling
- **JavaScript** - Client-side interactivity
- **Django Templates** - Server-side template rendering
- **Bootstrap** - Responsive design framework (optional)

### Development Tools
- **Git/GitHub** - Version control and collaboration
- **Roboflow** - Dataset annotation and labeling
- **LabelImg** - Image annotation tool
- **Jupyter Notebooks** - Model training and experimentation

### Other
- **NumPy/Pandas** - Data manipulation and analysis
- **Matplotlib/Seaborn** - Data visualization
- **Regex** - Pattern matching for date extraction
- **Logging** - Application-level logging

---

## 📁 Project Structure

```
FlipVision/
├── README.md                      # This file
├── .gitignore                     # Git ignore rules
├── .env.example                   # Example environment variables
├── manage.py                      # Django management script
│
├── flipkart/                      # Main Django project
│   ├── settings.py               # Project configuration
│   ├── urls.py                   # URL routing
│   ├── asgi.py                   # ASGI configuration
│   └── wsgi.py                   # WSGI configuration
│
├── flipkart_app/                 # Main application
│   ├── models.py                 # Database models
│   ├── views.py                  # View logic
│   ├── urls.py                   # App URL routing
│   ├── admin.py                  # Django admin configuration
│   │
│   ├── ml_models/                # Pre-trained ML models
│   │   ├── brand_type_flavour.pt # Brand detection model
│   │   ├── category.pt           # Category classification model
│   │   └── FRESH_MASS.pt         # Freshness detection model
│   │
│   └── templates/                # HTML templates
│       ├── flipkart_app/         # Customer templates
│       │   ├── home.html
│       │   ├── product_list.html
│       │   ├── product_detail.html
│       │   ├── cart.html
│       │   ├── checkout.html
│       │   ├── order_history.html
│       │   └── ...
│       │
│       └── Seller/               # Seller templates
│           ├── seller_dashboard.html
│           ├── add_product.html
│           ├── manage_products.html
│           ├── detect_items.html
│           ├── detect_freshness.html
│           └── ...
│
└── db.sqlite3                     # SQLite database (local development)
```

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Git
- Virtual environment (recommended)

### Step 1: Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/FlipVision.git
cd FlipVision
```

### Step 2: Create and Activate Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables
Copy the `.env.example` file and create a `.env` file:
```bash
cp .env.example .env
```

Edit `.env` with your configuration (see [Configuration](#configuration) section).

### Step 5: Apply Database Migrations
```bash
python manage.py migrate
```

### Step 6: Create Superuser (Admin Account)
```bash
python manage.py createsuperuser
```

### Step 7: Run Development Server
```bash
python manage.py runserver
```

Access the application at: `http://127.0.0.1:8000/`

Admin panel: `http://127.0.0.1:8000/admin/`

---

## 📖 Usage

### For Customers

1. **Register Account**
   - Visit the registration page
   - Select "Customer" role
   - Fill in personal and address details

2. **Browse Products**
   - Browse products by category
   - Use search and filters
   - View detailed product information

3. **Shopping**
   - Add items to cart
   - Save items to wishlist
   - Proceed to checkout

4. **Orders**
   - Place orders
   - Track order status
   - View order history

### For Sellers

1. **Register Account**
   - Create seller account
   - Submit business details (GST, bank info)
   - Wait for admin verification

2. **Manage Products**
   - Add new products with images
   - Edit product details
   - Manage inventory

3. **Validate Products**
   - Use freshness detection for unpacked items
   - Use brand detection for packed items
   - Verify product quality before shipment

4. **Handle Orders**
   - View incoming orders
   - Update order status
   - Manage shipments

### For Administrators

1. **User Management**
   - Verify seller registrations
   - Manage user accounts
   - Handle disputes

2. **Platform Oversight**
   - Monitor orders
   - Review analytics
   - Manage categories and settings

---

## 📸 Screenshots

### Homepage
![Homepage](https://github.com/user-attachments/assets/03d03268-71d8-4a5e-9807-1c17f589d58c)

### Brand Detection Example
| Detection Input | Results |
|---|---|
| ![Brand Detection 1](https://github.com/user-attachments/assets/6df98ea6-4a09-4672-a9dc-d99799552058) | ![Brand Detection 2](https://github.com/user-attachments/assets/59bf5606-d2ef-41c5-b42b-1777d28bca5c) |
| ![Brand Detection 3](https://github.com/user-attachments/assets/398dd991-0e50-4b94-ae57-3674cc1428ec) | ![Brand Detection 4](https://github.com/user-attachments/assets/dbe6691a-3bc5-4c1c-9d26-fe97cf93bb5e) |

### Freshness Detection Example
| Fresh Sample | Aging Sample |
|---|---|
| ![Fresh 1](https://github.com/user-attachments/assets/d9c67007-20ea-42c1-831c-a81685f6657c) | ![Fresh 2](https://github.com/user-attachments/assets/5b9d393e-ade0-4c52-8936-d0184fe46fc0) |
| ![Fresh 3](https://github.com/user-attachments/assets/b49d3c11-95fc-4347-8c41-2b61dc87bdb0) | ![Fresh 4](https://github.com/user-attachments/assets/721bdd63-3908-40fd-b24e-3cd352129120) |

### Expiry Date Detection Example
| Packed Product 1 | Packed Product 2 |
|---|---|
| ![Expiry 1](https://github.com/user-attachments/assets/a8d600f4-4a67-4142-9940-6bac7a59ff69) | ![Expiry 2](https://github.com/user-attachments/assets/11743aaa-9984-4138-96ed-522f782d7ad1) |
| ![Expiry 3](https://github.com/user-attachments/assets/c17cae87-83f8-4e49-b776-9fd9524aaa63) | ![Expiry 4](https://github.com/user-attachments/assets/80931929-f4c2-4d2a-a03b-4b186c024538) |

### System Workflow
![Workflow Diagram](https://github.com/user-attachments/assets/734c9b15-8121-46c9-9145-9d0c26a124cd)

---

## 🎓 Model Training Data

### Brand Detection Model
- **Classes**: Chips, Biscuits, Chocolates
- **Framework**: YOLO (You Only Look Once)
- **Dataset Source**: Roboflow annotations

### Freshness Classification Model
- **Classes**: Apple, Carrot, Banana, Cucumber, Orange
- **Framework**: ResNet50
- **Metrics**: High accuracy on agricultural products

### Expiry Date Detection
- **Input**: Product packaging images
- **Output**: Extracted and verified expiry dates
- **Supported Formats**: DMY, MDY

---

## 👥 Team

**FlipVision** was developed as part of the **Flipkart Grid 6.0 Robotic Challenge**. The project demonstrates advanced computer vision techniques combined with a complete e-commerce platform.

---