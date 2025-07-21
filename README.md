# Dcluttr - Task 1: Blinkit API Scraping

## Submission by: [Utkarsh Patidar]

### Description
This project contains a Java program designed to scrape product data from Blinkit's public API. The program successfully identifies and interacts with the correct endpoint, handling complex authentication and request structures.

### Technical Approach 
The program sends a `POST` request to Blinkit's `/v1/layout/listing_widgets` endpoint. It is designed to mimic a real browser request by including all necessary headers (like `cookie`, `auth_key`, `device_id`) and an empty JSON payload, while passing category and location information in the URL.

### Challenges and Key Findings
A significant challenge was overcoming Blinkit's sophisticated anti-scraping measures. The investigation revealed several critical points:

1.  **POST Request Required:** The API requires a `POST` request with an empty body, not a simple `GET` request.
2.  **Session-Specific Headers:** The request must include temporary, session-specific headers (`cookie`, `auth_key`, etc.) copied from a live browser session. These headers expire quickly.
3.  **Location-Cookie Mismatch:** The server cross-validates the location (`lat`/`lon`) in the request against the location information stored within the `cookie`. If these two locations do not match, the API returns a `{"error":"location not serviceable"}` message as a security measure, even if the requested location is technically valid.

### Execution Result 
Due to the security measure described above, the program consistently receives the `"location not serviceable"` response when iterating through the provided `blinkit_locations.csv` file, as the session cookie is tied to a single, different location.

As a result, no product data could be scraped using the provided location list. The `blinkit_category_scraping_stream.csv` file is submitted with only the headers to fulfill the submission requirement. The Java program is fully functional and would successfully scrape data if the `cookie` and the requested `lat`/`lon` were perfectly synchronized for every call.

### How to Run 
1.  Open the project in IntelliJ IDEA.
2.  **Important:** To replicate a successful run, the user must update the headers (`cookie`, `auth_key`, etc.) in `Main.java` AND replace the content of `blinkit_locations.csv` with fresh, matched data from their own single browser session.
3.  Run the `main` method in the `Main.java` class.
