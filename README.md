# Dcluttr - Task 1: Blinkit API Scraping

**Submitted by:** Utkarsh Patidar

---

## Overview

This project is a Java program that tries to collect product data from the Blinkit app's internal API. It sends the same kind of request a browser would send and saves the results in a `.csv` file.

---

## How It Works

- The program sends a **POST request** to this URL:  https://blinkit.com/v1/layout/listing_widgets


markdown
Copy
Edit

- It adds:
- **Location** (latitude, longitude)
- **Category IDs**
- It uses **real browser headers** like:
- `auth_key`
- `cookie`
- `device_id`
- `session_uuid`
- The program reads:
- `blinkit_locations.csv`: List of places
- `blinkit_categories.csv`: Product categories
- It saves the result in:  
**`blinkit_category_scraping_stream.csv`**

---

## Challenges Faced

1. **Needs POST, not GET:**  
 The API only works with `POST`, not regular `GET`.

2. **Browser Headers Required:**  
 You must copy headers from your browser (they change every few hours).

3. **Location Mismatch Issue (Main Problem):**  
 If the `latitude/longitude` in the API does **not match** the location in the cookie, the API will respond with:  {"error":"location not serviceable"}


yaml
Copy
Edit


---

## 📊 Result

- The program worked correctly.
- But **no products were returned** because the locations in the file did not match the cookie location.
- So, the file `blinkit_category_scraping_stream.csv` contains **only the column names**.

---

## How to Run It

### Requirements:

- Java 11+
- IntelliJ IDEA (or any Java IDE)
- Internet

### Steps:

1. Open the project in IntelliJ.
2. Go to `Main.java`.
3. Update these headers:
- `auth_key`
- `cookie`
- `device_id`
- `session_uuid`  
_(Copy from your browser using Developer Tools > Network tab on blinkit.com)_
4. In `blinkit_locations.csv`, use the **same location** as in the cookie.
5. Run the `main()` method.
6. The results will be saved in `blinkit_category_scraping_stream.csv`.

---

## Files Included

- `Main.java`: Java code
- `blinkit_locations.csv`: Location list
- `blinkit_categories.csv`: Categories
- `blinkit_category_scraping_stream.csv`: Final output (with headers only)
- `README.md`: This file

---

## About Me

- **Name:** Utkarsh Patidar  
- **Email:** utkarshpatidar011@gmail.com

---

## Note

The code will work and fetch real product data **only if**:
- Your cookie and the location in the API match.

---

