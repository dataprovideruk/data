# DataProvider Ltd - Datasets & API Documentation

## Overview
Welcome to **DataProvider Ltd**, your trusted source for high-quality datasets and API services. Our data solutions provide **verified geographical, historical, organizational, and people data** for researchers, analysts, and developers.

## Available Datasets
We offer structured datasets extracted from **reliable sources like Wikidata, OpenStreetMap, and historical archives.** Data Dictionary (https://github.com/dataprovideruk/data/blob/main/data-dictionary.md)

- **Geographical Data:** Locations, coordinates, and environmental attributes.
- **Historical Data:** Past events, cultural significance, and timelines.
- **Organizational Data:** Business records, institutions, and NGOs.
- **People Data:** Verified profiles with biographical details.

---

## 🔗 API Access

### **Base URL:**  
```
https://dataprovider.uk/api/
```

Our APIs allow you to extract verified entities, validate dates, and retrieve enriched metadata from **text, images, and PDFs.**  

🔹 **[Postman API Collection](https://github.com/dataprovideruk/data/blob/main/postman-api-collection.json)** - Import this into Postman to test APIs.

---

## 📌 API Endpoints

### **1️⃣ Extract Entities**
- **Endpoint:** `POST /api/extract_entities`
- **Description:** Extracts and verifies **People, Organizations, and Locations** from text, images, and PDFs.
- **Request Format (JSON)**:
  ```json
  { "text": "Sample text containing entities." }
  ```
- **Response:**
  ```json
  {
    "Verified People": ["John Doe", "Jane Smith"],
    "Verified Organizations": ["Google", "Microsoft"],
    "Verified Locations": ["London", "New York"]
  }
  ```
- **File Upload Support**: JPG, PNG, and PDF (`multipart/form-data`)

---

### **2️⃣ Extract Dates**
- **Endpoint:** `POST /api/extract_dates`
- **Description:** Extracts and validates dates from input data.
- **Request Format:**
  ```json
  { "text": "The event took place on July 4, 1776." }
  ```
- **Response:**
  ```json
  {
    "valid_dates": [
      { "date": "1776", "reason": "Recognized as a historical date" }
    ]
  }
  ```
- **Error Response:**  
  ```json
  { "error": "Invalid input. 'text' key is required." }
  ```

---

### **3️⃣ Enrich Organization Data**
- **Endpoint:** `POST /api/organisation_info`
- **Description:** Fetches additional metadata about an organization.
- **Request Format:**
  ```json
  { "query": "Organisation Name" }
  ```
- **Response:**
  ```json
  {
    "organization": {
      "name": "Organization Name",
      "metadata": {
        "linked_companies": ["Company A", "Company B"],
        "institutions": ["Institution X", "Institution Y"],
        "additional_info": "Other relevant metadata details"
      }
    }
  }
  ```
- **Error Response:**  
  ```json
  { "error": "Invalid input. 'query' key is required." }
  ```

---

### **4️⃣ Person Information**
- **Endpoint:** `POST /api/person_info`
- **Description:** Retrieves enriched details for an individual.
- **Request Format:**
  ```json
  { "query": "Person Name here" }
  ```
- **Response:**
  ```json
  {
    "person_info": {
      "name": "Person Name here",
      "details": "Enriched information such as summaries, dates, and additional metadata"
    }
  }
  ```

---

### **5️⃣ Extract Context**
- **Endpoint:** `POST /api/extract-context`
- **Description:** Extracts metadata, entities, and dates from a given **webpage URL**.
- **Request Format:**
  ```json
  { "url": "https://example.com/sample-page" }
  ```
- **Response:**
  ```json
  {
    "url": "https://example.com",
    "Title": "Example Title",
    "Heading": "Example H1 Heading",
    "People": {},
    "Organizations": {
      "Example Corp": { "context": "Industry-leading company.", "source": "text" }
    },
    "Dates": {
      "2024": { "context": "Event date: 2024", "source": "text" }
    },
    "Emails": ["info@example.com"],
    "Phone Numbers": ["+1 234-567-8901"],
    "Metadata": {
      "Canonical URL": "https://example.com",
      "Meta Description": "This is an example page.",
      "External Links": ["https://external-site.com"],
      "Internal Links": ["/about", "/contact"],
      "Headings": { "H1": ["Example H1 Heading"], "H2": ["Subheading"] }
    }
  }
  ```

---

## 📌 API Authentication
Currently, our APIs **do not require authentication** for basic access. However, for **high-volume usage or premium datasets**, please contact us for an API key.

---

## 📩 Contact & Support
For inquiries and partnerships, reach us at:  
📧 **Email:** [admin@dataprovider.uk](mailto:admin@dataprovider.uk)  
🌐 **Website:** [DataProvider Ltd](https://dataprovider.uk)  

---

### 🚀 **Contribute**
We welcome contributions! If you find issues or have suggestions for improvements, feel free to **submit a pull request**.

