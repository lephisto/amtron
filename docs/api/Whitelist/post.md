**Set Whitelist**
----

Saves new entries to Whitelist (aKa. _Authorize new RFID Tags_).

* **URL**

  /Whitelist?DevKey=:devKey&Pin=:pin
  
* **Method:**
  
  `POST`
  
*  **URL Params**

   **Required:**
 
   `devKey=[integer]`
   `pin=[integer] /* PIN2 */`              
* **Headers**
  **Required:**
  `Accept: 'application/json'`
  `Content-Type: 'application/json; charset=utf-8'`


* **Success Response:**
  
  * **Code:** 200 <br />
  
* **Error Response:**

  * **Code:** 403 FORBIDDEN

* **Notes:**

    * Set headers properly, otherwise the Webserver will `500`


